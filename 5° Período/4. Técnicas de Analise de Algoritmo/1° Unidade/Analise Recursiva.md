
### Técnicas de Analise de Recorrência

* Método da substituição
* Expansão telescópica (ou desdobramento)
* Árvore de recursão
* Teorema Mestre

---
##### Método da Substituição

* Método inspirado na indução matemática
* Eficiente para provar upper e lower bounds (Big Ômega)
	* Define dois passos:
		* Pressupor a relação de solução
		* Provar por indução que a suposição é verdadeira
* Útil quando é fácil estimar a forma da solução

* Seja T um teorema que se quer provar. 
	* Suponha que T inclui um parâmetro n que pode ter como valor qualquer número natural.
	* Ao invés de provar diretamente que T é verdade para todos os valores de n, provamos as seguintes condições:
* T é verdade para n = n0.
* Para n > n0, se T é verdade para todo n0 < n, então T é verdade para n

**Exemplo**

![[example-metodo-substituicao.png]]

---
##### **Método do Teorema Mestre**

* Sejam a >= 1 e b >= 1 constantes, seja f(n) uma fração e seja T(n) definida para inteiros não-negativos pela relação de recorrência

			T(n) = a T(n / b) + f(n)
			
* Onde interpretamos que n/b significa [n/b] (Função chão) ou [n/b] (Função teto)  então T(n) pertence limitada assintoticamente da seguinte maneira

![[Pasted image 20240312230641.png]]

**a = resultado do log do passo 2**
**$b^c$ = expoente da função f(n)**

**Algoritmos de aplicação**
* **Passo 1**: Identificar a, b e f (n)
* **Passo 2**: Determinar
* **Passo 3**: Comparar f(n) assintoticamente
* **Passo 4**: De acordo com o caso, aplicar a regra correspondente

---
**Exemplo:**

T(n) = 9T ($\frac{n}{3}$) + $n^c$

**Passo 1 - Variáveis:**
 * a = 9
 * b = 3
 * c = 1
 * f(n) = n

**Passo 2 - Determinar**
* n ^ ($log_b$a) 
* n ^ ($log_3 9)$
* $n^2$

**Passo 3 - Comparar a f(n)**
* Comparar a f(n) com o a função encontrada no passo anterior
	* $n^2$ e n
	* Para se achar o épsilon devemos subtrair -1

**Passo 4** - Analisar o caso
* Como se subtraiu o épsilon , então cai no caso 1
* Então será O (n ^ ($log_3 9)$) ou $n^2$

---
**Exemplo 2**

T(n) = 2 T($\frac{n}{2}$) + Ômega(n)

**Passo 1**
* a = 2
* b = 2
* c = 1
* f (n) = Ômega(n)

**Passo 2**
* n ^ ($log_2 2)$ 
* n

**Passo 4**
*  Como n = n então temos o caso 2
*  Ômega($n^1$ * $log_2$ n)
*  Ômega(n * $log_2$ n)

---
**Exemplo 3**

T(n) = 3 T($\frac{n}{4}$) + n $log_2 n$

**Passo 1**
* a = 3
* b = 4
* c = 1
* f (n) = n $log_2 n$

**Passo 2** 
* n ^ ($log_4 3)$ | [Mudança de Base](Anotações.md)
*  0.5 < n < 1

**Passo 3**

* Como o valor está entre 0.5 e 1 , e o **c** é 1  então podemos assumir que falta um determinado K para se chegar a 1 , então se aplica o **caso 3**
	* Ficando Ômega(n $log_2 n$))

--- 
##### Método da Visão Telescópica

* Consiste em desenvolver a relação de recorrência até que possa ser detectado o seu comportamento no caso geral.

* Resumindo:
	* Usar (algumas poucas) substituições repetidamente até encontrar um padrão.
	* Escrever uma fórmula em termos de n e o número de substituições i.
	* Escolher i de tal forma que todas as referências a T() sejam referências ao caso base.
	* Resolver a fórmula

![[Pasted image 20240312230921.png]]![[Pasted image 20240312230932.png]]![[Pasted image 20240312230944.png]]