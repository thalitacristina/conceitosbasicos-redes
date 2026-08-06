#  Comandos Básicos do Cisco IOS

O **Cisco IOS** (*Internetwork Operating System*) é o sistema operacional utilizado em roteadores e switches da Cisco. A interface de linha de comando (CLI) é estruturada em modos de navegação hierárquicos com níveis crescentes de privilégio.

---

## 🚦 1. Modos de Operação da CLI

| Modo | Prompt | Descrição / Permissão |
| :--- | :--- | :--- |
| **User EXEC Mode** | `Router>` ou `Switch>` | Modo inicial de visualização básica. Não permite alterações. |
| **Privileged EXEC Mode** | `Router#` ou `Switch#` | Acesso total a testes, diagnósticos e comandos `show`. |
| **Global Configuration Mode** | `Router(config)#` | Permite alterar configurações globais do dispositivo. |
| **Interface / Specific Mode** | `Router(config-if)#` | Permite configurar interfaces específicas (ex: `GigabitEthernet0/0`). |

### Transição entre Modos:

```plaintext
Router> enable
Router# configure terminal
Router(config)# interface gigabitEthernet 0/0
Router(config-if)# exit
Router(config)# exit
Router# disable
```

---

## 🔒 2. Configurações Iniciais do Dispositivo

```plaintext
! Definir nome do dispositivo
Router# configure terminal
Router(config)# hostname Roteador-Matriz

! Proteger o acesso ao modo Privilegiado
Roteador-Matriz(config)# enable secret SenhaForte123

! Proteger a porta de Console física
Roteador-Matriz(config)# line console 0
Roteador-Matriz(config-line)# password SenhaConsole123
Roteador-Matriz(config-line)# login
Roteador-Matriz(config-line)# exit

! Criptografar senhas gravadas no texto do arquivo de configuração
Roteador-Matriz(config)# service password-encryption

! Adicionar mensagem de aviso ao conectar (Banner MOTD)
Roteador-Matriz(config)# banner motd # Acesso Restrito a Pessoal Autorizado! #
```

---

## 🌐 3. Configuração de Interfaces

### Em Roteadores:
```plaintext
Roteador-Matriz(config)# interface gigabitEthernet 0/0
Roteador-Matriz(config-if)# description Conexao com a Rede LAN
Roteador-Matriz(config-if)# ip address 192.168.1.1 255.255.255.0
Roteador-Matriz(config-if)# no shutdown
Roteador-Matriz(config-if)# exit
```

### Em Switches (SVI para Gerenciamento):
```plaintext
Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.1.2 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit
Switch(config)# ip default-gateway 192.168.1.1
```

---

## 🛣️ 4. Configuração de Rota Estática

```plaintext
! Sintaxe: ip route [Rede_Destino] [Mascara] [Proximo_Salto_ou_Interface]
Roteador-Matriz(config)# ip route 10.0.0.0 255.0.0.0 192.168.1.254

! Rota Padrão (Default Route)
Roteador-Matriz(config)# ip route 0.0.0.0 0.0.0.0 gigabitEthernet 0/1
```

---

## 💾 5. Gerenciamento de Memória e Salvamento

Os dispositivos Cisco possuem dois arquivos de configuração principais:

- **Running-Config**: Fica na RAM (volátil). Perde-se se o equipamento desligar.  
- **Startup-Config**: Fica na NVRAM (não-volátil). Carregado na inicialização.

```plaintext
! Copiar a configuração ativa (RAM) para a inicial (NVRAM)
Roteador-Matriz# copy running-config startup-config

! Atalho tradicional de salvamento
Roteador-Matriz# write memory
```

---

## 🔍 6. Comandos de Diagnóstico e Verificação (show)

Estes comandos devem ser executados no modo Privileged EXEC (#):

| Comando | Função |
| :--- | :--- |
| `show ip interface brief` | Exibe o resumo do status e IP de todas as interfaces. |
| `show running-config` | Mostra a configuração atual em execução na memória RAM. |
| `show startup-config` | Mostra a configuração salva na memória NVRAM. |
| `show ip route` | Exibe a tabela de roteamento do dispositivo. |
| `show mac address-table` | Exibe a tabela de endereços MAC aprendidos (em switches). |
| `show cdp neighbors` | Mostra dispositivos Cisco vizinhos conectados diretamente. |
| `show vlan brief` | Exibe as VLANs configuradas e portas associadas. |

---

## 💡 Dica de Produtividade na CLI

- **Tab**: Completa o comando digitado.  
- **?**: Mostra os comandos disponíveis ou opções seguintes.  
- **Ctrl + C ou Ctrl + Z**: Sai de qualquer modo e volta para o modo Privilegiado (#).  
- **do**: Permite executar comandos `show` dentro de modos de configuração.  
  Exemplo: `Roteador(config)# do show ip route`
```

Esse bloco já está pronto para ser usado como um único arquivo `.md`.  

Quer que eu também monte um **resumo visual em diagrama** dos modos da CLI para complementar esse material?
