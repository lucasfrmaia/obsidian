
### **Probabilidade em Geral**

**Espaço Amostral (Ω)**
- Conjunto de todos os possíveis resultados de um experimento aleatório ou fenômeno aleatório.
    
**Operação com eventos**
* Sejam os eventos A e B definidos no mesmo espaço amostral
	- A∪B: União dos eventos A e B.
	- A∩B: Intersecção dos eventos A e B.
	- A e B são disjuntos ou mutuamente exclusivos quando não têm elementos em comum, isto é, A∩B= ∅
    
**O complementar de um evento A é representado por**
* A^C  ou A barra

**Exemplo 1.0**

* **Eventos**: A = {2, 4, 6}, B = {4, 5, 6} e C = {1}
	* **A ∩ B**: = {2, 4, 6} ∩ {4, 5, 6} = {4, 6}
	* **A ∩ C** = {2, 4, 6} ∩ {1} = ∅
	* **A ∪ B** = {2, 4, 6} ∪ {4, 5, 6} = {2, 4, 5, 6}
	* **A^C** = {1, 3, 5}


**Definição Clássica**
- Se um experimento aleatório tiver n(Ω) resultados mutuamente exclusivos e igualmente prováveis e se um evento A tiver n(A) desses resultados. A probabilidade do evento A representado por P(A), é dado por:

	* P(A) = $\frac{n (A)}{n (Ω)}$ 

 **Exemplo 1.1**
- Considere o lançamento de 2 dados balanceados. Calcular a probabilidade de:
	- Obter soma 7;
	- Obter soma maior que 10;
	- Que o resultado do primeiro dado seja superior ao resultado do segundo.

1. Possibilidades => (1+6) , (5+2), (4+3), como são 2 dados então para cada elemento terá seu oposto => (1,6) = (6,1) 
	* Dado isso a probabilidade é de **6/36** ou **1/6**

2.  Possibilidades => (6+5) , (6+6), Mesmo caso do anterior mas 6,6 são iguais então só conta uma vez  
	 *  *Dado isso a probabilidade é de 3/16 ou 1/12

