
## Coordenadas Homogêneas

a representação de um ponto P(x, y) em um sistema de coordenadas homogêneo é
	
	P(x * W, y * W, W) = P(X, Y, W)

onde W é uma constante != 0 

W é chamado de fator de escala, e x = X/W e y = Y/W

Sempre utilizamos W = 1, e a divisão acima é desnecessária

![[Pasted image 20240929220956.png]]

Com isso, podemos representar qualquer operação geométrica 3d como uma multiplicação de uma matriz 3x3 

**Forma Geral**:  [x', y', 1] = [x, y, 1] *   [ a  d 0 ]
							[ b  e 0 ]
							[ c   f 1 ]


--- 
### Translação

A equação matricial da translação é dada por: $$ \begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} x \\ y \\ 1 \end{bmatrix} \cdot \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ Dx & Dy & 1 \end{bmatrix} $$
Onde: * `(x', y')` são as coordenadas do ponto após a translação. * `(x, y)` são as coordenadas originais do ponto. * `Dx` e `Dy` são as distâncias de translação nos eixos x e y, respectivamente.


### Escalonamento

A equação matricial do escalonamento é dada por: $$ \begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} x \\ y \\ 1 \end{bmatrix} \cdot \begin{bmatrix} Sx & 0 & 0 \\ 0 & Sy & 0 \\ 0 & 0 & 1 \end{bmatrix} $$ Onde: * `(x', y')` são as coordenadas do ponto após o escalonamento. * `(x, y)` são as coordenadas originais do ponto. * `Sx` e `Sy` são os fatores de escala nos eixos x e y, respectivamente.

### Rotação

A equação matricial da rotação é dada por: $$ \begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} x \\ y \\ 1 \end{bmatrix} \cdot \begin{bmatrix} \cos{\theta} & -\sin{\theta} & 0 \\ \sin{\theta} & \cos{\theta} & 0 \\ 0 & 0 & 1 \end{bmatrix} $$ Onde: * `(x', y')` são as coordenadas do ponto após a rotação. * `(x, y)` são as coordenadas originais do ponto. * `θ` é o ângulo de rotação.

---

## Transformações Sucessivas

* Toda sucessão de operação de matrizes, sempre terá uma que realizará essa sucessão de operações, independente de quantidade de operações