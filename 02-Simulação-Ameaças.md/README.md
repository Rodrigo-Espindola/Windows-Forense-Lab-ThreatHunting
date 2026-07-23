[⬅️ Voltar para o Menu Principal](../README.md)

# ⚔️ 02 — Simulação de Ameaças (Emulação de Adversários)

> Este módulo documenta a reprodução controlada de técnicas do **MITRE ATT&CK** em ambientes **Windows**, com foco na geração de telemetria para **DFIR**, **Threat Hunting** e **Detection Engineering**.

---

## Visão Geral

Esta pasta reúne as **simulações de técnicas adversárias** utilizadas neste laboratório de **Windows DFIR, Threat Hunting e Detection Engineering**. Cada simulação reproduz, de forma controlada e isolada, comportamentos associados a técnicas reais observadas em ambientes Windows, com o objetivo de **gerar telemetria representativa de comportamentos reais** para estudo, análise e desenvolvimento de detecções.

O propósito deste módulo **não é ensinar como atacar**, mas sim:

- Compreender o comportamento técnico de cada técnica de ataque.
- Observar e interpretar a telemetria gerada (Sysmon e Elastic Stack).
- Identificar os artefatos forenses deixados no sistema.
- Praticar Threat Hunting sobre dados reais de execução.
- Servir como base para a criação de regras de detecção nos módulos seguintes.

> 💡 Este módulo é a **fonte de telemetria** de todo o repositório. Sem ele, os módulos de Engenharia de Detecção, Regras de Alerta e Dashboards não teriam dados reais para análise.

O foco central é sempre o **comportamento**, não a ferramenta.

Um adversário pode trocar o payload, a linguagem utilizada ou a técnica de ofuscação, mas para persistir, escalar privilégios, movimentar-se lateralmente ou exfiltrar dados ele inevitavelmente precisa interagir com mecanismos do sistema operacional. É justamente esse comportamento que produz telemetria consistente e permite construir detecções robustas, capazes de identificar a técnica empregada, e não apenas uma ferramenta específica.

> 💡 **Detectar uma assinatura identifica uma ferramenta. Detectar um comportamento identifica uma técnica.**

---

## Estrutura

As simulações são organizadas seguindo o **MITRE ATT&CK**, principal framework utilizado para classificar comportamentos observados em ataques reais.

Cada técnica é documentada individualmente e organizada conforme sua tática correspondente.

```text
02-Simulacao-Ameacas/
│
├── README.md
│
├── 01-Initial-Access/
├── 02-Execution/
├── 03-Persistence/
├── 04-Privilege-Escalation/
├── 05-Defense-Evasion/
├── 06-Credential-Access/
├── 07-Discovery/
├── 08-Lateral-Movement/
├── 09-Collection/
├── 10-Command-and-Control/
├── 11-Exfiltration/
├── 12-Impact/
│
└── 13-Cenarios-Completos/
```

O laboratório é desenvolvido de forma **incremental**. Novas técnicas são adicionadas conforme são estudadas e documentadas, refletindo a evolução natural do projeto.

> 💡 O repositório representa um processo contínuo de aprendizado. Cada técnica adicionada corresponde a um estudo efetivamente realizado.

---

## Como Cada Técnica é Documentada

Todas as simulações seguem um modelo padronizado de documentação.

```text
MITRE ATT&CK
      │
      ▼
Descrição da Técnica
      │
      ▼
Comportamento Simulado
      │
      ▼
Telemetria Gerada
      │
      ▼
Threat Hunting
      │
      ▼
Detecção
      │
      ▼
Mitigações
      │
      ▼
Referências
```

Essa padronização facilita a comparação entre técnicas, aumenta a consistência do laboratório e torna cada documento uma referência reutilizável para estudos futuros.

---

## Papel no Laboratório

Este módulo representa o início de todo o ciclo de detecção desenvolvido neste projeto.

```text
02 — Simulação de Ameaças
          │
          ▼
03 — Engenharia de Detecção e Análise
          │
          ▼
04 — Regras de Detecção e Alertas
          │
          ▼
05 — Dashboards de Triagem e Métricas
```

As simulações executadas aqui geram a telemetria utilizada pelos demais módulos para investigação, criação de regras, validação de hipóteses de Threat Hunting e desenvolvimento de dashboards.

---

## Escopo Defensivo

Todo o conteúdo desta pasta é desenvolvido sob a ótica de **Blue Team**.

- As simulações reproduzem comportamentos observáveis, e não ferramentas ofensivas completas.
- O foco está na geração e análise de telemetria.
- Técnicas sensíveis são tratadas apenas de forma conceitual, sem disponibilização de ferramentas funcionais.
- Todo o laboratório é executado em ambiente local, isolado e controlado.

> ⚠️ Este **não** é um repositório de Red Team ofensivo. O objetivo exclusivo deste módulo é apoiar estudos de DFIR, Threat Hunting, Detection Engineering e Resposta a Incidentes.

---

## Nota Ética

> Todo o conteúdo desta pasta destina-se exclusivamente a fins educacionais, pesquisa defensiva e desenvolvimento de capacidades de detecção. As simulações são executadas apenas em ambiente controlado, sem interação com sistemas de terceiros. O objetivo final é compreender o comportamento das técnicas para melhorar a capacidade de detecção e investigação, nunca sua utilização ofensiva.
