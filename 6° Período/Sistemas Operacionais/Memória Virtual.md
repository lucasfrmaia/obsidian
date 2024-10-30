
A memória virtual é uma técnica que permite a execução de processos que não estão totalmente na memória. Uma grande vantagem desse esquema é que os programas podem ser maiores do que a memória física. Além disso, a memória virtual abstrai a memória principal em um array de armazenamento uniforme extremamente grande, separando a memória lógica, conforme vista pelo usuário, da memória física. Essa técnica deixa os programadores livres de preocupações com as limitações de armazenamento da memória. 

A memória virtual também permite que os processos compartilhem arquivos facilmente e implementem a memória compartilhada. Além disso, ela fornece um mecanismo eficiente para a criação de processos. No entanto, a memória virtual não é fácil de implementar e pode piorar substancialmente o desempenho, se for usada sem cuidado. Neste capítulo, discutimos a memória virtual na forma de paginação por demanda e examinamos sua complexidade e custo.

A **memória virtual** envolve a separação entre a memória lógica como percebida pelos usuários e a
memória física.

O **espaço de endereçamento** virtual de um processo diz respeito à visão lógica (ou virtual) de como um processo é armazenado na memória. Normalmente, de acordo com essa visão, um processo começa em determinado endereço lógico

Os espaços de endereçamento virtuais que incluem brechas são conhecidos como
espaços de endereçamento **esparsos**.

Em vez disso, podemos usar uma técnica conhecida como **cópia-após-gravação**, que funciona permitindo que o processo-pai e o processo filho compartilhem inicialmente as mesmas páginas.

---
No contexto de sistemas operacionais, **algoritmos de paginação por demanda** são estratégias para gerenciar a memória quando o espaço físico (memória RAM) é limitado e não pode conter todas as páginas dos processos em execução. Cada vez que uma página não está na memória (ocorre um *page fault* ou falha de página), o sistema operacional precisa escolher uma página para remover e liberar espaço para a nova. Os algoritmos a seguir são técnicas para escolher qual página remover.

### 1. Algoritmo FIFO (First-In, First-Out)

O algoritmo **FIFO** remove a página que está na memória há mais tempo, sem considerar a frequência de acesso ou o tempo desde o último acesso. Isso é feito de forma simples, geralmente com uma fila: quando uma nova página precisa ser carregada, a página que está na frente da fila é removida.

#### Exemplo:
Suponha que temos uma sequência de acessos às páginas `1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5` e apenas três quadros de página disponíveis (espaços de memória).

1. Carregue `1, 2, 3` — Ocorreram *page faults* para cada página, pois não estavam carregadas. A memória agora tem `[1, 2, 3]`.
2. Carregue a página `4` — Como temos que remover uma página, eliminamos `1` (a mais antiga). A memória agora tem `[4, 2, 3]`.
3. Carregue a página `1` — Remove `2` (a mais antiga). A memória agora tem `[4, 1, 3]`.
4. E assim por diante...

#### Vantagens e desvantagens do FIFO:
- **Vantagem**: Fácil de implementar.
- **Desvantagem**: Não leva em conta o uso real das páginas, podendo remover uma página importante. Esse fenômeno é chamado de "anomalia de Belady", onde o aumento dos quadros disponíveis pode aumentar os *page faults*.

### 2. Algoritmo Ótimo

O **algoritmo ótimo** remove a página que será usada mais tarde ou que não será usada por mais tempo no futuro. Este é o algoritmo ideal e proporciona o menor número de falhas, mas é impossível de ser implementado na prática, pois exige conhecer a sequência futura de acessos.

#### Exemplo:
Usando a mesma sequência `1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5` e três quadros de página:

1. Carregue `1, 2, 3` — As páginas `1, 2` e `3` são carregadas inicialmente.
2. Carregue a página `4` — Para saber qual página remover, verificamos qual das páginas atuais será usada mais tarde. A próxima a ser usada é a `1`, então removemos a `3`. A memória agora é `[1, 2, 4]`.
3. Carregue `5` — Removemos `2`, que será usada mais tarde, mantendo `[1, 4, 5]`.
4. E assim por diante...

#### Vantagens e desvantagens do Ótimo:
- **Vantagem**: Teoricamente perfeito, pois minimiza o número de *page faults*.
- **Desvantagem**: Impraticável, pois o sistema operacional não conhece o futuro.

### 3. Algoritmo NRU (Not Recently Used)

O **algoritmo NRU** considera duas características: se a página foi referenciada e se foi modificada. Ele divide as páginas em quatro classes:
   1. Não referenciada, não modificada
   2. Não referenciada, modificada
   3. Referenciada, não modificada
   4. Referenciada, modificada

Durante uma substituição, a página é escolhida a partir das classes de menor prioridade (1 para 4) até encontrar uma página que pode ser removida. A estratégia se baseia na ideia de que páginas que não foram referenciadas recentemente provavelmente não serão usadas novamente em breve.

#### Exemplo:
Dado um cenário onde cada página tem uma flag para indicar se foi referenciada e modificada:
- Página `A`: referenciada, não modificada
- Página `B`: não referenciada, modificada
- Página `C`: não referenciada, não modificada
- Página `D`: referenciada, modificada

Se houver necessidade de liberar espaço, o algoritmo tentará remover `C` primeiro, pois está na classe de menor prioridade (não referenciada e não modificada).

#### Vantagens e desvantagens do NRU:
- **Vantagem**: Classifica páginas por prioridades, reduzindo *page faults* em alguns casos.
- **Desvantagem**: O estado das páginas só é redefinido periodicamente, o que pode não refletir exatamente o uso recente.

### 4. Algoritmo LRU (Least Recently Used)

O **algoritmo LRU** remove a página que não foi usada há mais tempo, considerando que páginas usadas recentemente serão usadas em breve. Este algoritmo mantém um histórico do tempo do último acesso de cada página e requer mecanismos de contagem para acompanhar a frequência de uso.

#### Exemplo:
Usando a mesma sequência `1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5` e três quadros de página:

1. Carregue `1, 2, 3` — Carrega as páginas com falhas de página. A memória agora é `[1, 2, 3]`.
2. Carregue a página `4` — Remove `1`, pois foi a que menos recentemente usada. A memória agora é `[4, 2, 3]`.
3. Carregue `1` — Remove `2`. A memória agora é `[4, 1, 3]`.
4. Carregue `2` — Remove `4`, ficando `[2, 1, 3]`.

#### Vantagens e desvantagens do LRU:
- **Vantagem**: Geralmente eficiente, pois se baseia no uso recente das páginas.
- **Desvantagem**: Implementação complexa e uso intensivo de memória e CPU, dependendo de listas ordenadas ou matrizes para rastrear o último uso.

### Resumo Comparativo

| Algoritmo | Vantagens | Desvantagens |
|-----------|-----------|--------------|
| **FIFO** | Simplicidade | Pode causar mais falhas (anomalia de Belady) |
| **Ótimo** | Minimiza falhas | Impraticável por prever o futuro |
| **NRU** | Boa priorização em classes | Atualização periódica |
| **LRU** | Bom desempenho | Custo alto de implementação |

Estes algoritmos são fundamentais em sistemas operacionais para garantir eficiência na gestão da memória e para otimizar o desempenho dos processos em execução.