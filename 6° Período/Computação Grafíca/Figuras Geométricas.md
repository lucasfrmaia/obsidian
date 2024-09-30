

## Método Explicito da Circunferência

A equação de uma circunferência com centro na origem e raio R, em coordenadas cartesianas, é dada por:
						x² + y² = R²

Outra abordagem seria usar a equação explícita da circunferência, y = f(x):
					    y =  $\sqrt{R² - x²}$

Para desenhar 1 4 de circunferência (os outros 3 4 são desenhados por simetria), poderíamos variar x de 0 a R, em incrementos de uma unidade, calculando +y a cada passo através da equação acima

## Método Explicito da Circunferência

Uma maneira de resolver o problema dos gaps é “plotar” x = R. cos θ e y = R * sin θ, para variando de 0 a 90 graus, mas essa solução também é ineficiente, pois precisa de funções caras (sin e cos).

## Algoritmo do "Ponto-Médio" para Circunferências

Consideraremos apenas um arco de 45º da circunferência, o 2º octante, de $x = 0$, $y = R$ a $x = y = \frac{R}{\sqrt{2}}$, e usaremos o procedimento Circle Points para traçar todos os pontos da circunferência. Assim como o algoritmo gerador de linhas, a estratégia é selecionar entre 2 pixels na malha aquele que está mais próximo da circunferência, avaliando-se uma função no ponto intermediário entre os dois pixels. 

No segundo octante, se o pixel $P = (x_p, y_p)$ foi previamente escolhido como o mais próximo da circunferência, a escolha do próximo pixel será entre os pixels $E$ e $SE$. 

Seja a função $F(x, y) = x^2 + y^2 - R^2$, cujo valor é 0 sobre a circunferência, positivo fora dela e negativo dentro. Se o ponto intermediário ("ponto-médio") entre os pixels $E$ e $SE$ está fora da circunferência, o pixel $SE$ é escolhido, porque está mais próximo dela. Por outro lado, se o ponto intermediário está dentro da circunferência, então o pixel $E$ é escolhido.

A escolha é feita com base na variável de decisão $d$, que dá o valor da função no "ponto-médio":

$$
d_{\text{old}} = F(x_p + 1, y_p - \frac{1}{2}) = (x_p + 1)^2 + (y_p - \frac{1}{2})^2 - R^2
$$

Se $d_{\text{old}} < 0$, $E$ é escolhido, e o próximo ponto-médio será incrementado de 1 na direção $x$. Assim, a nova função de decisão será:

$$
d_{\text{new}} = F(x_p + 2, y_p - \frac{1}{2}) = (x_p + 2)^2 + (y_p - \frac{1}{2})^2 - R^2
$$

E a diferença:

$$
\Delta E = 2x_p + 3
$$

Se $d_{\text{old}} \geq 0$, $SE$ é escolhido, e o próximo ponto-médio será incrementado de 1 na direção $x$ e decrementado de 1 na direção $y$. Portanto:

$$
d_{\text{new}} = F(x_p + 2, y_p - \frac{3}{2}) = (x_p + 2)^2 + (y_p - \frac{3}{2})^2 - R^2
$$

E a diferença:

$$
\Delta NE = 2x_p - 2y_p + 5
$$

Como $d_{\text{new}} = d_{\text{old}} + (2x_p - 2y_p + 5)$, $\Delta E = 2x_p - 2y_p + 5$.

As funções podem ser avaliadas diretamente, a cada passo, dando os valores de $x$ e $y$ do pixel escolhido na iteração anterior, tornando a avaliação eficiente, uma vez que as funções são lineares.

						
						  		

				


