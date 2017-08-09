# Lista de exercícios 4
## Camada de rede

1) **Qual a diferença entre rotear e repassar?**
    
    Rotear signifca encontrar encontrar um caminho que será feito pelo pacote para sair de sua origem e chegar em seu destino. Isso envolve a execução de algoritmos de roteamento. Já o repasse acontece quando um pacote é movido da entrada para a saída apropriada do roteador.

2) **Cite pelo menos três protocolos da camada de rede e o objetivo de cada um deles.**

    - **IP**: protocolo de transferência de datagramas pela rede. Esse protocolo contém funções para roteamento de pacotes.

    - **ICMP**: protocolo para envio de mensagens de erro e informações operacionais entre dispositivos da rede (roteadores inclusos).

    - **RIP**: protocolo mais antigo de roteamento, ele contém um mecanismo para impedir loop na rede. Este protocolo utiliza a contagem de dispositivos em que o pacote passou. Caso esse contador ultrapasse um limite (15), o pacote é descartado, pois o protocolo entende que o pacote entrou em um loop de roteamento.

    - **OSPF**: protocolo de roteamento para o IP que utiliza o algoritmo de Dijkstra para encontrar o menor caminho entre os nós de início e fim.

    - **BGP**: protocolo de roteamento que utiliza o algoritmo de Bellman-Ford (vetor de distâncias) para encontrar o melhor caminho entre os nós de início e fim.

3) **Qual o tamanho do cabeçalho IP? Quais de seus campos são utilizados na remontagem de datagramas fragmentados?**

    O IPv4 contém um cabeçalho de 20 a 32 bytes contendo 13 ou 14 campos -- dependendo da inclusão do campo **options** -- entre esses campos, os campos **Identification** (16 bits, identifica o grupo de datagramas IP), **Fragment Offset** (13 bits, informa qual é o número do primeiro byte do datagrama) são utilizados na remontagem dos datagramas IP.

4) **Como se obtém endereços IP? Como é garantido que não haja dois, ou mais, hosts na internet com o mesmo endereço IP?**

    O Endereço de IP pode ser obtido de duas formas:

    - O administrador do sistema pode definir o endereço de IP do equipamento.
    - O endereço de IP pode ser definido por um servidor DHCP de maneira dinâmica.

    A internet é formada por sub-redes. Cada sub-rede recebe uma faixa de IPs que ela pode utilizar, e a sub-rede fica responsável por distribuir os ips de forma que nenhum dispositivo de sua rede tenha um IP igual a outro dispositivo da mesma rede. Como toda faixa de IP é única, se todas as sub-redes manterem o controle de seus IPs, não haverá chance de existir IPs duplicados na internet. **[Não tenho certeza nessa resposta]**

5) **Uma empresa possui 230 máquinas, mas apenas 110 endereços IP válidos. O que essa empresa pode fazer para colocar todas as máquinas na Internet? Descreva detalhadamente.**

    Pode-se utilizar alguns *Network Address Translation* (NATs) para fazer a tradução dos IPs da rede local. O NAT funciona da seguinte maneira, um dispositivo qualquer identificado pelo IP (x.x.x.x:yy) envia um pacote, esse pacote passa pelo NAT, e este faz a tradução do IP, substituindo o endereço do dispositivo pelo seu próprio IP e porta e armazena em sua tabela a relação entre o IP:porta do NAT e o IP:porta do dispositivo. Após fazer isso, o NAT envia a requisição. Quando um pacote chega para um dispositivo da rede que contém o NAT, o NAT recebe esse pacote e faz a substituição do IP:porta pelo IP:porta do dispositivo (utilizando sua tabela de tradução) e repassa o pacote ao dispositivo.

6) **Por que existe o IP versão 6 (IPv6)? Descreva pelo menos três diferenças para o IPv4**

    O IPv4 suporta apenas 4.3 bilhões de IPs, e hoje existem mais dispositivos do que IPs válidos, portanto, o IPv6 foi criado para que novos dispositivos possam se conectar à internet.

    Diferenças:

        1. Mudança no cabeçalho para incorporar mecanismos de qualidade de serviço.
        2. Remoção do checksum para diminuir tempo de processamento
        3. Campo **options** é adicionado em cabeçalhos suplementares indicados pelo campo **Next header** para diminuir tamanho gasto pelo cabeçalho no datagrama.


