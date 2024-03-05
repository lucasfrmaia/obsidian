### - **Introdução**

- Ao analisar um algoritmo, é importante termos como expressar a sua eficiência

- Analisar algoritmos em termos de:
	- Tempo
	- Espaço
	
* Estudar o comportamento do tempo de execução do algoritmo quando aumentamos substancialmente a sua entrada (Quando o Valor de n tende a infinito)

* Elaborar funções que delineiam o tempo x entrada
	* Funções possuem ordens, onde todas as funções de uma mesma ordem são consideradas equivalentes
	
---
### **Notações Assintótica**

##### - Notação O (Big O) 

* Função que delimita o limite superior de uma outra função
* Funções assintoticamente não negativas
* Funções f tal que f(n) ≥ 0 para todo n suficientemente grande

**Definição**: O (g(n)) = { f(n): se existe constantes positivas c e n0 tal que 0 ≤ f(n) ≤ cg(n) para todo n ≥ n0 e n0 ≥ 0 }

**Exemplo**

![[exemplo-big-o.png| 500 ]]
* A função g(n) é maior que a f(n) , ∀(n) > n0
*  A função f(n) é O (n²)

**Exemplo 2**

* Exemplos positivos
	* 5n + 2 = O(n), pois 5n + 2 ≤ cn, lembrando n e c > 0 
	*  n = O(5n + 2), pois n ≤ (5n + 2)/5, para n > 0
	* 3n² + 5n = O(n²)  => 3n² + 5n ≤ cn²

* Exemplos negativos
	* 3n² + 5n não é O(n), pois para valores n > 0 e c > 0 não existe resultado para a inequação

---
#### - **Notação Ω (Big Ômega)**

* A notação Ω delimita o limites inferior de uma dada função f(n)

 **Definição:** Para uma dada função g(n) nós denotamos Ω(g(n)) o conjunto de funções:
	-  Ω (g(n)) = { f(n) : Ǝ c, n0 > 0 : 0 ≤ cg(n) ≤ f(n), qualquer que seja n ≥ n0 }
	
* Limites assintóticos inferiores
* Exemplo: 3n2 + 5n = Ω(n2)

![[exemplo-big-omega.png| 500]]

---
#### - **Notação Θ (Big Theta)**

* A notação Θ delimita os limites superiores e inferiores de uma dada função f(n)

* Para uma dada função g(n) nós denotamos Θ(g(n)) o conjunto de funções:
	* Θ(g(n)) = { f(n) : Ǝ c1, c2 e n0 > 0 : ≤ c1g(n) ≤ f(n) ≤ c2g(n) para todo n ≥ n0 } 

![[exemplo-big-theta.png| 500]]

---
### **Classes de Algoritmos**

* **Linear** se consome tempo Θ(n) no pior caso
	* Algoritmos muito rápidos
	
* **Quadrático** se consome Θ(n2) no pior caso
	* Eficiente para n pequeno mas para valores de n altos não é eficiente

* **n x log (n)** se consome tempo Θ(n lg n) no pior caso
	* Algoritmos razoáveis

* **Polinomial**se consome tempo O(n ^ k) no pior caso
	* Sendo k um número natural

* **Exponencial** se consome o tempo Ω(a ^ n) no pior caso
	* Sendo a um número real maior que 1
	* Não são algoritmos polinomiais

![[algoritmos-classficiacoes.png| 400]]

---
### **Exercícios**

#### **- Exercício 1**

* Implemente em Python o Insertion Sort e faça uma análise estatística dos resultados para entradas de tamanho (pior, melhor caso e caso médio)

```
- 100
- 200
- 250
- 300
- 1.000
- 5.000	
```

* Trace um gráfico com os tempos e os tamanhos da entradas

**Resposta**

```python
def insertionSort(arr):
    n = len(arr)
     
    for i in range(1, n):
        key = arr[i]
        j = i-1
          
	    while j >= 0 and key < arr[j]:
		     arr[j+1] = arr[j]
		     j -= 1
	    arr[j+1] = key
```

![[grafico_insertionsort.png]]

---
#### - Exercício 2

- A afirmação Θ(n) = Θ(n2) é verdadeira ou falsa? Se for verdadeira justifique. Se for falsa, mostre um contraexemplo.

	- A primeira afirmação, Θ(n) = Θ(n^2), é falsa. Isso porque a notação Θ descreve limites assintóticos apertados de uma função. Para Θ(n) = Θ(n^2) ser verdadeira, significaria que as funções n e n^2 crescem no mesmo ritmo, o que não é o caso. Um contraexemplo simples pode ser observado quando n cresce. Por exemplo, para n = 10, temos n = 10 e n^2 = 100. Para n = 1000, temos n = 1000 e n^2 = 1000000. Claramente, n^2 cresce muito mais rapidamente do que n.

- A afirmação Θ(n2) = Θ(n) é verdadeira ou falsa? Se for verdadeira justifique. Se for falsa, mostre um contraexemplo.

	* A segunda afirmação, Θ(n^2) = Θ(n), também é falsa, por motivos semelhantes. Novamente, as funções n^2 e n não crescem no mesmo ritmo. Um contraexemplo simples pode ser observado com valores crescentes de n, onde n^2 aumenta muito mais rapidamente do que n. 


---
### **- Exercício 3**

|       | T(n) = n | T(n) = n x lg(n) | T(n) = n² | T(n) = n³ | T(n) = 2^n |
| ----- | -------- | ---------------- | --------- | --------- | ---------- |
| 5     | 0        | 0                | 0         | 0         | 0          |
| 10    | 0        | 0                | 0         | 0         | 0          |
| 20    | 0        | 0                | 0         | 0         | 0          |
| 50    | 0        | 0                | 0         | 0         | 1125899    |
| 100   | 0        | 0                | 0         | 0         | 1.2676e+21 |
| 1.000 | 0        | 0                | 0         | 1         | 1.071e+292 |
