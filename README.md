# Sub-redes e demais conceitos

Nessa instrução, vamos falar especialmente de mapeamento de redes locais usando IPV4 para criar redes e subredes, mas também vamos transitar por:

1) Organização dos protocolos em camadas (Modelo OSI);
2) Protocolo IPV6;
3) Topologias de redes;
4) TCP e UDP;


Existe dois tipos de redes: 

* Local
  - **PAN (Personal Area Network):** basicamente feita de dispositivos de curto alcance, em especial, os sem fio, via bluetooth;
  - **LAN (Local Area Network):** feita de cabos e WiFi, conectando computadores, notebooks, impressores e servidores
  - **MAN (Metropolitan Area Network):** feita de fibra óptica e rádio tipo minilink
    
* Mundial
  - **WAN (Wide Area Network):** feita de fibra óptica e satélite. A Internet se mistura com uma WAN.

Ambas as redes servem para conectar os hosts (que são end-devices numa grande rede chamada Internet).

Os hosts se comunincam usando diversos protocolos que trabalham de **camada N para camada N**.


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SubRedes/blob/main/imgs/modelo_osi.png">
   <img alt="Modelo OSI" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SubRedes/blob/main/imgs/modelo_osi.png)">
</picture>

Alguns detaques da figura:

* O Modelo OSI (Opened Standard Interconnection) possui 7 camadas. É uma pilha de camadas totalmente abstrata, isto é, não existe essas camadas na vida real e não correspondem à nenhuma placa específica do computador;

## Modelo OSI
  
* **Camada 07 - Aplicação :** cuida de tudo o que aparece na sua tela, é a aplicação;
* **Camada 06 - Apresentação :** é o tradutor com criptografia/descriptografia;
* **Camada 05 - Sessão :** é a camada de intercomunicação entre hosts. É como se fosse uma sessão de cinema que tem hora para começar e acabar, isto é, o serviço ficará disponível para você por X minutos ou horas;
* **Camada 04 - Transporte :** é a camada de transferência de dados fim a fim. É o frete de pacotes. É a cada do TCP e UDP. TCP garante a entrega, UDP transporta, mas não garante a entrega de pacotes;
* **Camada 03 - Redes :** determina o caminho e a lógica de roteamento de pacotes. É a cada do IPV4 e IPV6;
* **Camada 02 - Enlace :** é a camada que trata do endereço físico dos dispositivos de redes, isto é, o chassis da placa que trafega dados;
* **Camada 01 - Física :** é a camada dos padrões elétricos, eletrônicos e mecânicos. 

## Topologias de Redes

Os hosts podem ser organizados em algum tipo de topologia a seguir:

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SubRedes/blob/main/imgs/network-topology.png">
   <img alt="Topologias de Redes" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SubRedes/blob/main/imgs/network-topology.png)">
</picture>

O mais comum para o ambiente de computadores é o **Estrela** que também pode ser estendido para **Estrela Estendida** quando uma estrela dá origem para outra estrela.


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SubRedes/blob/main/imgs/estrela_extendida.png">
   <img alt="Estrela Estendida" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SubRedes/blob/main/imgs/estrela_extendida.png)">
</picture>

## Protocolo IPV4 vs IPV6

A figura a seguir aponta as principais diferenças. Contudo, na rede local, só se usa o IPV4.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SubRedes/blob/main/imgs/ipv4_vs_ipv6.png">
   <img alt="IPV4 vs IPV6" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SubRedes/blob/main/imgs/ipv4_vs_ipv6.png)">
</picture


# Redes e Sub-redes

As redes de computadores servem para criar hierarquias de estações de trabalho dentro de numa organização. Por exemplo, numa instituição de ensino, existe a rede de alunos, a de professores e a administrativa. As redes geralmente não se conversam e há critérios de segurança entre elas.

E as sub-redes são redes menores que nascem a partir de uma rede, e para isso, precisamos do CIDR (Classes Inter-Domain Routing) para organizar essas redes dentro de redes.

**Basicamente, o que você precisa saber pra dominar esse trem?**

| Fazer conversão de binária para decimal.|
|-|

## Exemplos:

### 10.0.0.0/26
CIDR = 26, então significa 26 bits são fixos, isto é, uma máscara de 26 bits "1" e 6 bits irrelevantes marcados por x.

Então, você pode brincar com os bits flexíveis marcados por **X**, mas não pode mudar os bits marcados por **1**.

|1 1 1 1 1 1 1 1 | 1 1 1 1 1 1 1 1 | 1 1 1 1 1 1 1 1 | 1 1 X X X X X X |
|-|-|-|-|
| 255 | 255 | 255 | 192 |

<font color=\"red\"> x x x x x x </font>

<font color=\"red\"> Texto com cor vermelha </font>


Olhando para **10.0.0.0/26** sua missão é:

a) Qual é o endereço de rede?

b) Qual é o primeiro IPV4 disponível?

c) Qual é o endereço de broadcast na rede?

d) Qual é o último endereço IPV4 útil disponível?


#### a) Endereço de rede é o primeiro endereço da faixa (quando os bits X são só ZERO): 

Pega o IP original dado no enunciado:

| 10 | 0 | 0 | 0 |
|-|-|-|-|

Compare com a máscara e encontre os bits flexíveis **X** e não mexa com os bits marcados em **1**:

|1 1 1 1 1 1 1 1 | 1 1 1 1 1 1 1 1 | 1 1 1 1 1 1 1 1 | 1 1 X X X X X X |
|-|-|-|-|
| 255 | 255 | 255 | 192 |

Resulta em:

| 0 0 0 0 1 0 1 0 | 0 0 0 0 0 0 0 0 | 0 0 0 0 0 0 0 0 | 0 0 X X X X X X |
|-|-|-|-|
| 10 | 0 | 0 | 0 0 X X X X X X |

Finalmente, coloque **0** no lugar dos **X** para encontrar o endereço da rede:

| 10 | 0 | 0 | 0 0 0 0 0 0 0 0 |
|-|-|-|-|

Que é o mesmo que **10.0.0.0**

### b) Qual é primeiro IP útil disponível?

É sempre o primeiro após o endereço da rede. Portanto:

| 10 | 0 | 0 | 0 0 0 0 0 0 0 1 |
|-|-|-|-|
| 10 | 0 | 0 | 1 |


### c) Qual o endereço de broadcast da rede? 

Quando os **X** flexíveis são semopre **1**: 

| 10 | 0 | 0 | 0 0 1 1 1 1 1 1 |
|-|-|-|-|

Resulta em:

| 10 | 0 | 0 | 63 |
|-|-|-|-|

porque 1 1 1 1 1 1 = 63

### d) Qual é o último endereço ÚTIL da faixa?

É sempre o penúltimo endereço do broadcast.

| 10 | 0 | 0 | 62 |
|-|-|-|-|


**Portanto, temos:**
- Primeiro endereço: 10.0.0.0 (endereço da rede)
- Último endereço: 10.0.0.63 (endereço de broadcast)
- Faixa útil: 10.0.0.1 até 10.0.0.62
- Quantidade de hosts possíveis: 62