7) **Se a máscara 255.255.255.128 for usada com um endereço classe B, quantas sub-redes são criadas? Quantos hosts são possíveis em cada uma dessas sub-redes?**

    Fazendo a distribuição dos bits da máscara, obtemos:
    ```
    11111111.11111111.11111111.10000000
    ```
    Podemos notar que o ultimo byte contém apenas 1 bit preenchido com 1, portanto, podemos fizer que temos ![equation](http://latex.codecogs.com/gif.latex?2^1) subredes que contém ![equation](http://latex.codecogs.com/gif.latex?2^7) endereços de IP em cada sub-rede.  

8) **Defina uma máscara de rede para ser usada com um endereço classe A de forma a subdividi-la em 164 sub-redes. É possível se chegar a exatamente 164 sub-redes? Quantos hosts são possíveis em cada rede criada?**

    Não é possível alcançar exatamento 164 sub-redes, pois o número de subredes é um na forma ![equation](http://latex.codecogs.com/gif.latex?2^n). Uma máscara que consegue ser dividida em 256 sub-redes pode ser usada para criar uma rede para ser dividida em 164 sub-redes. A máscara `255.255.0.0/16` é capaz de criar até 256 sub-redes capazes de comportar 254 endereços de IP em cada (descontando os endereços da rede e de broadcast)

9) **Uma empresa recebeu de seu provedor a faixa de endereços 126.237.89.0/14. A empresa precisa dividir essa faixa entre seus 12 departamentos/setores. Descreva como poderia ser a rede dessa empresa, mostre os endereços de rede utilizados, bem como 2 endereços IP válidos para cada uma dessas sub-redes. Pode-se fazer um desenho da rede para melhor visualização.**

    Fazendo a divisão de bits da máscara, obtemos o número `1111110.11101100.00000000.00000000`, que é equivalente a `126.236.0.0/14`. Para dividr a faixa para 12 departamentos, serão necessários 4 bits para representar o número do departamento, portanto, a nova máscara da rede será: `1111110.111011xx.xx000000.00000000`.

    Ips válidos para cada departamento:
        
        01) Endereço de rede:        126.236.0.0
            Endereço de broadcast:   126,236.63.255

        02) Endereço de rede:        126.236.64.0
            Endereço de broadcast:   126.236.127.255

        03) Endereço de rede:        126.236.128.0
            Endereço de broadcast:   126.236.191.255

        04) Endereço de rede:        126.236.192.0
            Endereço de broadcast:   126.236.255.255

        05) Endereço de rede:        126.237.0.0
            Endereço de broadcast:   126.237.63.255

        06) Endereço de rede:        126.237.64.0
            Endereço de broadcast:   126.237.127.255

        07) Endereço de rede:        126.237.128.0
            Endereço de broadcast:   126.237.191.255

        08) Endereço de rede:        126.237.192.0
            Endereço de broadcast:   126.237.255.255

        09) Endereço de rede:        126.238.0.0
            Endereço de broadcast:   126.238.63.255

        10) Endereço de rede:        126.238.64.0
            Endereço de broadcast:   126.238.127.255

        11) Endereço de rede:        126.238.128.0
            Endereço de broadcast:   126.238.191.255

        12) Endereço de rede:        126.238.192.0
            Endereço de broadcast:   126.238.255.255



10) **Descreva como pode ocorrer perda de pacotes en portas de entrada. Descreva como a perda de pacotes pode ser eliminada em portas de entrada (sem usar buffers infinitos).**

    A perda de pacotes em portas de entrada ocorre quando a rede interna transfere mais pacotes do que o switch consegue enviar para a rede externa. Por esse motivo, o `throughput` não é alto o suficiente e, eventualmente, o buffer de pacotes fica cheio e o switch é forçado a rejeitar pacotes na porta de entrada. Isso causa a perda de pacotes. **[Como resolver?]**

11) **Em uma rede local, que funciona apenas internamente a uma instituição, o técnico responsável determinou endereços IPs para as máquinas da forma que lhe pareceu melhor, sem respeitar endereços externos. Assim, uma das interfaces dessa rede recebeu endereço: 192.168.141.5/18.**
    
        a) Defina endereços IP para outras 3 interfaces dessa mesma rede.

        b) O endereço 192.168.130.1/18 está na mesma rede que a máquina citada acima? E o endereço 192.168.127.1/18? Explique.

        c) Devido ao acréscimo de várias novas máquinas, a instituição resolveu dividir a rede citada acima em três sub-redes. Estabeleça endereços de rede para essas 3 sub-redes. Estabeleça pelo menos 2 endereços IP pertencentes a cada uma dessas sub-redes.
    
    Fazendo a distribuição de bits do endereço, temos: `11000000.10101000.10000000.00000000/18` e sabemos que existem ![equation](http://latex.codecogs.com/gif.latex?2^2) subredes, pois temos 2 bits para representar o conjunto de subredes. O endereço `192.168.141.5` se encontra na terceira sub-rede (bits 10).

        a) 192.168.128.1, 192.168.128.2, 192.168.128.3

        b) Não, pois quando se olha os bits do ip: 11000000.10101000.10000010.00000101, podemos notar que os bits 16 e 17 são 10, enquanto os bits 16 e 17 do ip 192.168.127.1 são 01.

        c) Máscara: 192.168.128.0/20
            
            1. Endereço da rede:        192.168.128.0
               Endereço de broadcast:   192.168.143.255

            2. Endereço de rede:        192.168.144.0
               Endereço de broadcast:   192.168.159.255

            3. Endereço de rede:        192.168.160.0
               Endereço de broadcast:   192.168.175.255

