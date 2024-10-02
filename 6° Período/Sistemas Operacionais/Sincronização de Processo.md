
## **Seção Crítica**

**O problema da seção crítica** surge quando múltiplos processos acessam e modificam os mesmos dados simultaneamente, podendo levar a resultados imprevisíveis e inconsistentes. Essa situação é conhecida como **condição de corrida**.

**Seção crítica** é um segmento de código onde um processo manipula dados compartilhados. Para evitar problemas, é necessário garantir que apenas um processo por vez execute sua seção crítica.

**Solução para o problema:**
- **Exclusão mútua:** Apenas um processo pode estar na seção crítica por vez.
- **Progresso:** Se nenhum processo estiver na seção crítica e houver processos esperando, a decisão de quem entrará não pode ser adiada indefinidamente.
- **Espera limitada:** Existe um limite para o número de vezes que outros processos podem entrar na seção crítica após um processo solicitar acesso.

**Importância da sincronização:**
- **Sistemas operacionais:** Estruturas de dados do kernel (listas de processos, alocação de memória) são suscetíveis a condições de corrida.
- **Sistemas multicore:** Múltiplos threads podem compartilhar dados, exigindo sincronização para evitar conflitos.

**Tipos de kernels:**
- **Com preempção:** Um processo em execução pode ser interrompido a qualquer momento.
- **Sem preempção:** Um processo em execução só é interrompido voluntariamente ou ao finalizar uma tarefa.

**Vantagens e desvantagens:**
- **Kernels com preempção:** Maior responsividade, mais adequados para programação em tempo real, mas mais complexos de implementar e propensos a condições de corrida.
- **Kernels sem preempção:** Mais simples, menos propensos a condições de corrida, mas menor responsividade.

## **Solução de Peterson**

- **Objetivo:** Garantir que apenas um processo por vez execute uma seção crítica, evitando conflitos em dados compartilhados.
- **Restrição:** Funciona apenas para dois processos, P0 e P1.
- **Variáveis compartilhadas:**
    - `turn`: Indica qual processo tem a vez de entrar na seção crítica.
    - `flag[2]`: Indica se um processo está pronto para entrar na seção crítica.
