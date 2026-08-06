# Roteadores e Roteamento na Camada de Rede

O **Roteador** é o dispositivo fundamental da Camada de Rede (Camada 3 do Modelo OSI). Sua principal função é interconectar **redes diferentes** e determinar o melhor caminho para o tráfego dos pacotes de dados da origem até o destino através da internet ou de redes corporativas.

---

## 🆚 1. Switch vs. Roteador

| Característica | Switch (Camada 2) | Roteador (Camada 3) |
| :--- | :--- | :--- |
| **Escopo** | Interconecta dispositivos na **mesma** rede local. | Interconecta **redes diferentes** (ex: LAN para WAN). |
| **Endereçamento** | Utiliza endereços **MAC**. | Utiliza endereços **IP**. |
| **Unidade de Dados** | Quadro (*Frame*). | Pacote. |
| **Domínio de Broadcast** | Mantém 1 único domínio (sem VLANs). | **Divide** e bloqueia domínios de broadcast. |

---

## 🗺️ 2. Tabela de Roteamento

Para decidir para onde enviar cada pacote, o roteador consulta sua **Tabela de Roteamento**, que armazena as rotas conhecidas para diversas redes de destino.

### Principais componentes de uma entrada na tabela:
* **Rede de Destino:** O endereço da rede remota que se deseja alcançar (ex: `10.0.0.0/8`).
* **Próximo Salto (*Next Hop*):** O IP do próximo roteador no caminho para aquela rede.
* **Interface de Saída:** A porta física do roteador usada para enviar o pacote (ex: `GigabitEthernet0/0`).
* **Métrica / Custo:** Valor numérico usado para escolher a melhor rota quando existem múltiplos caminhos para o mesmo destino (quanto menor o valor, melhor o caminho).

---

## 🔀 3. Tipos de Roteamento

### A. Roteamento Estático
* Configurado **manualmente** pelo administrador de rede.
* **Vantagens:** Seguro, baixo consumo de processamento e memória do roteador.
* **Desvantagens:** Inviável em redes grandes; se um link cair, o roteador não encontra um caminho alternativo sozinho.
* **Rota Padrão (*Default Route*):** Uma rota estática especial (`0.0.0.0/0`) usada para encaminhar todo o tráfego direcionado a redes desconhecidas (como a Internet).

### B. Roteamento Dinâmico
* Os roteadores usam **Protocolos de Roteamento** para descobrir redes e atualizar suas tabelas automaticamente.
* **Vantagens:** Escalável; adapta-se rapidamente a falhas de links na rede.
* **Desvantagens:** Consome mais recursos de hardware (CPU/RAM) e largura de banda.

#### Principais Protocolos de Roteamento Dinâmico:
* **Vector de Distância (ex: RIP):** Escolhe o caminho com base na quantidade de roteadores intermediários (número de saltos).
* **Estado do Link (ex: OSPF):** Analisa a velocidade e o estado dos links para calcular o caminho mais rápido usando o algoritmo de Dijkstra.
* **Vetor de Caminho (ex: BGP):** Protocolo padrão usado para trocar informações de roteamento entre os grandes provedores na Internet global.

---

## 🛡️ 4. NAT (*Network Address Translation*)

O **NAT** é uma tecnologia executada em roteadores (especialmente residenciais e corporativos) que traduz endereços **IP Privados** da rede local em um único endereço **IP Público** para acesso à Internet.

* **Objetivo:** Economizar o uso de endereços IPv4 públicos e fornecer uma camada básica de segurança ocultando a estrutura da rede interna.
* **PAT (*Port Address Translation* / NAT Overload):** Variante mais comum do NAT, que utiliza números de portas lógicas (ex: 80, 443) para mapear múltiplos dispositivos locais usando o mesmo IP público.

---

💡 **Resumo Prático:**
> Enquanto o **Switch** conecta computadores para formarem uma rede, o **Roteador** conecta redes para formarem a **Internet**.
