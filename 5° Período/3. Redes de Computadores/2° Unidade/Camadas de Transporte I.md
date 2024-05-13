
# Modulo I - Introdução
## Camadas de Rede

1. **Camada de Transporte:**
    - Responsável por transportar segmentos do host transmissor para o receptor.
    - Fim-a-fim de mais baixo nível, ou seja, opera entre os sistemas finais.
    - Determina o roteamento dos pacotes.
    - Realiza saltos intermediários no caminho.
    - No lado transmissor, encapsula os segmentos em datagramas.
    - Repassa os datagramas entre enlaces de entrada e saída.
    - No lado receptor, entrega os segmentos à camada de transporte.
    
1. **Camada de Rede:**
    - Exclusiva dos roteadores (ou comutadores).
    - Desconsidera protocolos de transporte e aplicação.
    - Roteadores examinam campos de cabeçalho em todos os datagramas IP que passam por eles.
    - Esses campos definem o repasse de pacotes.
    
1. **Funções Adicionais da Camada de Rede:**
    - **Controle de Congestionamento:** Gerencia o fluxo de tráfego para evitar congestionamentos na rede.
    - **Negociação de Quality of Service (QoS):** Define prioridades para diferentes tipos de tráfego (por exemplo, voz, vídeo, dados) com base em requisitos de desempenho.
    - **Interconexão de Redes:** Permite a comunicação entre redes diferentes, como a interligação de redes locais (LANs) por meio de roteadores.

### Repasse e Roteamento

1. **Repasse de Pacotes:**
    - O repasse de pacotes é o processo pelo qual os roteadores conduzem pacotes entre os enlaces apropriados, da entrada para a saída.
    - Cada pacote é despachado ao seu destino ou sistema intermediário com base nas informações contidas em seu cabeçalho.
    
1. **Roteamento de Pacotes:**
    - O roteamento envolve o estabelecimento dos melhores caminhos (rotas) para encaminhar pacotes de um ponto a outro na rede.
    - Os roteadores utilizam algoritmos de roteamento para determinar como encaminhar pacotes.
    - Existem dois tipos principais de algoritmos de roteamento:
        - **Centralizado:** Um algoritmo central roda em um local central e descarrega informações de roteamento em cada roteador. Essa abordagem é menos comum.
        - **Descentralizado:** Algoritmos locais rodam em cada elemento de comutação de pacotes (roteador) para gerar a tabela de rotas. Exemplos incluem o algoritmo de vetor de distância e o algoritmo de estado de enlace.
    
1. **Tabela de Repasse:**
    - Cada roteador mantém uma tabela de repasse que contém informações sobre como encaminhar pacotes.
    - O roteador examina o cabeçalho do pacote para indexar valores relevantes na tabela.
    - O algoritmo de roteamento determina a inserção dessas informações na tabela.

## Estabelecimento de Conexão

1. **ATM (Asynchronous Transfer Mode):**
    - O ATM é uma tecnologia de comutação de pacotes que utiliza células fixas de tamanho pequeno (53 bytes).
    - Troca de mensagens entre roteadores ao longo do caminho para estabelecer conexões virtuais.
    - Antes de repassar pacotes de dados, os roteadores ATM estabelecem um estado para garantir recursos suficientes para o fluxo de dados.
    - As conexões ATM são virtuais e podem ser permanentes (PVC) ou comutadas (SVC).
    
1. **Frame Relay:**
    - O Frame Relay é uma tecnologia de comutação de pacotes que utiliza quadros (frames) para transmitir dados.
    - Também envolve troca de mensagens entre roteadores para estabelecer conexões virtuais.
    - Os roteadores Frame Relay estabelecem um estado antes de repassar pacotes de dados.
    - Oferece garantia de recursos (largura de banda) para fluxos de dados específicos.
    
