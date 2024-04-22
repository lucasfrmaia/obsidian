
# Protocolo UDP

-  Uso de Datagrama
+ Mais libertário 
*  Sem garantia para camadas superiores
*  A aplicação interage diretamente com o IP
* Não possui verificações
	* Não há apresentação entre o UDP transmissão e o receptor
	* Utilizados em ataques, pois enviam pacotes sem apresentação
### Serviço effort

* O serviço effort dos seguimentos UDP podem ser:
	* Perdidos
	* Entregues em ordem aleatória para a aplicação

### Por que existe UDP?

* Usado em aplicações de multimedia continua
	* Tolerante a perdas
	* Sensiveis a taxas
	* Rapido (Possui pacotes pequenos)
	* Outros usos: (UDP, DNS e SNMP)

					     Pacote de 32 Bits:
--- 
			 Número da porta de Origem | Número da porta de Destino
-------------------------------------------------------------------------------------------------------------
				Outros Campos de Cabeçaçho
--------------------------------------------------------------------------
				  Dados da aplicação (Mensagem)
-------------------------------------------------------------------------------------------------------------

### Segurança UDP

* Implementação de transferência confiável sobre o UDP na camada  de aplicação
* Recuperação de especifica de cada aplicação

#### UDP Checksum

* Detecta erros (Exemplos bits trocados) no segmento transmitido
	* Transmissor
		* Trata o segmento como sequencia inteira de 16 bits
		* Se soma complemente de 1 do conteúdo do segmento
		* Transmissor coloca o valor do checksum no campo de checksum do UDP
	* Receptor
		* Computa o checksum recebido
			* Verifica se o checksum calculado é igual ao valor do campo do checksum

![[Pasted image 20240421214234.png]]

# Protocolo TCP

* **Ponto-a-ponto**: Envolve um transmissor e um receptor.
- **Confiabilidade**: O TCP garante a entrega confiável dos dados, com controle de fluxo e janelas de congestionamento.
- **Pipelined**: Permite a transmissão de vários pacotes sem confirmação.
- **Buffers de transmissão e recepção**: Armazenam dados temporariamente.
- **Dados full-duplex**: Transmissão bidirecional na mesma conexão.

1. **Buffers de Transmissão e Recepção**:
    - Os **buffers de transmissão** e **recepção** são áreas de memória usadas para armazenar dados temporariamente durante a comunicação.
    - **Buffer de transmissão**:
        - Armazena os dados que serão enviados pela conexão.
        - Ajuda a otimizar a transmissão, permitindo que o sistema organize os dados antes de enviá-los.
    - **Buffer de recepção**:
        - Armazena os dados recebidos da conexão.
        - Permite que o sistema processe os dados à medida que chegam.
        
1. **Dados Full-Duplex**:
    - No modo **full-duplex**, ambos os dispositivos podem transmitir e receber dados simultaneamente na mesma conexão.
    - Isso significa que não há necessidade de alternar entre transmissão e recepção.
 
1. **MSS (Maximum Segment Size)**:
    - O **MSS** é o tamanho máximo do segmento (payload) que um dispositivo pode aceitar de uma conexão de rede.
    
- Orientado à conexão: 
- Apresentação (troca de mensagens de controle) inicia o estado do transmissor e do receptor antes da troca de dados  
- Controle de fluxo: Transmissor não esgota a capacidade do receptor

### Características

1. **Orientado à Conexão**:
    - Isso significa que antes de iniciar a troca de dados, ocorre uma **fase de estabelecimento da conexão**.
    
2. **Apresentação (Troca de Mensagens de Controle)**:
    - A fase de apresentação inicia o estado do transmissor e do receptor antes da troca de dados.
    - É nesse momento que as entidades negociam parâmetros e estabelecem a conexão.

1. **Controle de Fluxo**:
    - O TCP implementa um mecanismo de **controle de fluxo**.
    - O objetivo é evitar que o transmissor sature a capacidade do receptor.

---
### Controle de Bits

