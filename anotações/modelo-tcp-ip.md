# 🌐 Modelo TCP/IP

O **Modelo TCP/IP** é a arquitetura prática de rede utilizada na internet real. Ao contrário do modelo teórico OSI (de 7 camadas), o TCP/IP é mais conciso e focado na implementação funcional da comunicação de dados.

---

## 📌 As 4 Camadas do Modelo TCP/IP

### 1. Aplicação
* **Descrição:** Camada superior onde os aplicativos e o usuário interagem direta ou indiretamente com a rede.
* **Função:** Agrupa o papel das camadas de Aplicação, Apresentação e Sessão do modelo OSI.
* **Protocolos Principais:** 
  * **HTTP / HTTPS:** Navegação web (portas 80 / 443).
  * **DNS:** Resolução de nomes de domínio para endereços IP.
  * **FTP / SFTP:** Transferência de arquivos.
  * **SSH:** Acesso remoto seguro.
  * **DHCP:** Atribuição dinâmica de endereços IP.

### 2. Transporte
* **Descrição:** Responsável pelo controle de fluxo, ordenação e integridade da comunicação ponta a ponta entre a origem e o destino.
* **Protocolos Principais:**
  * **TCP (*Transmission Control Protocol*):** Orientado à conexão. Garante a entrega de todos os pacotes na ordem correta, com verificação de erros e reenvio. *(Usado em web, e-mail, arquivos)*.
  * **UDP (*User Datagram Protocol*):** Sem conexão. Não garante a entrega nem a ordem, mas oferece baixíssima latência e alta velocidade. *(Usado em chamadas de voz, streaming, jogos online)*.

### 3. Internet (ou Rede)
* **Descrição:** Responsável pelo endereçamento lógico dos dispositivos e pelo roteamento dos dados através de redes heterogêneas.
* **Função:** Determina o caminho que os pacotes de dados devem seguir até chegarem ao destino.
* **Protocolos Principais:**
  * **IP (IPv4 / IPv6):** Endereçamento e empacotamento.
  * **ICMP:** Diagnóstico de rede e controle de erros (ex.: comando `ping`).

### 4. Acesso à Rede (Interface de Rede / Física)
* **Descrição:** Camada inferior que lida com o meio físico de transmissão e o acesso aos dispositivos locais.
* **Função:** Converte os pacotes em quadros (*frames*) e depois em sinais físicos (elétricos, ópticos ou de rádio).
* **Tecnologias e Padrões:** Ethernet (cabos UTP), Wi-Fi (802.11), Bluetooth, MAC Address.

---

## 🔄 Tabela Comparativa: TCP/IP vs. OSI

| Camada TCP/IP | Camada OSI Equivalente | Unidade de Dados (PDU) | Dispositivos / Protocolos |
| :--- | :--- | :--- | :--- |
| **1. Aplicação** | 7. Aplicação<br>6. Apresentação<br>5. Sessão | Dados | HTTP, HTTPS, DNS, SSH, FTP |
| **2. Transporte** | 4. Transporte | Segmento (TCP) / Datagrama (UDP) | Portas lógicas (80, 443, 22...) |
| **3. Internet** | 3. Rede | Pacote | Roteador, IPv4, IPv6, ICMP |
| **4. Acesso à Rede** | 2. Enlace de Dados<br>1. Física | Quadro (*Frame*) / Bits | Switch, Placa de rede, Ethernet, Wi-Fi |

---

💡 **Resumo Prático do Fluxo de Dados (Encapsulamento):**
> **Dados** (Aplicação) $\rightarrow$ adicione a Porta (Transporte: **Segmento**) $\rightarrow$ adicione o IP (Internet: **Pacote**) $\rightarrow$ adicione o MAC (Acesso à Rede: **Quadro**) $\rightarrow$ envie como **Bits** no meio físico.
