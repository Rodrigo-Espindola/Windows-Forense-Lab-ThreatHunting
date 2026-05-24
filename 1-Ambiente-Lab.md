---
[⬅️ Voltar para a Introdução Geral](./README.md)

# 🖥️ Módulo 1: Arquitetura e Montagem do Ambiente de Laboratório

🎯 **Objetivo do Módulo: Estabelecer uma infraestrutura de laboratório local segregada e protegida contra movimentação lateral, utilizando uma Rede NAT Customizada. Este design garante o isolamento lógico da rede física local (produção), permitindo que ferramentas de simulação de ataque (Kali Linux) e coleta de telemetria (Windows + Sysmon) operem de forma segura, mantendo o acesso controlado à internet apenas para a atualização de pacotes e assinaturas.

## 🗺️ Topologia Lógica e Perímetro de Rede

O diagrama abaixo ilustra o fluxo de comunicação estabelecido dentro do hipervisor. Ambas as máquinas compartilham o mesmo switch virtual isolado, permitindo o tráfego de ataques e coletas internas sem expor o sistema hospedeiro:

[ VM Atacante: Kali Linux ] ──(Rede NAT: Lab-Secure)──> [ VM Alvo: Windows + Sysmon ]

---

## 🗺️ Índice do Módulo

1. [🌐 1. Arquitetura e Topologia da Rede Isolada](#-1-arquitetura-e-topologia-da-rede-isolada)
   * 1.1 Configuração do Switch Virtual (Rede NAT Customizada)
   * 1.2 Regras de Isolamento e Mitigação de Riscos (Análise de Segurança)
2. [🐧 2. Provisionamento da Máquina do Atacante (Kali Linux)](#-2-provisionamento-da-maquina-do-atacante-kali-linux)
   * 2.1 Especificações de Hardware e Vinculação de Rede
3. [🪟 3. Provisionamento da Máquina Alvo (Windows 11)](#-3-provisionamento-da-maquina-alvo-windows-11)
   * 3.1 Especificações de Hardware e Vinculação de Rede
4. [🔍 4. Validação Prática do Perímetro e Conectividade](#-4-validacao-pratica-do-perimetro-e-conectividade)
   * 4.1 Teste de Endereçamento IP (DHCP)
   * 4.2 Teste de Conectividade Interna (Kali 🤝 Windows)
