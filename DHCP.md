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
