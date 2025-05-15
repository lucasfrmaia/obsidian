
O PySpark é a interface de programação em Python para o Apache Spark, um poderoso framework de processamento de dados distribuído e de código aberto. O Apache Spark é projetado para lidar com grandes volumes de dados e realizar análises complexas de forma rápida e eficiente, aproveitando o poder do processamento distribuído em clusters de computadores.

O PySpark permite que os desenvolvedores usem a linguagem Python para escrever programas que podem ser executados no Apache Spark. Isso torna o desenvolvimento de aplicações de big data mais acessível para os programadores Python, aproveitando a simplicidade e a facilidade de uso dessa linguagem.

Com o PySpark, os desenvolvedores podem criar pipelines de processamento de dados, executar consultas SQL em grandes conjuntos de dados, realizar análises avançadas e criar modelos de machine learning, tudo dentro do ambiente do Apache Spark. Essa integração entre Python e Spark torna o PySpark uma ferramenta poderosa para lidar com tarefas de big data e análise de dados em escala.

---
### Arquitetura

![[Pasted image 20250121083342.png]]

### 1. **Driver Program**

- É o ponto inicial de qualquer aplicação Spark.
- Contém a lógica do programa e define o trabalho a ser executado no cluster.
- Atua como o "cérebro" da aplicação, gerenciando e distribuindo as tarefas para os Workers.
- Envia tarefas para os Executors, acompanha o progresso e coleta os resultados finais.
- Tipicamente roda em uma máquina central e é mais utilizado para controle do fluxo da aplicação.
- Exemplos de linguagens usadas para o Driver Program: Python, Scala, Java e R.

### 2. **SparkContext**

- É a principal interface para interagir com o cluster.
- Cria e gerencia o ambiente da aplicação Spark.
- Inicializa a conexão com o Cluster Manager e distribui as tarefas no cluster.
- Responsável por abstrair a complexidade de gerenciar os recursos do cluster.
- Fornece APIs para definir RDDs (Resilient Distributed Datasets), executar transformações e ações.
- Exemplos de operações coordenadas pelo `SparkContext`: leitura de arquivos, execução de mapas e reduções.

### 3. **Cluster Manager**

- É o responsável por orquestrar os recursos (CPU, memória) disponíveis no cluster.
- Recebe solicitações do `SparkContext` para alocar recursos e agendar tarefas.
- Os principais tipos de Cluster Managers suportados pelo Spark são:
    - **Standalone Mode**: Um gerenciador de cluster simples e embutido no Spark.
    - **YARN (Yet Another Resource Negotiator)**: Usado em ambientes Hadoop para gerenciar recursos.
    - **Apache Mesos**: Um gerenciador de cluster de propósito geral.
    - **Kubernetes**: Gerencia recursos no cluster baseado em containers.
- Envia informações ao Driver Program sobre os recursos disponíveis e os Executors criados.

### 4. **Worker Nodes**

- São os "trabalhadores" do cluster, ou seja, as máquinas que realizam o processamento real dos dados.
- Cada Worker Node contém um ou mais processos chamados Executors.
- O Worker Node pode ser uma máquina física, virtual ou um container.
- Executa as tarefas enviadas pelo Driver Program através do Cluster Manager.
- Envia atualizações sobre o progresso das tarefas para o Driver.

### 5. **Executors**

- São os processos responsáveis por executar tarefas atribuídas pelo Driver Program.
- Cada Executor é iniciado em um Worker Node e atua exclusivamente para a aplicação Spark em execução.
- Responsabilidades dos Executors:
    - Executar as tarefas (tasks) atribuídas.
    - Gerenciar a memória e dados intermediários em cache.
    - Comunicar-se com o Driver Program para reportar o progresso e enviar os resultados.
- Normalmente, cada Executor processa múltiplas tarefas paralelamente.
- São encerrados assim que o Driver Program finaliza.

### 6. **Tarefas (Tasks)**

- São as menores unidades de trabalho no Spark.
- Cada transformação ou ação no Spark é dividida em tarefas individuais, que são distribuídas para os Executors.
- Exemplos de tarefas:
    - **Leitura de dados**: Acessar e particionar dados de uma fonte.
    - **Transformações**: Como `map`, `filter` ou `reduceByKey`.
    - **Ações**: Como `collect`, `count` ou `saveAsTextFile`.
- Uma tarefa é executada em um único núcleo de CPU.
- As tarefas são criadas e atribuídas com base na divisão dos dados (partições).

### 7. **Cache**

- É uma parte importante da arquitetura do Spark que melhora o desempenho da aplicação.
- Permite que dados intermediários sejam armazenados em memória nos Worker Nodes.
- Reduz a necessidade de recalcular resultados ou carregar os mesmos dados várias vezes.
- Pode ser usado para armazenar:
    - Resultados intermediários de transformações.
    - Dados que serão reutilizados em várias operações (ex.: RDDs ou DataFrames frequentemente acessados).
- Os dados em cache podem ser armazenados em memória, disco ou uma combinação, dependendo da política de armazenamento definida.

---

![[Pasted image 20240318175846.png]]

### 1. **Jobs**

- Um **Job** é criado sempre que uma ação (como `collect`, `count` ou `save`) é chamada em um RDD ou DataFrame.
- Representa o trabalho completo necessário para realizar a ação solicitada.
- O Driver divide o Job em **Stages** com base em operações de **barreira** (como `shuffle` ou agregações que exigem reordenação dos dados).
- Por exemplo:
    - Um `collect()` pode gerar um único Job.
    - Várias ações no mesmo programa podem gerar múltiplos Jobs.

### 2. **Stages**

- Um **Stage** é uma subdivisão de um Job. Ele representa um conjunto de operações que podem ser executadas sequencialmente sem necessidade de comunicação entre os Workers.
- É definido pelo Spark com base nos **barriers** (como `shuffle`), que forçam a divisão do Job em múltiplos estágios.
- Tipos de Stages:
    - **Narrow Dependencies**: Operações onde as partições dependem de um subconjunto das partições originais (ex.: `map`, `filter`).
    - **Wide Dependencies**: Operações onde as partições dependem de todas as partições originais (ex.: `reduceByKey`, `groupBy`).
- Cada Stage é dividido em múltiplas **Tasks**.

