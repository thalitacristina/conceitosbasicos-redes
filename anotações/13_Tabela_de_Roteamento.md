#  Tabela de Roteamento

A **Tabela de Roteamento** é um banco de dados mantido na memória de roteadores e dispositivos de rede (como switches L3 e computadores). Ela serve como um "mapa de navegação" para a **Camada de Rede (Camada 3)**, contendo o conjunto de regras e caminhos que definem para onde um pacote de dados deve ser encaminhado a fim de atingir seu destino.

---

## 📌 1. Estrutura e Componentes de uma Tabela de Roteamento

Cada entrada (*rota*) na tabela de roteamento contém campos essenciais para a tomada de decisão do roteador:

| Componente | Descrição | Exemplo |
| :--- | :--- | :--- |
| **Rede de Destino (*Destination*)** | O IP/sub-rede de destino do pacote recebido. | `192.168.2.0/24` |
| **Próximo Salto (*Next Hop*)** | O IP do próximo roteador intermediário no caminho. | `10.0.0.2` |
| **Interface de Saída (*Out Interface*)** | A porta física do roteador usada para enviar o pacote. | `GigabitEthernet0/1` |
| **Métrica / Custo (*Metric*)** | Valor numérico usado para comparar e escolher o melhor caminho. | `20` |
| **Origem da Rota (*Protocol*)** | Como a rota foi aprendida (direta, estática ou dinâmica). | `C`, `S`, `O`, `B` |

---

## 🏷️ 2. Tipos e Origens de Rotas

As rotas presentes na tabela são classificadas pela forma como foram descobertas e adicionadas:

1. **Conectadas Diretamente (*Directly Connected - C*):**
   * Redes que estão ligadas fisicamente às interfaces ativas do próprio roteador.
   * Possuem a menor distância administrativa (prioridade máxima).

2. **Rotas Estáticas (*Static - S*):**
   * Inseridas **manualmente** pelo administrador de rede.
   * **Rota Padrão / Default Route (`0.0.0.0/0`):** Uma rota estática coringa usada para encaminhar pacotes destinados a redes desconhecidas (como o tráfego que vai para a Internet).

3. **Rotas Dinâmicas (*Dynamic*):**
   * Aprendidas automaticamente através da comunicação com outros roteadores usando protocolos de roteamento:
     * **OSPF (`O`):** Baseado no estado do link.
     * **BGP (`B`):** Protocolo de vetor de caminho para a Internet global.
     * **RIP (`R`):** Baseado no número de saltos.

---

## 📏 3. Critérios de Seleção de Rota (Como o Roteador Decide?)

Quando um pacote chega, o roteador pode encontrar múltiplos caminhos para o mesmo destino. Ele utiliza a seguinte ordem de desempate:

### 1º Prefixo Mais Longo (*Longest Prefix Match*)
O roteador sempre prefere a rota mais específica (a que tem a maior máscara de sub-rede).
* *Exemplo:* Para o IP de destino `192.168.1.50`:
  * Rota A: `192.168.1.0/24`
  * Rota B: `192.168.1.0/28` 👈 **Escolhida** (mais específica, máscara maior).

### 2º Distância Administrativa (*AD - Administrative Distance*)
Se existirem rotas com a mesma máscara vindas de fontes diferentes, o roteador escolhe a fonte mais confiável (menor valor de AD):

| Fonte da Rota | Distância Administrativa (AD Padrão) |
| :--- | :--- |
| **Conectada Diretamente** | `0` |
| **Rota Estática** | `1` |
| **BGP (Externo)** | `20` |
| **OSPF** | `110` |
| **RIP** | `120` |

### 3º Métrica (*Metric*)
Se houver empate na máscara e na distância administrativa, o roteador escolhe a rota com a **menor métrica** (menor custo, maior velocidade ou menor número de saltos).

---

## 🛠️ 4. Como Visualizar a Tabela de Roteamento

* **No Windows (Prompt de Comando):**
  ```cmd
  route print