3. 
**![](https://lh7-us.googleusercontent.com/Nu_0Lbizvs7OSYw5B-gJZia6ZuVxY1wEUWyMY9TRfRSGZJrHIimGhFnHT6aaorQld8SbueLohSolIq63-d77uSChz3v2wSD8JPj8TNw-gkFE3Xjr5aMVfJQPG_vpeDMBBuAx6YrLC8OS3M_464IUlyE)*
* Serão os elementos da matriz triangular inferior, acima da diagonal principal que são 15/36

---
### **Definição axiomática**
- A probabilidade de um evento A define-se com o número P(A), tal que satisfaz os

**![](https://lh7-us.googleusercontent.com/4vaaHu6mqMHFnW-YILM389hid7TSrFFeWi9Cg64X24eRQT0IwIpwqvgLiWyIMeiBvKBQ-P7Z3FOd72x_ykflYjuhxqzL2973NGGCaJyLqg1gt6ph4QWoEwnvekUTe2LNnafWw83oSGPuysKECUpEKGg)**

1. A probabilidade sempre estará entre 0 e 1 inclusivo
2. A probabilidade de todo espaço amostral é 1
3. se os eventos são exclusivos então a probabilidade será o somatório de todos os eventos
    
**Propriedades**

**![](https://lh7-us.googleusercontent.com/aRotW6sDWEPxkRoFI9T9ZN7VEA1Ver0ONXMCpfJZetyKkv3IqhRSvZWvoAfGe3wl_vFvArkl52xgZXb3Ob-E_HD0mXyQBzQN7jwovueYg3sbyL066cfTHWqZ8YstBUlssz7Z2U5FJIajUQ7e0jAmbcY)

**Exemplo 1.3**

**![](https://lh7-us.googleusercontent.com/Zqrk3H-Yf_M7xwm_qN5xV5Xs9pIQRPV-tmPEx0LBs0bCVkZDrsTaTYroe86_gTUSCmOTiPBB8Lk4YM70Qz2U_niR2kR1HXmXe-dFESzSS7dyt0DNc_iq88HX2UpRVraWvlgOIqbyr8AEo0co6KdTYv8)**

**![](https://lh7-us.googleusercontent.com/d7iVGvekeUcdnwc4p9zWQOFPj0kx9J1ZfLw5Rdg1j2lBT77AAZl1jZ32pMDuzfZeUymcgwyBgqq0uaBiga8QluJOw43hE-PelMtFKL-1GYefuz6dcx6cwptw3aQOal2JiXj_CSqtFPCl0Ka1BPVH08o)**

1. **H** é o conjunto de pessoas que são dos sexo masculino
2. **H^c** é o conjunto complementar a H, ou seja todos os elementos que não estão em H, então será o conjunto das mulheres
3. **B** será o conjuntos de todas as pessoas brancas
4. **B^C** será o conjunto de todas as pessoas que não são brancas, ou seja outra raça
5. **H ∩ B** serão todos os homens brancos
6. **H U B** serão todas as pessoas homens ou da raça branca
7. **H^C** ∩ B serão todas mulheres que são da raça branca
8. **H^C** U B serão todas as mulheres ou pessoas da raça branca
9. **H^C ∩ B^C** serão todas as mulheres de outra raça
10. **H^C U B^C** serão todas as mulheres ou pessoas de outra raça

**Calculando probabilidades**

- **P (H)** = 2354693 / 5218071 = 0.451
- **P (H^C)** = 1 - P(H) = 1 - 0.451 = 0.549
- **P (B)** = 3836637 / 5218071 = 0.735
- **P (B^C)** = 1 - 0.735 = 0.265
- **P (H ∩ B)** = 1726384 / 5218071 = 0.33
- **P (H U B)** = P(H) + P(B) - P (H ∩ B) = 0.451 + 0;735 - 0.33 = 0,856
- **P(H^C ∩ C)** = 2110253 / 5218071 = 0.404
- **P(H^C U B) = P(H^C) + P(B) - P(H^C ∩ B)** = 0.549 + 0.735 - 0.404 = 0.8

---
### **Probabilidade Condicional e Independência**

* ***Definição**: Probabilidade condicional Sejam A e B dois eventos em um mesmo espaço amostral, Ω, a probabilidade condicional de A dado que ocorreu o evento B, é representado por P(A|B) é dado por:

**![](https://lh7-us.googleusercontent.com/T7EI1Q9Zu6a5Rqm3lkrkAJsn5w-0nYm2XQI9U-Sge7CNtaCquwCu3RrLCzBFsu-QKd6ReKSkGVBoAWI-T2cIHjI746ffj0hoJw5QZOBvCPUcWNvzmBpnPJZvjY5vvDC_XEf7xrHMy0GAC5A4dPYC9lw)**


**Exemplo 2.0 **

- Selecionamos uma semente, ao acaso, uma a uma e sem reposição de uma sacola que contém 10 sementes de flores vermelhas e 5 de flores brancas. Qual é a probabilidade de que
	(a) a primeira semente seja vermelha.
	(b) a segunda seja branca se a primeira foi vermelha.

1. **P(A)** = 10/15 => ⅔
2. **P(A ∩ B) / P(B)** => 5/14

**Fórmula**

**![](https://lh7-us.googleusercontent.com/ypEjGlVTT6dQ9IuGJsHorofS8I-3kHc0GQQ5zKhmowND1guLVSx0LE9hdAJbZs23VQtx9XryMXQ_bO2COMfrkCAmaKLKwPf1J6WsrKY_JKibyswDuMRdf-YmxJEWdh6jdgm8b4F645KLS1a2eCC4wRM)**

**Exemplo 2.1**
* No exemplo 2, suponha que temos interesse em determinar a probabilidade que as duas sementes selecionadas sejam brancas.

**Método redução espaço amostral**

* **P(A) = 5/15**
	* Ao remover uma branca ficamos com 4 flores brancas e 10 vermelhas
	* A probabilidade de ser uma branca de novo é de 4/14
	* Multiplicando fica 20/210 = 2/21

**Exemplo 2.2**
* Na Cidade de São Paulo, a probabilidade de chuva no primeiro dia de setembro é 0,50 e a probabilidade de chuva nos dois primeiros dias de setembro é 0,40. Se no primeiro de setembro choveu, qual é a probabilidade que no dia seguinte não chova ?

* A = “Chove primeiro dia” 
* B = “Chove segundo dia”

P(A) = 0.5
P(A∩B)=0,40

**![](https://lh7-us.googleusercontent.com/pi0_qlVpONjkLyrdG_euZdrVN_O5_J24q0zQCXioetqcwFa63bLQPlP8otRCGVCh9CZr0h1cKTMvsG7ZICSQ1z0Dm23aNiXbehR0pj7VPBSvK1opxX3Td_d0yrAwe6RjWCOBUv91HzKjaZxKdB4TC1s)**

--- 

### **Independência de eventos**

* Dois eventos A e B são independentes se a informação da ocorrência ou não de B não altera a probabilidade da ocorrência de é dado por
	* P(A|B)=P(A), P(B)>0
* Consequentemente, temos que dois eventos A e B são independentes se somente se,
	* P(A∩B)=P(A)P(B).

**Exemplo 3.0**
* Em uma escola, 20% dos alunos tem problemas visuais, 8% problemas auditivos e 4% tem problemas visuais e auditivos. Selecionamos um aluno desta escola ao acaso:
	a) Os eventos de ter problemas visuais e auditivos são eventos independentes?
	
	b)  se aluno selecionado tem problemas visuais, qual é a probabilidade de que tenha problemas auditivos?

	c) qual é a probabilidade de não ter problemas visuais ou ter problemas auditivos

**Tendo como** 
* A = Cegos
* B = Surdos
* C = Cegos e Surdos

a) P(A ∩ B) = P(A)P(B)
4% = 20% * 8%
4%  != 160%

b) P(V | B) = 4% / 8% = 20%

c)  P(A U B) => 8% + 20% - 4% => 24%
	P(A^C U B) => P(A^C) + P(B) - P(A  ∩ B)
	1 - P(A) + P (B) - P(A  ∩  B)
	1 - 0,2 + 0,08 - 0,04 = 0,84

#### **Teorema**

**![](https://lh7-us.googleusercontent.com/Cc_rXWdQDI-bHY0sMgqvXB60weDjR3DSzl8p980Hqt1RvhMKsMkikhl0elggs1KVEU-pBqgT8HI3GdNGzH2AGayLEPuWst8pZOQm76zkyEiNEK_wbl8yseczkQRoCaL7wWYq3PIoJ47S9j0yoy6h2u8)**

**Exemplo 3.1:** 
* Um atirador acerta 80% de seus disparos e outro (nas mesmas  condições de tiro), 70%. Qual é a probabilidade de acertar se ambos atiradores disparam simultaneamente no alvo? Considere que o alvo foi acertado quando, pelo menos, uma das duas balas tenha feito impacto no alvo.

**P(A U B) = 0.8 + 0.7 - (0.8*0.7)**

--- 
### **Lista de Exercício de Probabilidade**


1.  Em uma empresa há 10 homens e 25 mulheres. Entre os homens, 5 são
Formados em Direito e, entre as mulheres, 7 são formadas também em Direito. Os demais são formados em Administração. Ao sortear uma pessoa desse grupo:

A = Administração
D = Direito
H = Homem
M = Mulher

a) Qual é a probabilidade de ser um homem formado em Administração?

* P(H ∩ A) = 5/35 => 1/7

b) Sabendo-se que a pessoa sorteada é formada em Administração, qual é a
probabilidade de ser homem?

* P(H | A) =  5 / 23
* P(H ∩ A) = 1/7
* P(A) = 22 / 35
* P(H | A) = 1/7 / 22 / 35

c) Sabendo-se que é um homem, qual é a probabilidade de ser formado em
Administração?

