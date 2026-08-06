# ⚡ Padrão Ethernet e Meios de Transmissão

O **Ethernet** é a tecnologia padrão mais amplamente utilizada em redes locais cabeadas (**LANs**). Ele define regras de formatação de dados, controle de acesso ao meio e especificações físicas para a transmissão de informações na camada de Enlace e Física do Modelo OSI.

---

## 📦 1. Quadro Ethernet (*Ethernet Frame*)

Na camada de Enlace de Dados, a unidade de dados (PDU) do Ethernet é chamada de **Quadro** (*Frame*). Ele empacota os dados recebidos da camada de Rede adicionando cabeçalhos e rodapés de controle.

### Estrutura Principal do Quadro:
1. **Preâmbulo e SFD:** Sincronizam a comunicação entre o transmissor e o receptor.
2. **MAC de Destino (6 bytes):** Endereço físico do dispositivo que receberá o quadro.
3. **MAC de Origem (6 bytes):** Endereço físico da placa de rede que enviou o quadro.
4. **Tipo / Tamanho (EtherType):** Indica o protocolo da camada superior (ex.: IPv4 ou IPv6).
5. **Dados (*Payload*):** Os dados reais da camada de rede (pacote IP), variando entre 46 e 1500 bytes.
6. **FCS (*Frame Check Sequence*):** Mecanismo de verificação de erros (CRC) para garantir que o quadro não foi corrompido durante a transmissão.

---

## 🛠️ 2. Controle de Acesso ao Meio: CSMA/CD

Em redes Ethernet antigas (que utilizavam *Hubs* ou cabos coaxiais compartilhados), múltiplos dispositivos podiam tentar transmitir ao mesmo tempo, gerando **colisões de dados**.

Para resolver isso, o protocolo **CSMA/CD** (*Carrier Sense Multiple Access with Collision Detection*) foi criado:
* **Sensoriamento de Portadora (*Carrier Sense*):** O dispositivo escuta o meio físico antes de transmitir para verificar se a rede está livre.
* **Acesso Múltiplo (*Multiple Access*):** Vários dispositivos compartilham o mesmo meio.
* **Detecção de Colisão (*Collision Detection*):** Se dois dispositivos transmitirem ao mesmo tempo, a colisão é detectada, o envio é interrompido e um sinal de alerta (*jam signal*) é emitido. Os dispositivos aguardam um tempo aleatório antes de tentar novamente.

> 💡 **Nota Moderna:** Em redes atuais que utilizam **Switches** e comunicação **Full-Duplex** (transmissão e recepção simultâneas em canais separados), as colisões foram eliminadas, tornando o CSMA/CD praticamente obsoleto na prática do dia a dia.

---

## 🔌 3. Meios de Transmissão Cabedos

O padrão Ethernet suporta diferentes mídias físicas para a transmissão dos bits:

### A. Cabo Par Trançado (UTP / STP)
É o cabo de rede mais comum em residências e escritórios. Usa conectores **RJ-45**.
* **UTP (*Unshielded Twisted Pair*):** Sem blindagem; ideal para ambientes internos sem muita interferência.
* **STP (*Shielded Twisted Pair*):** Com blindagem; indicado para ambientes industriais com alta interferência eletromagnética.

#### Categorias Principais (Cat):
| Categoria | Velocidade Máxima | Frequência | Uso Típico |
| :--- | :--- | :--- | :--- |
| **Cat5e** | 1 Gbps (1000 Mbps) | 100 MHz | Redes domésticas e pequenas empresas. |
| **Cat6** | 10 Gbps (até 55 metros) | 250 MHz | Redes corporativas e conexões Gigabit. |
| **Cat6a** | 10 Gbps (até 100 metros) | 500 MHz | Data centers e infraestruturas de alta performance. |

### B. Fibra Óptica
Transmite dados através de **pulsos de luz** em vez de sinais elétricos.
* **Vantagens:** Imune a interferências eletromagnéticas, alcances muito maiores (quilômetros) e altíssimas velocidades.
* **Tipos:**
  * **Monomodo (SMF):** Núcleo fino, usa laser; ideal para longas distâncias (WANs, Backbones).
  * **Multimodo (MMF):** Núcleo mais amplo, usa LED; ideal para distâncias curtas/médias (Data centers, LANs corporativas).

---

## 🔀 4. Padrões de Pinos T568A e T568B

Para a conectorização dos cabos UTP com conectores RJ-45, existem dois padrões de cores:

* **Padrão T568A:** Verde-Branco, Verde, Laranja-Branco, Azul, Azul-Branco, Laranja, Marrom-Branco, Marrom.
* **Padrão T568B:** Laranja-Branco, Laranja, Verde-Branco, Azul, Azul-Branco, Verde, Marrom-Branco, Marrom.

> 📌 **Cabo Direto (*Straight-Through*):** Mesma sequência nas duas pontas (A-A ou B-B). Usado para conectar dispositivos diferentes (ex.: PC para Switch).  
> 📌 **Cabo Cruzado (*Crossover*):** Uma ponta A e outra B. Usado historicamente para conectar dispositivos iguais (ex.: PC para PC), embora a tecnologia **Auto-MDIX** moderna ajuste isso automaticamente nos switches e placas de rede.
