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

    O IPv4 contém um cabeçalho de 20 a 32 bytes contendo 13 ou 14 campos -- dependendo da inclusão do campo **options** -- entre esses campos, os campos **Identification** (16 bits, identifica o grupo de datagramas IP), **Fragment Offset** (13 bits, informa quantos bits devem ser ignorados até o primeiro bit do conteúdo do datagrama) são utilizados na remontagem dos datagramas IP **[Talvez faltem campos aqui]**

4) **Como se obtém endereços IP? Como é garantido que não haja dois, ou mais, hosts na internet com o mesmo endereço IP?**

    O Endereço de IP pode ser obtido de duas formas:

    - O administrador do sistema pode definir o endereço de IP do equipamento.
    - O endereço de IP pode ser definido por um servidor DHCP de maneira dinâmica.

5) **Uma empresa possui 230 máquinas, mas apenas 110 endereços IP válidos. O que essa empresa pode fazer para colocar todas as máquinas na Internet? Descreva detalhadamente.**

6) **Por que existe o IP versão 6 (IPv6)? Descreva pelo menos três diferenças para o IPv4**

7) **Se a máscara 255.255.255.128 for usada com um endereço classe B, quantas sub-redes são criadas? Quantos hosts são possíveis em cada uma dessas sub-redes?**

8) **Defina uma máscara de rede para ser usada com um endereço classe A de forma a subdividi-la em 164 sub-redes. É possível se chegar a exatamente 164 sub-redes? Quantos hosts são possíveis em cada rede criada?**

9) **Uma empresa recebeu de seu provedor a faixa de endereços 126.237.89.0/14. A empresa precisa dividir essa faixa entre seus 12 departamentos/setores. Descreva como poderia ser a rede dessa empresa, mostre os endereços de rede utilizados, bem como 2 endereços IP válidos para cada uma dessas sub-redes. Pode-se fazer um desenho da rede para melhor visualização.**

10) **Descreva como pode ocorrer perda de pacotes me portas de entrada. Descreva como a perda de pacotes pode ser eliminada em portas de entrada (sem usar buffers infinitos).**

11) **Em uma rede local, que funciona apenas internamente a uma instituição, o técnico responsável determinou endereços IPs para as máquinas da forma que lhe pareceu melhor, sem respeitar endereços externos. Assim, uma das interfaces dessa rede recebeu endereço: 192.168.141.5/18.**
    
        a) Defina endereços IP para outras 3 interfaces dessa mesma rede.

        b) O endereço 192.168.130.1/18 está na mesma rede que a máquina citada acima? E o endereço 192.168.127.1/18? Explique.

        c) Devido ao acréscimo de várias novas máquinas, a instituição resolveu dividir a rede citada acima em três sub-redes. Estabeleça endereços de rede para essas 3 sub-redes. Estabeleça pelo menos 2 endereços IP pertencentes a cada uma dessas sub-redes.

12) **Existem sites e servidores que podem ser acessados como IPv4 e/ou IPv6. Como os roteadores lidam com isso?**

13) **Compare e aponte as diferenças entre os algoritmos de roteamento de estado de enlace e por vetor de distâncias.**

14) **Por que devo agrupar os roteadores em sistemas autônomos.**

15) **Por que são usados protocolos inter-AS e intra-AS diferentes na Internet?**

16) **Explique as técnicas de inundação não controlada, inundação controlada e spanning tree.**