1. **MPLS (Multiprotocol Label Switching):**
    - O MPLS é uma técnica de comutação de pacotes que utiliza rótulos (labels) para encaminhar pacotes.
    - A troca de mensagens entre roteadores MPLS ocorre para estabelecer conexões virtuais baseadas em rótulos.
    - Antes de repassar pacotes, os roteadores MPLS estabelecem um estado (rótulo) para cada fluxo de dados.
    - O MPLS oferece flexibilidade e eficiência na rede, permitindo diferentes classes de serviço (QoS).
    
1. **Conexões Virtuais:**
    - Todas essas tecnologias (ATM, Frame Relay e MPLS) utilizam conexões virtuais.
    - As conexões virtuais são estabelecidas entre hospedeiros ou roteadores.
    - Elas garantem recursos suficientes para o fluxo de dados, como largura de banda e qualidade de serviço.
    
1. **Diferença entre Camada de Transporte e Camada de Rede:**
    - A camada de transporte lida com a comunicação entre processos (por exemplo, entre aplicativos em sistemas finais).
    - A camada de rede lida com a comunicação entre hospedeiros ou roteadores, estabelecendo conexões virtuais para o repasse de pacotes.


---
# Modulo II - Serviços de Redes
## Modelos de Serviços de Redes

1. **Entrega Garantida:**
    - Assegura que o pacote chegará ao seu destino, mais cedo ou mais tarde.
    - Define restrições de tempo para a entrega, garantindo que o pacote não seja perdido.
    - Pode haver atrasos, mas a entrega é garantida.
    
1. **Entrega Garantida com Atraso Limitado:**
    - Semelhante à entrega garantida, mas com restrições de tempo mais rigorosas.
    - O pacote chegará ao destino dentro de um limite de tempo especificado.
    
1. **Entrega de Pacotes na Ordem:**
    - Assegura que os pacotes serão entregues no destinatário na ordem em que foram enviados/transmitidos.
    - Importante para aplicações que dependem da ordem dos pacotes, como streaming de vídeo.
    
1. **Largura de Banda Mínima Garantida:**
    - Emula o comportamento de um enlace de transmissão com uma taxa específica (por exemplo, 1 Mbps).
    - Garante que a largura de banda mínima seja mantida para o fluxo de dados.
    
1. **Jitter (Variação do Atraso) Máximo Garantido:**
    - Assegura um intervalo de tempo entre a transmissão de dois pacotes sucessivos no remetente igual à quantidade de tempo entre o recebimento dos dois pacotes no destino.
    - Evita grandes variações no atraso, o que é importante para aplicações sensíveis ao tempo.
    
1. **Serviços de Segurança:**
    - Provê a codificação da carga útil de todos os datagramas trocados entre remetente e destinatário.
    - Garante a confidencialidade e integridade dos dados transmitidos.

## Arquiteturas de Rede

1. **Rede ATM (Asynchronous Transfer Mode):**
    - A rede ATM é uma tecnologia de comutação de pacotes que oferece serviços além do modelo de melhor esforço da arquitetura TCP/IP.
    - Ela utiliza células de tamanho fixo (53 bytes) para transmitir dados.
    - Vamos explorar os modelos de serviço específicos da rede ATM:
    
1. **Constant Bit Rate (CBR):**
    - O CBR é um modelo de serviço na rede ATM que provê um fluxo de pacotes (células) com propriedades semelhantes a enlaces de transmissão dedicados de banda fixa.
    - Características do CBR:
        - Garante uma taxa de transmissão constante.
        - Há garantias contra perda de dados e atrasos.
        - A ordenação dos pacotes (células) é garantida.
        - Tendem a ter valores menores do que os acordados no estabelecimento da conexão.
        
1. **Available Bit Rate (ABR):**
    - O ABR é outro modelo de serviço na rede ATM.
    - Características do ABR:
        - Provê um fluxo de células a uma taxa mínima (MCR - Minimum Cell Transmission Rate).
        - Não permite a reordenação das células, embora não haja garantias contra perda de dados.
        - Haverá indicação de congestionamento.
    
