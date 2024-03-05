
### **Introdução**

- Analisar um algoritmo é
	* Provar a corretude
	* Avaliar o seu desempenho (Eficiência)

- Avaliar Eficiência
	* Método experimental
	* Método analítico

- Impactam em projeto de algoritmos
	* Aspecto funcional
	* Aspecto de criação (ou design)
##### - Tamanho da entrada de uma instância
* Especificar com precisão a entrada
* Quantidade de dados necessária para descrever a instância do problema
* Depende do problema que está sendo estudado
	* Ordenação: A[1...n]
	* Grafos: G(4,5)
	* Matrizes: N x N
	* Entre outros...

---
##### **- Tipos de casos**

*  Melhor Caso
	* Raramente acontece em situações do mundo real
	* **Exemplo**: Ordenar um vetor ordenado com um Insertion Sort

* Caso médio
	* Frequentemente é tão ruim quanto o pior caso
	* **Exemplo**: imagine no Insertion Sort a adição do próximo número ordenado
	
* Pior Caso
	* Quando temos uma entrada grande ou desfavorável para o algoritmo
	* Determina o limite superior para o tempo de execução do algoritmo
	* Muito frequente para alguns algoritmos

---
#### **Analise em Geral**

* Operação primitivas
	* Atribuição: x = 3
	* Operação aritmética: y + 1
	* Comparação de números: a > b
	* Indexar um array: A[j]
	* Retorno de um método: return x

* Como Realizar a analise
	* Identifique operações primitivas
	* Determine o custo inerente de cada linha, somando o custo das operações primitivas
	* Defina a situação ou o caso a analisar
	* Determine quantas vezes cada linha é executada
	* Obtenha o custo total de cada linha
		* Multiplicando o número de vezes em que é executada pelo custo da linha
	* Obtenha o custo total somando tudo
	* 
```java 
public class InsertionSort {
    public static void insertionSort(int[] arr) {
        int n = arr.length;
        
1.        for (int i = 1; i < n; ++i) {
2.            int key = arr[i];
3.            int j = i - 1;

4.         while (j >= 0 && arr[j] > key) {
5.              arr[j + 1] = arr[j];
6.              j = j - 1;
            }
            
7.            arr[j + 1] = key;
        }
    }
}```

* Considerando $t_j$ a quantidade de vezes que o while executa, temos:

|     | Cost | Time                       |
| --- | ---- | -------------------------- |
| 1   | c1   | n                          |
| 2   | c2   | n - 1                      |
| 3   | c3   | n - 1                      |
| 4   | c4   | $$\sum_{i=j}^{n} t_j$$     |
| 5   | c5   | $$\sum_{i=j}^{n} t_j - 1$$ |
| 6   | c6   | $$\sum_{i=j}^{n} t_j - 1$$ |
| 7   | c7   | n - 1                      |
|     |      |                            |
Ficando: 
 * T(n) = c1 * n + c2 * (n - 1) +  c3 * (n - 1) + c4 *  $\sum_{i=j}^{n} t_j$  +  c5 * $\sum_{i=j}^{n} t_j - 1$ + c6 * $\sum_{i=j}^{n} t_j - 1$    c7 * (n - 1) 

* No pior caso os somatórios executará um serie aritmética dadas pela formulas

	* $\sum_{j=2}^{n} j - 1$ = $\frac{n * (n + 1)}{2}$ + 1
	
	*  $\sum_{j=2}^{n} j - 1$ = $\frac{n * (n - 1)}{2}$


Simplificando a formula, temos:

T(n) = ($\frac{c4}{2}$ + $\frac{c5}{2}$ + $\frac{c6}{2}$) n² + c1 + c2 + c3 + ($\frac{c4}{2}$ + $\frac{c5}{2}$ + $\frac{c6}{2}$) n



