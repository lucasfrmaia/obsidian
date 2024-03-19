
O PySpark é a interface de programação em Python para o Apache Spark, um poderoso framework de processamento de dados distribuído e de código aberto. O Apache Spark é projetado para lidar com grandes volumes de dados e realizar análises complexas de forma rápida e eficiente, aproveitando o poder do processamento distribuído em clusters de computadores.

O PySpark permite que os desenvolvedores usem a linguagem Python para escrever programas que podem ser executados no Apache Spark. Isso torna o desenvolvimento de aplicações de big data mais acessível para os programadores Python, aproveitando a simplicidade e a facilidade de uso dessa linguagem.

Com o PySpark, os desenvolvedores podem criar pipelines de processamento de dados, executar consultas SQL em grandes conjuntos de dados, realizar análises avançadas e criar modelos de machine learning, tudo dentro do ambiente do Apache Spark. Essa integração entre Python e Spark torna o PySpark uma ferramenta poderosa para lidar com tarefas de big data e análise de dados em escala.

---
### Arquitetura

![[Pasted image 20240318115225.png]]
    Particionamento de dados: Os dados são divididos em partições, que são distribuídas pelos nós do cluster. Isso permite que o Spark processe diferentes partes dos dados em paralelo.

    Execução em memória: O Spark mantém dados em memória sempre que possível, o que melhora significativamente o desempenho, especialmente para operações repetidas sobre os mesmos conjuntos de dados.

    Avaliação de expressões: O Spark utiliza a avaliação de expressões para otimizar consultas, reduzindo a quantidade de dados que precisam ser movidos entre os nós do cluster.

    Execução de tarefas em paralelo: O Spark divide as operações em tarefas menores, que são executadas em paralelo em diferentes nós do cluster. Isso permite que o Spark processe grandes volumes de dados de forma eficiente.

![[Pasted image 20240318175846.png]]
    **Job**: Um job é uma unidade de trabalho que o Spark executa em resposta a uma ação, como um `collect()` ou um `saveAsTextFile()`. Cada ação no seu programa PySpark geralmente desencadeia a execução de um job. Um job é composto por um ou mais stages.

    Stage: Um stage é uma unidade de execução que consiste em um conjunto de tarefas (tasks) que podem ser executadas em paralelo. Um stage é definido pelas operações de transformação (por exemplo, map, filter, reduce) em seu programa PySpark. O Spark tenta dividir as operações em estágios de forma que as operações que exigem movimentação de dados sejam executadas juntas, minimizando a quantidade de dados que precisam ser movidos pela rede.

    Task: Uma task é a unidade básica de execução no Spark. Elas são as unidades de trabalho individuais que são enviadas para os nós do cluster para processamento. Cada task executa uma parte específica de um stage em um único bloco de dados. O Spark paraleliza a execução das tasks para processar os dados de forma eficiente.