1. **Arquiteturas de Rede Relacionadas:**
    - Além da rede ATM, existem outras arquiteturas de rede:
        - **Rede de Melhor Esforço (TCP/IP):**
            - Não oferece garantias específicas de qualidade de serviço.
            - Os pacotes são entregues conforme disponibilidade.
        - **Rede Ethernet:**
            - Baseada em comutação de quadros.
            - Amplamente utilizada em redes locais (LANs).
        - **Rede MPLS (Multiprotocol Label Switching):**
            - Utiliza rótulos para encaminhar pacotes.
            - Oferece diferentes classes de serviço (CoS).



## Questão de Projeto

- Os serviços oferecidos à camada de transporte devem:
- Ser independentes da tecnologia do roteador
- Protegê-la do conhecimento dos seguintes dados: número, tipo e topologias dos roteadores presentes
- Disponibilizar endereços de rede usando um plano de numeração uniforme, até mesmo entre LANs e WANs
    




---
# Modulo III - Organização de Rede
## Organização de Rede

- Analogia aos serviços da camada de transporte
- Orientado ou não a conexão
- Diferenças:
	- Serviços : entre hospedeiros
	- Sem escolhas: a rede oferece um ou outro
	- Implementação: roteadores núcleo da rede
    
## Circuitos Virtuais

1. **Analogia aos Circuitos Físicos da Rede Telefônica:**
    - Os circuitos virtuais (CVs) têm uma analogia com os circuitos físicos usados na rede telefônica.
    - Assim como os circuitos telefônicos dedicados, os CVs estabelecem uma conexão pré-definida entre remetente e destinatário.
    
1. **Características dos Circuitos Virtuais:**
    - **Rede Complexa e Segura:**
        - Os CVs são usados em redes complexas e seguras, como a rede ATM (Asynchronous Transfer Mode).
        - Eles oferecem serviços além do modelo de melhor esforço da arquitetura TCP/IP.
    - **Estabelecimento de Conexão:**
        - Antes que os dados possam fluir, há um processo de estabelecimento e término de conexão.
        - Cada pacote carrega um identificador do circuito virtual no cabeçalho, em vez do endereço do “host”, para o roteamento.
    - **Número do VC (Virtual Circuit):**
        - O VC é usado para rotear os pacotes ao longo do caminho virtual.
        - Pode ser alterado em cada enlace, pois a alocação de identificadores é local e não global.
    - **Tabela de Repasse:**
        - Em cada roteador, a tabela de repasse contém a tradução dos números de VC.
        - É atualizada a cada novo estabelecimento ou encerramento de um VC através de um roteador.
    - **Estado nos Roteadores:**
        - Cada roteador no caminho entre remetente e destinatário mantém estado para cada conexão estabelecida por ele.
    - **Recursos Alocados:**
        - Recursos do enlace e roteador (largura de banda, buffers) são alocados ao VC.
        - Isso oferece serviço de qualidade previsível, desde que os recursos reservados atendam aos requisitos da aplicação.
        
1. **Uso Atual e Limitações:**
    - Os CVs não são amplamente usados na Internet atualmente.
    - No entanto, eles ainda são aplicáveis em redes específicas, como ATM, frame-relay e X.25.





## Redes Datagrama 

1. **Redes de Datagrama:**
    - Nas redes de datagrama, não é estabelecida uma conexão prévia na camada de rede.
    - Os roteadores não mantêm informações de estado sobre conexões fim-a-fim.
    - O conceito de “conexão” não existe nessa camada.
    - Os pacotes (datagramas) são encaminhados para o endereço do host de destino.
    - Pacotes destinados ao mesmo destino podem seguir rotas diferentes.
    - Não há uso de circuitos virtuais (VCs) para roteamento.
    
