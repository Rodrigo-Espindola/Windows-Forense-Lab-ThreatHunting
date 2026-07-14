[⬅️ Voltar para o Menu Principal](./README.md)

# 🛡️ Detection Lab: Engenharia de Logs com Docker (Elastic Stack), Sysmon e Elastic Agent Standalone



## Visão Geral



Este repositório documenta um **ambiente laboratorial de estudos** projetado para simular comportamentos maliciosos no host, capturar essa telemetria em nível de sistema operacional e centralizá-la em uma stack de análise para prática de **SIEM (Security Information and Event Management)**.



O propósito é didático: reproduzir, em escala reduzida, o fluxo de trabalho real de um **SOC (Security Operations Center)** — desde a execução de scripts que simulam técnicas ofensivas até a ingestão da telemetria correspondente em uma stack de análise.



O foco não está em ferramentas prontas ou dashboards genéricos, mas em **entender e controlar manualmente cada camada do pipeline de dados**, o que é essencial para quem deseja atuar em **Engenharia de Detecção (Detection Engineering)** e Blue Team.



> 💡 **Nota de propósito:** Este ambiente prioriza a compreensão da arquitetura sobre a automação. Cada etapa — da simulação no host ao armazenamento no Elasticsearch — é configurada manualmente para expor a lógica interna do processo de coleta.



---



## Arquitetura do Ambiente



O ecossistema é sustentado por três pilares que se complementam em papéis distintos, porém interdependentes:



- **Docker (Elasticsearch + Kibana)** → Camada de **armazenamento e visualização**, executando localmente apenas os serviços da stack Elastic, isolados do sistema operacional hospedeiro.

- **Scripts de simulação no host** → Camada de **geração de comportamento**, responsável por executar ações que reproduzem técnicas maliciosas diretamente no Windows.

- **Sysmon** → Camada de **instrumentação do sistema operacional**, responsável por capturar, em riqueza de detalhes, os eventos gerados por essas simulações.

- **Elastic Agent (Standalone)** → Camada de **coleta e transporte**, responsável por ler os logs gerados pelo Sysmon e enviá-los diretamente ao Elasticsearch.



Importante destacar a separação de responsabilidades neste laboratório:



- O **Docker não simula nada** — ele apenas hospeda o Elasticsearch e o Kibana, ou seja, o destino final e a interface de análise dos dados.

- A **simulação ocorre no próprio host Windows**, por meio de scripts de teste que reproduzem situações maliciosas (execução de processos suspeitos, conexões de rede, manipulação de arquivos, etc.).



Cadeia lógica do ambiente:



```

[Simulação] Scripts no Host → [Captura] Sysmon → [Coleta/Envio] Elastic Agent → [Armazenamento/Análise] Elasticsearch + Kibana (Docker)

```



---



## O Papel do Docker (Elasticsearch + Kibana)

Neste cenário, o Docker é utilizado exclusivamente como **camada de infraestrutura da stack de análise**, e não como gerador de comportamento.

- **Isolamento dos serviços**: Elasticsearch e Kibana rodam em containers separados, evitando instalação direta desses serviços no sistema operacional host.
- **Ambiente de estudo descartável**: os containers podem ser recriados a qualquer momento, permitindo resetar a base de dados de estudo sem afetar o host.
- **Destino final da telemetria**: o Elasticsearch (dentro do Docker) recebe os eventos enviados pelo Elastic Agent, e o Kibana é utilizado como **interface de consulta e visualização** desses dados.
- **Simplicidade operacional**: por rodar apenas dois serviços (sem Logstash, sem Fleet Server), o ambiente Docker fica leve e focado unicamente em armazenamento e análise.

> 💡 Aqui o Docker representa o **"laboratório de análise"**, enquanto a geração de eventos acontece inteiramente fora dele, no host.

### Explicação do Código
Este arquivo configura o Elastic Agent em modo Standalone, definindo manualmente a coleta de eventos do Sysmon no Windows e enviando-os diretamente para o Elasticsearch rodando no Docker, sem intermediários ou gerenciamento via Fleet Server.

