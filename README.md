# 0️⃣ Introdução Geral e Escopo do Projeto

# 🛡️ Windows DFIR, Threat Hunting & Detection Engineering Lab

## 📑 Apresentação do Laboratório

Este repositório documenta a construção de um laboratório prático de **Blue Team**, voltado para **Windows DFIR**, **Threat Hunting** e **Engenharia de Detecção**.

O ambiente foi desenvolvido para transformar uma estação Windows em uma fonte de telemetria defensiva, integrando o **Sysmon** a um SIEM baseado na **Elastic Stack**.

O projeto não representa um curso ou apenas uma coleção de anotações. Ele documenta um fluxo técnico completo de laboratório, no qual comportamentos potencialmente maliciosos são executados de maneira controlada, coletados pelo Sysmon, analisados no Elastic SIEM e posteriormente transformados em hipóteses e regras de detecção.

Cada etapa procura reproduzir atividades realizadas por profissionais de **SOC**, **Threat Hunting**, **DFIR** e **Detection Engineering**.

---

## 🔎 Propósito do Projeto

O propósito deste laboratório é demonstrar, de maneira prática e documentada, como diferentes técnicas de ataque podem ser observadas a partir da telemetria de um endpoint Windows.

O projeto acompanha o processo desde a geração dos eventos até a criação e validação das detecções:

```text
Simulação de ameaças
        ↓
Geração de telemetria no Windows
        ↓
Coleta de eventos pelo Sysmon
        ↓
Ingestão dos dados no Elastic SIEM
        ↓
Análise e Threat Hunting
        ↓
Engenharia de detecção
        ↓
Criação e validação de regras
        ↓
Visualização em dashboards
        ↓
Documentação das lições aprendidas
```
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

| Módulo | O que você vai aprender aqui? |
| :--- | :--- |
| 🖥️ **[1. Ambiente SIEM](./01-Ambiente-SIEM.md)** | Criação e configuração do ambiente SIEM. |
| ⚔️ **[2. Simulação de Ameaças](./02-Simulaçao-Ameaças.md)** | Scripts e documentação da emulação de adversários. |
| 🔍 **[3. Engenharia de Detecção](./03-Engenharia-Detecçao.md)** | Análise de telemetria e baseline. |
| 🚨 **[4. Regras de Detecção](./04-Regras-Detecçao.md)** | Arquivos EQL/KQL/Sigma. |
| 📈 **[5. Dashboards](./05-Dashboards.md)** | Prints e modelos de Kibana. |
| 🛡️ **[6. Conclusões](./06-Conclusoes.md)** | Relatório de lições aprendidas. |


---
