# Modulo I - Protocolo IP
## Protocolo IP

- Versões em Uso:
	- IPv4 (RFC 791) 
	- IPv6 (RFC 2460; RFC 4291)

- Principais funcionalidades:
	- Endereçamento
	- Formato dos datagramas
	- Tratamento dos pacotes
    
## Componentes de Rede

- Protocolo IP (Internet Protocol): conjunto de regras e procedimentos que governam a troca de datagramas IP entre dispositivos pares 
- Componente de Roteamento: determina o caminho que o datagrama irá percorrer desde o remetente até o destinatário 
- Dispositivo para Comunicação de Erros: tem como principal elemento o Protocolo ICMP (Internet Control Message Protocol)

## Formato do Datagrama IP

1. **Versão (4 bits):**
    - Especifica a versão do protocolo do datagrama.
    - O roteador utiliza a versão para determinar como interpretar o restante do datagrama.
    - O datagrama IPv4 tem uma versão de 4 bits.
    
1. **Comprimento do Cabeçalho (IHL) (4 bits):**
    - Determina onde os dados começam no datagrama.
    - Um datagrama IPv4 pode conter um número variável de opções, incluídas no cabeçalho.
    - A maioria dos datagramas IP não contém opções.
    - O tamanho típico do cabeçalho é de 20 bytes.
    
1. **Tipo de Serviço (TOS):**
    - Diferencia diferentes tipos de datagramas IP (baixo atraso, alta vazão ou confiabilidade).
    - Composto por DSCP (8 bits) e ECN (2 bits).
    - DSCP (Differentiated Services Code Point) permite classificar o tráfego.
    - ECN (Explicit Congestion Notification) possibilita notificação de congestionamento sem perda de pacotes.
    
1. **Comprimento do Datagrama (16 bits):**
    - Define o comprimento total do datagrama em bytes (cabeçalho + dados).
    - O tamanho máximo teórico é de 65.535 bytes, mas datagramas raramente são maiores que 1.500 bytes.
    
1. **Identificação (16 bits):**
    - Usada para identificação unívoca de fragmentos pertencentes ao mesmo datagrama.
    - Flags (3 bits) controlam e identificam fragmentos:
        - 0 (Reservado)
        - 1 (Don’t Fragment - DF)
        - 2 (More Fragments - MF)
    
1. **Fragment Offset (13 bits):**
    - Relacionado à fragmentação do datagrama IPv4 (IPv6 não permite fragmentação).
    - Tempo de Vida (TTL) (8 bits):
        - Número de saltos entre máquinas antes de descartar o pacote.
    
1. **Protocolo de Camada Superior (8 bits):**
    - Indica o protocolo da camada de transporte (TCP, UDP, SCTP, RTP etc.).
    - Permite a ligação entre as camadas de rede e transporte.
    
1. **Soma de Verificação do Cabeçalho (Header Checksum) (16 bits):**
    - Permite que o roteador detecte erros de bits no datagrama IP.
    - Calculada tratando cada 2 bytes do cabeçalho como um número e realizando uma soma em complemento 1.
    - Se o valor calculado não corresponder ao valor do campo de soma de verificação, o datagrama é descartado.
    
1. **Endereço de Origem/Destino (32 bits):**
    - Representam as interfaces de rede do remetente e destinatário.
    
1. **Opções (0 a 40 bits):**
    - Permite ampliar o cabeçalho do datagrama IP, mas raramente é utilizado devido à sobrecarga.
    - Na versão IPv6, o campo de opções foi descartado.

1. **Dados (0 a 65.515 bytes):**
    - Contém o segmento da camada de transporte (TCP, UDP, SCTP, RTP etc.).
    - Se o campo de opções for 0 bytes, o restante do campo é usado para os dados (payload).
    - Por exemplo, se a carga for um segmento TCP, teremos 40 bytes de cabeçalho TCP mais a mensagem da camada de aplicação.

## Restrições de Datagrama IP

1. **Quadros Ethernet (802.3 e 802.1Q):**
    - Na camada física, os quadros Ethernet (também conhecidos como frames) são usados para transportar dados.
    - Esses quadros têm um tamanho mínimo de 72 bytes e um tamanho máximo de 1526 bytes.
    - Os quadros Ethernet 802.1Q são usados para redes VLAN (Virtual Local Area Network) e podem ter tamanhos semelhantes.