1. **Regra da Concordância do Prefixo Mais Longo:**
    - Quando um roteador precisa escolher entre vários prefixos de destino, ele utiliza a regra da concordância do prefixo mais longo.
    - O roteador seleciona o prefixo que melhor se ajusta ao endereço de destino.

    - **Exemplos**:
        - Endereço de destino: `11001000 00010111 00010110 10100001`
            - Possíveis prefixos:
                - `11001000 00010111 00010110 10100000` (24 bits)
                - `11001000 00010111 00010110 10100001` (32 bits)
            - O roteador escolherá o prefixo mais longo (32 bits) para encaminhar o pacote.
        - Endereço de destino: `11001000 00010111 00011000 10101010`
            - Possíveis prefixos:
                - `11001000 00010111 00011000 10100000` (24 bits)
                - `11001000 00010111 00011000 10101010` (32 bits)
            - O roteador escolherá novamente o prefixo mais longo (32 bits).



## Rede Datagrama ou VCS?

1. **Diferenças entre Redes de Datagrama e Circuitos Virtuais:**
    - **Redes de Datagrama:**
        - Não há estabelecimento de conexão na camada de rede.
        - Roteadores não mantêm informações de estado fim-a-fim.
        - Pacotes são encaminhados para o endereço do host de destino.
        - Não há uso de circuitos virtuais (VCs).
    - **Circuitos Virtuais:**
        - Estabelecem conexões prévias na camada de rede.
        - Roteadores mantêm estado para cada conexão estabelecida.
        - Pacotes carregam identificadores de VC no cabeçalho.
        - Recursos são alocados ao VC, oferecendo serviço de qualidade previsível.

![[Pasted image 20240513144212.png]]



# Modulo IV - Estrutura de Roteamento

## Funções de um Roteador

- Repassar datagramas dos enlaces de entrada para os de saída  
- Executar algoritmo/protocolo de roteamento (OSPF, RIP, BGP)

## Arquitetura de um Roteador

![[Pasted image 20240513144358.png]]

## Portas de Entrada

1. **Funções da Camada de Enlace na Porta de Entrada:**
    - A porta de entrada de um roteador realiza funções da camada física para terminar um enlace físico.
    - Também executa as funções da camada de enlace necessárias para interoperar com as funções da camada de enlace do outro lado do enlace de entrada.
    - Desempenha o exame e o repasse, garantindo que o pacote seja encaminhado ao elemento de comutação do roteador e surja na porta de saída apropriada.
    
1. **Implementação das Camadas Física e de Enlace no Roteador:**
    - Cada porta de entrada do roteador implementa as camadas física e de enlace associadas a um enlace de entrada específico.
    - A determinação da porta de saída para a qual o pacote será repassado ocorre frequentemente na porta de entrada.
    - A escolha da porta de saída é baseada na tabela de repasse.
    
1. **Tabela de Repasse e Decisões de Repasse:**
    - A tabela de repasse é calculada pelo processador de roteamento.
    - É comum copiar a tabela de repasse para cada porta de entrada, permitindo decisões de repasse locais.
    - O repasse descentralizado evita gargalos de processamento em um único ponto no roteador.
    
1. **Processamento nas Portas de Entrada:**
    - Quando as portas de entrada não têm capacidade de processamento suficiente, um “servidor” pode desempenhar o papel de roteador.
    - O processador examina a tabela de repasse e transmite o pacote à porta de saída apropriada.
    - Idealmente, o processamento da porta de entrada deve operar na velocidade da linha para evitar atrasos.

1. **Otimização da Consulta à Tabela de Repasse:**
    - Consultar uma tabela de repasse extensa linearmente é impraticável.
    - Técnicas de armazenamento em estruturas de árvore permitem consultas mais eficientes.
    - A velocidade de consulta binária ainda não é suficiente para os requisitos atuais de roteamento.
    
