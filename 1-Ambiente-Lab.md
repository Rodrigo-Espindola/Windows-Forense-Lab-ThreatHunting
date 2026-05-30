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
Para garantir que os testes defensivos e os artefatos manipulados não ofereçam riscos ao ambiente de produção ou à minha rede física residencial, configurei um segmento de rede logicamente isolado no VirtualBox.

### 📸 Evidência da Configuração de Rede:
*(Insira a sua imagem aqui. No GitHub fica assim: ![](Rede-Nat-config.png)*

---

## 🔍 Descrição e Funcionamento Técnico do Switch Virtual

O adaptador de rede da máquina virtual foi configurado sob os seguintes critérios de engenharia de segurança:

1. **Modo Ligado a [Rede NAT]:** Diferente do modo NAT padrão (que isola as máquinas entre si), a *Rede NAT* cria um switch virtual interno chamado **`Lab-Secure`**. Isso permite que, no futuro, novas VMs (como um Kali Linux ou um servidor de logs) sejam adicionadas ao laboratório e consigam se comunicar de forma restrita apenas entre si.
2. **Promiscuous Mode [Recusar]:** Configurado estritamente para rejeitar tráfego promiscuo, garantindo que a placa de rede intercepte apenas pacotes direcionados ao seu próprio endereço MAC (`08002774E635`), simulando o comportamento padrão de uma estação de trabalho corporativa.
3. **Isolamento de Vazamento (Leak Protection):** O switch virtual atua como uma barreira de contenção, impedindo que varreduras de portas (port scans), exploits de rede ou requisições maliciosas geradas no laboratório afetem dispositivos físicos reais da minha rede doméstica.

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