1. **Maximum Transmission Unit (MTU):**
    - O MTU é a quantidade máxima de dados que um quadro da camada de enlace (como o Ethernet) pode carregar.
    - Ao longo de uma rota entre remetente e destinatário, pode haver diferentes enlaces, cada um com MTUs diferentes.
    - O MTU limita o comprimento máximo do datagrama IP.
    - Problemas surgem quando um datagrama é encaminhado por diferentes enlaces com MTUs variados.
    
1. **Fragmentação de Datagramas IP:**
    - Quando um datagrama IP é maior que o MTU de um enlace, ele precisa ser fragmentado.
    - A solução é dividir o datagrama em 2 ou mais fragmentos IP e enviá-los através do enlace, respeitando a MTU desse enlace.
    - Os fragmentos precisam ser reconstruídos antes de serem entregues à camada de transporte no destino.

## Fragmentação de Datagramas IP

1. **Identificação e Flags:**
    - Quando um datagrama é montado no remetente, ele recebe um identificador juntamente com os endereços de origem e destino.
    - A cada novo datagrama com o mesmo endereço de origem e destino, o identificador é incrementado pelo remetente.
    - O destinatário, ao receber datagramas do mesmo remetente, examina os identificadores para determinar quais são fragmentos.
    - O datagrama fragmentado contém a flag ajustada para “1” para todos os fragmentos, exceto para o último fragmento do datagrama original.
    
1. **IPv4 vs. IPv6:**
    - No IPv4:
        - O campo de identificação é usado principalmente para identificar fragmentos pertencentes ao mesmo datagrama.
        - As flags (3 bits) controlam e identificam fragmentos:
            - 0 (Reservado)
            - 1 (Don’t Fragment - DF)
            - 2 (More Fragments - MF)
    - No IPv6:
        - Não permite fragmentação. O remetente deve garantir que o datagrama não exceda o MTU da rede.
        
1. **Exemplo de Fragmentação:**
    - Suponha um datagrama de 4000 bytes chegando a um roteador que deve repassá-lo a um enlace com MTU de 1500 bytes.
    - Cabeçalho de 20 bytes + Payload de 3980 bytes = 4000 bytes.
    - O datagrama original com identificação “777” precisa ser dividido em 3 fragmentos, cujo tamanho deve ser múltiplo de 8 bytes.
    
1. **Reconstrução no Destino:**
    - No destino, a carga útil do datagrama é passada para a camada de transporte somente após a reconstrução do datagrama original.
    - Se um dos fragmentos não chegar ao destino, o datagrama é descartado e não entregue à camada de transporte.
    
1. **Importância e Riscos:**
    - A fragmentação desempenha um papel importante na união de diferentes tecnologias da camada de enlace.
    - Roteadores e hosts são projetados para acomodar a fragmentação e o reagrupamento.
    - No entanto, a fragmentação pode ser explorada para criar ataques de negação de serviço (DoS) se os sistemas não estiverem preparados para tratar esses fragmentos inesperados.


# Modulo II - Endereçamento IPv4

## Endereçamento IPv4

- Um datagrama IP exige que cada interface tenha o seu próprio endereço IP, assim, 01 endereço IP está associado a 01 interface
- Cada endereço tem 32 bits
- São possíveis 232 endereços IP possíveis (cerca de 4 bilhões)
- Escritos em notação decimal separado por pontos
	- Por exemplo: 193.32.216.9
    
## Blocos de Endereço

1. **Provedor de Serviço de Internet (ISP):**
    - O ISP fornece blocos de endereços IP que já estão alocados.
    - O ISP divide seu bloco de endereços em outros blocos para distribuição.
    - Quando há escassez de espaço de endereçamento, técnicas como NAT (Network Address Translation) são usadas para traduzir endereços internos para externos.
    
1. **Classes de Endereços IP:**
    - Classe A: Primeiro bit é 0.
    - Classe B: Primeiros dois bits são 10.
    - Classe C: Primeiros três bits são 110.
    - Classe D (endereço multicast): Primeiros quatro bits são 1110.
    - Classe E (endereço especial reservado): Primeiros quatro bits são 1111.
    