12) **Existem sites e servidores que podem ser acessados como IPv4 e/ou IPv6. Como os roteadores lidam com isso?**
    Podemos citar três principais mecanismo para lidar com tal transição, sendo eles:
    ```
    **Pilha dupla:** consiste na convivência do IPv4 e do IPv6 nos mesmos equipamentos, de forma nativa
    simultâneamente. Essa técnica é a técnica padrão escolhida para a transição para IPv6 na Internet e deve ser
    usada sempre que possível;
    **Tunelamento:** IPv6 transportado dentro de pacotes IPv4 entre roteadores IPv4;
    **Tradução:** Permitem que equipamentos usando IPv6 comuniquem-se com outros que usam IPv4, por meio da
    conversão dos pacotes.
    ```

13) **Compare e aponte as diferenças entre os algoritmos de roteamento de estado de enlace e por vetor de distâncias.**
    ```
    **Estado de Enlace:** faz uso do algorítmo de Dijkstra para computar caminhos de menor custo de um nó (fonte) para todos os outros nós, onde, a topologia de rede e custo dos enlaces são conhecidos por todos os nós, ou seja, todos os nós têm a mesma informação, sendo que tal informação é disseminada via link state broadcast.
    **Vetor Distâncias:** faz uso do algorítmo de  Bellman-Ford (programação dinâmica) para computar caminhos de menor custo de um nó (fonte) para todos os seus vizinhos. Cada nó envia periodicamente sua própria estimativa de vetor de distância aos vizinhos, quando o nó x recebe nova estimativa de DV (Distance Vector) do vizinho, ele atualiza seu próprio DV usando a equação Bellman-Ford: dx(y) = min {c(x,v) + dv(y)}.
    ```

14) **Por que devo agrupar os roteadores em sistemas autônomos.**

    Imagine um cenário onde exista 200 milhões de roteadores em uma mesma rede, tal quantidade tornaria impossível armazenar todos os destinos numa única tabela de rotas e as  mudanças na tabela de rotas irão congestionar os enlaces, por esse motivos e outros devo agrupar os roteadores em sistemas autônomos, permitindo que cada AS trabalhe como uma sub-rede idependente, onde, roteadores no mesmo AS rodam o mesmo protocolo de roteamento e roteadores em diferentes AS podem rodar diferentes protocolos de roteamento, permitindo que cada administração de rede pode controle o roteamento em sua própria rede.
 

15) **Por que são usados protocolos inter-AS e intra-AS diferentes na Internet?**
   
    Os protocolos inter-AS são usada dentro de um mesmo AS e em suma principal papel é estabelecer  entradas para destinos externos de uma AS (AS diferentes), por outro lado os protocolos intra-AS além de possuirem papel de estabelecer entradas para destinos externos também estabelece entradas para destinos internos (Dentro de uma mesma AS). 
    
    Podemos citar como principal motivo de ser usado protocolos diferentes para roteamento inter-AS e intra-AS o fato de que a administração de rede quer ter controle sobre como seu tráfego é roteado e sobre quem roteia através da sua rede logo usára um protocolo Inter-AS baseado em suas políticas, por outro lado o roteamento inter-AS possuem administração única (Dentro de uma mesma AS), então não são necessárias políticas de decisão, logo a maior preocupação nesse caso seria desempenho, por esses motivos e outros nasce a necessdiade de usar protocolos diferente para roteamento inter-AS e intra-AS.


16) **Explique as técnicas de inundação não controlada, inundação controlada e spanning tree.**
    ```
    **Inundação não controlada:** quando nó recebe pacotes de broadcast, envia cópia para todos os vizinhos.
    **Inundação não controlada:** nó somente faz broadcast com o pacote se já não tiver feito antes com o mesmo pacote.
    **Spanning Trees:** primeiro é construído uma árvore geradora (conectando todos os roteadores com membros locais do grupo mcast), nós encaminham cópias somente ao longo da árvore geradora, o que faz com que nenhum pacote redundante recebido por nenhum nó.
    ```