- **Funcionamento:**
    - Um processo indica sua intenção de entrar na seção crítica marcando seu flag como `true` e cedendo a vez para o outro processo (atribuindo `turn` ao outro).
    - O processo só entra na seção crítica se o outro processo não estiver interessado (flag como `false`) ou se for a sua vez (`turn` igual ao seu índice`).
- **Garantias:**
    - **Exclusão mútua:** Apenas um processo pode estar na seção crítica por vez.
    - **Progresso:** Se nenhum processo estiver na seção crítica e houver processos esperando, a decisão de quem entrará não pode ser adiada indefinidamente.
    - **Espera limitada:** Existe um limite para o número de vezes que um processo pode ser impedido de entrar na seção crítica.

**Pontos importantes:**
- **Limitada a dois processos:** A solução não se estende diretamente para mais processos.
- **Dependência da arquitetura:** A solução pode não funcionar corretamente em todas as arquiteturas devido a características específicas das instruções de máquina.
- **Valor didático:** Apesar das limitações, a solução de Peterson é importante para entender os conceitos básicos de sincronização e os desafios envolvidos na implementação de algoritmos para garantir a exclusão mútua.

## **Locks Mutex:**
- **Conceito:** Uma ferramenta de software utilizada para proteger regiões críticas e evitar condições de corrida.

- **Funcionamento:**
    - **Acquire:** Adquire o lock, tornando-o indisponível para outros processos. Se o lock já estiver em uso, o processo fica bloqueado até que seja liberado.
    - **Release:** Libera o lock, permitindo que outros processos o adquiram.
- **Implementação:**
    - **Variável booleana `available`:** Indica se o lock está disponível ou não.
    - **Atomicidade:** As operações de `acquire` e `release` devem ser atômicas, ou seja, indivisíveis.
- **Desvantagens dos Spinlocks:**
    - **Espera em ação:** Processos que não conseguem adquirir o lock ficam em um loop contínuo, desperdiçando ciclos de CPU.
    - **Ineficiência em sistemas multiprogramados:** Em sistemas com um único processador, a espera em ação impede que outros processos sejam executados.
- **Vantagens dos Spinlocks:**
    - **Rapidez em sistemas multiprocessadores:** Em sistemas com múltiplos processadores, um processo pode esperar em um lock enquanto outro executa sua seção crítica em outro processador, evitando a necessidade de troca de contexto.
    - **Úteis para bloqueios curtos:** Ideais para situações em que o tempo de espera pelo lock é esperado ser curto.

## **Semáforos**

- **Conceito:** Variáveis inteiras utilizadas para sincronizar processos, controlando o acesso a recursos compartilhados.
- **Operações:**
    - **wait(S):** Decrementa o valor do semáforo S. Se o valor ficar negativo, o processo é bloqueado até que outro processo execute signal(S).
    - **signal(S):** Incrementa o valor do semáforo S. Se houver processos bloqueados, um deles é desbloqueado.
- **Tipos:**
    - **Semáforos de contagem:** Valor pode variar livremente, indicando a quantidade de recursos disponíveis.
    - **Semáforos binários:** Valor varia entre 0 e 1, funcionando como um lock mutex.
- **Implementação:**
    - **Estrutura:** Cada semáforo possui um valor e uma lista de processos bloqueados.
    - **Atomicidade:** As operações wait e signal devem ser atômicas, ou seja, indivisíveis.
    - **Bloqueio e desbloqueio:** Quando um processo executa wait e o semáforo está negativo, ele é bloqueado e adicionado à lista de espera. Quando outro processo executa signal, um processo bloqueado é removido da lista e desbloqueado.
- **Gerenciamento da lista de espera:**
    - **FIFO:** Uma forma simples de gerenciar a lista é utilizando uma fila FIFO.
    - **Outras estratégias:** Outras estratégias podem ser utilizadas, como prioridade ou aleatória.
- **Atomicidade em sistemas multiprocessadores:**
    - **Desafios:** Garantir a atomicidade em sistemas multiprocessadores é mais complexo devido à possibilidade de interação entre processos em diferentes núcleos.
    - **Soluções:** Utilizar mecanismos como compare_and_swap ou spinlocks.

**Vantagens dos semáforos:**

- **Flexibilidade:** Podem ser utilizados para implementar diversos mecanismos de sincronização, além de locks mutex.
- **Reuso:** Uma vez implementados, podem ser reutilizados em diferentes partes do sistema.

**Desvantagens:**

- **Complexidade:** A implementação correta de semáforos requer cuidado para evitar deadlocks e outras condições de corrida.
- **Erro Prone:** O uso incorreto de semáforos pode levar a erros difíceis de detectar e corrigir.

## **Deadlocks**
- **Definição:** Um estado em que dois ou mais processos ficam esperando indefinidamente por um evento que só pode ser causado por outro processo do conjunto.
- **Causas:**
    - **Interbloqueio:** Quando processos se bloqueiam mutuamente ao esperar por recursos que outros processos estão segurando.
    - **Condições necessárias:** Para que ocorra um deadlock, as seguintes condições devem ser satisfeitas:
        - **Mutua exclusão:** Um recurso só pode ser usado por um processo de cada vez.
        - **Posse e espera:** Um processo pode manter recursos enquanto solicita outros.
        - **Não preempção:** Um recurso não pode ser retirado de um processo a não ser que ele o libere voluntariamente.
        - **Circularidade:** Existe um ciclo de espera, onde cada processo está esperando por um recurso que é mantido por outro processo no ciclo.
- **Exemplo:**
    - Dois processos, P0 e P1, cada um esperando por um recurso que o outro processo está segurando.
- **Consequências:**
    - **Sistema inativo:** Os processos envolvidos no deadlock não podem progredir, afetando o desempenho do sistema.
    - **Perda de recursos:** Os recursos alocados aos processos em deadlock ficam indisponíveis para outros processos.

## **Bloqueio Indefinido (Inanição)**

- **Definição:** Uma situação em que um processo espera indefinidamente por um recurso, mesmo que o recurso seja eventualmente liberado.
- **Causas:**
    - **Estratégias de escalonamento injustas:** Se a ordem de atendimento aos processos bloqueados não for justa, alguns processos podem ser permanentemente negligenciados.
    - **Ordem LIFO:** Se a lista de processos bloqueados for gerenciada em ordem LIFO, os processos que chegam por último podem ter prioridade para serem atendidos, causando inanição para os processos que chegaram antes.

### Prevenção e Detecção de Deadlocks
- **Prevenção:**
    - **Quebrar uma das condições necessárias para o deadlock:** Por exemplo, garantindo que todos os recursos sejam solicitados de uma só vez ou permitindo a preempção de recursos.
- **Detecção:**
    - **Algoritmos de detecção:** Periodicamente, o sistema pode verificar se existe um ciclo de espera entre os processos.
- **Recuperação:**
    - **Abortar processos:** Terminar um ou mais processos envolvidos no deadlock para liberar os recursos.
    - **Rollback:** Retornar os processos a um estado anterior, antes de entrarem no deadlock.
- **Evitação:**
    - **Alocação de recursos de forma segura:** Utilizar algoritmos de alocação de recursos que garantam que o sistema nunca entre em um estado de deadlock.


## **Problemas de Sincronização**

### O Problema dos Leitores-Gravadores

- **Contexto:** Múltiplos processos acessam um banco de dados compartilhado, alguns apenas lendo (leitores) e outros lendo e escrevendo (gravadores).
- **Desafio:** Garantir que a concorrência entre leitores e gravadores não corrompa os dados.
- **Solução:** Implementar mecanismos de sincronização para controlar o acesso ao banco de dados.

##### Tipos de Problemas

- **Primeiro problema:** Nenhum leitor deve esperar se não houver gravadores esperando.
- **Segundo problema:** Um gravador deve executar sua gravação assim que possível, sem que novos leitores sejam permitidos.

##### Solução para o Primeiro Problema

- **Variáveis compartilhadas:**
    - `rw_mutex`: Semáforo para controlar o acesso exclusivo dos gravadores.
    - `mutex`: Semáforo para proteger a atualização da variável `read_count`.
    - `read_count`: Contador do número de leitores ativos.
- **Lógica:**
    - **Leitores:**
        - Incrementam `read_count` antes de ler e decrementam após ler.
        - O primeiro leitor adquire `rw_mutex` e os demais apenas `mutex`.
        - O último leitor libera `rw_mutex`.
    - **Gravadores:**
        - Adquirem `rw_mutex` antes de escrever e liberam após escrever.

##### Vantagens e Desvantagens

- **Vantagens:**
    - Permite alta concorrência entre leitores.
    - Garante que os gravadores tenham acesso exclusivo ao banco de dados.
- **Desvantagens:**
    - Pode levar à inanição de gravadores no segundo problema.
    - Maior complexidade de implementação em comparação com mecanismos mais simples.

##### Locks de Leitor-Gravador
- **Conceito:** Extensão dos semáforos, permitindo diferentes modos de acesso (leitura ou escrita).
- **Utilização:**
    - Quando há muitos leitores e poucos gravadores.
    - Quando a distinção entre leitores e gravadores é clara.
- **Benefícios:**
    - Maior concorrência entre leitores.
    - Facilidade de uso em comparação com implementações personalizadas.

### Problema dos Filósofos Comensais

#### O Problema

- **Descrição:** Cinco filósofos sentados em torno de uma mesa circular, cada um com um prato de comida e dois hashis.
- **Objetivo:** Cada filósofo deve alternar entre pensar e comer, utilizando os dois hashis mais próximos.
- **Desafio:** Evitar que os filósofos entrem em um estado de deadlock, onde todos estão esperando pelo outro liberar um hashi.

#### A Solução Simples (e problemática)

- **Semáforos:** Cada hashi é representado por um semáforo.
- **Funcionamento:** Um filósofo pega um hashi executando `wait` no semáforo correspondente e libera o hashi executando `signal`.
- **Problema:** Pode ocorrer deadlock se todos os filósofos pegarem um hashi ao mesmo tempo e ficarem esperando pelo outro.

#### Soluções Propostas

- **Limitar o número de filósofos:** Permitir apenas quatro filósofos à mesa.
- **Verificar disponibilidade dos dois hashis antes de pegar qualquer um:** Garante que ambos os hashis estejam disponíveis antes de iniciar a refeição.
- **Assimetria:** Filósofos ímpares pegam o hashi esquerdo primeiro, e os pares pegam o direito primeiro.

#### Considerações Importantes

- **Deadlock:** Situação em que dois ou mais processos estão bloqueados, esperando por um recurso que outro processo está segurando.
- **Inanição:** Situação em que um processo é indefinidamente impedido de progredir.
- **Solução Ideal:** Uma solução para o problema dos filósofos comensais deve garantir a ausência de deadlocks e inanição.

