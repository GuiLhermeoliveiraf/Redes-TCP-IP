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

