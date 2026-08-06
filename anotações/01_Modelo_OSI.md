#  Modelo OSI (*Open Systems Interconnection*)

O **Modelo OSI** é um modelo conceitual de 7 camadas criado pela ISO para padronizar e facilitar o entendimento do funcionamento das redes de computadores.

---

## 📌 As 7 Camadas do Modelo OSI

### 7. Aplicação
* **Descrição:** Interface direta com os softwares e aplicativos.
* **Função:** Permite que as aplicações interajam com a rede.
* **Protocolos:** HTTP, HTTPS, FTP, SMTP, DNS, SSH.

### 6. Apresentação
* **Descrição:** Camada de tradução e formatação de dados.
* **Função:** Criptografia, compressão e conversão de formatos (ex.: UTF-8).
* **Exemplos:** SSL/TLS, JPEG, MP3.

### 5. Sessão
* **Descrição:** Gerenciamento da comunicação.
* **Função:** Estabelece, mantém, sincroniza e encerra as conexões entre aplicações.
* **Exemplos:** API REST, chamadas de áudio/vídeo, autenticação.

### 4. Transporte
* **Descrição:** Comunicação ponta a ponta e controle de entrega.
* **Função:** Garante o envio, a ordem e o controle de fluxo/erros.
* **Protocolos:**
  * **TCP:** Confiável, garante a entrega e a ordem dos pacotes.
  * **UDP:** Sem conexão, prioriza a velocidade (jogos, streaming).

### 3. Rede
* **Descrição:** Endereçamento lógico e roteamento.
* **Função:** Determina o melhor caminho para os dados trafegarem entre redes diferentes.
* **Dispositivo:** Roteador.
* **Protocolos:** IPv4, IPv6, ICMP (ping).

### 2. Enlace de Dados (*Data Link*)
* **Descrição:** Comunicação física na mesma rede local.
* **Função:** Empacota os dados em *Quadros* (Frames) e utiliza o endereço físico (**MAC Address**).
* **Dispositivo:** Switch, Placa de Rede.
* **Tecnologias:** Ethernet, Wi-Fi (802.11).

### 1. Física
* **Descrição:** Transmissão dos dados brutos.
* **Função:** Converte e transmite bits (0s e 1s) em impulsos elétricos, sinais de luz ou ondas de rádio.
* **Meios:** Cabos de rede (UTP), fibra óptica, conectores RJ-45, antenas.

---

## 🔄 Comparativo: Modelo OSI vs. Modelo TCP/IP

| Camada OSI | Camada TCP/IP | Exemplos / Unidade |
| :--- | :--- | :--- |
| **7. Aplicação**<br>**6. Apresentação**<br>**5. Sessão** | **1. Aplicação** | HTTP, HTTPS, DNS *(Dados)* |
| **4. Transporte** | **2. Transporte** | TCP, UDP *(Segmentos/Datagramas)* |
| **3. Rede** | **3. Internet** | IPv4, IPv6, Roteadores *(Pacotes)* |
| **2. Enlace**<br>**1. Física** | **4. Acesso à Rede** | Ethernet, Wi-Fi, Switches, Cabos *(Frames/Bits)* |

---

💡 **Dica de memorização (da Camada 1 para a 7):**
> **F**ísica $\rightarrow$ **E**nlace $\rightarrow$ **R**ede $\rightarrow$ **T**ransporte $\rightarrow$ **S**essão $\rightarrow$ **A**presentação $\rightarrow$ **A**plicação
