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