* P (A | H) = 5 / 10

d) Sabendo-se que a pessoa sorteada é formada em Direito, qual é a
probabilidade de ser uma mulher?

* P(M | D) = 7 / 13

e) Sabendo-se que a pessoa sorteada é uma mulher, qual é a probabilidade de ser formada em Direito?

* P(D | M) = 7 / 25

2. Um casal vai mergulhar em busca de pérolas no oceano. Sabemos que em
razão das habilidades e do condicionamento físico deles, o rapaz tem 3/7 de
chance de encontrar alguma pérola e a moça, 2/7 de chance. Sabemos que a
chance de os dois encontrarem pérolas é de 1/7. Sabendo-se que o rapaz
encontrou uma pérola:

* R = Rapaz
* M = Moça

* P* (R) = 3/7
* P(M) = 2/7
* P(R U M) = 1/7

a) Qual é a chance de a moça NÃO ter achado pérola alguma antes e depois
de saber que seu esposo encontrou uma delas?

* P(M^C) = 1 - 2/7
* Eventos independentes
* P(M^C | R) = P(M) * P(R) / P(R) = P(M^C)

b) Qual é a chance de a moça encontrar uma pérola depois de saber que o
rapaz conseguiu uma pérola?

* P(M) = 2/7

c) Decida se o evento de não encontro de pérola do rapaz é mutuamente
excludente ao evento do não encontro de pérola da moça.