1. **Intervalos de Endereços para Classes:**
    - A: 10.0.0.1 a 10.255.255.254 (16.777.216 endereços por rede).
    - B: 172.16.0.1 a 172.31.255.254 (65.536 endereços por rede).
    - C: 192.168.0.1 a 192.168.255.254 (256 endereços por rede).
    - D (Multicast): 224.0.0.0 a 239.255.255.255.
    - E (Uso futuro; testes): 240.0.0.0 a 255.255.255.254.
    
1. **CIDR (Classless InterDomain Routing):**
    - O prefixo de rede é definido pelos “x” bits mais significativos do endereço IP.
    - O formato do endereço é a.B.C.D/x, onde x é o número de bits na parte de rede do endereço.
    
1. **Endereços Especiais:**
    - 0.0.0.0: Este host.
    - 0.0.0.124: Host 124 nesta rede.
    - 255.255.255.255: Todos os hosts desta rede.
    - N.N.N.255: Todos os hosts da rede.
    - 127.X.X.X (Loopback).
    
1. **Endereços Inválidos para Hosts:**
    - 10.1.0.0: O IP do host não pode ser 0.
    - 10.1.0.255: O IP do host não pode ser 255.
    - 10.123.255.4: A sub-rede não pode ter valor 255.
    - 0.12.16.89: Parte do endereço não pode ter valor 0.
    - 255.9.56.45: Parte do endereço não pode ter valor 255.
    - 10.34.255.1: Parte do endereço não pode ter valor 255.

## Protocolo DHCP

1. **Funcionamento do DHCP:**
    - O DHCP permite que um host receba um endereço IP dinâmico automaticamente.
    - O processo envolve as seguintes etapas:
        - **Descoberta do Servidor DHCP:**
            - O cliente envia uma mensagem de descoberta para encontrar servidores DHCP disponíveis na rede.
        - **Oferta(s) dos Servidores DHCP:**
            - Os servidores DHCP respondem com ofertas de configuração, incluindo endereços IP disponíveis.
        - **Solicitação DHCP:**
            - O cliente escolhe uma oferta e envia uma solicitação para obter o endereço IP.
        - **Confirmação DHCP (ACK):**
            - O servidor confirma a alocação do endereço IP ao cliente.
            
1. **Problemas do DHCP:**
    - **Segurança:**
        - As mensagens DHCP não são autenticadas.
        - Isso significa que alguém pode forjar um servidor DHCP ou um cliente.
        - Clientes não podem confiar plenamente nos servidores e vice-versa.
    - **Configuração em Redes com Múltiplos Servidores:**
        - Quando há mais de um servidor DHCP na rede:
            - Os servidores não podem trocar informações diretamente.
            - Não existe um protocolo específico para comunicação entre servidores DHCP.
            - Os servidores devem ter espaços de endereçamento disjuntos para evitar a distribuição de IPs duplicados.
            - A configuração dos servidores é feita manualmente.

## Tradução de Endereço

1. **Motivação para o NAT:**
    - Redes locais podem utilizar apenas um endereço IP público.
    - Vantagens:
        - Não é necessário alocar uma gama de endereços do ISP; apenas um endereço IP é usado para todos os dispositivos internos.
        - Alterações nos endereços dos dispositivos na rede local não precisam ser notificadas ao mundo exterior.
        - Mudanças de ISP não afetam os endereços dos dispositivos na rede local.
        - Dispositivos internos não são explicitamente endereçáveis ou visíveis pelo mundo exterior, proporcionando segurança adicional.
        
