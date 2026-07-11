# 0️⃣ Introdução Geral e Escopo do Projeto

# 📑 Resumo do Laboratório
Resumo do Projeto: Este projeto transforma uma estação Windows em um ambiente de visibilidade defensiva e engenharia de detecção, integrando o Sysmon a um SIEM baseado na Elastic Stack.

O foco central é documentar o ciclo de vida da detecção, desde a configuração e o ajuste das regras do Sysmon até a correlação de telemetria no SIEM. Este processo permite não apenas identificar técnicas de ataque, mas também realizar a triagem de falsos positivos, diferenciando atividades legítimas de ações maliciosas.

O laboratório abrange todo o fluxo operacional:

Coleta: Implementação e configuração do Sysmon.

Emulação: Execução de ataques controlados para geração de telemetria.

Normalização: Aplicação de regras (XML para Sysmon e YAML para Elastic).

Correlação: Desenvolvimento de detecções utilizando KQL e baseando-se no framework Sigma.

Triagem: Análise de alertas e refinamento de detecções.

O objetivo final é demonstrar como a engenharia de detecção, apoiada pelo poder de busca e análise da Elastic Stack, reduz pontos cegos e aumenta a resiliência da defesa em ambientes corporativos.
<br><br>
---
<br><br>

## 🗺️ Índice

| Módulo | O que você vai aprender aqui? |
| :--- | :--- |
| 🖥️ **[1. Ambiente-Lab](./1-Ambiente-Lab.md)** | Criação do ambiente.
| 🔍 **[2. Prática-Investigando](./2-Prática-Investigando-Malwares-antigos-Força-Bruta.md)** | Detecção inicial e análise das ameaças presentes e  e Filtro e refinamento para separar o que é ruído do Windows e o que é ameaça real. |
| 🚨 **[3. Automatizacao-Alertas](./3-Automatização-Alertas.md)** | Criação de gatilhos para que o sistema avise automaticamente sobre novos comportamentos maliciosos. |

---
