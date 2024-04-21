
# Protocolos

O **Protocolo UDP** (User Datagram Protocol) é um protocolo de transporte da Internet que é conhecido por ser “sem gorduras” e “sem frescuras”. Ele não oferece garantias para as camadas superiores e permite que a aplicação interaja quase diretamente com o IP. O serviço UDP é baseado no princípio de “melhor esforço”, o que significa que os segmentos UDP podem ser perdidos ou entregues fora de ordem para a aplicação.

Algumas características importantes do UDP incluem:

- **Não orientado a conexão**: Não há verificações de conexão entre o transmissor e o receptor.
- **Sem apresentação**: Não há troca de mensagens de controle entre o UDP transmissor e o receptor.
- **Tratamento independente de segmentos**: Cada segmento UDP é tratado de forma independente dos outros.
- **Utilização em ataques**: O UDP é frequentemente usado em ataques, pois permite o envio de diversos pacotes sem apresentação.

Mas por que existe o UDP? Ele é amplamente utilizado por aplicações de multimídia contínua, como streaming de áudio e vídeo, pois é tolerante à perda e sensível à taxa. Além disso, sua simplicidade e rapidez (devido ao menor tamanho dos pacotes) o tornam uma escolha popular. Além das aplicações de multimídia, o UDP também é usado em serviços como DNS e SNMP.

O UDP não oferece segurança por si só, mas é possível implementar transferência confiável sobre UDP na camada de aplicação, com recuperação de erros específica para cada aplicação. O UDP também utiliza um checksum para detectar erros, como bits trocados, nos segmentos transmitidos.

Já o **Protocolo TCP** (Transmission Control Protocol) é um protocolo de transporte confiável, orientado à conexão e baseado em fluxo de bytes sequencial. Algumas características do TCP incluem:

- **Ponto-a-ponto**: Envolve um transmissor e um receptor.
- **Confiabilidade**: O TCP garante a entrega confiável dos dados, com controle de fluxo e janelas de congestionamento.
- **Pipelined**: Permite a transmissão de vários pacotes sem confirmação.
- **Buffers de transmissão e recepção**: Armazenam dados temporariamente.
- **Dados full-duplex**: Transmissão bidirecional na mesma conexão.

O TCP também utiliza números de sequência para rastrear os bytes transmitidos e ACKs (acknowledgments) para confirmar o recebimento dos dados. Além disso, o estabelecimento de conexão no TCP envolve troca de mensagens de controle, como os segmentos SYN e ACK.

1. **Controle de Fluxo**:
    - Garante que os dados sejam entregues ao destinatário de forma controlada.
    - Utiliza buffers para evitar que o remetente esgote os buffers de recepção enviando dados muito rapidamente.
    - O conceito de “speed-matching” busca ajustar a taxa de envio à taxa de consumo da aplicação receptora.
    - A variável de janela é mantida e alterada conforme a velocidade de consumo.
    - O destinatário informa a área disponível (RcvWindow) nos segmentos, e o remetente limita os dados dentro dessa janela.
    
1. **Métodos de Controle de Fluxo**:
    - **Pare e Espere**:
        - Envia um segmento por vez e espera pelo reconhecimento antes de enviar o próximo.
    - **Janela Deslizante**:
        - Envia vários segmentos sem esperar confirmação do receptor.
    - **Go-Back-N**:
        - O remetente envia N pacotes sem esperar por reconhecimento, mas limita-se a N pacotes não reconhecidos.
    - **Repetição Seletiva**:
        - Evita retransmissões desnecessárias, retransmitindo apenas os pacotes suspeitos de erro.

# **Controle de Congestionamento**

1. **Tamanho da Janela de Congestionamento (w)**:
    - O TCP controla a taxa de transmissão limitando o número de segmentos transmitidos sem confirmações.
    - O tamanho da janela de congestionamento é o número máximo de segmentos não confirmados.
    - É determinado pelo mínimo entre os tamanhos das janelas de congestionamento e do receptor.
    
1. **Fases do Controle de Congestionamento**:
    - **Inicialização Lenta (Slow Start)**:
        - Começa com o tamanho de um segmento.
        - A taxa de transmissão cresce exponencialmente.
    - **Prevenção de Congestionamento (Congestion Avoidance)**:
        - Após ultrapassar o limiar, o crescimento da janela é linear.
        - Duração depende da não ocorrência de timeouts e aceitação pelo receptor.
    
1. **Ajustes de Limiar**:
    - Timeout: Limiar é configurado como metade do tamanho atual da janela de congestionamento.
    - 3 ACKs duplicados: Limiar é ajustado para metade do tamanho atual da janela.
    
1. **Congestionamento Pesado e Leve**:
    - ACKs repetidos causam queda pela metade na janela de congestionamento.
    - O controle visa evitar congestionamento excessivo.
