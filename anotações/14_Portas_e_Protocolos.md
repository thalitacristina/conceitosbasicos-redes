
#  Portas Lógicas e Protocolos de Rede

Na **Camada de Transporte (Camada 4 do Modelo OSI)**, as **Portas Lógicas** funcionam como "ponto de acesso" ou "endereços de apartamentos" dentro de um computador (cujo IP seria o prédio). Elas permitem que o sistema operacional direcione o tráfego de rede recebido para a aplicação ou serviço correto.

---

## ⚡ 1. TCP vs. UDP: Os Protocolos de Transporte

As portas operam sob dois protocolos de transporte principais:

### 🤝 TCP (*Transmission Control Protocol*)
* **Orientado à conexão:** Estabelece uma conexão prévia através do *Handshake de 3 vias* (*SYN*, *SYN-ACK*, *ACK*).
* **Confiável:** Garante a entrega dos pacotes na ordem correta e retransmite dados perdidos.
* **Uso típico:** Navegação Web (HTTP/HTTPS), e-mails, transferência de arquivos e conexões remotas.

### ⚡ UDP (*User Datagram Protocol*)
* **Não orientado à conexão:** Envia os dados sem verificar se o destinatário está pronto ou recebeu o pacote.
* **Sem garantia de entrega:** Focado em velocidade e baixa latência, sem retransmissão de pacotes perdidos.
* **Uso típico:** Transmissões ao vivo (*streaming*), jogos online, chamadas VoIP e consultas DNS.

---

## 📊 2. Categorias de Portas Lógicas

Os números das portas variam de **0 a 65535** e são divididos pela IANA (*Internet Assigned Numbers Authority*) em três faixas:

* **Portas Conhecidas (*Well-Known Ports*): `0` a `1023`**
  * Reservadas para serviços e protocolos de infraestrutura padrão (HTTP, SSH, DNS, etc.).
* **Portas Registradas (*Registered Ports*): `1024` a `49151`**
  * Usadas por aplicações e serviços de terceiros mediante registro (ex: bancos de dados como MySQL, PostgreSQL).
* **Portas Efêmeras / Dinâmicas (*Dynamic Ports*): `49152` a `65535`**
  * Atribuídas temporariamente pelo sistema operacional aos clientes que iniciam uma conexão externa.

---

## 📋 3. Principais Portas e Protocolos do Dia a Dia

A tabela abaixo reúne as portas mais cobradas em exames de certificação e utilizadas no mercado:

| Porta | Protocolo | Transporte | Descrição / Aplicação |
| :--- | :--- | :--- | :--- |
| **20 / 21** | **FTP** (*File Transfer Protocol*) | TCP | Transferência de arquivos (20 para dados, 21 para controle). |
| **22** | **SSH** (*Secure Shell*) | TCP | Acesso remoto seguro via linha de comando e SFTP. |
| **23** | **Telnet** | TCP | Acesso remoto não criptografado (obsoleto por questões de segurança). |
| **25** | **SMTP** (*Simple Mail Transfer Protocol*) | TCP | Envio de e-mails entre servidores. |
| **53** | **DNS** (*Domain Name System*) | UDP / TCP | Tradução de nomes de domínio em endereços IP. |
| **67 / 68** | **DHCP** (*Dynamic Host Config Protocol*) | UDP | Atribuição dinâmica de configurações IP (67 servidor, 68 cliente). |
| **80** | **HTTP** (*HyperText Transfer Protocol*) | TCP | Navegação web sem criptografia. |
| **110** | **POP3** (*Post Office Protocol v3*) | TCP | Recebimento de e-mails (baixa e remove do servidor). |
| **123** | **NTP** (*Network Time Protocol*) | UDP | Sincronização de relógio e horário entre sistemas. |
| **143** | **IMAP** (*Internet Message Access Protocol*) | TCP | Recebimento de e-mails (sincroniza mantendo as mensagens no servidor). |
| **161 / 162** | **SNMP** (*Simple Net Management Protocol*) | UDP | Monitoramento e gerenciamento de ativos de rede. |
| **443** | **HTTPS** (*HTTP Secure*) | TCP | Navegação web segura com criptografia (TLS/SSL). |
| **3389** | **RDP** (*Remote Desktop Protocol*) | TCP | Conexão de Área de Trabalho Remota do Windows. |

---

## 🛠️ 4. Comandos para Verificar Portas Abertas no Sistema

* **Exibir conexões ativas e portas em escuta (Windows / Linux):**
  ```bash
  netstat -ano
* **Verificar conexões e o nome do processo associado (Linux):**
  ```Bash
    ss -tulpn
* **Testar se uma porta remota está aberta (PowerShell):**

  ```PowerShell
  Test-NetConnection -ComputerName 192.168.1.1 -Port 80
