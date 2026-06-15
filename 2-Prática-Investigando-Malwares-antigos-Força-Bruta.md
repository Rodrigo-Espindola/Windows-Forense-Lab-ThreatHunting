[⬅️ Voltar para o Menu Principal](./README.md)

# 📑 Engenharia de Detecção e Telemetria Inicial


### 📌 Objetivo do Tópico

Este tópico documenta de forma prática as configurações e regras aplicadas no Sysmon, detalhando como cada etapa foi construída e implementada no laboratório. O foco é registrar o processo de criação, ajuste e validação das regras XML, mostrando passo a passo como cada configuração foi aplicada para capturar telemetria relevante.

### 🔄 Ciclo de Desenvolvimento

1. **Conceito da Técnica**  
   Compreensão teórica do objetivo do atacante e da ação que precisa ser monitorada.  
   - Estudo da técnica de ataque.  
   - Identificação do comportamento esperado no sistema.  
   - Definição do ponto cego que precisa ser evitado.  

2. **Emulação do Ataque**  
   Execução controlada de scripts ou comandos no laboratório para gerar telemetria.  
   - Simulação prática da técnica em ambiente seguro.  
   - Registro dos eventos gerados pelo Sysmon.  
   - Validação de que a telemetria está sendo capturada corretamente.  

3. **Regra de Detecção no Sysmon**  
   Construção do filtro XML customizado e documentação de como cada configuração foi aplicada.  
   - Criação da regra XML específica para o evento.  
   - Ajuste fino para reduzir ruído e falsos positivos.  
   - Registro no laboratório de como a configuração foi implementada.  



<br><br>

## Vivendo da Terra (Abuso de Ferramentas Legítimas).
Uso de ferramentas já presentes no sistema (como PowerShell, WMI, etc.) para realizar ações maliciosas sem levantar suspeitas.


# 🛠️ Metodologia de Desenvolvimento de Detecção

---

### 🧠 1. A Hipótese

> *"Se um atacante tentar a técnica X..."*

* **Seu foco:** Definir o comportamento do ataque e, se possível, citar a ID técnica do framework MITRE ATT&CK (ex: `T1547.001 - Registry Run Keys`). Isso dá autoridade internacional para o seu texto.

<br>

### 💻 2. A Simulação do Ataque 🆕 *(O que faltava)*

> *"Para simular o ataque no laboratório, eu executei o seguinte comando no terminal..."*

* **Por que acrescentar:** O leitor precisa saber o que gerou o log. Se você pular direto da hipótese para o XML, o leitor não sabe qual comando exato disparou o gatilho. Coloque o comando exato em bloco de código (ex: `reg add ...` ou `powershell -enc ...`).

<br>

### ⚙️ 3. A Configuração

> *"Eu usei este trecho de XML para fazer o Sysmon capturar essa ação..."*

* **Seu foco:** Colocar o bloco de código XML limpo, explicando brevemente por que escolheu aquela tag (ex: `<TargetObject>`) e aquela condição (ex: `contains`).

<br>

### 📸 4. A Prova Real

> *"Aqui está o print do log provando que o comando foi pego."*

* **Seu foco:** Mostrar o print do Event Viewer. Uma dica de ouro aqui: destaque no print (ou no texto) os campos cruciais que confirmam o sucesso, como o **EventID**, a linha de comando (**CommandLine**) e o usuário que executou.

<br>

### 🛡️ 5. O Desafio do Falso-Positivo / Mitigação 🆕 *(O diferencial)*

> *"Em um ambiente real, o programa legítimo Y também faz isso. Para evitar alarmes falsos, o analista deve..."*

* **Por que acrescentar:** Na vida real, o maior inimigo do Sysmon não é o hacker, é o falso-positivo. Se você criar uma regra que pega o hacker, mas gera 5.000 alertas falsos por dia por causa do Google Chrome ou do Windows Update, a regra é descartada. Mostrar como refinar a regra para ignorar o que é legítimo separa o júnior do sênior.





---

## Process Injection e Process Hollowing (Injeção de Código) 
Técnicas que inserem código malicioso em processos legítimos para mascarar a execução e evitar detecção.

<br><br>
<br><br>
<br><br>
<br><br>
<br><br>
<br><br>





---

## Acesso à Memória do LSASS (Roubo de Credenciais)
Extração de credenciais diretamente da memória do processo **LSASS**, permitindo acesso indevido a contas e sistemas.

<br><br>
<br><br>
<br><br>
<br><br>
<br><br>
<br><br>





---

## Persistência via Registro ou Tarefas Agendadas
Criação de entradas no **Registro do Windows** ou uso de **tarefas agendadas** para garantir que o código malicioso seja executado mesmo após reinicializações.

<br><br>
<br><br>
<br><br>
<br><br>
<br><br>
<br><br>





---

## Conexões de Rede Suspeitas (Comando e Controle / C2)
Estabelecimento de canais de comunicação entre o sistema comprometido e o servidor do atacante para envio de comandos e exfiltração de dados.
