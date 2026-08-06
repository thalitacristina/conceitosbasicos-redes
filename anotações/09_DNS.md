# Sistema de Nomes de Domínio (DNS)

O **DNS** (*Domain Name System*) é um dos serviços mais fundamentais da internet (operando na Camada de Aplicação do Modelo OSI, porta UDP/TCP 53). Sua função principal é traduzir nomes de domínio amigáveis para humanos (como `www.google.com`) em endereços IP numéricos que os computadores utilizam para se comunicar (como `142.250.190.46`).

---

## 🎯 1. Por que o DNS é Necessário?

Os roteadores e dispositivos na internet se comunicam utilizando endereços IP (v4 ou v6). Como é inviável para seres humanos memorizarem os IPs numéricos de todos os sites que visitam, o DNS atua como a **"lista telefônica da Internet"**, resolvendo nomes legíveis em endereços de IP.

---

## 🌳 2. Estrutura Hierárquica do DNS

O sistema DNS é estruturado em uma árvore hierárquica invertida, dividida em diferentes níveis:

1. **Raiz (*Root Domain*):** Representado por um ponto (`.`) no final de cada domínio. Existem 13 grupos de servidores raiz espalhados pelo mundo que coordenam o topo da hierarquia.
2. **Domínio de Nível Superior (*TLD - Top-Level Domain*):** A extensão final do domínio.
   * *gTLDs (Genéricos):* `.com`, `.org`, `.net`, `.edu`.
   * *ccTLDs (Código de País):* `.br` (Brasil), `.us` (EUA), `.uk` (Reino Unido).
3. **Domínio de Segundo Nível (*Second-Level Domain*):** O nome do site registrado pelo usuário ou empresa (ex: `google` em `google.com`).
4. **Subdomínio:** Um nome criado antes do domínio para organizar seções do site (ex: `dev.google.com` ou `mail.google.com`).

---

## ⚡ 3. Como funciona uma Consulta DNS (Passo a Passo)

Quando você digita `www.exemplo.com` no seu navegador, ocorre o seguinte processo de resolução:

[ Navegador ] ──> 1. Cache Local / Arquivo Hosts
│
└── (Se não encontrar) ──> 2. Resolver DNS (Provedor / Google)
│
├──> 3. Servidor Raiz (.)
├──> 4. Servidor TLD (.com)
└──> 5. Servidor Autoritativo


1. **Cache Local / Hosts:** O sistema operacional e o navegador verificam se a resposta já está armazenada na memória local.
2. **DNS Resolver (Recursivo):** Se não estiver em cache, a solicitação vai para o servidor DNS da sua operadora ou configurado na placa de rede (ex: `8.8.8.8`).
3. **Servidor Raiz (*Root Server*):** O Resolver pergunta ao servidor Raiz, que responde apontando para o servidor TLD responsável por `.com`.
4. **Servidor TLD:** O Resolver pergunta ao servidor TLD `.com`, que responde apontando para o servidor autoritativo de `exemplo.com`.
5. **Servidor Autoritativo (*Authoritative Server*):** É a fonte oficial que guarda as zonas DNS do domínio. Ele devolve o IP final ao Resolver, que o entrega ao seu navegador e armazena em cache para futuras consultas.

---

## 📋 4. Principais Tipos de Registros DNS (*Resource Records*)

A tabela de zona de um domínio armazena diferentes tipos de registros para finalidades específicas:

| Tipo | Nome | Função |
| :--- | :--- | :--- |
| **A** | *IPv4 Address* | Mapeia um nome de domínio para um endereço **IPv4**. |
| **AAAA** | *IPv6 Address* | Mapeia um nome de domínio para um endereço **IPv6**. |
| **CNAME** | *Canonical Name* | Cria um alias/apelido apontando de um nome para outro (ex: `blog.site.com` $\rightarrow$ `site.com`). |
| **MX** | *Mail Exchange* | Aponta para os servidores de e-mail responsáveis por receber mensagens daquele domínio. |
| **NS** | *Name Server* | Indica quais são os servidores DNS autoritativos do domínio. |
| **TXT** | *Text Record* | Armazena texto livre; muito usado para validação de segurança e e-mail (SPF, DKIM, DMARC). |

---

## 🛠️ 5. Comandos Úteis no Terminal

* **Limpar o cache DNS local no Windows:**
  ```cmd
  ipconfig /flushdns
* **Consultar o IP de um domínio via terminal:**

  ```Bash
  nslookup exemplo.com
* **Consulta detalhada no Linux/macOS:**

  ```Bash
  dig exemplo.com
