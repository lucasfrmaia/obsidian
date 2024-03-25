
# MiniTeste
## Questões

 1.  Considerando a divisão em camadas dos protocolos de rede, exemplifique, de forma genérica, como funciona o encapsulamento de dados, comparando os dois modelos de arquiteturas existentes.

2. Conceitue (se necessário), verifique e justifique, se verdadeiro, ou comja, se falso, as afirmativas a seguir:

	a. Uva protocolo POP3 funciona no modo de download-and-delete de mensagens, enquanto que o protocolo IMAP funciona no modo (95) download-and-keep. 
	also 

	b. No processo de comunicação, o servidor de correio tem um lado cliente, ao realizar o contato com o servidor de correio do destinatário, usando o protocolo HTTP ao invés do SMTP De

	c. O uso de GET condicional possibilita a obtenção de objetos de forma O SMTP; ROLL, HAR e paralela durante o processo de comunicação, dispensando o uso de FCFS

	 d. Servidores DNS do tipo Top-Level Domain (TLD) estão no topo da hierarquia, concentrando uma maior quantidade de dados, e, por isso, mais susceptiveis a ataques DDoS e de falsificação.

3. (3,0 pontos) O uso de cookies e cache durante a navegação proporcionam rapidez e consistência na obtenção de objetos HTTP. Sabendo disso, simule uma linha do tempo para uma navegação em dois sites na Internet, sendo um deles institucional e o outro de e-commerce, destacando a dinâmica de uso dessas ferramentas.

## Respostas

1. **Encapsulamento de Dados:**
    - No modelo de referência OSI, o encapsulamento de dados ocorre à medida que os dados descem pelas camadas. Cada camada adiciona seu próprio cabeçalho (e, em alguns casos, trailer) aos dados recebidos da camada superior, formando assim um novo PDU (Protocol Data Unit) para ser transmitido.
    
    - No modelo TCP/IP, o processo é semelhante, mas o modelo é mais simples, com menos camadas. Os dados são enviados para a camada de rede (Internet Protocol - IP), que adiciona seu próprio cabeçalho para formar um datagrama IP. Esse datagrama é então enviado para a camada de transporte (TCP ou UDP), que adiciona seu cabeçalho para formar um segmento (no caso do TCP) ou um datagrama (no caso do UDP).
    
2.  **Afirmativas:** 
	* a. **Verdadeira.** O protocolo POP3 (Post Office Protocol version 3) permite que o cliente baixe e apague as mensagens do servidor, enquanto o protocolo IMAP (Internet Message Access Protocol) permite que o cliente baixe e mantenha as mensagens no servidor.
	
	* b. **Falsa.** No processo de comunicação de e-mail, o servidor de correio atua como um servidor SMTP (Simple Mail Transfer Protocol), não HTTP. O HTTP (Hypertext Transfer Protocol) é usado para comunicação web, não para correio eletrônico.
	
	* c. **Falso.** O GET condicional não está relacionado com a obtenção de objetos de forma paralela durante o processo de comunicação. O GET condicional é um recurso do HTTP que permite verificar se um objeto foi modificado desde a última vez que foi acessado, evitando assim o download desnecessário de objetos não modificados. 
	
	*  d. **Verdadeira.** Os servidores DNS do tipo Top-Level Domain (TLD) estão no topo da hierarquia e são responsáveis por armazenar informações sobre os domínios de alto nível, como .com, .org, .net, entre outros. Por estarem no topo da hierarquia, eles são mais visados em ataques DDoS e de falsificação.
    
3. **Uso de Cookies e Cache:**
    - O uso de cookies e cache durante a navegação pode melhorar significativamente a experiência do usuário, proporcionando rapidez e consistência na obtenção de objetos HTTP.
    
    - **Simulação de uma linha do tempo:**
        - **Institucional:**
            - O navegador faz uma solicitação HTTP para carregar a página inicial do site institucional.
            - O servidor responde com a página HTML e define um cookie para identificar a sessão do usuário.
            - O navegador armazena em cache os recursos estáticos (imagens, CSS, JavaScript) da página.
            - O usuário navega por diferentes seções do site, e o navegador utiliza o cache para recuperar recursos estáticos, reduzindo a quantidade de solicitações ao servidor.
        - **E-commerce:**
            - O navegador solicita a página inicial do site de e-commerce.
            - O servidor responde com a página HTML e define cookies para identificar a sessão e o carrinho de compras do usuário.
            - O navegador armazena em cache os recursos estáticos da página e os cookies.
            - Durante a navegação, o navegador utiliza o cache para recuperar recursos estáticos e os cookies para manter a sessão e o carrinho de compras atualizados.

---
# Exercício

## Questões 

1. Descreva rapidamente redes de acesso doméstico e redes corporativas, citando diferenças de implementação e de tecnologia entre elas.  
  
