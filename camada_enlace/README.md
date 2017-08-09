# Lista de exercícios 5
## Camada de enlace

1) **Descreva sucintamente 5 (cinco) serviços que a Camada de Enlace pode desempenhar.**

    1. Controle de fluxo
    2. Detecção de erros
    3. Correção de erros sem retransmissão
    4. Enquadramento
    5. Entrega confiável entre dois equipamentos

2) **Se todos os enlaces (links) da internet oferecessem um serviço de entrega confiável, o serviço de transporte confiável, oferecido na camada de transporte, seria redundante? Por quê?**

    Não, pois a detecção de erros feita na camada de enlace não é totalmente confiável.

3) **Foram estudadas três grandes classes de protocolos de múltiplo acesso. Quais são essas três classes e quais as vantagens e desvantagens de cada uma delas?**

    1. ALOHA
    2. CSMA
    3. Token Ring

4) **Para se atingir um protocolo de múltiplo acesso ideal, foram destacados 4 pontos. Quais desses pontos o protocolo Aloha Segmentado (slotted aloha) atende? Quais desses pontos o protocolo Token passing atende?**

    1. Quando um nó quer transmitir, ele pode enviar a uma taxa R;
    2. Quando M nós querem transmitir, cada um envia a uma taxa média R/M;
    3. Totalmente descentralizada;
    4. Simples

5) **Qual é a capacidade de endereçamento da C. de Enlace (endereço MAC)? Como é garantido que não há duas interfaces com o mesmo endereço MAC no mundo?**

    O endereço MAC consiste em 48 bits, ou seja, ![equation](http://latex.codecogs.com/gif.latex?2^48) possiveis endereços MAC. A IEEE administra a alocação desses endereços, portanto, eles são responsáveis por garantir que não existam duas interfaces no mundo que utilizam o mesmo endereço MAC.

6) **Como é feita a tradução de endereços MAC em endereços IP? E a tradução inversa?**

    Cada nó de uma LAN tem uma tabela ARP que faz o mapeamento do endereço IP --> endereço MAC de alguns nós daquela lan. Quando um nó A quer enviar um dado para um nó B, ele tentará encontrar o endereço MAC do nó B em sua tabela ARP, caso não exista uma chave em sua tabela, ele envia um broadcast para todos os nós da lan, ao receber o pacote ARP, B responde A -- via unicast -- o seu endereço MAC. O nó A, por sua vez, recebe o endereço MAC de B e armazena a entrada <IP, MAC> de B em sua tabela ARP por um tempo determinado (até expirar a entrada da tabela).

7) **E possível a um nó descobrir o endereço MAC de outro nó que não esteja em sua rede local? Explique.**

    Sim, quando uma interface não está na rede local, o broadcast feito pelo nó A chegará ao roteador R, que por sua vez irá verificar sua tabela ARP para verificar se ele conhece o endereço MAC de B, caso isso seja falso, ele fará um broadcast para os outros roteadores R1, R2, ..., Rn (sendo estes seus vizinhos), que irão verificar suas tabelas ARP até que o endereço de B seja encontrado e retornado recursivamente até o nó A.

8) **Por que uma consulta ARP é enviada para o endereço de broadcast? E por que a resposta ARP não é enviada para o endereço de broadcast?**

    Pois o nó solicitante não sabe qual de seus nós vizinhos tem o endereço procurado, por isso, ele pergunta a todos. Quando o nó responde, ele não usa um broadcast porque no pacote ARP contém o endereço do solicitante, logo não é preciso informar todos os nós vizinhos.

9) **Explique as diferenças existentes nas traduções IPv4 para MAC e IPv6 para MAC.**

10) **Descreva diferenciando os métodos de acesso ao meio destacados abaixo:**

        a) ALOHA

        b) CSMA

        c) Token Ring

11) **Foi discutido em sala que se deve gerenciar Equipamentos e Serviços em uma rede. Dê um exemplo de equipamento e um de serviço que você gerenciaria. Descreva resumidamente como seria esse gerenciamento. Quais informações seriam contabilizadas? Que tipo de tratamento de falhas poderia acontecer?**

12) **Imagine um cenário em que estariam envolvidas 4 áreas de gerenciamento OSI, destacadas em sala. Descreva como essas áreas se relacionam na solução de um problema.**

13) **Faça uma descrição sucinta dos conceitos MPLS e VLAN. Evidencie as diferenças entre esses conceitos.**

14) **Compare o funcionamento do MPLS com redes de circuitos virtuais.**