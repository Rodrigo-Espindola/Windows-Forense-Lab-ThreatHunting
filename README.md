# 0️⃣ Introdução Geral e Escopo do Projeto

# 📑 Resumo do Laboratório

Em resumo: Este projeto transforma uma máquina Windows comum em um ambiente de **visibilidade defensiva e análise de detecção**.  
O foco é documentar e demonstrar as **configurações e regras aplicadas no Sysmon**, registrando como cada etapa foi construída e validada no laboratório.  

A telemetria inicial capturada pelo Sysmon é então enviada para o **SIEM**, onde regras de correlação são aplicadas para identificar comportamentos suspeitos.  
Esse processo permite não apenas detectar técnicas de ataque, mas também realizar a **triagem de falsos positivos**, diferenciando atividades legítimas de ações maliciosas.  

Assim, o laboratório cobre todo o ciclo:  
- **Coleta cirúrgica com Sysmon**  
- **Emulação controlada de ataques**  
- **Construção de regras XML**  
- **Correlação no SIEM (SPL/KQL/Sigma)**  
- **Triagem de alertas e falsos positivos**  

O objetivo final é criar um ambiente prático que demonstre como a engenharia de detecção pode reduzir pontos cegos e aumentar a confiabilidade da defesa.

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
