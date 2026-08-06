# Endereço MAC e Protocolo ARP

Enquanto o **Endereço IP** cuida da localização lógica na rede (camada de Rede/Internet), o **Endereço MAC** e o **Protocolo ARP** trabalham juntos na camada de Enlace de Dados para garantir a entrega física dos pacotes entre dispositivos na mesma rede local.

---

## 🆔 1. Endereço MAC (*Media Access Control*)

O **Endereço MAC** é o identificador físico e exclusivo gravado pelo fabricante na Placa de Rede (*NIC - Network Interface Card*) de cada dispositivo.

* **Tamanho:** 48 bits (6 bytes).
* **Formato:** Representado em **12 dígitos hexadecimais**, agrupados de 2 em 2 e separados por dois-pontos ou hífens (ex: `A4:5E:60:E2:B1:09`).
* **Estrutura (48 bits):**
  * **Primeiros 24 bits (OUI - *Organizationally Unique Identifier*):** Identificam o fabricante do hardware (ex: Cisco, Dell, Apple).
  * **Últimos 24 bits:** Número de série único do dispositivo atribuído pelo fabricante.

### Característica Chave:
> O endereço IP pode mudar conforme a rede onde você se conecta, mas o **endereço MAC é permanente** para a placa de rede.

---

## 🔍 2. Protocolo ARP (*Address Resolution Protocol*)

O **ARP** é o protocolo responsável por fazer a ponte entre a camada de Rede (IP) e a camada de Enlace (MAC). Ele **traduz um endereço IP conhecido em um endereço MAC desconhecido** dentro da mesma rede local.

### Como funciona o processo ARP (Passo a Passo):
1. **Requisição (*ARP Request*):** O PC A quer enviar dados para o PC B (`192.168.1.50`), mas não sabe o MAC do PC B. O PC A envia uma pergunta em **Broadcast** (para toda a rede): *"Quem tem o IP `192.168.1.50`? Responda para o meu MAC"*.
2. **Resposta (*ARP Reply*):** Todos os dispositivos recebem a mensagem, mas apenas o PC B responde em **Unicast** (diretamente para o PC A): *"Eu sou o IP `192.168.1.50` e o meu MAC é `B2:4A:11:...`"*.
3. **Armazenamento:** O PC A grava essa relação na sua **Tabela ARP** para não precisar perguntar novamente a cada envio.

---

## 📋 3. Tabela ARP (*ARP Cache*)

A **Tabela ARP** é um registro temporário mantido no sistema operacional do dispositivo que associa IPs a seus respectivos endereços MAC.

* **Exibir a Tabela ARP no Windows/Linux:**
  ```bash
  arp -a