2. Quais são as cinco camadas da pilha de protocolo da Internet? Quais as principais responsabilidades de cada uma dessas camadas?  
  
3. Que camadas da pilha do protocolo da Internet um roteador processa? Que camadas um comutador de camada de enlace processa? Que camadas um sistema final processa?  
  
4. Suponha que você queria fazer uma transação de um cliente remoto para um servidor da maneira mais rápida possível. Você usaria o UDP ou o TCP? Por quê?  
  
5. Suponha que Alice envie uma mensagem a Bob por meio de uma conta de e-mail da Web (como o Hotmail ou Gmail), e que Bob acesse seu e-mail por seu servidor de correio usando POP3. Descreva como a mensagem vai do hospedeiro de Alice até o hospedeiro de Bob. Não se esqueça de relacionar a série de protocolos de camada de aplicação usados para movimentar a mensagem entre os dois hospedeiros.
## Respostas

1. **Redes de Acesso Doméstico vs. Redes Corporativas:**
    - **Redes de Acesso Doméstico:** Geralmente são redes menores, comumente usadas em residências, e são implementadas com tecnologias mais simples, como Wi-Fi, Ethernet e Powerline. São projetadas para atender às necessidades básicas de conectividade da família.
    
    - **Redes Corporativas:** São redes maiores, projetadas para atender às necessidades de uma organização. Podem incluir tecnologias mais avançadas, como VLANs, VPNs, firewalls, balanceadores de carga, entre outros. São implementadas com foco na segurança, desempenho e escalabilidade.
    
1. **Cinco Camadas da Pilha de Protocolo da Internet:**
    - **Camada de Aplicação:** Responsável pela comunicação entre os programas de aplicação. Exemplos de protocolos nesta camada incluem HTTP, SMTP e FTP.
    
    - **Camada de Transporte:** Fornece comunicação de host para host, garantindo a entrega ordenada e confiável dos dados. Exemplos de protocolos nesta camada incluem TCP e UDP.
    
    - **Camada de Rede:** Responsável pelo roteamento dos dados da origem para o destino. O protocolo principal nesta camada é o IP (Internet Protocol).
    
    - **Camada de Enlace:** Responsável pela comunicação entre dispositivos em uma mesma rede local. Inclui o controle de acesso ao meio e a detecção de erros. Exemplos de protocolos nesta camada incluem Ethernet e Wi-Fi.
    
    - **Camada Física:** Envolvida na transmissão física dos dados através do meio de comunicação. Inclui especificações de hardware, como cabos, placas de rede e sinais elétricos.
    
1. **Processamento de Protocolos em Roteadores, Comutadores e Sistemas Finais:**
    - **Roteador:** Processa as camadas de Rede (IP) e Transporte (TCP/UDP).
    - **Comutador:** Processa a camada de Enlace (Ethernet).
    - **Sistema Final:** Processa as camadas de Aplicação, Transporte, Rede e Enlace.
    
1. **UDP ou TCP para Transação Rápida:**
    - Se a velocidade for a principal prioridade e a perda de alguns dados não for crítica, o UDP (User Datagram Protocol) seria mais adequado. O UDP é mais rápido porque não estabelece uma conexão antes da transmissão dos dados, ao contrário do TCP, que realiza um handshake para garantir a confiabilidade da transmissão.
    
1. **Movimentação de Mensagem de Alice para Bob:**
    - A mensagem é enviada por meio do protocolo SMTP (Simple Mail Transfer Protocol) do cliente de e-mail de Alice para o servidor de e-mail da Web (como Hotmail ou Gmail).
    - Bob acessa seu e-mail por meio do protocolo POP3 (Post Office Protocol version 3), baixando a mensagem do servidor de e-mail para seu dispositivo.

---

# Resumo

* 1. No modelo OSI, o encapsulamento de dados ocorre a medida que os dados descem pelas camadas onde cada camada adiciona seu cabeçalho, no modelo TCP/IP é parecido só que mais simplificado onde os dados são enviado para camada de rede que adiciona seu próprio cabeçalho formando um datagrama IP

2. 
	*  **Verdadeiro**, o protocolo POP3 permite que o cliente baixe e apague mensagem do servidor enquanto O IMAP baixa e mantém

	*  **Falsa**: o servidor atua como SMTP e não HTTTP

	* **Falso** o get não está relacionado com a obtenção de objetos de forma paralela durante o processo de comunicação

	* **Verdadeiro**: os servidores estão no TLD e armazenam informações de alto nivel e por estarem no topo da hierarquia , são mais visados paras ataques DDos

3. 
	* O uso de cookies serve para melhorar a experência do usuário
	* **Institucional**: O usuário faz uma requisição HTTPS para o servidor, o servidor responde e verifica cookies de autenticação e já define uma sessão sem precisar do login
	* **E-commerce**: O usuário faz uma requisição HTTPS para o servidor, o servidor responde e verifica cookies de autenticação e já define uma sessão sem precisar do login
		