* São eventos que não podem ocorrer simultaneamente. 
* Não são 


d) Sem ter a informação do achado do rapaz, qual é a chance de somente um
deles encontram alguma pérola?

* Sem Resposta

3. Considere três caixas, cada uma delas com dois compartimentos. Na caixa 1 há uma nota de R$ 50 em cada compartimento. Na caixa 2 há uma nota de RS 10 em cada compartimento. Na caixa 3 há uma nota de R$ 50 em um compartimento e uma nota de RS 10 em outro. Escolhendo uma caixa ao acaso, abrimos um compartimento. Se a nota é de R$ 50, qual é a probabilidade de que no outro compartimento também haja uma nota de R$50?

* Caixas com 50: 2
* Caixa com 2 notas de 50: 1

* P(A) = 1/2

4. Em uma caixa existem 3 envelopes brancos e 2 envelopes pardos. Eles são
extraídos da caixa sem reposição. Calcule:

a) A chance de que saiam três envelopes brancos sucessivos.

* P(A) = ⅕ * ¼ * ⅓ = 1/60

b) A chance de que saiam 2 pardos sucessivamente.

* P(B) = ⅕ * ¼ = 1/20 

c) A chance de que saiam ou 2 pardos sucessivos ou 3 brancos sucessivos.

* P(A U B) = 1/60 + 1/20 - 

d) A chance de que os envelopes sejam sorteados em tipos intercalados.

* Espaço: 5! / 3! * 2! = 10
* P(C) = 1/10

5-Considere dois eventos A e B. Sabendo que P(A) = 0,4 e P (A U B) = 0,7. Seja P(B) = p. A partir disso, calcule os valores de p para que os eventos A e B sejam:

a) Mutuamente excludentes
**![](https://lh7-us.googleusercontent.com/HnOdjF7toMh40gpXd__FfB9tWmxy_5cB2tOXb22NJ253t--44CUTwoVPlH6Mksad6aqttO-7ZxIwZj2mRvVDRlELgoUlh5XKjVdNN9xLexkW314fRrAeKTOn1sBVWWozROPg14B724RebDu2dPvNWJc)**
* 0.7=0.4+p−0
* p = 0.3

b) Independentes

* 0,7 - 0,4 - p = - P (A V B)

* P (A V B) = - 0.3 + p
	* -0.3´+ p = p * 0.4
	* -0.3 = p * 0,4 - p
	* 0.3 = -0.6p
	* 0.3 = 0.6p
	* p = 0.3/0.6 => 1/2 

--- 
### **Variáveis bidimensionais**

**Variáveis bidimensionais**
* Distribuições conjuntas e marginais
* Associação entre variáveis

**Exemplo: 4.1** 
* Uma amostra de 20 alunos do primeiro ano de uma faculdade foi escolhida. Perguntou-se aos alunos se trabalhavam, variável que foi representada por X, e o número de vestibulares prestados, variável representada por Y . Os dados obtidos estão na tabela abaixo.

