
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

### Transformações Sucessivas

* Toda sucessão de operação de matrizes, sempre terá uma que realizará essa sucessão de operações, independente de quantidade de operações
* Não são comutativas , apenas em casos específicos

## Transformações Janela Windows to Viewport

- Uma área de coordenadas do mundo selecionada para exibição é chamada de **janela**.
- Uma área em um dispositivo de exibição para a qual uma janela é mapeada é chamada de **viewport**.
- A janela define o que será visualizado; o viewport define onde será exibido.
- Frequentemente, janelas e viewports são retângulos em posição padrão, com as bordas dos retângulos paralelas aos eixos coordenados.
- Outras geometrias de janelas ou viewports, como formas poligonais gerais e círculos, são usadas em algumas aplicações, mas essas formas demoram mais para processar.
- O mapeamento de uma parte de uma cena de coordenadas do mundo para coordenadas do dispositivo é chamado de **transformação de visualização** ou **transformação de janela para viewport**, também conhecida como **transformação de janela**.

![[Pasted image 20240930190027.png]]

- Suponha que um objeto $\((x_w,  y_w)\)$ esteja colocado no sistema de coordenadas do mundo como mostrado na figura. Agora precisamos transformar o conjunto de coordenadas para um viewport $\((x_v, y_v)$
- Para manter a mesma colocação relativa no viewport como na janela, exigimos que:

$$
\frac{x_v - x_{vmin}}{x_{vmax} - x_{vmin}} = \frac{x_w - x_{wmin}}{x_{wmax} - x_{wmin}}
$$

$$
\frac{y_v - y_{vmin}}{y_{vmax} - y_{vmin}} = \frac{y_w - y_{wmin}}{y_{wmax} - y_{wmin}}
$$
