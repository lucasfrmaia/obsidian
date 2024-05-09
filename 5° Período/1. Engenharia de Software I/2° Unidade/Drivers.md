
**Drivers arquiteturais** são considerações **significativamente críticas** para o sucesso de um sistema de software. [Eles são **dependentes de contexto** e formalmente estabelecem modelos para guiar o processo de design de arquitetura, abrangendo todos os elementos que compõem o sistema](https://medium.com/@marcelomg21/architectural-design-drivers-arquitetura-d0f4cf284e56)[1](https://medium.com/@marcelomg21/architectural-design-drivers-arquitetura-d0f4cf284e56)

Para entender melhor, vamos explorar alguns conceitos:

1. **O que é arquitetura de software?**
    
    - A arquitetura de software é a **estrutura fundamental** ou o **esqueleto** de um sistema de software. [Ela define seus componentes, suas relações e seus princípios de projeto e evolução](https://www.alura.com.br/artigos/padroes-arquiteturais-arquitetura-software-descomplicada)[2](https://www.alura.com.br/artigos/padroes-arquiteturais-arquitetura-software-descomplicada).
    - Assim como na arquitetura física, onde profissionais projetam casas e prédios, a arquitetura de software também envolve **normas, princípios e técnicas** para construir software.
    - No entanto, a dinâmica é diferente: os softwares não têm elementos físicos como tijolos ou cimento, mas sua “materialidade” é estabelecida por componentes e módulos dentro do código.
    
1. **Padrões em arquitetura de software**
    - Os padrões arquiteturais são essenciais para concretizar a abstração e escolher a melhor solução para um modelo de negócio específico.
    - Alguns padrões incluem:
        - **Separation of Concerns (SoC)**: Separa a lógica principal do aplicativo das dependências externas, como bancos de dados e interfaces de usuário.
        - **Model-View-Controller (MVC)**: Divide o sistema em três componentes: modelo (dados), visão (interface) e controlador (lógica).
        - **Microservices**: Divide o sistema em serviços independentes e escaláveis.
        - [**Hexagonal Architecture**: Define interfaces claras (portas) e implementa adaptadores para sistemas externos](https://lgertel.medium.com/arquitetura-de-software-em-ambientes-%C3%A1geis-33e93e505530)[3](https://lgertel.medium.com/arquitetura-de-software-em-ambientes-%C3%A1geis-33e93e505530).
        
1. **Requisitos arquiteturais**
    - Os requisitos arquiteturais são a base para tomar decisões críticas durante o desenvolvimento de software.
    - [Eles garantem que a solução final seja sólida, confiável e alinhada com os objetivos do projeto](https://blog.infnet.com.br/arquitetura_software/o-que-sao-os-requisitos-arquiteturais-em-arquitetura-de-software/)[4](https://blog.infnet.com.br/arquitetura_software/o-que-sao-os-requisitos-arquiteturais-em-arquitetura-de-software/).

Em resumo, os **drivers arquiteturais** são as forças motrizes que moldam a arquitetura de software, considerando o contexto, os requisitos e os padrões específicos para cada sistema.

---

**Drivers arquiteturais** são considerações **significativamente críticas** para o sucesso de um sistema de software. Eles são **dependentes de contexto** e formalmente estabelecem modelos para guiar o processo de design de arquitetura, abrangendo todos os elementos que compõem o sistema.

Para entender melhor, vamos explorar alguns conceitos:

1. **O que é arquitetura de software?**
    
    - A arquitetura de software é a **estrutura fundamental** ou o **esqueleto** de um sistema de software. Ela define seus componentes, suas relações e seus princípios de projeto e evolução.
    - Assim como na arquitetura física, onde profissionais projetam casas e prédios, a arquitetura de software também envolve **normas, princípios e técnicas** para construir software.
    - No entanto, a dinâmica é diferente: os softwares não têm elementos físicos como tijolos ou cimento, mas sua “materialidade” é estabelecida por componentes e módulos dentro do código.
2. **Padrões em arquitetura de software**
    
    - Os padrões arquiteturais são essenciais para concretizar a abstração e escolher a melhor solução para um modelo de negócio específico.
    - Alguns padrões incluem:
        - **Separation of Concerns (SoC)**: Separa a lógica principal do aplicativo das dependências externas, como bancos de dados e interfaces de usuário.
        - **Model-View-Controller (MVC)**: Divide o sistema em três componentes: modelo (dados), visão (interface) e controlador (lógica).
        - **Microservices**: Divide o sistema em serviços independentes e escaláveis.
        - **Hexagonal Architecture**: Define interfaces claras (portas) e implementa adaptadores para sistemas externos.
3. **Requisitos arquiteturais**
    
    - Os requisitos arquiteturais são a base para tomar decisões críticas durante o desenvolvimento de software.
    - Eles garantem que a solução final seja sólida, confiável e alinhada com os objetivos do projeto.

Em resumo, os **drivers arquiteturais** são as forças motrizes que moldam a arquitetura de software, considerando o contexto, os requisitos e os padrões específicos para cada sistema.

Agora, vamos resumir os tópicos abordados na engenharia de software:

- **Drivers Arquiteturais**:
    
    - São considerações críticas para o sucesso de um sistema de software.
    - Dependem do contexto e guiam o processo de design de arquitetura.
    - Incluem padrões, requisitos e considerações específicas.
    
- **Arquitetura de Software**:
    - Define a estrutura fundamental de um sistema.
    - Envolve normas, princípios e técnicas para construir software.
    - Componentes e módulos dentro do código formam sua “materialidade”.
    
- **Padrões Arquiteturais**:
    - Essenciais para concretizar a abstração.
    - Exemplos incluem SoC, MVC, Microservices e Hexagonal Architecture.
    
- **Requisitos Arquiteturais**:
    - Base para decisões críticas no desenvolvimento.
    - Garantem soluções sólidas e alinhadas com objetivos do projeto.


![[Pasted image 20240508081506.png]]

Segurança é a medida da habilidade de um sistema de proteger dados e resistir a acessos não
autorizados enquanto proveem serviços a usuários e sistemas que são autorizados. Segurança pode

ser caracterizada pelas características:
1) Confidencialidade: garante que dados ou serviços são protegidos contra o acesso não autorizado.
2) Integridade: garante que dados ou serviços não estão sujeitos a manipulação não autorizada.
3) Disponibilidade: garante que o sistema estará disponível para uso legítimo.
4) Autenticação: garante ambas as partes de uma transação são quem eles dizem ser.
5) Não Repudiação: garante que o remetente de uma mensagem não pode negar ter enviado e que