**![](https://lh7-us.googleusercontent.com/qEwBJKB97BsXm4fAHFbGc_uTrMwla6lR3le_GhLeloSRKokVs7iInj8xaUONTE0SuNaHPiU5zvc93tEFG8vqcr1iOAJIOgGzjr8l1I6Ilv6DHlKhkaNJI6P4gyaZzf6JbPzQGnTsi9aaLQBsMr7PwYw)**

**Melhor Visualização**

**![](https://lh7-us.googleusercontent.com/T2LaihLF31suyXZQ1dRt96XLpzjgYxfyfz_VC8w6Lzt6ogpdX-QESqK-uSncD4isBpLH_HqBF3hw7TgKafO3X7SYi09HBGw1ywUcS7Q0OrrzaHqlpNMMcJzYw5VYiPKtLHXefB--6NrW55QlqnR5ruI)**

**Eixo x**: total de variáveis do eixo x
**Eixo y**: total de variáveis do eixo y**
**Dados da Tabela**: São as frequências
**Sum**: soma das frequências em relação verticalmente e horizontalmente

**Marginais**
* são a soma das frequências em relação ao eixo

**Exemplo:**
* Marginal de X é 12 e 8 que somados é 20
* Marginal de y é 5 + 4, 6 + 2 e 2 + 1 = 20

**Exemplo 4.0**
	Um estudo envolveu 345 pacientes HIV positivos, acompanhados
	durante um ano, pelo setor de doenças infecciosas de um grande
	hospital público. Os dados apresentados contêm as ocorrências
	relacionadas às variáveis número de internações (I) e número de crises
	com infecções oportunistas (C).

**![](https://lh7-us.googleusercontent.com/-ikhqgkoNo0HRd0OwYXRX16Lv0J4rE6ysqC2o0zUxmFbUl1qbZG2zYHGXsdBSpA9JBuiQsFWp0AB8YFyVi18v_WN9a1xWR4Qz8_cLRUOpVGg8VV4hGFVg6J4EdgHKl6uX5BEaGR0jxPXehzTS0OIi6g)**

**Marginal de I**
	0 => 84 + 21 + 8 + 2 + 0 = 115
	1 => 20 + 59 + 35 + 14 + 2 = 130 
	2 => 6 + 11 + 43 + 28 + 12 = 100
	=> 115 + 130 + 100 = 345

**Marginal de C**
	0 => 84 + 20 + 6 = 110
	1 => 21 + 59 + 11 =  91
	2 => 8 + 35 + 43 = 86
	3 => 2 + 14 + 28 = 44
	4 => 0 + 2 + 12 = 12
	=> 110 + 91 + 86 + 44 + 12 = 345

---
### **Função de probabilidade conjunta**

* Sejam X e Y duas VAs discretas originárias do mesmo fenômeno aleatório,
com valores atribuídos a partir do mesmo espaço amostral.

* A função de probabilidade conjunta é definida, para todos os possíveis
pares de valores (X, Y ), da seguinte forma:
	- p(x, y) = P(X = x) ∩ (Y = y) = P(X = x, Y = y).

* Ou seja, p(x, y) representa a probabilidade de (X, Y) ser igual a (x, y).
	*  A função de probabilidade conjunta também pode ser chamada de distribuição conjunta ou simplesmente conjunta das variáveis.

**Exemplo 5.0**

**![|350](https://lh7-us.googleusercontent.com/ZTPA6UK0ZyjnmSwz39U9vNbIPSNoLh7OVKQ_Y18vAdr8MiND5UMApG2ZwpJz8ixeMUs9-WcXQfX_gbcqpnCFaAAYlZ750CvjfOgmopiO4AWW_9TtRlR0iQ7fdP4_4iY6uZk8ytsNeiqAn3fi6kL8ayI)**

**![350](https://lh7-us.googleusercontent.com/OSZXf97bbMlgeJsR3NiWTNsKwc1WBc8VuWRL6-WVZbpimXJ_uNhJatdx3wizbSpO7nTxmkJyHe33_Hk7-a8fcKUhAZVkW34zRsxpnBwrspgffpzD_ahAb6mg99rL4N6hfvtJsBWSF93pEUY8PZF1hq4)**

p(2,2) = 0,2
p(0,0) = 0
p(X = 1) = 0.3 ***Marginal**

--- 

### **Probabilidade Condicional**

* A Probabilidade Condicional de X = x, dado que Y = y ocorreu, é
dada pela expressão:
	* P(X = x|Y = y) = P(X = x, Y = y)
	* P(Y = y) , se P(Y = y) > 0.

- Duas VAs discretas são independentes, se a ocorrência de qualquer
valor de uma delas não altera a probabilidade de valores da outra. Em
termos matemáticos
	* P(X = x|Y = y) = P(X = x).