```yaml
version: '3.8'

services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:8.12.0
    container_name: elasticsearch
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
      - xpack.security.enrollment.enabled=false
      - xpack.security.http.ssl.enabled=false
      - xpack.security.transport.ssl.enabled=false
      - "ES_JAVA_OPTS=-Xms1g -Xmx1g" # Limita a RAM para não travar o PC
    ports:
      - 9200:9200
    volumes:
      - es_data_clean:/usr/share/elasticsearch/data

  kibana:
    image: docker.elastic.co/kibana/kibana:8.12.0
    container_name: kibana
    environment:
      - ELASTICSEARCH_HOSTS=http://elasticsearch:9200
      - XPACK_SECURITY_ENABLED=false
    ports:
      - 5601:5601
    depends_on:
      - elasticsearch

volumes:
  es_data_clean: # Mudamos o nome do volume para garantir que ele nasça do zero
```

---



## A Simulação de Cenários Maliciosos (Scripts no Host)



Diferente de uma abordagem que isola comportamento em containers, este laboratório executa as simulações **diretamente no sistema operacional Windows**, através de scripts de teste.



- **Scripts de teste controlados**: pequenos scripts (ex: PowerShell, batch, ou binários de teste) são executados no host para reproduzir **táticas e técnicas conhecidas** (ex: criação de processos suspeitos, conexões de rede incomuns, manipulação de arquivos sensíveis).

- **Ambiente real de captura**: por rodar no host — e não em um container isolado — o comportamento gerado é capturado exatamente como ocorreria em uma máquina de usuário real, aumentando o realismo da telemetria.

- **Mapeamento a frameworks de referência**: os cenários simulados podem ser alinhados a técnicas do **MITRE ATT&CK**, permitindo posteriormente validar se as regras de detecção construídas no Kibana identificam corretamente o comportamento simulado.

- **Repetibilidade controlada**: os scripts podem ser reexecutados a qualquer momento para gerar novos eventos de teste, sem qualquer dependência do ambiente Docker.



> 💡 **Nota de segurança:** por rodar no host, esses scripts devem ser executados em um ambiente de estudo isolado (VM ou máquina dedicada), nunca em um ambiente de produção ou pessoal sensível.



---



## O Papel do Sysmon



O **System Monitor (Sysmon)**, parte do Sysinternals Suite da Microsoft, é a camada de **instrumentação profunda** do sistema operacional. Ele opera como um serviço e driver de kernel, registrando eventos com um nível de detalhe muito superior ao Visualizador de Eventos padrão do Windows.



Principais categorias de eventos capturados durante a execução dos scripts de simulação:



- **Criação de processos** (Event ID 1): linha de comando completa, hash do binário, processo pai/filho.

- **Conexões de rede** (Event ID 3): IP de origem/destino, porta e processo responsável pela conexão.

- **Criação e modificação de arquivos** (Event ID 11): rastreamento de artefatos criados em disco pelos scripts de teste.

- **Alterações de registro** (Event ID 12/13/14): modificações em chaves críticas do Windows Registry.

- **Carregamento de drivers e DLLs** (Event ID 6/7): visibilidade sobre módulos carregados em processos.



Essa riqueza de contexto é o que transforma a execução de um script simples em um **conjunto de indicadores de comportamento (IOA/IOC)** com valor real para prática de detecção.



> 💡 O Sysmon é o "sensor" do ambiente: ele é quem efetivamente traduz "o script foi executado" em "evento estruturado e analisável".



---



## A Lógica de Coleta e Envio: Elastic Agent Standalone

Esta é a camada que conecta a captura de eventos no host à stack de análise rodando no Docker — e o ponto onde este laboratório se diferencia por adotar uma abordagem **manual e não gerenciada**.

### O que significa operar em modo Standalone