1. **Tradução de Endereços de Saída (Outbound NAT):**
    - Quando datagramas saem da rede local:
        - O NAT substitui o (endereço IP de origem, porta #) de cada datagrama pelo (endereço IP do NAT, nova porta #).
        - Clientes/servidores remotos respondem usando o (endereço IP do NAT, nova porta #) como endereço de destino.
        - O NAT mantém uma tabela de tradução, lembrando cada (endereço IP de origem, porta #) e seu par de tradução (endereço IP do NAT, nova porta #).
        
1. **Tradução de Endereços de Entrada (Inbound NAT):**
    - Quando datagramas chegam à rede local:
        - O NAT substitui o (endereço IP do NAT, nova porta #) nos campos de destino de cada datagrama pelos correspondentes (endereço IP de origem, porta #) armazenados na tabela NAT.
         
1.  **Problemas do NAT**
	- Roteadores deveriam processar somente até a camada de rede  
	- Violação do argumento fim-a-fim 
	- A possibilidade de NAT deve ser levada em conta pelos desenvolvedores de aplicações (por exemplo,aplicações P2P)
	- A escassez de endereços deveria ser resolvida pelo IPv6

# Modulo III - Protocolo ICMP

## Protocolo ICMP

1. **Funcionamento do ICMP:**
    - O ICMP é usado por hosts e roteadores para comunicar condições de erro ao processar datagramas no nível de rede.
    - Exemplos de mensagens ICMP:
        - Relato de erro: informa sobre host, rede, porta ou protocolo inalcançável.
        - Eco de solicitação/resposta (ping).
    - O ICMP apenas informa erros ao nível do IP de origem e não tem responsabilidade pela correção dos mesmos.
    
1. **Posição na Arquitetura:**
    - O ICMP é considerado parte do IP, mas em termos de arquitetura, está logo acima do IP, assim como o TCP e o UDP (carga útil).
    - Ao receber um datagrama IP com ICMP, o host demultiplexa o conteúdo para ICMP.
    - Uma mensagem ICMP inclui campo de tipo, código e os primeiros 8 bytes do datagrama IP que causou o erro, permitindo a identificação do datagrama problemático.
    
1. **Cenários de Uso do ICMP:**
    - Quando um roteador descarta um pacote devido ao TTL ter expirado.
    - Quando o roteador não possui capacidade de bufferização para encaminhar o datagrama.
    - Quando o roteador precisa fragmentar um datagrama com o bit “don’t fragment” ligado.
    
1. **Observações sobre o ICMP:**
    - Mensagens ICMP são roteadas como qualquer outro datagrama, sem garantia de entrega ao destino final.
    - Não existe mensagem ICMP para reportar erros ou descarte de pacotes ICMP.
    - Erros são reportados apenas em datagramas não fragmentados ou no primeiro fragmento de um datagrama.
    
1. **Quando Não Usar o ICMP:**
    - Roteamento ou entrega de mensagens ICMP.
    - Datagramas broadcast ou multicast.
    - Fragmentos de datagramas que não sejam os primeiros.
    - Mensagens cujo endereço fonte não identifica um único host (por exemplo, 127.0.0.1 ou 0.0.0.0).
    
1. **Protocolo ICMP:**
    - O cabeçalho ICMP inicia após o cabeçalho IPv4 e é identificado pelo número de protocolo 1.
    - Todos os pacotes ICMP têm um cabeçalho de 8 bytes e um campo de dados de tamanho variável.
    - Os primeiros 4 bytes do cabeçalho têm formato fixo, enquanto os 4 bytes restantes dependem do tipo/código do pacote ICMP.
    
1. **Exemplos:**
    - Exemplo 1: O comando “ping” envia uma mensagem ICMP do tipo “8” e código “0” para um host, que responde com uma mensagem do tipo “0” e código “0”.
    - Exemplo 2 (traceroute):
        - O remetente envia segmentos UDP com diferentes valores de TTL.
        - Quando a mensagem ICMP de “porta inalcançável” é recebida, o traceroute para de enviar segmentos UDP.

# Modulo IV - Endereçamento IPv6

1. **Características do IPv6:**
    - Capacidade de endereçamento expandida: de 32 para 128 bits.
    - Introdução de endereço “anycast”.
    - Cabeçalho fixo e aprimorado de 40 bytes.
    - Maior velocidade de processamento e transmissão.
    - Sem suporte a fragmentação de datagramas.
    - Rotulação de fluxo e prioridade (conforme padrões RFC 1752 e RFC 2460).
    
1. **Campos Ausentes no IPv6:**
    - **Fragmentação/Remontagem:**
        - Essas operações são realizadas apenas pelo remetente e destinatário.
        - Caso um roteador não consiga processar um datagrama, ele o descarta e envia uma mensagem ICMP de volta.
    - **Checksum:**
        - Funcionalidade considerada redundante na camada de rede, uma vez que tanto a camada de transporte quanto a camada de enlace contemplam tal funcionalidade.
        
1. **Campos Adicionais no IPv6:**
    - **Opções:**
        - Não faz parte do cabeçalho padrão, mas também não foi excluído.
        - Está presente no cabeçalho como “próximo cabeçalho”.
        - Sugere que o IPv6 poderá comportar adições no cabeçalho, assim como nos protocolos TCP e UDP.
        
1. **Estrutura do Datagrama IPv6:**
    - **Versão (4 bits):**
        - Número de versão do IP = 6.
    - **Classe de Tráfego (8 bits):**
        - Pode ser usado para dar prioridade a certos datagramas dentro de um fluxo ou de certas aplicações.
    - **Rótulo de Fluxo (20 bits):**
        - Permite identificar um fluxo de datagramas para o qual se deseja tratamento particular.
    - **Comprimento da Carga Útil (16 bits):**
        - Informa quantos bytes há no datagrama IPv6 que segue o cabeçalho.
    - **Próximo Cabeçalho (8 bits):**
        - Identifica o protocolo ao qual deve ser entregue a carga (payload) do datagrama.
        
1. **Outros Detalhes:**
    - **Limite de Saltos (4 bits):**
        - Valor decrementado em 1 unidade em cada roteador.
        - Se chegar a zero, o datagrama é descartado.
    - **Endereços de Origem e Destino:**
        - Padrão RFC 4291 - contempla multicast, unicast e anycast.
    - **Dados (Payload):**
        - Contém a carga útil do datagrama.
        
## Transição IPv4 -> IPv6

1. **Desafios da Transição:**
    - O IPv6 pode receber e rotear datagramas IPv4, mas o IPv4 não pode manusear datagramas IPv6.
    - Nem todos os roteadores podem ser atualizados simultaneamente.
    - A ideia de um “Dia da Conversão” envolve modificar todas as máquinas da Internet em uma data específica, atualizando do IPv4 para o IPv6.
    
1. **Tunelamento:**
    - O tunelamento permite transportar datagramas IPv6 dentro de pacotes IPv4 entre roteadores que suportam apenas IPv4.
    - Por exemplo, datagramas IPv6 podem ser encapsulados em datagramas IPv4.
    - O IPv6 é tratado como carga útil do IPv4.
    
1. **Pilhas Duplas com IPv6:**
    - A pilha dupla envolve a implementação completa do IPv4 e do IPv6.
    - Datagramas IPv6 são transportados como carga útil em datagramas IPv4 quando necessário.
    - A conversão depende da habilidade dos roteadores e hosts em lidar com ambos os formatos.
    
1. **Exemplo de Pilhas Duplas:**
    - Suponha que o host “A” use IPv6 e deseje enviar datagramas ao nó “F”, que também utiliza IPv6.
    - No caminho, há roteadores que não conseguem rotear datagramas IPv6.
    - A solução é converter datagramas IPv6 para IPv4, mas isso apresenta problemas, pois nem todos os campos no IPv6/IPv4 estão presentes em ambos os formatos.

# Modulo V - Segurança no IP
## IP Seguro

1. **IPsec (IP Security):**
    - O IPsec é um protocolo que oferece serviços de segurança a nível de rede.
    - É amplamente empregado em Redes Virtuais Privadas (VPNs).
    - É compatível com IPv4 e IPv6.
    - Dispensa a substituição de outros protocolos existentes nos roteadores e hosts conectados.
    - Protege toda a comunicação entre dois hosts para todas as aplicações de rede.
    - Codifica e autentica segmentos TCP e UDP.
    
1. **Serviço do IPsec:**
    - **Acordo Criptográfico:**
        - Envolve a concordância nos algoritmos criptográficos e chaves entre os hospedeiros.
    - **Codificação das Cargas Úteis do Datagrama IP:**
        - Segmentos da camada de transporte com carga útil codificada pelo IPsec.
        - Somente pode ser decodificada pelo IPsec no hospedeiro destinatário.
    - **Integridade dos Dados:**
        - Verificação no host destinatário dos campos do cabeçalho do datagrama e da carga útil codificada.
        - Observa se não foram modificados enquanto o datagrama estava no caminho da origem ao destino.
    - **Autenticação de Origem:**
        - Por meio de chaves confiáveis, o host destinatário verifica que o IP remetente é de fato a origem do datagrama recebido.

