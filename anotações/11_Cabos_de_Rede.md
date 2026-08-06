#  Cabos de Rede e Mídias de Transmissão

Os **Cabos de Rede** formam a infraestrutura física (Camada 1 do Modelo OSI) responsável por guiar os sinais elétricos ou ópticos que transportam os dados entre os dispositivos de uma rede.

---

## 🧵 1. Cabo Par Trançado (UTP / STP)

É o meio físico mais utilizado em redes locais (LANs) residenciais e corporativas. Os fios são trançados em pares para **reduzir a interferência eletromagnética** e a diafonia (*crosstalk*) entre os pares vizinhos.

### Tipos de Blindagem:
* **UTP (*Unshielded Twisted Pair*):** Sem blindagem. Mais flexível, barato e comum para ambientes internos.
* **STP (*Shielded Twisted Pair*):** Com blindagem individual ou global de fita/malha metálica. Usado em ambientes industriais ou com alta interferência externa.

---

## 🏷️ 2. Categorias de Cabos de Par Trançado (Cat)

| Categoria | Frequência | Velocidade Máxima | Distância Máxima | Aplicação Principal |
| :--- | :--- | :--- | :--- | :--- |
| **Cat5e** | 100 MHz | 1 Gbps (1000 Mbps) | 100 metros | Redes domésticas e pequenas empresas. |
| **Cat6** | 250 MHz | 10 Gbps | 55 m (10 Gbps) / 100 m (1 Gbps) | Redes corporativas e conexões Gigabit. |
| **Cat6a** | 500 MHz | 10 Gbps | 100 metros | Data centers e infraestruturas de alta performance. |
| **Cat7 / Cat8** | 600–2000 MHz | 25 a 40 Gbps | 30 metros | Data centers e conexões entre switches (*Backbone*). |

---

## 🎨 3. Padrões de Conectorização RJ-45 (T568A e T568B)

Os conectores **RJ-45** utilizam 8 pinos dispostos segundo duas sequências padrão de cores estipuladas pela TIA/EIA:

### Padrão T568A:
1. Branco/Verde
2. Verde
3. Branco/Laranja
4. Azul
5. Branco/Azul
6. Laranja
7. Branco/Marrom
8. Marrom

### Padrão T568B:
1. Branco/Laranja
2. Laranja
3. Branco/Verde
4. Azul
5. Branco/Azul
6. Verde
7. Branco/Marrom
8. Marrom

---

## 🔄 4. Tipos de Montagem do Cabo

* **Cabo Direto (*Straight-Through*):**
  * Mesma norma nas duas pontas (A-A ou B-B).
  * **Uso:** Conectar dispositivos de camadas diferentes (ex: PC para Switch, Switch para Roteador).

* **Cabo Cruzado (*Crossover*):**
  * Norma A em uma ponta e Norma B na outra.
  * **Uso:** Historicamente usado para conectar dispositivos de mesma camada (ex: PC para PC, Switch para Switch).
  * *Nota:* Dispositivos modernos possuem **Auto-MDIX**, tecnologia que detecta e corrige o tipo de cabo automaticamente.

---

## 💡 5. Fibra Óptica

A fibra óptica transmite dados na forma de **feixes de luz** através de um núcleo de vidro ou plástico.

### Vantagens sobre os cabos de cobre:
* **Imunidade total** a interferências eletromagnéticas e ruídos elétricos.
* **Alcance significativamente maior** (quilômetros sem necessidade de repetidores).
* **Largura de banda e velocidades muito superiores**.

### Tipos de Fibra Óptica:
* **Monomodo (SMF - *Single-Mode Fiber*):**
  * Núcleo muito fino (~9 micras); utiliza diodo **laser**.
  * Transmite um único modo de luz por longas distâncias (WANs, links intermunicipais/submarinos).
* **Multimodo (MMF - *Multi-Mode Fiber*):**
  * Núcleo mais amplo (~50 a 62.5 micras); utiliza **LED**.
  * A luz reflete em múltiplos ângulos; ideal para curtas e médias distâncias (LANs corporativas, Data Centers).

---

## 📟 6. Cabo Coaxial

Apesar de praticamente obsoleto nas redes LAN internas modernas, ainda é utilizado por operadoras de TV a cabo e Internet de banda larga (HFC - *Hybrid Fiber-Coaxial*) para levar o sinal da rua até o modem do cliente (utilizando conectores do tipo BNC ou F-type).
