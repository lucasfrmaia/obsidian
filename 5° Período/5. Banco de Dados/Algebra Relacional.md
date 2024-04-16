



## Operações com Algebra Relacional

![[Pasted image 20240415170030.png]]


# Seleção

* Sintaxe: σ  <Condição de Seleção> (Tabela)
### Operadores da seleção

![[Pasted image 20240415170736.png]]

### Exemplo de Tabela

![[Pasted image 20240415174138.png]]

* σ saldo >= 100 (Cliente)
* Essa query seleciona todos os clientes com saldo maior que 100

## Projeção

* A projeção está intimamente ligados com outras relações, 

* Sintaxe: π lista de atributos (Alguma operação relacional, como produto cartesiano, seleções e etc...)

* Lista de atributos separados por virgula

![[Pasted image 20240415174418.png]]

### Exemplo

1. Selecionar e mostrar todos os clientes com saldo >= 100

* π ... Atributos) ( σ saldo >= 100 (Cliente) ) 


## Atribuição

* Serve para salvar query's em variáveis

![[Pasted image 20240415175328.png]]

### Apelidos para query's

![[Pasted image 20240415175530.png]]

- R(...atributos) <= Relação


## Produto Cartesiano

![[Pasted image 20240415175703.png]]

* Relação de Todos com Todos, juntando cada tuple de uma tabela x , com todas as tuples da tabela Y

### Exemplo

![[Pasted image 20240415180104.png]]

## Operações Sobre Conjunto

![[Pasted image 20240415182438.png]]

### União

### União

![[Pasted image 20240415184236.png]]

### Interseção 

![[Pasted image 20240415184327.png]]

### Diferença

![[Pasted image 20240415184355.png]]

### Exemplo

![[Pasted image 20240415185254.png]]
![[Pasted image 20240415185318.png]]

