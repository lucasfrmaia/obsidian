
### Primeira Questão

- Construir arvore de derivação
- Para provar se é ambígua ou não, é só fazer uma mesma sentença gerar 2 arvores

### Segunda Questão


Para um analisador sintático preditivo recursivo funcionar, ele deve seguir 2 regras:

1. Não possuir recursão a Esquerda
		Exemplo: S -> Sa
2. As produções serem bem fatoradas e não começarem com um mesmo terminal
		Exemplo: S -> aAb | abC | B

### Terceira Questão


Passos para verificar se é uma LL(1)
1. Calcular os conjuntos FIRSTS e Follows
2. Montar a Tabela
3. Verificar se tem duplicatas na tabela


#### Calcular o Firsts

Esse conjunto é composto pelo primeiro terminal de cada produção
	 Se o primeiro elemento for uma terminal, o conjunto também incluirá o conjunto desse terminal

### Calcular os Follows

1. Obs: esse conjunto não possui o simbolo epislon
2. Obs: Notaçao de conjuntos

3. A variavel de partida sempre conterá o simbolo $
4. Se existir uma do tipo A -> aXB, então o first de B será o follow de X
5. Se for uma produção do tipo A -> aX ou então aXB onde B tem uma produção de epislon então os terminais que estão em A será o follow de X

#### Montar a Tabela

1. Montar a tabela Terminais x Variavel (Incluir o $)
2. Para cada variavel, no conjunto do first, verificar qual é a primeira produção que gera aquele terminal com base na tabela e anotar na tabela
	1.  Se o terminal for o epilson, preencher essa produção nos follows
3. A gramática não é LL(1) porque, ao tentar montar a tabela de análise, encontramos dois caminhos diferentes para S' quando o próximo símbolo é ‘e’. Isso quebra a regra de escolha única e impede que a gramática seja analisada por um analisador preditivo LL(1).

---







