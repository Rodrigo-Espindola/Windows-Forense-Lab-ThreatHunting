# 0️⃣ Introdução Geral e Escopo do Projeto

🎯 **Em resumo:** Este projeto transforma uma máquina Windows comum em um ambiente de auditoria avançada. Combinando o Sysmon e o Event Viewer, eu demonstro como emular técnicas de ataque e identificar os indicadores de comprometimento (IoCs) que as ameaças deixam ativas no sistema operacional.

---
## 📈 A Lógica do Laboratório (Passo a Passo)

Para entender este projeto de forma clara e linear, siga a sequência natural do fluxo de trabalho abaixo:
---

> ⚙️ **01. O Cenário Inicial**
> * **Foco:** Montagem e isolamento da rede "Lab-Secure" no VirtualBox.
> * **Ação:** Instalação do Sysmon via linha de comando e preparação do Event Viewer para auditoria de logs.
> * **Resultado** Ambiente seguro e monitorado, pronto para capturar a telemetria dos ataques do Kali Linux.

---

> 🔍 **02. A Ação Defensiva**
> * **Foco:** Investigação minuciosa de incidentes em tempo real e caça a malwares presentes.
> * *Resultado:* Detecção inicial de ameaças e artefatos.

---

> ⏳ **03. A Reconstrução do Ataque**
> * **Foco:** Correlação e agrupamento de eventos para montar a linha do tempo do incidente.
> * *Resultado:* Compreensão total do comportamento do artefato malicioso.

---

> 🧹 **04. A Lapidação da Análise**
> * **Foco:** Triagem fina e filtragem para separar ruídos do sistema operacional de ameaças reais.
> * *Resultado:* Redução drástica de falsos positivos na análise.

---

> 💥 **05. A Resposta ao Incidente**
> * **Foco:** Aplicação de novas políticas rígidas de mitigação para neutralizar o malware descoberto.
> * *Resultado:* Contenção da ameaça e endurecimento pós-crise.

---

> 🚨 **06. A Proatividade**
> * **Foco:** Automação de gatilhos e alertas para detecção imediata de novos comportamentos.
> * *Resultado:* Monitoramento contínuo e inteligente estabelecido.

---


## 🗺️ Índice de Navegação Direta

Caso queira ir direto a um ponto específico, utilize o menu abaixo. Cada tópico resolve uma dor específica da cibersegurança defensiva:

| Módulo | O que você vai aprender aqui? |
| :--- | :--- |
| 🖥️ **[1. Ambiente-Lab](./1-Ambiente-Lab.md)** | Criação e configuração do ambiente de trabalho. |
| ⚙️ **[2. Instalacao-Sysmon-Configuracoes](./2-Instalacao-Sysmon-Configuracoes.md)** | Configuração de logs e endurecimento (hardening). |
| 🔍 **[3. Pratica-Investigando-Malwares-Antigos-Forca-Bruta](./3-Pratica-Investigando-Malwares-Antigos-Forca-Bruta.md)** | Detecção inicial e análise das ameaças presentes. |
| ⏳ **[4. Linha-Tempo-Evidencias](./4-Linha-Tempo-Evidencias.md)** | Agrupamento e correlação de eventos para montar a história do ataque. |
| 🧹 **[5. Triagem-Falsos-Positivos](./5-Triagem-Falsos-Positivos.md)** | Filtro e refinamento para separar o que é ruído do Windows e o que é ameaça real. |
| 🛡️ **[6. Mitigacao-Hardening-Pos-Incidente](./6-Mitigacao-Hardening-Pos-Incidente.md)** | Aplicação de novas políticas no Windows para neutralizar o malware detectado. |
| 🚨 **[7. Automatizacao-Alertas](./7-Automatizacao-Alertas.md)** | Criação de gatilhos para que o sistema avise automaticamente sobre novos comportamentos maliciosos. |

---