1. **Memória de Conteúdo Endereçável (CAM) e Cache:**
    - A CAM permite retornar um endereço de 32 bits da tabela de repasse em tempo constante.
    - Roteadores modernos, como o Cisco 8500, usam CAM para acelerar as consultas.
    - Manter registros recentemente acessados em cache também melhora o desempenho.
## Elementos da Computação

1. **Elementos de Comutação:**
    - Os elementos de comutação conectam as portas de entrada do roteador às suas portas de saída.
    - Eles estão integralmente contidos no interior do roteador e são responsáveis pelo repasse (comutação) de pacotes.
    
1. **Tipos de Comutação:**
    - Existem três principais tipos de comutação:
        - **Comutação por Memória:**
            - O processador de roteamento copia um pacote do buffer da porta de entrada para a memória.
            - Realiza uma consulta à tabela de repasse.
            - Em seguida, efetua a cópia da memória para o buffer da porta de saída.
            - As portas de entrada e saída funcionam como dispositivos de entrada/saída de um sistema operacional tradicional.
        - **Comutação por Barramento:**
            - As portas de entrada transferem um pacote diretamente para a porta de saída por um barramento compartilhado.
            - Não há intervenção do processador de roteamento.
            - Os enlaces disputam acesso ao barramento.
            - A velocidade de comutação é limitada pela largura de banda do barramento.
            - Exemplo: Cisco 5600 utiliza barramento da placa-mãe de 32 Gbps, adequado para roteadores de acesso e corporativos.
        - **Comutação por Rede de Interconexão:**
            - Uma rede de interconexão de 2n barramentos conecta n portas de entrada com n portas de saída.
            - Exemplo: Cisco 12000 utiliza uma rede de interconexão que fornece até 60 Gbps pelo elemento de comutação.
            - Pode apresentar taxas ainda maiores quando os pacotes comutados têm tamanhos iguais.
    
## Portas de Saída

- Recupera os pacotes que foram armazenados na memória da porta de saída e os transmite pelo enlace de saída
- O processamento de enlace e a terminação da linha são as funcionalidades de camada de enlace e de camada física do lado remetente 
- Interagem com a porta de saída do outro lado do enlace de saída

## Repasse e Descarte de Pacotes

1. **Filas de Pacotes e Perda de Pacotes:**
    - Filas de pacotes podem se formar tanto nas portas de entrada quanto nas portas de saída dos roteadores.
    - A perda de pacotes pode ocorrer à medida que as filas crescem.
    - A falta de buffers disponíveis no roteador resulta em descarte de pacotes.
    
1. **Local de Descarte e Fatores Dependentes:**
    - O local exato do descarte (nas filas de entrada ou saída) depende de:
        - Carga de tráfego.
        - Velocidade relativa do elemento de comutação.
        - Taxa de linha.
        - Taxa do elemento de comutação (velocidade de movimentação de pacotes de entrada para saída).
    
1. **Buffering e Tamanho do Buffer:**
    - O buffering ocorre quando a taxa de chegada via comutador excede a taxa da linha de saída.
    - O tamanho médio do buffer deve ser igual ao tempo de ida e volta (RTT) típico.
    - Recomendações recentes consideram o número de fluxos TCP para dimensionar o buffer.
    
1. **Escalonamento de Pacotes e Políticas de Descarte:**
    - O escalonador de pacotes deve escolher um pacote da fila para transmitir.
    - Políticas como FCFS (First Come First Served) ou WFQ (Weighted Fair Queuing) são usadas para escolher o pacote.
    - Políticas de descarte, como AQM (Active Queue Management), também são aplicadas para evitar congestionamento.
    
1. **Bloqueio de Cabeça de Fila (HOL Blocking):**
    - Se um pacote na fila de entrada está bloqueado por outro pacote na cabeça da fila de saída, ocorre o HOL blocking.
    - Isso pode levar a filas de entrada crescentes e perda significativa de pacotes.
    




    