# Switches e Comutação na Camada de Enlace

O **Switch** (Comutador) é o dispositivo central da Camada de Enlace de Dados (Camada 2 do Modelo OSI) responsável por interconectar dispositivos em uma rede local (**LAN**). Diferente dos antigos *Hubs*, o switch envia os dados de forma direcionada apenas para o dispositivo de destino correto.

---

## 🔁 1. Diferença entre Hub e Switch

| Característica | Hub (Camada 1) | Switch (Camada 2) |
| :--- | :--- | :--- |
| **Funcionamento** | Repete o sinal para **todas** as portas (*Flooding* constante). | Envia o quadro **apenas para a porta de destino**. |
| **Domínio de Colisão** | 1 único domínio para todas as portas (ocorre colisão). | 1 domínio de colisão **por porta** (sem colisões). |
| **Modo de Operação** | *Half-Duplex* (envia ou recebe por vez). | *Full-Duplex* (envia e recebe simultaneamente). |
| **Inteligência** | Não lê endereços. | Lê e aprende endereços **MAC**. |

---

## 📖 2. Tabela MAC (*CAM Table*) e Aprendizado

O switch mantém uma tabela em memória (chamada **Tabela MAC** ou *CAM Table*) que associa cada endereço MAC de dispositivo à porta física onde ele está conectado.

### Como o Switch constrói a Tabela MAC (Passo a Passo):
1. **Aprendizado (*Learning*):** Quando um quadro chega a uma porta, o switch lê o **MAC de Origem** e grava na tabela associado àquela porta.
2. **Encaminhamento (*Forwarding*):** O switch lê o **MAC de Destino**. Se o MAC estiver na tabela, ele encaminha o quadro diretamente para a porta correspondente.
3. **Inundação (*Flooding*):** Se o MAC de destino **não estiver** na tabela (ou se for um quadro de Broadcast), o switch envia a cópia do quadro para todas as portas, exceto a porta de origem.
4. **Exaltação / Expiração (*Aging*):** Registros na tabela MAC são mantidos por um tempo limite (ex.: 300 segundos) e apagados se o dispositivo ficar inativo.

---

## ⚙️ 3. Modos de Comutação (*Switching Modes*)

O switch possui diferentes estratégias para processar e retransmitir os quadros recebidos:

* **Store-and-Forward (Armazena e Encaminha):**
  * O switch recebe o quadro inteiro, verifica se há erros via **FCS/CRC** e, se estiver correto, encaminha ao destino.
  * *Vantagem:* Alta confiabilidade (descarta quadros corrompidos).
  * *Desvantagem:* Maior latência.

* **Cut-Through (Atalho):**
  * O switch lê apenas os primeiros bytes (onde fica o MAC de destino) e já começa a retransmitir o quadro antes mesmo de recebê-lo por inteiro.
  * *Vantagem:* Latência extremamente baixa.
  * *Desvantagem:* Não verifica erros, retransmitindo quadros corrompidos.

* **Fragment-Free:**
  * Meio-termo entre os dois modos. O switch lê os primeiros **64 bytes** (onde ocorre a maioria das colisões e erros) antes de iniciar a retransmissão.

---

## 🌐 4. Domínios de Colisão vs. Domínios de Broadcast

* **Domínio de Colisão:** Área de rede onde quadros transmitidos simultaneamente podem colidir. Cada porta de um switch forma seu próprio domínio de colisão independente.
* **Domínio de Broadcast:** Área de rede onde um quadro de broadcast (`FF:FF:FF:FF:FF:FF`) é recebido por todos os dispositivos. Por padrão, um switch possui **um único domínio de broadcast** em todas as suas portas (a menos que sejam configuradas **VLANs**).

---

💡 **Resumo Prático:**
> O switch conecta computadores em uma mesma rede local com eficiência e velocidade, aprendendo endereços **MAC** para enviar dados no modo **Unicast** diretamente ao destino final.
