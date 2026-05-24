---
[⬅️ Voltar para a Introdução Geral](./README.md)

# 🖥️ Módulo 1: Arquitetura e Montagem do Ambiente de Laboratório

🎯 Objetivo do Módulo: Estabelecer uma infraestrutura de laboratório local segregada e protegida contra movimentação lateral, utilizando uma Rede NAT Customizada. Este design garante o isolamento lógico da rede física local (produção), permitindo que ferramentas de simulação de ataque (Kali Linux) e coleta de telemetria (Windows + Sysmon) operem de forma segura, mantendo o acesso controlado à internet apenas para a atualização de pacotes e assinaturas.

## 🗺️ Topologia Lógica e Perímetro de Rede

O diagrama abaixo ilustra o fluxo de comunicação estabelecido dentro do hipervisor. Ambas as máquinas compartilham o mesmo switch virtual isolado, permitindo o tráfego de ataques e coletas internas sem expor o sistema hospedeiro:

[ VM Atacante: Kali Linux ] ──(Rede NAT: Lab-Secure)──> [ VM Alvo: Windows + Sysmon ]

---


## 🗺️ Passo a Passo do Laboratório

 📈 Fluxo do Laboratório (Clique para ir direto ao Passo)

* **[🚀 Passo 01](#passo1)** **Conectando a Rede Isolada (`Lab-Secure`)**
  * _Como configurar o Switch Virtual no VirtualBox e o print da placa de rede._

* **[🪟 Passo 02](#passo2)** **Configurando a Vítima (Windows 11 + Sysmon)**
  * _Instalação prática do Sysmon via linha de comando e validação dos logs no Event Viewer._

* **[🐧 Passo 03](#passo3)** **Preparando o Atacante (Kali Linux)**
  * _Colocando o Kali na mesma rede e deixando as ferramentas de ataque prontas._

* **[🔍 Passo 04](#passo4)** **Validação Final (O Teste de Conectividade)**
  * _Print do comando `ipconfig` / `ifconfig` e o teste de ping entre as duas máquinas._

---

## 🚀 Passo 01 <a name="passo1"></a>
### Conectando a Rede Isolada (`Lab-Secure`)
> Escreva o conteúdo do Passo 1 aqui...

---

## 🪟 Passo 02 <a name="passo2"></a>
### Configurando a Vítima (Windows 11 + Sysmon)
> Escreva o conteúdo do Passo 2 aqui...

---

## 🐧 Passo 03 <a name="passo3"></a>
### Preparando o Atacante (Kali Linux)
> Escreva o conteúdo do Passo 3 aqui...

---

## 🔍 Passo 04 <a name="passo4"></a>
### Validação Final (O Teste de Conectividade)
> Escreva o conteúdo do Passo 4 aqui...

---
