
* Antigamente, implantação era sempre traumática

![[Pasted image 20240324170931.png|500]]

* Dois silos independentes, com pouquíssima comunicação
* Ops = administradores de sistema, suporte, sysadmin, pessoal de IT, etc
---
![[Pasted image 20240324171225.png|500]]
- Ideia central de DevOps: aproximar Dev e Ops

## Princípios do DevOps

* Aproximar Devs e Ops, desde o início do projeto
* Adotar princípios ágeis na fase de implantação
* Transformar implantações em um não-evento
* Implantar sistemas (partes dele) todos os dias
* Automatização do processo de implantação

## Práticas do DevOps

* Controle de Versões
* Integração Contínua
* Estratégias de Branch
* Deployment Contínuo 
* Feature Flags

### Controle de Versão

- Fundamental para desenvolvimento colaborativo
- Armazena última versão do sistema (fonte da verdade)
- Permite recuperar versões anteriores

#### **Distribuído**

![[Pasted image 20240324171635.png|400]]

### Vantagens de DVCS

- Pode-se fazer commits com mais frequência
- Commits são mais rápidos
- Pode-se trabalhar off-line
- Existe um histórico de versões local
- Arquiteturas alternativas: P2P, hierárquica, etc

### **Multirepos x Monorepo**

1. **Multirepos**:
    - **Definição**: Vários repositórios de código-fonte, cada um representando um projeto ou componente separado.
    
    - **Vantagens**:
	    * Uma única fonte de verdade
		* Promovem visibilidade e, portanto, reúso de código
		* Mesma versão de uma biblioteca usada em todos subsistemas
		* Mudanças são atômicas (1 commit pode alterar n sistemas)
		* Facilitam refactorings em larga escala

    - **Desvantagens**:
        - Dificuldade em coordenar mudanças que afetam vários projetos.
        - Complexidade aumentada para manter dependências entre repositórios.
        
1. **Monorepo**:
    - **Definição**: Um único repositório de código-fonte que contém todo o código de vários projetos ou componentes.
    
    - **Vantagens**:
        - Facilita a reutilização de código e compartilhamento de dependências.
        - Permite a coordenação simplificada de mudanças em vários projetos.
    - **Desvantagens**:
        - Pode se tornar difícil de gerenciar à medida que o repositório cresce em tamanho e complexidade.
        - Requer ferramentas e práticas específicas para lidar com build, testes e implantação.

### Integração Continua

- Prática proposta por XP
- Como o nome diz, integrar o código com frequência
- Mas com qual frequência? 
- Não existe consenso, mas a maioria dos autores recomenda pelo menos uma vez por dia

#### Boas Práticas de IC
- Build automatizado
- Testes automatizados    
- Programação em pares

#### Estratégias de branches

- Como organizar branches e gerenciar o fluxo de trabalho
	- **Principais estratégias:**
	- Git-flow
	- GitHubFlow
	- Trunk-based Development

#### Git-Flow

- Estratégia de branch muito comum

- Dois branches permanentes:
	- Master
		- Código que está pronto para produção
		- Chamado também de main ou trunk 

	- Develop
		- Funcionalidades que estão implementadas
		- Mas não passaram por um “teste final”
		- Por exemplo, pela equipe de QA
		    
- Principal uso quando:
	- Vários clientes com versões diferentes
	- Testes manuais e times de QA
	- Releases precisam de aprovação dos clientes
    
- Desvantagens: 
	- Tendência a ter merges maiores e com mais conflitos
	- E um ciclo de feedback dos clientes mais longo

---
### GitHubFlow

- Fluxo comum quando se usa GitHub
    
- Git-Flow simplificado:
	- Sem branches develop, release e hotfix
	- Apenas feature e master
	- Mas com suporte a Pull Requests (PR)

**Passos do GithubFlow**

- Desenvolvedor cria “feature branch” no seu repo local
- Implementa uma funcionalidade
- Faz um push do branch para o GitHub
- Entra no GitHub e abre um Pull Request (PR)
- Pull Request: pedido para alguém revisar seu branch
- Revisor (outro dev) revisa e faz o merge do PR em “main”

**Quando usar:**
* Sistemas com apenas uma versão em produção
* Exemplo: sistemas Web

* Desvantagem: 
	* PRs podem levar muito tempo para serem revisados

---
### Desenvolvimento baseado no Trunk (TBD)

* Já que merges podem gerar conflitos, TBD defende: não usar mais branches de desenvolvimento

