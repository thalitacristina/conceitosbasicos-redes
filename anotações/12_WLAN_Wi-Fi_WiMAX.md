# Redes Sem Fio: WLAN, Wi-Fi e WiMAX

As tecnologias de rede sem fio (**Wireless**) operam principalmente na Camada Física e na Camada de Enlace de Dados do Modelo OSI, permitindo a transmissão de dados por meio de ondas de radiofrequência sem a necessidade de cabos físicos.

---

## 🌐 1. WLAN (*Wireless Local Area Network*)

Uma **WLAN** é uma rede local que utiliza ondas de rádio em vez de cabos para interconectar dispositivos dentro de uma área geográfica limitada (como residências, escritórios ou campus universitários).

### Componentes Principais:
* **Ponto de Acesso (*Access Point - AP*):** Dispositivo central que recebe o sinal cabeado e o converte em sinal de rádio para os dispositivos clientes.
* **Estações / Clientes (*STA*):** Smartphones, notebooks e dispositivos IoT equipados com placas de rede sem fio.
* **SSID (*Service Set Identifier*):** O nome público atribuído à rede sem fio para que os usuários possam identificá-la e se conectar.

---

## ⚡ 2. O Padrão Wi-Fi (IEEE 802.11)

**Wi-Fi** é a marca registrada e o nome popular para o conjunto de especificações do padrão **IEEE 802.11** utilizado em redes WLAN.

### Evolução e Gerações do Wi-Fi:

| Geração | Padrão IEEE | Frequência Principal | Velocidade Máxima Teórica |
| :--- | :--- | :--- | :--- |
| **Wi-Fi 4** | 802.11n | 2.4 GHz e 5 GHz | Até 600 Mbps |
| **Wi-Fi 5** | 802.11ac | 5 GHz | Até 6.9 Gbps |
| **Wi-Fi 6 / 6E** | 802.11ax | 2.4 GHz, 5 GHz e 6 GHz | Até 9.6 Gbps |
| **Wi-Fi 7** | 802.11be | 2.4 GHz, 5 GHz e 6 GHz | Até 46 Gbps |

### Comparativo de Frequências (2.4 GHz vs. 5 GHz):
* **2.4 GHz:** Maior alcance físico e melhor capacidade de atravessar obstáculos (paredes), porém menor velocidade e maior suscetibilidade a interferências (micro-ondas, Bluetooth).
* **5 GHz:** Altas velocidades e menor interferência, porém menor alcance e dificuldade para ultrapassar barreiras físicas.

### Protocolo de Acesso ao Meio: CSMA/CA
Diferente do Ethernet cabeado (que usa CSMA/CD para detectar colisões), as redes sem fio utilizam o **CSMA/CA** (*Carrier Sense Multiple Access with Collision Avoidance*). Como o dispositivo não consegue ouvir enquanto transmite via rádio, ele tenta **evitar a colisão** escutando o canal, aguardando um tempo aleatório e enviando sinais de confirmação (*ACK*).

---

## 🔒 3. Segurança em Redes Wi-Fi

Para proteger o tráfego de dados transmitido pelo ar contra interceptações, são utilizados protocolos de criptografia:

* **WEP (*Wired Equivalent Privacy*):** Antigo e extremamente vulnerável (obsoleto).
* **WPA / WPA2:** Padrões amplamente difundidos utilizando criptografia **AES** (*Advanced Encryption Standard*).
* **WPA3:** Padrão moderno mais seguro, que oferece proteção contra ataques de força bruta no handshake e suporta criptografia mais forte.

---

## 🏙️ 4. WiMAX (*Worldwide Interoperability for Microwave Access*)

O **WiMAX** é uma tecnologia sem fio de alta velocidade baseada no padrão **IEEE 802.16**, projetada para redes metropolitanas sem fio (**WMAN** - *Wireless Metropolitan Area Network*).

### Principais Características do WiMAX:
* **Escopo:** Cobertura de longa distância (até dezenas de quilômetros), funcionando como uma "última milha" (*last mile*) para levar Internet banda larga a áreas rurais ou de difícil acesso cabeado.
* **Topologia:** Funciona de forma semelhante à telefonia celular, utilizando antenas de grande porte em torres de transmissão.
* **Declínio:** Embora tenha sido uma alternativa promissora ao cabo e DSL, o WiMAX foi amplamente substituído globalmente pelas tecnologias de redes móveis **4G LTE** e **5G**.

---

## 🔄 Resumo Comparativo: Wi-Fi vs. WiMAX

| Característica | Wi-Fi (IEEE 802.11) | WiMAX (IEEE 802.16) |
| :--- | :--- | :--- |
| **Tipo de Rede** | **WLAN** (Rede Local Sem Fio) | **WMAN** (Rede Metropolitana Sem Fio) |
| **Alcance Típico** | ~30 a 100 metros | Até 50 km |
| **Aplicação Principal** | Conectar dispositivos locais (casa/escritório) | Prover acesso à internet em áreas amplas ou rurais |
| **Licenciamento** | Frequências não licenciadas (2.4/5/6 GHz) | Requer frequências licenciadas em muitos países |
