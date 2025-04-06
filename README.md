# Camadas do Modelo TCP/IP
---

### 🔌 1. Camada de Acesso à Rede (ou Interface de Rede)

#### O que faz:
- Controla a forma como os dados são fisicamente transmitidos de um dispositivo a outro na mesma rede.
- Lida com o hardware da rede (placas de rede, cabos, switches, Wi-Fi).
- Envolve o envio de quadros (frames) entre dispositivos.

#### Exemplos práticos:
- Conectar notebook ao Wi-Fi ou via cabo Ethernet.
- Switch transmitindo dados entre computadores.
- Placa de rede reconhecendo o endereço MAC de outro dispositivo.

#### Tecnologias/protocolos:
- Ethernet
- Wi-Fi (IEEE 802.11)
- ARP
- PPP

---

### 🌐 2. Camada de Internet

#### O que faz:
- Responsável por enviar pacotes de dados entre diferentes redes.
- Define endereços IP para dispositivos.
- Usa roteadores para decidir o melhor caminho até o destino.

#### Exemplos práticos:
- Acesso a sites (como `fapam.edu.br`) usando IPs.
- Pacote de dados saindo de casa até o servidor remoto.

#### Protocolos:
- IP (IPv4, IPv6)
- ICMP (ping)
- ARP (descoberta de endereços MAC)

---

### 📡 3. Camada de Transporte

#### O que faz:
- Garante a entrega dos dados entre aplicações em dispositivos diferentes.
- Pode ser confiável (TCP) ou mais rápido e leve (UDP).

#### Protocolos principais:
- **TCP (Transmission Control Protocol)**:
  - Verifica entrega de dados e retransmite se necessário.
  - Exemplo: carregar páginas web, login em banco online.
  
- **UDP (User Datagram Protocol)**:
  - Mais rápido, sem controle de erro.
  - Exemplo: chamadas de vídeo, streaming, jogos online.

#### Exemplos práticos:
- Assistir a vídeos no YouTube (TCP/UDP).
- Jogar online com comunicação em tempo real (UDP).

---

### 🖥️ 4. Camada de Aplicação

#### O que faz:
- Torna os dados úteis para o usuário final.
- Contém protocolos para comunicação entre aplicações.

#### Protocolos comuns:
- **HTTP/HTTPS**: Navegação em sites.
- **FTP**: Transferência de arquivos.
- **SMTP/IMAP/POP3**: Envio e recebimento de e-mails.
- **DNS**: Tradução de domínios para IPs.

#### Exemplos práticos:
- Acessar Gmail via navegador (HTTPS).
- Baixar arquivos via FTP.
- Chamada de vídeo pelo WhatsApp (sobre TCP/UDP).

---

# 📡 Endereçamento IPv4

## O que é o endereçamento IPv4

O endereçamento IPv4 é o sistema que permite identificar e localizar dispositivos em uma rede.  
Cada dispositivo conectado a uma rede (como computador, smartphone, impressora, roteador, etc.) precisa de um endereço IP único para se comunicar com outros dispositivos.

## Exemplo de aplicação

Imagine que o endereço IP funciona como o endereço da sua casa.  
Se alguém quiser te enviar uma carta, precisa saber seu endereço.  
O mesmo acontece com os pacotes de dados na internet — eles precisam saber para onde ir.

## Formato do Endereço IPv4

Um endereço IPv4 é composto por 32 bits, divididos em 4 grupos de 8 bits (chamados de octetos).  
Exemplo: `192.168.1.1`  
Cada número (octeto) pode variar de 0 a 255.

## Componentes de um IP

Um endereço IP IPv4 é dividido em duas partes:
- **Parte da rede** – identifica a rede à qual o dispositivo pertence.
- **Parte do host** – identifica o dispositivo dentro da rede.

A separação dessas partes é feita com uma **máscara de sub-rede**, como `255.255.255.0`.

## 📊 Máscara de Sub-rede

A máscara de sub-rede define qual parte do IP representa a rede e qual representa os hosts.

**Exemplo:**
- IP: `192.168.1.1`
- Máscara: `255.255.255.0` ou `/24`

Significa que os 24 primeiros bits são para a rede, e os 8 restantes para identificar os dispositivos (hosts).

## Como funciona a Máscara?

A máscara é um número de 32 bits, assim como o endereço IP.  
Ela possui bits em `1` para a parte da rede e bits em `0` para a parte do host.

**Exemplo:**  
`255.255.255.0` → `11111111.11111111.11111111.00000000`  
Ou seja: 24 bits para a rede e 8 bits para hosts → `/24` (notação CIDR).  
Com 8 bits restantes, é possível ter até **254 dispositivos únicos**.

## O que é CIDR

**CIDR** (Classless Inter-Domain Routing) é uma forma mais moderna e flexível de representar máscaras de rede.  
Foi criado para substituir o antigo sistema de classes IP (A, B, C), que era limitado.

**Notação CIDR:**  
Em vez de escrever a máscara completa, usamos a quantidade de bits `1` da máscara.

| CIDR | Máscara            | Hosts possíveis* |
|------|--------------------|------------------|
| /8   | 255.0.0.0          | 16.777.214       |
| /16  | 255.255.0.0        | 65.534           |
| /24  | 255.255.255.0      | 254              |
| /30  | 255.255.255.252    | 2                |

---
# Laboratório de Protocolos de Redes
---

# 📚 DHCP (Dynamic Host Configuration Protocol)

## O que é exatamente o DHCP

O DHCP é um protocolo da camada de aplicação (modelo OSI) que permite que dispositivos em uma rede obtenham automaticamente as configurações de rede necessárias para se comunicar com outros dispositivos, como:

- Endereço IP
- Máscara de sub-rede
- Gateway padrão
- Servidores DNS

Sem o DHCP, os administradores de rede precisariam configurar manualmente cada dispositivo da rede — o que seria trabalhoso e propenso a erros, especialmente em redes grandes.

---

## 🔁 Etapas do processo DHCP 

O processo de concessão de IP via DHCP envolve quatro passos, conhecidos pela sigla **DORA**:

1. **DHCP Discover**  
   O cliente envia um broadcast na rede procurando por servidores DHCP disponíveis.

2. **DHCP Offer**  
   Um servidor DHCP responde oferecendo um endereço IP e outras configurações de rede.

3. **DHCP Request**  
   O cliente escolhe uma das ofertas (caso haja mais de uma) e solicita a concessão do IP ao servidor escolhido.

4. **DHCP Acknowledgment (ACK)**  
   O servidor confirma a concessão e envia os detalhes da configuração de rede.

---

## 📆 Concessão (Lease) de IPs

O endereço IP fornecido por um servidor DHCP **não é permanente**.  
Ele é concedido por um **período de tempo**, chamado de *lease time*.

- Após o vencimento do lease, o cliente pode tentar **renovar** o mesmo IP.
- Caso o IP esteja indisponível, o servidor pode fornecer outro IP livre.

---

## 🖥️ Onde o DHCP é usado?

O DHCP está presente em praticamente todos os ambientes de rede:

- **Redes domésticas**: Roteadores residenciais normalmente já atuam como servidores DHCP.
- **Ambientes corporativos e escolas**: Uso de servidores dedicados, como o DHCP do Windows Server.
- **Provedores de internet (ISPs)**: Distribuição de IPs dinâmicos para clientes residenciais ou empresariais.
