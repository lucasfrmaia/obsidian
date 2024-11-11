
## Características Desejáveis para Algoritmos de Rasterização da Reta

- **linearidade** - Os pixels traçados devem dar a aparência de
que estão sobre uma reta.

- **Espessura (densidade) uniforme** - A densidade da
reta é dada pelo número de pixels traçados dividido pelo
comprimento da reta. Para manter a densidade constante, os
pixels devem ser igualmente espaçados. A imagem do
segmento de reta não deve variar de intensidade ou
espessura ao longo de sua extensão.

- **precisão** - os segmentos devem iniciar e terminar
nos pontos especificados. Caso isso não ocorra,
pequenos gaps podem surgir entre o final de um
segmento e o início de outro.

- **Intensidade independente da inclinação** - para segmentos de retas de diferentes inclinações.

-  **continuidade** - a imagem não apresenta interrupções indesejáveis.

**rapidez** no traçado dos segmentos

## DDA 

O DDA escolhe entre x e y qual variável será incrementada uniformemente, e a outra será calculada com base nisso. Para determinar qual delas deve ser incrementada, compararemos a diferença Δx\e Δy:
###### Decisão de Incremento

1. Se Δx > Δy Então => y k +1 = yk + m (Δx = 1)
2. Se Δy > Δx Então => x k + 1 = xk + 1/m (Δy = 1)

##### Procedimento do Algoritmo

- Inicializamos com as coordenadas iniciais $(x_1, y_1)$ e $(x_2, y_2)$.
- Calculamos as diferenças $\Delta x = x_2 - x_1$ e $\Delta y = y_2 - y_1$.
- Determinamos o número de passos necessários para desenhar a reta. Isso será o maior valor entre $|\Delta x|$ e $|\Delta y|$:

$$
\text{steps} = \max(|\Delta x|, |\Delta y|)
$$

- A partir disso, calculamos os incrementos por passo para $x$ e $y$:

$$
x_{\text{inc}} = \frac{\Delta x}{\text{steps}}, \quad y_{\text{inc}} = \frac{\Delta y}{\text{steps}}
$$

- Começamos a partir de $x = x_1$ e $y = y_1$, e em cada passo do algoritmo, incrementamos $x$ e $y$ pelos valores calculados $x_{\text{inc}}$ e $y_{\text{inc}}$, respectivamente. Após cada incremento, as coordenadas são arredondadas para o pixel mais próximo na tela.


```c
void DDA(int X0, int Y0, int X1, int Y1) {
	// calculate dx & dy
	int dx = X1 - X0;
	int dy = Y1 - Y0;
	
	// calculate steps required for generating pixel
	int steps = abs(dx) > abs(dy) ? abs(dx) : abs(dy);
	
	// calculate increment in x & y for each steps
	float Xinc = dx / (float) steps;
	float Yinc = dy / (float) steps;
	
	// Put pixel for each step
	float X = X0;
	float Y = Y0;

	while (X < X1) {
		putpixel(round(X), round(Y), RED); // put pixel at (X,Y)
		X += Xinc; // increment in x at each step
		Y += Yinc; // increment in y at each step
	}

}
```

## Método do Ponto Médio


### Estudo do valor da Função


Equação Implícita da Reta: F(x , y) = ax + by + c = 0
Equação da Reta: y = $\frac{dx}{dy}$ + B

Ao Multiplicar ambos os lados por dx, organizar a equação e na equação implícita da reta considerar: 

- $a = dy$
- $b = -dx$
- $c = dx \cdot B$

A equação da reta é apresentada na forma implícita:

$$
F(x, y) = dy \cdot x - dx \cdot y + dx \cdot B = 0
$$
#### Verificação dos pontos:
- $F(x, y) = 0$: o ponto está **sobre a linha**.
- $F(x, y) > 0$: o ponto está **abaixo da linha**.
- $F(x, y) < 0$: o ponto está **acima da linha**.

---

### Determinando a variável de decisão

 O ponto médio do segmento de reta entre P1 e P3 => P2 = ( (X1+X3)/2 , (Y1+Y3)/2 )

---

Para o teste do ponto-médio, calculamos a função implícita no ponto médio:

$$
F(M) = F(x_p + 1, y_p + \frac{1}{2})
$$

A decisão é tomada com base no valor da função no ponto $F(x_p + 1, y_p + \frac{1}{2})$.

Definimos a **variável de decisão**:

$$
d = a(x_p + 1) + b(y_p + \frac{1}{2}) + c
$$
Com base nisso:
- Se $d > 0$, escolhemos o pixel **NE**.
- Se $d < 0$, escolhemos o pixel **E**.
- Se $d = 0$, podemos escolher qualquer um dos dois.

### Incremento no ponto M
 
- Se **E** for escolhido, $M$ é incrementado de 1 na direção $x$:

$$
d_{\text{new}} = F(x_p + 2, y_p + \frac{1}{2}) = a(x_p + 2) + b(y_p + \frac{1}{2}) + c
$$

$$
d_{\text{old}} = a(x_p + 1) + b(y_p + \frac{1}{2}) + c
$$

- Subtraindo $d_{\text{old}}$ de $d_{\text{new}}$ para obter a diferença incremental, tem-se:

$$
d_{\text{new}} = d_{\text{old}} + a
$$

---

### Determinando a Forma Incremental

- Se **NE** for escolhido, $M$ é incrementado de 1 em ambas as direções $x$ e $y$:

$$
d_{\text{new}} = F(x_p + 2, y_p + 1 + \frac{1}{2}) = a(x_p + 2) + b(y_p + \frac{3}{2}) + c
$$

$$
d_{\text{old}} = a(x_p + 1) + b(y_p + \frac{1}{2}) + c
$$

- Subtraindo $d_{\text{old}}$ de $d_{\text{new}}$, tem-se:

$$
d_{\text{new}} = d_{\text{old}} + a + b
$$

---

### Determinando o Ponto Inicial

- Como o primeiro pixel corresponde ao ponto $(x_0, y_0)$, pode-se calcular diretamente o valor inicial de $d$ para escolher entre **E** e **NE**. O primeiro ponto-médio está em $(x_0 + 1, y_0 + \frac{1}{2})$. Temos:

$$
d_{\text{start}} = F(x_0 + 1, y_0 + \frac{1}{2}) = a(x_0 + 1) + b(y_0 + \frac{1}{2}) + c
$$

$$
d_{\text{start}} = a \cdot x_0 + b \cdot y_0 + \frac{b}{2} + a + c
$$

Como $F(x_0, y_0)$ está sobre a reta, temos que $F(x_0, y_0) = 0$, o que resulta em:

$$
d_{\text{start}} = a + \frac{b}{2}
$$




