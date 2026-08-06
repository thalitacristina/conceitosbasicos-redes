#  NAT (Network Address Translation)

O **NAT** (*Network Address Translation*) é uma técnica da Camada de Rede (executada principalmente em roteadores e firewalls) criada para reescrever os endereços IP de origem e destino dos pacotes enquanto eles transitam entre redes diferentes — geralmente da rede interna (privada) para a Internet (pública).

---

## 🎯 1. Por que o NAT é necessário?

Devido ao crescimento exponencial da Internet, o total de endereços **IPv4 públicos** (~4,3 bilhões) tornou-se insuficiente. O NAT permitiu adiar o esgotamento do IPv4 ao possibilitar que centenas de dispositivos em uma rede local compartilhem um **único endereço IP público** para acessar a Internet.

### Benefícios do NAT:
* **Conservação de IPs:** Reduz drasticamente a necessidade de IPs públicos globais.
* **Segurança por Ocultação:** Os IPs privados da rede interna ficam ocultos da Internet pública.
* **Flexibilidade:** Permite alterar o provedor de Internet (ISP) sem precisar reconfigurar os IPs internos de toda a empresa.

---

## 🏢 2. Tipos de Endereços IP: Públicos vs. Privados

O NAT atua na fronteira entre o espaço privado e o público:

### Endereços IP Privados (RFC 1918)
Não são roteáveis na Internet pública e podem ser reutilizados livremente em qualquer rede local (LAN):
* **Classe A:** `10.0.0.0` a `10.255.255.255` (`10.0.0.0/8`)
* **Classe B:** `172.16.0.0` a `172.31.255.255` (`172.16.0.0/12`)
* **Classe C:** `192.168.0.0` a `192.168.255.255` (`192.168.0.0/16`)

### Endereços IP Públicos
Endereços únicos no mundo inteiro, atribuídos pelos provedores de Internet (ISPs) e roteáveis globalmente.

---

## ⚙️ 3. Modalidades do NAT

Existem três formas principais de implementar o NAT em um roteador:

### A. NAT Estático (*Static NAT*)
* Mapeia **um IP privado específico para um IP público único** de forma fixa (relação 1:1).
* **Uso típico:** Servidores internos (web, e-mail) que precisam ser acessados permanentemente a partir da Internet.

### B. NAT Dinâmico (*Dynamic NAT*)
* Mapeia um IP privado não registrado para um IP público disponível de um **grupo (*Pool*) de IPs públicos**.
* Mapeamento sob demanda (relação 1:1 temporária). Se o pool de IPs públicos esgotar, novos dispositivos aguardam na fila.

### C. PAT / NAT Overload (*Port Address Translation*)
* A forma mais comum de NAT (usada em redes domésticas e corporativas).
* Mapeia **múltiplos IPs privados para um único IP público**, utilizando diferentes **números de portas lógicas** (ex: porta 50001, 50002) para diferenciar as conexões.
* Relação N:1 (muitos computadores saindo por um único IP público).

---

## 🔄 4. Como o PAT Funciona na Prática (Exemplo Passo a Passo)

1. **Envio:** O PC A (`192.168.1.10:49152`) envia uma requisição para o Google (`142.250.190.46:443`).
2. **Tradução:** O Roteador intercepta o pacote, altera o IP de origem para o seu IP público (`200.100.50.1:50001`) e registra essa associação na sua **Tabela de Tradução NAT**.
3. **Servidor Responde:** O servidor do Google responde enviando para `200.100.50.1:50001`.
4. **Retorno:** O Roteador consulta sua tabela NAT, identifica que a porta `50001` pertence ao PC A (`192.168.1.10`) e reencaminha o pacote de volta para a rede local.

---

## 🛠️ 5. Redirecionamento de Portas (*Port Forwarding*)

Em uma rede com NAT (onde todas as portas de entrada não solicitadas são bloqueadas pelo roteador), o **Port Forwarding** permite direcionar requisições externas que chegam em uma porta específica do IP público diretamente para um dispositivo interno.

* **Exemplo:** Direcionar conexões que chegam na porta `80` (HTTP) do roteador para o servidor interno `192.168.1.100:80`.
