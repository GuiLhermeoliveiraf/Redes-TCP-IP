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

#### Exemplo

![Image](https://github.com/user-attachments/assets/0414b589-6bd6-4748-a13a-d1563f643060)

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
---

# 🧪 Laboratório de Teste – Configuração de DHCP em Roteador

![Topologia de Rede com DHCP](https://github.com/user-attachments/assets/74c38704-6194-435e-88cc-3fb79b64609e)

Este laboratório mostra uma topologia de rede com DHCP configurado em um roteador, permitindo que os dispositivos da rede (PCs) obtenham seus endereços IP automaticamente. Abaixo está uma explicação detalhada dos componentes e da configuração.

## 🧠 Objetivo do Laboratório

Demonstrar como configurar um servidor DHCP em um roteador (R1) para distribuir IPs na rede `10.99.99.0/24` aos PCs conectados.

## 📌 Configuração do DHCP no Roteador (R1)

Comandos usados no roteador:

```shell
dhcp enable
dhcp server database enable

ip pool DHCP-SERVER
 gateway-list 10.99.99.254
 network 10.99.99.0 mask 255.255.255.0
 dns-list 222.222.222.222

interface GigabitEthernet0/0/0
 description DHCP-SERVER
 ip address 10.99.99.254 255.255.255.0
 dhcp select global
```

**Explicação:**

- `dhcp enable`: Habilita o serviço DHCP.
- `dhcp server database enable`: Habilita o banco de dados do DHCP.
- `ip pool DHCP-SERVER`: Cria um pool de endereços DHCP.
- `gateway-list 10.99.99.254`: Define o gateway padrão (o roteador).
- `network 10.99.99.0 mask 255.255.255.0`: Define o escopo da rede.
- `dns-list 222.222.222.222`: Define o servidor DNS.
- A interface `GigabitEthernet0/0/0` recebe IP fixo e será usada para distribuir os IPs via DHCP.

## 🔌 Topologia de Rede

- **R1**: Roteador com IP fixo `10.99.99.254`, atuando como servidor DHCP.
- **Switches (LSW1, LSW2, LSW3)**: Conectam os PCs ao roteador e apenas repassam o tráfego.
- **PCs (clientes DHCP)**:
  - PC1: `10.99.99.1`
  - PC2: `10.99.99.22`
  - PC3: `10.99.99.3`

## 📡 Rede Utilizada

- Rede: `10.99.99.0/24`
- Gateway padrão: `10.99.99.254`
- DNS: `222.222.222.222`

## ✅ Funcionamento Esperado

- O roteador distribui IPs dentro da faixa `10.99.99.1` até `10.99.99.253`.
- Os PCs solicitam IPs via DHCP e recebem IP, máscara, gateway e DNS automaticamente.
- Os switches apenas encaminham os pacotes entre os dispositivos e o roteador.
