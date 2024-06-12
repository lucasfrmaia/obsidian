
### Problema da Mochila Binária

No problema da mochila binária, temos uma mochila com capacidade `W` e `n` itens, cada um com um peso `w[i]` e um valor `v[i]`. O objetivo é maximizar o valor total dos itens colocados na mochila sem exceder a capacidade `W`.

### Diferenças Principais
1. **Exploração do Espaço de Busca**: O backtracking explora todas as possíveis soluções, enquanto o branch and bound usa limites para podar ramos que não podem levar a uma solução melhor.
    
2. **Eficiência**: O branch and bound é geralmente mais eficiente porque evita explorar ramos desnecessários, usando uma abordagem mais dirigida pela heurística dos limites.
    
3. **Complexidade**: O backtracking pode ter uma complexidade exponencial no pior caso, enquanto o branch and bound pode ser mais eficiente em termos de tempo devido à poda de ramos.

```java
function backtrack(i, currentWeight, currentValue, capacity, weights, values, n):
    if i == n:
        return currentValue
    
    if currentWeight + weights[i] <= capacity:
        include = backtrack(i + 1, currentWeight + weights[i], currentValue + values[i], capacity, weights, values, n)
    else:
        include = 0
    
    exclude = backtrack(i + 1, currentWeight, currentValue, capacity, weights, values, n)
    
    return max(include, exclude)
```


---

## **Subset Sum**

```java
function subsetSum(S, T):
    n = length(S)
    dp = array of size (n+1) x (T+1) filled with False

    for i from 0 to n:
        dp[i][0] = True

    for i from 1 to n:
        for j from 1 to T:
            if S[i-1] > j:
                dp[i][j] = dp[i-1][j]
            else:
                dp[i][j] = dp[i-1][j] or dp[i-1][j - S[i-1]]

    return dp[n][T]
```


## Triangulo de Pascal

```java
function generatePascalTriangle(n):
    dp = array of size (n+1) x (n+1) filled with 0

    for i from 0 to n:
        for j from 0 to i:
            if j == 0 or j == i:
                dp[i][j] = 1
            else:
                dp[i][j] = dp[i-1][j-1] + dp[i-1][j]
                
    return dp

```

![[Pasted image 20240612012236.png]]

### LCS

```java
LCS

LCS(X, Y)
m ← length(X)
n ← length(Y)

for i ← 1 to m do
  c[i, 0] ← 0

for j ← 1 to n do
  c[0, j] ← 0

for i ← 1 to m do
  for j ← 1 to n do
	  if (Xi == Yj) 
		  c[i, j] ← c[i-1, j-1] + 1
	  else
		 c[i, j] ← max(c[i-1, j], c[i, j-1])

return c[m, n]
```

![[Pasted image 20240612024817.png]]

### Mochila binaria dinamica

```java
MochilaPD(itens[1..n],W)

criar matriz V[n,W]
inicializar V[0,j]<-0 e V[i,0]<-0

for i<- 1 to n do
  for j<- 1 to W do
	if peso(i) > j then
	 V[i,j]<- V(i-1,j)
	else
	 V(i,j)<-max{V(i-1,j-peso(i)]+valor(i),V[i-1,j]}

return V(n,W)
```

### Mochila Fracionaria

![[Pasted image 20240612025124.png]]