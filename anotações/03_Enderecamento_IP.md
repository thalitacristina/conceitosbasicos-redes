# 🌐 Aula 03 – Endereçamento IPv4, Classes e DHCP

O **IPv4** (*Internet Protocol version 4*) é o protocolo responsável por identificar unicamente cada dispositivo conectado a uma rede de computadores, permitindo o roteamento e a troca de dados entre eles.

---

## 📌 1. Fundamentos do IPv4

* **Estrutura:** O IPv4 é composto por **32 bits**, organizados em **4 octetos** (blocos de 8 bits) separados por pontos.
* **Representação:** Decimal pontuado (ex: `192.168.1.1`), onde cada octeto varia de `0` a `255`.
* **Conversão Binária:** O endereço combina representação binária (bits 0 e 1) e decimal.
  * *Exemplo:* O octeto binário `11000000` equivale ao valor decimal `192`.

---

## 🎭 2. Máscara de Sub-rede e Notação CIDR

A **Máscara de Sub-rede** define qual parte do endereço IP identifica a **Rede** e qual parte identifica o **Host** (dispositivo).

* **Bits `1`:** Identificam a rede.
* **Bits `0`:** Identificam o host.

### Notação CIDR (*Classless Inter-Domain Routing*)
É a forma simplificada de indicar a quantidade de bits `1` da máscara através de uma barra (`/`):

| Máscara Decimal | Notação CIDR | Parte de Rede / Host |
| :--- | :--- | :--- |
| `255.0.0.0` | `/8` | 8 bits de Rede / 24 bits de Host |
| `255.255.0.0` | `/16` | 16 bits de Rede / 16 bits de Host |
| `255.255.255.0` | `/24` | 24 bits de Rede / 8 bits de Host |

---

## 🏢 3. Classes de Endereços IPv4

Historicamente, o IPv4 foi dividido em classes para organizar a distribuição de redes:

| Classe | Faixa do 1º Octeto | Máscara Padrão | Uso Típico |
| :--- | :--- | :--- | :--- |
| **Classe A** | `1` a `126` | `/8` (`255.0.0.0`) | Grandes corporações e governos (muitos hosts). |
| **Classe B** | `128` a `191` | `/16` (`255.255.0.0`) | Médias empresas e universidades. |
| **Classe C** | `192` a `223` | `/24` (`255.255.255.0`) | Pequenas redes locais e residências. |

### ⚠️ Endereços Reservados e Especiais:
* **Loopback (`127.0.0.1`):** Usado para testes internos de conectividade na própria interface de rede da máquina (*localhost*).
* **Endereço de Rede:** Ocorre quando todos os bits do host estão zerados (`0`). Identifica a rede inteira (ex: `192.168.1.0`).
* **Endereço de Broadcast:** Ocorre quando todos os bits do host estão preenchidos com `1`. Utilizado para comunicação com todos os dispositivos daquela rede (ex: `192.168.1.255`).

---

# 🌐 Endereçamento IPv6

O **IPv6** (*Internet Protocol version 6*) é a versão mais recente do protocolo de internet, criada para substituir o IPv4 e resolver o problema do esgotamento dos endereços IP no mundo.

---

## 📌 Fundamentos e Estrutura

* **Tamanho Total:** 128 bits (fornece cerca de $3,4 \times 10^{38}$ endereços únicos).
* **Representação:** Hexadecimal, dividido em **8 grupos de 4 dígitos** (chamados de *hextetos*) separados por dois-pontos (`:`).
* **Exemplo:** `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

---

## ✂️ Regras de Compressão de IPv6

Para facilitar a leitura e escrita, o IPv6 possui duas regras de simplificação:

### 1. Omitir zeros à esquerda
Zeros no início de qualquer grupo de 4 dígitos podem ser removidos.
* **Original:** `2001:0db8:0001:0000:...`
* **Simplificado:** `2001:db8:1:0:...`

### 2. Uso dos dois-pontos duplos (`::`)
Uma sequência contínua de grupos formados apenas por zeros (`0000`) pode ser substituída por `::`.
* *Atenção:* Essa substituição com `::` só pode ser usada **uma única vez** por endereço para evitar ambiguidade na reconstrução.

#### Exemplo Completo de Compressão:
1. **Endereço Completo:** `2001:0db8:0000:0000:0000:0000:1428:57ab`
2. **Omitindo zeros à esquerda:** `2001:db8:0:0:0:0:1428:57ab`
3. **Aplicando `::`:** `2001:db8::1428:57ab`

---

## 🔄 Comparativo Rápido: IPv4 vs. IPv6

| Característica | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Tamanho** | 32 bits | 128 bits |
| **Formato** | Decimal pontuado (`192.168.1.1`) | Hexadecimal separado por dois-pontos |
| **Total de Endereços** | ~4,3 bilhões | ~340 undecilhões |
| **Broadcast** | Utilizado para comunicação na rede | Substituído por **Multicast** e **Anycast** |
| **Configuração Auto** | Requer servidor DHCP | Possui autoconfiguração nativa (SLAAC) |

---

💡 **Endereço de Loopback em IPv6:**
> O equivalente ao `127.0.0.1` do IPv4 é o endereço `0:0:0:0:0:0:0:1`, totalmente comprimido como **`::1`**.


## ⚙️ 4. Protocolo DHCP (*Dynamic Host Configuration Protocol*)

O **DHCP** é o serviço responsável por **automatizar e gerenciar** a atribuição de configurações de rede para os dispositivos de forma dinâmica.

* **O que o DHCP atribui automaticamente:**
  1. **Endereço IP** (ex: `192.168.0.10`)
  2. **Máscara de Sub-rede** (ex: `255.255.255.0`)
  3. **Gateway Padrão** (IP do roteador, ex: `192.168.0.1`)
  4. **Servidor DNS** (ex: `8.8.8.8`)

* **Vantagens:** Evita conflitos de IP duplicados na rede e elimina a necessidade de configurar manualmente cada dispositivo conectado.