1. **URG (Urgent)**:
    - O flag **URG** (Urgent) indica **dados urgentes**.
    - Embora pouco usado, ele serve para sinalizar que o pacote contém informações que devem ser tratadas com prioridade.
    - O campo de **ponteiro de urgência** no cabeçalho TCP especifica a posição do último byte de dados urgentes.
    
1. **ACK (Acknowledgment)**:
    - O flag **ACK** (Acknowledgment) é usado para **confirmação de recebimento**.
    - Quando definido como 1, indica que o pacote confirma o recebimento de dados anteriores.
    - O flag **ACK** é fundamental para garantir a integridade e a ordem dos dados durante a comunicação.

1. **PSH (Push)**:
    - O flag **PSH** (Push) é usado para **envio imediato de dados**.
    - Quando definido como 1, indica que os dados contidos no pacote devem ser entregues diretamente à aplicação, sem aguardar mais dados no buffer.

1. **RST, SYN, FIN**:
    - Esses são comandos relacionados ao **estabelecimento e término de conexões**:
        - **RST (Reset)**: Indica que a conexão está sendo encerrada abruptamente ou que o serviço não está aceitando mais solicitações.
        - **SYN (Synchronize)**: Usado para iniciar uma conexão. Durante o estabelecimento, o TCP envia um segmento com o flag SYN definido.
        - **FIN (Finish)**: Indica que a conexão está sendo encerrada.
        
1. **Internet Checksum**:
    - O **Internet Checksum** é um mecanismo usado para verificar a integridade dos dados transmitidos.
    - Ele é semelhante ao checksum usado no UDP.
    - O checksum é calculado a partir dos dados do segmento TCP e incluído no cabeçalho.

# Serviços 

### Controle de Fluxo:

1. **Definição**:
    - O controle de fluxo garante que o remetente não envie dados rápido demais para o receptor, evitando congestionamento.
    - O objetivo é ajustar a taxa de envio para corresponder à capacidade de recepção do destinatário.
    
1. **Mecanismos**:
    - **Janela deslizante**:
        - Permite o envio de vários segmentos sem esperar por confirmações.
        - O receptor informa a área disponível (janela de recepção) usando o valor RcvWindow nos segmentos.
    - **Go-Back-N**:
        - O remetente envia N pacotes sem esperar por reconhecimento.
        - Limita-se a N pacotes não reconhecidos.
    - **Repetição Seletiva**:
        - Evita retransmissões desnecessárias.
        - O remetente retransmite apenas os pacotes suspeitos de erro.


### Controle de Congestionamento:

1. **Definição**:
    - O controle de congestionamento é essencial para evitar sobrecarga na rede.
    - O TCP limita a taxa de transmissão para evitar congestionamento.
    
1. **Variáveis**:
    - **Janela de Congestionamento (Janela do TCP)**:
        - Determina quantos segmentos podem ser transmitidos sem confirmações.
        - Começa com o tamanho de um segmento e cresce exponencialmente.
        - Após um timeout, volta ao tamanho de um segmento.
        - Após 3 ACKs duplicados, o limiar é ajustado e a janela cresce linearmente.
    - **Limiar**:
        - Controla o crescimento da janela de congestionamento.
        - Define o ponto de transição entre controle lento e controle rápido.
        
1. **Fases**:
    - **Inicialização Lenta (Slow Start)**:
        - A taxa de transmissão começa pequena e cresce rapidamente.
        - A janela de congestionamento aumenta exponencialmente.
    - **Prevenção de Congestionamento (Congestion Avoidance)**:
        - Após ultrapassar o limiar, o crescimento da janela é linear.
        - Duração depende da não ocorrência de timeouts e aceitação pelo receptor.
    - **Timeouts**:
        - Se ocorrer um timeout, o limiar é reduzido e a janela volta ao tamanho de um segmento.
        - O crescimento recomeça exponencialmente.
        
1. **Congestionamento Pesado e Leve**:
    - **Pesado**:
        - ACKs repetidos levam à redução da janela pela metade.
    - **Leve**:
        - A janela cresce linearmente quando o limiar é ultrapassado.