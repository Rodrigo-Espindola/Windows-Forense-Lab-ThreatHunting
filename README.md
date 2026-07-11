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

## Ferramentas
- **Windows:** Sistema operacional alvo.
- **Sysmon:** Ferramenta de monitoramento de atividades do sistema.
- **Elastic Stack:** SIEM para armazenamento, busca e visualização (Elasticsearch + Kibana).
- **Sigma:** Framework para padronização de regras de detecção.


<br><br>
---
<br><br>

## Índice

| Módulo | Caminho |
| :--- | :--- |
| ⚔️ **1. Simulação de Ameaças** | 01-Simulacao-Ameacas/ → scripts e documentação da emulação de adversários |
| 🔍 **2. Engenharia de Detecção** | 02-Engenharia-Deteccao/ → análise de telemetria e baseline |
| 🚨 **3. Regras de Detecção** | 03-Regras-Deteccao/ → arquivos EQL/KQL/Sigma |
| 📈 **4. Dashboards** | 04-Dashboards/ → prints e modelos de Kibana |
| 🛡️ **5. Conclusões** | 05-Conclusoes/ → relatório de lições aprendidas |

---