o destinatário não pode negar ter recebido.
6) Auditoria: garante o rastreamento de atividades de forma que o sistema possa reconstruí-las.
7) 
![[Pasted image 20240509013039.png]]

---

1. **User Story: Preencher Dados Pessoais**
    - **Driver Arquitetural 1 (DA1)**: Garantir que o sistema colete e armazene com segurança os dados pessoais do usuário.
    - **Driver Arquitetural 2 (DA2)**: Manter a integridade e confidencialidade dos dados pessoais.
    - **Driver Arquitetural 3 (DA3)**: Facilitar a entrada e validação dos dados pelo usuário.
2. **User Story: Sistema Disponibiliza Termos de Uso**
    
    - **Driver Arquitetural 4 (DA4)**: Fornecer uma interface para exibir os termos de uso.
    - **Driver Arquitetural 5 (DA5)**: Garantir que os termos sejam facilmente acessíveis e compreensíveis para os usuários.
3. **User Story: Sistema Envia Email de Ativação**
    
    - **Driver Arquitetural 6 (DA6)**: Integrar com serviços de envio de email.
    - **Driver Arquitetural 7 (DA7)**: Garantir que os emails de ativação sejam entregues com sucesso e não sejam marcados como spam.
4. **User Story: Cadastro com Alguma Plataforma (Exemplo: Google)**
    
    - **Driver Arquitetural 8 (DA8)**: Integrar com APIs de autenticação de terceiros (por exemplo, OAuth).
    - **Driver Arquitetural 9 (DA9)**: Gerenciar tokens de acesso e autorização.
5. **User Story: Botão Relembre**
    
    - **Driver Arquitetural 10 (DA10)**: Implementar um mecanismo para lembrar os usuários de eventos importantes (por exemplo, aniversários, prazos, etc.).
6. **User Story: Verificação de 2 Etapas**
    
    - **Driver Arquitetural 11 (DA11)**: Implementar autenticação de dois fatores (2FA) para aumentar a segurança do login.
    - **Driver Arquitetural 12 (DA12)**: Garantir que o processo de verificação seja eficiente e confiável.
7. **User Story: Ver Dados de Perfis**
    
    - **Driver Arquitetural 13 (DA13)**: Criar uma interface para exibir os dados do perfil do usuário.
    - **Driver Arquitetural 14 (DA14)**: Garantir que apenas os dados autorizados sejam exibidos.
8. **User Story: Editar Perfil**
    
    - **Driver Arquitetural 15 (DA15)**: Implementar uma interface para que os usuários possam editar suas informações de perfil.
    - **Driver Arquitetural 16 (DA16)**: Garantir que as alterações sejam refletidas corretamente no sistema.
