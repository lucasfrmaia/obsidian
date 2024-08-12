
####  Inicio de Desenvolvimento:
- Separar **Requisitos**, **arquitetura**, **implementação**, **testes** e **entrega**.

#### Estimativa de Custos

- Custos de Esforço
- Custos de hardware e software (com manutenção)
- Custos de Viagens e Treinamentos
#### Custos de Esforço

- Esse custo não incluem custos salariais mas outros custos como:
	- Custo de subsistência, aquecimento, iluminação do escritório
	- Custos de operações de rede de comunicação
	- Custos de seguridade social
#### Evolução do plano de Projeto

**Planning (Planejamento)**:
- **Descrição**: O planejamento é a primeira etapa crucial em qualquer projeto de engenharia de software. Envolve a definição dos objetivos, o escopo do projeto, a criação de cronogramas e a alocação de recursos.

**Risk Analysis (Análise de Risco)**:
- **Descrição**: A análise de risco é um processo contínuo durante o ciclo de vida do projeto. Envolve a identificação, avaliação e mitigação de riscos que podem afetar o projeto.

**Monitoring the project's progress (Monitoramento do progresso do projeto)**:
- **Descrição**: Monitorar o progresso do projeto envolve acompanhar continuamente as atividades em relação ao cronograma e aos objetivos definidos

**Meet quality standards and offer high-quality results (Atender aos padrões de qualidade e oferecer resultados de alta qualidade)**:
- **Descrição**: Garantir que o software atenda aos padrões de qualidade requeridos é um aspecto fundamental do desenvolvimento.

**Flexibility to accommodate changes (Flexibilidade para acomodar mudanças)**:
- **Descrição**: A flexibilidade refere-se à capacidade do projeto de adaptar-se a mudanças nos requisitos, tecnologias, ou condições de mercado.

#### Definição de Preço de Software

- **Oportunidade de mercado**:
    - Empresas podem oferecer preços mais baixos para entrar em novos mercados, visando lucro futuro e aquisição de experiência.
    
- **Incerteza de estimativa de custo**:
    - Quando há incerteza nas estimativas de custo, as empresas podem incluir uma margem de contingência para se proteger contra possíveis perdas.
    
- **Condições contratuais**:
    - Clientes podem permitir que desenvolvedores mantenham a propriedade do código-fonte, resultando em preços menores.
    
- **Volatilidade de requisitos**:
    - Em projetos onde os requisitos podem mudar, empresas podem inicialmente oferecer preços mais baixos para ganhar o contrato, mas cobrar mais por alterações futuras.
    
- **Saúde financeira**:
    - Desenvolvedores com dificuldades financeiras podem reduzir preços para assegurar contratos, priorizando fluxo de caixa sobre o lucro.

#### Desenvolvimento dirigido a Planos

É uma abordagem em que o processo de desenvolvimento é planejado em detalhes
- Um plano de projeto é criado para registrar o trabalho.
- os gerentes usam o plano para suportar a tomadas de decisões de projetos e como uma forma de progresso

##### Vantagens 

Planejamento antecipado permite questões organizacionais possam ser levadas em considerações e que problemas sejam descobertos antes do início do projeto

##### Desvantagens

São as decisões inicias que precisam ser atualizadas por causas de mudanças do ambiente do software, Postergar tais decisões é complicado

##### Plano de Projeto

Em um plano de projeto, são definidos recursos, divisões de trabalho e cronograma para a realizacão dos trabalhos

São Divididos em

- Introdução
- Organização de Projeto
- Análise de Riscos
- Requisitos de recursos de software/hardware
- Divisão de Trabalho
- Cronograma de Projeto
- Monitoração

##### Processo de Planejamento

É um processo iterativo que começa quando um plano inicial de projeto é criado

###### Técnicas de Estimas de custo

Técnicas baseadas em experiências
Técnicas baseadas em  modelagem
Técnicas baseadas em algoritma de curso

###### Técnicas baseadas em experiências

as estimativas se baseiam na experência do gerente em projetos anteriores e em seu domínio de aplicação

Modelagem algorítmica de Curso

Esforço = A * Tamanho^B * M

A = Fato constante que depende das praticas organizacionais
Tamanho = Avaliação do tamanho do código do software
B = Se encontra entre 1 e 1.5
M é um multiplicador feito pela combinação de atributos de processo

As estimativas para B e M são subjetivas, variando muito para isso temos os modelos:

##### Modelo COCOMO II

leva em consideração o desenvolvimento rápido usando linguagens dinâmicas, desenvolvimento voltado a componentes e linguagem de banco de dados

Modelo Priliminar

Pode ser usado em estagios iniciais,

Coeficinete de A = 2.94

---

- **COCOMO II**:
    - **Modelo de Reuso**: Este modelo é utilizado quando partes do software são reutilizadas de projetos anteriores. O modelo de reuso considera o esforço necessário para adaptar e integrar código existente ao novo projeto, levando em conta fatores como a compreensão, modificação e integração do código. Este modelo é essencial quando se trabalha com grandes bases de código pré-existentes.
- **Projeto Preliminar (Early Design Model)**:
    
    - O modelo de estimativa nesta fase é utilizado durante as etapas iniciais do projeto, onde há uma compreensão geral, mas ainda não detalhada do que será desenvolvido. Baseia-se em parâmetros como a complexidade do projeto, experiência da equipe e tecnologia utilizada. Nesta fase, o COCOMO II usa fatores de escala e multiplicadores de esforço mais gerais.
- **Pós-Arquitetura (Post-Architecture Model)**:
    
    - Aplicado após a definição da arquitetura de software, quando os requisitos e o design do sistema já estão mais bem definidos. Neste ponto, o modelo é mais detalhado e considera um conjunto completo de 17 multiplicadores de esforço, além de fatores de escala. Este é o modelo mais preciso do COCOMO II, já que utiliza informações mais específicas e detalhadas.
- **Modelo Empírico**:
    
    - Refere-se a modelos baseados em dados históricos e experiência passada, utilizados para fazer estimativas. No contexto do COCOMO II, o modelo empírico se refere à base de dados utilizada para calibrar o modelo, permitindo que ele seja adaptado para diferentes tipos de projetos e organizações. É essencial para garantir que as estimativas reflitam a realidade das operações de desenvolvimento de software da organização.



![[Pasted image 20240812020948.png]]














