# 0️⃣ Introdução Geral e Escopo do Projeto

# 📑 Resumo do Laboratório

Este projeto transforma uma estação Windows em um ambiente de visibilidade defensiva e engenharia de detecção, integrando o **Sysmon** a um SIEM baseado na **Elastic Stack**.

O foco central é documentar o ciclo de vida da detecção, desde a configuração e o ajuste fino das regras do Sysmon até a correlação de telemetria no SIEM. Este processo permite não apenas identificar técnicas de ataque, mas também realizar a triagem de falsos positivos, diferenciando atividades legítimas de ações maliciosas.

---

## Fluxo Operacional
O laboratório abrange todo o ciclo de vida de um incidente:

* **Coleta:** Implementação e configuração do Sysmon para captura de eventos críticos.
* **Emulação:** Execução de ataques controlados para geração de telemetria baseada em ameaças reais.
* **Normalização:** Aplicação de regras de filtragem e estruturação (XML para Sysmon e YAML para Elastic).
* **Correlação:** Desenvolvimento de detecções utilizando **KQL** (*Kibana Query Language*) e baseando-se no framework **Sigma**.
* **Triagem:** Análise de alertas e refinamento contínuo das detecções para redução de falsos positivos.

---

## Objetivo
O objetivo final é demonstrar como a engenharia de detecção, apoiada pelo poder de busca e análise da **Elastic Stack**, reduz pontos cegos e aumenta a resiliência da defesa em ambientes corporativos.



---
### Tecnologias Utilizadas
- **Windows:** Sistema operacional alvo.
- **Sysmon:** Ferramenta de monitoramento de atividades do sistema.
- **Elastic Stack:** SIEM para armazenamento, busca e visualização (Elasticsearch + Kibana).
- **Sigma:** Framework para padronização de regras de detecção.


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
