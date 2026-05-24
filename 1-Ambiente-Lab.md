---
[⬅️ Voltar para a Introdução Geral](./README.md)

# 🖥️ Módulo 1: Arquitetura e Montagem do Ambiente de Laboratório

🎯 Objetivo do Módulo: Estabelecer uma infraestrutura de laboratório local segregada e protegida contra movimentação lateral, utilizando uma Rede NAT Customizada. Este design garante o isolamento lógico da rede física local (produção), permitindo que ferramentas de simulação de ataque (Kali Linux) e coleta de telemetria (Windows + Sysmon) operem de forma segura, mantendo o acesso controlado à internet apenas para a atualização de pacotes e assinaturas.

## 🗺️ Topologia Lógica e Perímetro de Rede

O diagrama abaixo ilustra o fluxo de comunicação estabelecido dentro do hipervisor. Ambas as máquinas compartilham o mesmo switch virtual isolado, permitindo o tráfego de ataques e coletas internas sem expor o sistema hospedeiro:

[ VM Atacante: Kali Linux ] ──(Rede NAT: Lab-Secure)──> [ VM Alvo: Windows + Sysmon ]

---


## 🗺️ Passo a Passo do Laboratório

* **[🚀 Passo 01]** **Conectando a Rede Isolada (`Lab-Secure`)**
  * *Como configurar o Switch Virtual no VirtualBox e o print da placa de rede.*
<br>

* **[🪟 Passo 02]** **Configurando a Vítima (Windows 11 + Sysmon)**
  * *Instalação prática do Sysmon via linha de comando e validação dos logs no Event Viewer.*
<br>

* **[🐧 Passo 03]** **Preparando o Atacante (Kali Linux)**
  * *Colocando o Kali na mesma rede e deixando as ferramentas de ataque prontas.*
<br>

* **[🔍 Passo 04]** **Validação Final (O Teste de Conectividade)**
  * *Print do comando `ipconfig` / `ifconfig` e o teste de ping entre as duas máquinas.*

---