- O Elastic Agent pode operar de duas formas: **gerenciado** (via Fleet Server/Kibana, com políticas centralizadas) ou **Standalone** (configurado localmente, sem dependência de um servidor de gerenciamento).  
- No modo Standalone, **toda a lógica de coleta é definida manualmente** pelo engenheiro, através de um arquivo de configuração local — não há orquestração remota nem políticas aplicadas via interface gráfica.

### A abordagem prática adotada neste ambiente

- **Download direto do agente**: o pacote `.zip` do Elastic Agent é obtido diretamente do site oficial e extraído no host Windows, sem uso de instaladores gerenciados ou registro prévio em um Fleet Server.  
- **Configuração manual via `elastic-agent.yml`**: o arquivo de configuração é editado à mão para definir explicitamente as fontes de dados — neste caso, instruindo o agente a ler o **canal de logs do Sysmon** no Visualizador de Eventos do Windows (`Microsoft-Windows-Sysmon/Operational`).  
- **Envio direto para o Elasticsearch (rodando no Docker)**: o output do agente é apontado diretamente para a **porta 9200**, endereço exposto pelo container do Elasticsearch, eliminando intermediários como Logstash ou Fleet Server nesta etapa do pipeline.  
- **Execução como serviço nativo do Windows**: após configurado, o agente é instalado e registrado como um **serviço do sistema operacional**, garantindo que a coleta seja persistente, resiliente a reinicializações e operando em segundo plano de forma nativa — mesmo estando fora do Docker.  

> 💡 **Por que Standalone?** Essa escolha é deliberada e didática: operar sem Fleet Server força o entendimento completo da estrutura de inputs, outputs e autenticação do Elastic Agent — conhecimento que se perde quando tudo é abstraído por uma interface de gerenciamento centralizada. É a diferença entre "clicar em um botão" e "saber exatamente o que aquele botão faria".


### Explicação do Código
Este trecho configura o **Elastic Agent** em modo Standalone:  

```yaml
agent.logging.level: info

outputs:
  default:
    type: elasticsearch
    hosts: ["http://localhost:9200"]
    ssl.verification_mode: none

inputs:
  - type: winlog
    id: sysmon-logs
    data_stream.namespace: default
    use_output: default
    streams:
      - data_stream:
          dataset: windows.sysmon_operational
        name: Microsoft-Windows-Sysmon/Operational

```

---

Scripts de teste (host, simulação maliciosa)

      ↓

Sysmon (telemetria detalhada do host)

      ↓

Elastic Agent Standalone (leitura + envio manual)

      ↓

Elasticsearch :9200 (Docker) → indexação

      ↓

Kibana (Docker) → análise / detecção / threat hunting

```



Essa cadeia reproduz, em pequena escala, o mesmo princípio encontrado em ambientes corporativos de monitoramento: **gerar, capturar, transportar e analisar** — só que aqui, cada etapa é compreendida em profundidade, e não apenas consumida como "caixa-preta".



---



## Objetivo Profissional e Conclusão



Dominar a arquitetura **Standalone** do Elastic Agent, aliada à execução controlada de scripts de simulação e ao uso do Docker exclusivamente como stack de análise (Elasticsearch + Kibana), representa um diferencial competitivo real para profissionais que buscam atuar em:



- **Detection Engineering** — criação e validação de regras de detecção baseadas em telemetria real gerada por simulações controladas.

- **Blue Team / SOC** — compreensão profunda de como os dados chegam até as ferramentas de análise, essencial para troubleshooting e tuning de pipelines.

- **Threat Hunting** — capacidade de rastrear a origem e a integridade dos dados consumidos durante investigações, desde o script executado até o evento indexado.



> 💡 Entender a "engenharia por trás do dado" — como ele é gerado no host, capturado pelo Sysmon, transportado pelo Elastic Agent e armazenado na stack rodando em Docker — é o que separa um analista que apenas consome alertas de um profissional capaz de **construir, auditar e confiar** na própria infraestrutura de detecção.



Este repositório representa, portanto, mais do que um ambiente de testes: é uma demonstração prática de competência técnica na construção de um pipeline de SIEM do zero, com controle total sobre cada camada da arquitetura.
