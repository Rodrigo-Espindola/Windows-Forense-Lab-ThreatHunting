---
[⬅️ Voltar para a Introdução Geral](./README.md)

# 🖥️ Módulo 1: Arquitetura e Montagem do Ambiente de Laboratório

🎯 **Objetivo do Módulo:** Estabelecer uma infraestrutura local controlada, segura e 100% isolada da rede física (produção), composta por uma máquina de ataque (Kali Linux) e uma máquina de auditoria/vítima (Windows 11). Este ambiente servirá de base para a geração, coleta e análise de telemetria defensiva através do Sysmon e do Windows Event Viewer.

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