9. **User Story: Usuário Digita Sua Nova Senha**
    
    - **Driver Arquitetural 17 (DA17)**: Implementar um fluxo seguro para redefinição de senha.
    - **Driver Arquitetural 18 (DA18)**: Garantir que a nova senha seja armazenada de forma criptografada e segura.

---

Os **drivers arquiteturais** são considerações **significativamente críticas** para o sucesso de um sistema de software. [Eles são **dependentes de contexto** e formalmente estabelecem modelos para guiar o processo de design de arquitetura, abrangendo todos os elementos que compõem o sistema](https://blog.infnet.com.br/arquitetura_software/o-que-sao-os-requisitos-arquiteturais-em-arquitetura-de-software/)[1](https://blog.infnet.com.br/arquitetura_software/o-que-sao-os-requisitos-arquiteturais-em-arquitetura-de-software/).

Aqui estão algumas especificações e características dos drivers arquiteturais:

1. **Compensação**:
    
    - Lidam com a falta de conhecimento completo dos requisitos.
    - Abordam casos excepcionais e complexos.
2. **Agregação**:
    
    - Tratam de situações com grande quantidade de tipos similares de requisitos.
    - Consolidam diferentes opiniões e preocupações de stakeholders (negócio vs. técnica).
3. **Consolidação**:
    
    - Antecipam mudanças futuras.
    - Consideram investimentos a longo prazo.
4. **Negociação**:
    
    - Equilibram qualidade externa (runtime) e qualidade interna (devtime).
    - Alinham conflitos entre os interesses dos stakeholders.
    - Levam em conta restrições.
5. **Especificação de Atributos de Qualidade**:
    
    - Define os atributos de qualidade desejados para o sistema.
    - Evita ambiguidades e fornece critérios mensuráveis.
    - Geralmente baseada em cenários que descrevem situações específicas.
6. **Exemplos de Drivers Arquiteturais**:
    
    - **AD1**: “Um usuário deseja atualizar o Sistema. A atualização é realizada dentro de no máximo 3 cliques.”
    - **AD2**: “Durante uma operação, o servidor falha. Todas as operações subsequentes não são afetadas pela falha.”
    - **AD3**: “Cada entrada do usuário gera uma resposta visual dentro de 0.2s.”
---

**Cenários arquiteturais** são descrições nítidas e concisas de situações que um sistema de software provavelmente irá lidar, juntamente com a definição da resposta requerida do sistema. [Eles desempenham um papel fundamental no design e na avaliação da arquitetura de software, permitindo uma descrição precisa dos requisitos](https://www.devmedia.com.br/uso-de-cenarios-para-especificacao-de-requisitos-de-qualidade-e-avaliacao-de-arquitetura/22528)[1](https://www.devmedia.com.br/uso-de-cenarios-para-especificacao-de-requisitos-de-qualidade-e-avaliacao-de-arquitetura/22528).

Aqui estão alguns exemplos de cenários arquiteturais:

2. **Verificação de 2 Etapas**:
    - **Cenário**: Um usuário deseja fazer login no sistema.
    - **Descrição**: O sistema solicita um segundo fator de autenticação (por exemplo, código enviado por SMS) após a inserção da senha.
    - **Resposta Requerida**: O sistema valida o segundo fator e concede acesso ao usuário
1. . **Atualização do Sistema**:
    - **Cenário**: Um usuário deseja atualizar o software.
    - **Descrição**: O usuário inicia o processo de atualização.
    - **Resposta Requerida**: O sistema executa a atualização com sucesso, garantindo que não haja mais de 3 cliques necessários para concluir o processo.
    
--- 

Certamente! Vamos explorar alguns cenários arquiteturais relacionados ao atributo de qualidade de **segurança** com base nas partes especificadas:

1. **Cenário: Autenticação de Usuário**
    - **Estímulo**: Um usuário tenta fazer login no sistema.
    - **Fonte de Estímulo**: O próprio usuário.
    - **Artefato**: Módulo de autenticação.
    - **Ambiente**: Sistema em produção.
    - **Resposta**: O sistema verifica as credenciais do usuário e concede ou nega o acesso.
    - **Medida de Resposta**: Tempo médio de resposta para autenticação (por exemplo, menos de 2 segundos).
    
1. **Cenário: Proteção contra Ataques**
    
    - **Estímulo**: Um atacante tenta explorar uma vulnerabilidade conhecida.
    - **Fonte de Estímulo**: Entidade mal-intencionada.
    - **Artefato**: Componente vulnerável (por exemplo, servidor web).
    - **Ambiente**: Ambiente de produção.
    - **Resposta**: O sistema detecta o ataque e bloqueia o acesso do atacante.
    - **Medida de Resposta**: Taxa de detecção de ataques bem-sucedidos (por exemplo, menos de 1% dos ataques passam despercebidos)