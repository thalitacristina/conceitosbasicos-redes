# Protocolo DHCP e Atribuição Dinâmica de IPs

O **DHCP** (*Dynamic Host Configuration Protocol*) é um protocolo da Camada de Aplicação (operando sobre a camada de Transporte com portas UDP 67 e 68) responsável por **automatizar a distribuição e o gerenciamento de configurações de IP** para os dispositivos conectados à rede.

---

## 🎯 1. Por que usar o DHCP?

Antes do DHCP, os endereços IP precisavam ser configurados manualmente (*IP Estático*) em cada computador. 

### Vantagens do DHCP:
* **Automação:** Dispositivos recebem as configurações de rede assim que se conectam.
* **Eliminação de Erros:** Evita conflitos de IP duplicados na mesma rede.
* **Redução do Trabalho Administrativo:** Não é necessário alterar as configurações do PC manualmente quando o usuário muda de local ou de rede.
* **Reaproveitamento de Endereços:** IPs são liberados de dispositivos inativos e reaproveitados para novos dispositivos.

---

## ⚡ 2. O Processo DORA (Como o DHCP funciona)

Quando um dispositivo entra na rede e solicita um IP, ocorre uma troca de 4 mensagens entre o **Cliente** e o **Servidor DHCP** conhecida pelo acrônimo **DORA**:

[ Cliente ]  --- (D) Discover --->  [ Servidor DHCP ]
[ Cliente ]  <--- (O) Offer ------  [ Servidor DHCP ]
[ Cliente ]  --- (R) Request ---->  [ Servidor DHCP ]
[ Cliente ]  <--- (A) Acknowledge -  [ Servidor DHCP ]


1. **D - Discover (Descoberta):** O cliente envia uma mensagem em **Broadcast** (`255.255.255.255`) na rede procurando por qualquer servidor DHCP ativo.
2. **O - Offer (Oferta):** O servidor DHCP responde propondo um endereço IP disponível, máscara de sub-rede, gateway e tempo de concessão (*Lease Time*).
3. **R - Request (Solicitação):** O cliente aceita a oferta enviando uma mensagem confirmando que deseja utilizar aquele IP específico.
4. **A - Acknowledge (Confirmação):** O servidor envia um pacote final de confirmação (ACK) liberando o uso do IP para o dispositivo.

---

## 📋 3. O que o Servidor DHCP fornece?

Além do Endereço IP, o servidor DHCP envia um pacote de informações fundamentais para a conectividade:

* **Endereço IP:** Identificador lógico do dispositivo.
* **Máscara de Sub-rede:** Define o tamanho da rede e divide IP entre Rede/Host.
* **Gateway Padrão (*Default Gateway*):** O endereço do Roteador para sair da rede local rumo à Internet.
* **Servidores DNS:** IPs dos servidores encarregados de traduzir nomes de domínio em IPs (ex: `8.8.8.8`).
* **Tempo de Concessão (*Lease Time*):** Duração de tempo pelo qual o cliente tem permissão de usar aquele IP.

---

## 📌 4. Tipos de Alocação de IP no DHCP

* **Alocação Dinâmica:** O servidor empresta um IP de um grupo (*Pool*) por um período determinado. Quando o tempo de concessão expira, o IP pode mudar.
* **Alocação Automática:** O servidor atribui permanentemente um IP livre a um cliente na primeira conexão.
* **Reserva de IP (*DHCP Reservation*):** O administrador associa um endereço IP específico ao **Endereço MAC** do dispositivo. Toda vez que aquela placa de rede conectar, receberá sempre o mesmo IP (usado em impressoras, servidores e câmeras).

---

## 🛠️ 5. Comandos Úteis no Prompt de Comando (Windows)

* **Solicitar novo IP via DHCP:**
  ```cmd
  ipconfig /renew
* **Liberar o IP atual:**
  ```DOS
  ipconfig /release
* **Verificar servidor DHCP atual:**

  ```DOS
  ipconfig /all