* Em vez disso, implementação ocorre diretamente no branch principal branch principal = trunk, master, main 


- CI: merges realizados com frequência
- CD: código integrado entra quase que mediatamente em produção
- Objetivo: experimentação e feedback!

---
## Resumo do GPT

DevOps é uma cultura, conjunto de práticas e conjunto de ferramentas que visam melhorar a colaboração entre as equipes de desenvolvimento de software (Dev) e de operações de TI (Ops). Aqui está um resumo do que é DevOps:

1. **Cultura**:
    - Encoraja a colaboração e comunicação entre desenvolvedores, operadores e outras partes interessadas.
    - Promove a automação e a monitorização em todas as fases do ciclo de vida do desenvolvimento de software.
2. **Práticas**:
    
    - Integração Contínua (CI) e Entrega Contínua (CD) para automatizar a construção, teste e implantação de código.
    - Infraestrutura como código (IaC) para automatizar a implantação e gestão de infraestrutura.
    - Monitoramento e logging contínuos para identificar e resolver problemas rapidamente.
3. **Ferramentas**:
    
    - Ferramentas de automação de CI/CD, como Jenkins, GitLab CI/CD, GitHub Actions.
    - Ferramentas de IaC, como Terraform, AWS CloudFormation, Ansible, Puppet, Chef.
    - Ferramentas de monitoramento e logging, como Prometheus, Grafana, ELK Stack (Elasticsearch, Logstash, Kibana).
    
---
### Papelines

1. **Integração Contínua (CI)**:
    
    - **Definição**: Processo de automatização da integração de código de diferentes desenvolvedores em um repositório compartilhado.
    - **Objetivo**: Detectar e corrigir problemas de integração rapidamente, melhorando a qualidade do software e a eficiência do desenvolvimento.
    
* ***Entrega Contínua (CD)**:
	A entrega contínua é uma prática da engenharia de software em que o código é produzido de forma rápida e confiável, permitindo que seja entregue aos usuários de maneira frequente e sustentável. Em vez de grandes lançamentos espaçados no tempo, a entrega contínua visa criar um fluxo constante de funcionalidades e melhorias.

	1. **Integração Contínua (CI)**: Os desenvolvedores integram seu código ao repositório principal com frequência, várias vezes ao dia. Isso ajuda a identificar problemas de integração mais cedo e a manter um código-base saudável.
    
	1. **Testes Automatizados**: São criados testes automatizados, como testes unitários, testes de integração e testes de aceitação, para garantir que as alterações no código não quebrem o sistema existente.
    
	1. **Implantação Automatizada**: O processo de implantação do software é automatizado, desde a compilação até a implantação em um ambiente de produção ou de teste.
    
	1. **Monitoramento Contínuo**: Após a implantação, o sistema é monitorado continuamente para garantir que esteja funcionando conforme o esperado e para identificar possíveis problemas rapidamente.
    
	1. **Retroalimentação Contínua**: A equipe recebe feedback contínuo dos usuários e do sistema, permitindo ajustes rápidos e melhorias contínuas.


--- 
### Desenvolvimento Baseado no Trunk

O Desenvolvimento Baseado no Trunk (TBD) é uma abordagem de desenvolvimento de software que se concentra em manter uma única linha principal de desenvolvimento, conhecida como "trunk" ou "master", onde todos os desenvolvedores integram continuamente seu código. Aqui está um resumo do TBD:

1. **Trunk**:
    - O "trunk" é a linha principal de desenvolvimento no repositório de código-fonte.
    - Todos os desenvolvedores contribuem para o "trunk" e mantêm-no sempre em um estado funcional e pronto para implantação.

1. **Características**:
    
    - Integração Contínua (CI): Os desenvolvedores integram seu código ao "trunk" várias vezes ao dia.
    - Testes Automatizados: São executados regularmente para garantir que o código integrado não quebre a aplicação.
    - Implantação Contínua (CD): O código integrado ao "trunk" é automaticamente construído, testado e, se aprovado, implantado em ambientes de produção.
3. **Benefícios**:
    
    - Maior visibilidade e transparência: Todos os desenvolvedores têm uma visão clara do progresso do projeto.
    - Redução de conflitos de integração: Como o código é integrado continuamente, há menos chances de conflitos entre as alterações feitas por diferentes desenvolvedores.
    - Velocidade e agilidade: O TBD permite entregas mais rápidas e frequentes de software.