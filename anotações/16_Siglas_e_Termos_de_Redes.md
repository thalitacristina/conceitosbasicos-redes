# Glossário de Siglas e Termos de Redes de Computadores

Guia de referência rápida para consulta das principais siglas utilizadas em arquitetura de redes, protocolos e infraestrutura de TI.

---

## 🏗️ 1. Modelos de Referência e Organizações

| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **OSI** | Open Systems Interconnection | Modelo de referência de 7 camadas para padronização de redes. |
| **TCP/IP** | Transmission Control Protocol / Internet Protocol | Conjunto de protocolos base que move a Internet moderna (4 ou 5 camadas). |
| **IANA** | Internet Assigned Numbers Authority | Entidade global responsável por gerenciar blocos de IP, portas lógicas e ASNs. |
| **IEEE** | Institute of Electrical and Electronics Engineers | Instituto que cria padrões de hardware e comunicação (ex: 802.3, 802.11). |
| **ISO** | International Organization for Standardization | Organização internacional de normatização. |

---

## 🌍 2. Tipos e Escopos de Redes

| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **LAN** | Local Area Network | Rede de área local (residências, escritórios, prédios). |
| **WLAN** | Wireless Local Area Network | Rede local sem fio (baseada no padrão Wi-Fi). |
| **WAN** | Wide Area Network | Rede de longa distância que conecta cidades, países ou continentes (ex: Internet). |
| **MAN** | Metropolitan Area Network | Rede de alcance metropolitano (conecta bairros ou uma cidade). |
| **PAN** | Personal Area Network | Rede de área pessoal de curtíssimo alcance (ex: conexões Bluetooth). |
| **SAN** | Storage Area Network | Rede dedicada de alta velocidade para armazenamento de dados/servidores. |

---

## ⚙️ 3. Protocolos Principais por Camada (Modelo OSI)

### 🔵 Camada 7 – Aplicação
| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **HTTP** | HyperText Transfer Protocol | Protocolo de transferência de hipertexto para navegação web. |
| **HTTPS** | HTTP Secure | Versão criptografada/segura do HTTP (utiliza TLS/SSL). |
| **DNS** | Domain Name System | Traduz nomes de domínio (ex: `site.com`) para endereços IP. |
| **DHCP** | Dynamic Host Configuration Protocol | Atribui automaticamente endereços IP e configurações à rede. |
| **FTP** | File Transfer Protocol | Protocolo para transferência de arquivos na rede. |
| **SSH** | Secure Shell | Protocolo de acesso remoto seguro via linha de comando. |
| **SMTP** | Simple Mail Transfer Protocol | Protocolo padrão para o envio de e-mails. |
| **IMAP** | Internet Message Access Protocol | Protocolo para recebimento/sincronização de e-mails mantidos no servidor. |
| **POP3** | Post Office Protocol v3 | Protocolo antigo de recebimento de e-mail (baixa as mensagens do servidor). |
| **SNMP** | Simple Network Management Protocol | Utilizado para monitorar e gerenciar dispositivos de rede. |
| **NTP** | Network Time Protocol | Sincroniza o relógio/horário dos equipamentos na rede. |

### 🟢 Camada 4 – Transporte
| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **TCP** | Transmission Control Protocol | Orientado à conexão, confiável, garante a entrega e ordem dos dados. |
| **UDP** | User Datagram Protocol | Não orientado à conexão, focado em velocidade e baixa latência. |

### 🟡 Camada 3 – Rede
| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **IP** | Internet Protocol | Endereçamento lógico e roteamento de pacotes (IPv4 / IPv6). |
| **ICMP** | Internet Control Message Protocol | Usado para diagnósticos e mensagens de erro (ex: comando `ping`). |
| **NAT** | Network Address Translation | Traduz IPs privados de uma LAN em um IP público para a Internet. |
| **PAT** | Port Address Translation | Variação do NAT que mapeia múltiplos IPs privados usando portas lógicas. |
| **OSPF** | Open Shortest Path First | Protocolo de roteamento dinâmico baseado em estado de link. |
| **BGP** | Border Gateway Protocol | Protocolo de roteamento usado entre grandes provedores na Internet global. |
| **RIP** | Routing Information Protocol | Protocolo de roteamento dinâmico clássico baseado em contagem de saltos. |

### 🔴 Camada 2 – Enlace de Dados
| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **MAC** | Media Access Control | Endereço físico gravado na placa de rede (48 bits). |
| **ARP** | Address Resolution Protocol | Traduz um endereço IP conhecido em um endereço MAC desconhecido. |
| **VLAN** | Virtual Local Area Network | Agrupamento lógico de dispositivos para segmentar redes dentro de um switch. |
| **CSMA/CD**| Carrier Sense Multiple Access with Collision Detection | Controle de acesso ao meio com detecção de colisão (Ethernet). |
| **CSMA/CA**| Carrier Sense Multiple Access with Collision Avoidance | Controle de acesso ao meio com prevenção de colisão (Wi-Fi). |

---

## 🛠️ 4. Conceitos de Endereçamento e Tecnologia

| Sigla | Termo em Inglês | Significado / Descrição |
| :--- | :--- | :--- |
| **CIDR** | Classless Inter-Domain Routing | Notação por barra (`/24`) para indicar a máscara de sub-rede. |
| **NIC** | Network Interface Card | Placa de interface de rede (física ou sem fio). |
| **PDU** | Protocol Data Unit | Nome do bloco de dados em cada camada (Dados, Segmento, Pacote, Quadro, Bit). |
| **SSID** | Service Set Identifier | Nome atribuído a uma rede sem fio Wi-Fi. |
| **ISP** | Internet Service Provider | Provedor de serviços de Internet. |
| **OUI** | Organizationally Unique Identifier | Primeiros 24 bits do endereço MAC que identificam o fabricante do hardware. |
| **UTP** | Unshielded Twisted Pair | Cabo de par trançado sem blindagem. |
| **STP** | Shielded Twisted Pair | Cabo de par trançado com blindagem metálica. |
