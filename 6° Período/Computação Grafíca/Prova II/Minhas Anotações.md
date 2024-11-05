
## Exercício

**Imagem Monocromática:** é uma imagem de tons de cinza, composta de diferentes níveis de intensidade em um único canal de cor

**Passos fundamentais de um sistema de visão artificial:**

- **Aquisição:** Captura de imagem a partir de dispositivos
- **Pré-Processamento:** Realiza remoções de ruídos e outros ajustes como contrastes.
- **Segmentação:** Separação da imagem em regiões de interesse.
- **Extração de atributos:** Extração de bordas, formas e texturas
- **Classificação e Interpretação**: Classificar/Interpretar o conteúdo da imagem

**Sistema de Processamento de Imagem**
   - **Aquisição:** Captura da imagem a partir de dispositivos como câmeras digitais. **Armazenamento:** Salva a imagem em uma mídia digital.
   - **Processamento:** Aplicação de algoritmos para melhorar a qualidade, segmentar, analisar ou modificar a imagem.
   - **Comunicação:** Transferência de imagens e dados para outros sistemas ou dispositivos por redes ou cabos.
   - **Exibição:** Exibição da imagem em um monitor ou dispositivo de saída para interpretação visual.
   
 **Modelo simples de imagem digital:**
   - Uma imagem digital é representada como uma matriz de pixels, onde cada elemento possui um valor correspondente à intensidade (para imagens monocromáticas) ou valores para cada canal de cor (para imagens coloridas). Cada pixel é um ponto da imagem com uma posição e intensidade definidas.

5) **Amostragem e Quantização:**

- **Amostragem**: É o processo de discretização em coordenadas espaciais (x,y).
- **Quantização**: É o processo de discretização em amplitude.

7) **Vizinhança de um pixel:**

   - Refere-se ao conjunto de pixels ao redor de um pixel central. A vizinhança pode ser definida de várias formas, como:

     - **Vizinhança de 4:** Inclui os pixels acima, abaixo, à esquerda e à direita.
     - **Vizinhança de 8:** Inclui os pixels acima, abaixo, à esquerda, à direita e os quatro diagonais.

8) **Medida de distância entre pixels:**

   - **Distância Euclidiana:** A distância entre dois pixels $p(x_1, y_1)$ e$ q(x_2, y_2)$ é dada pela fórmula $d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$. Por exemplo, entre $p(1, 2)$ e$ q(4, 6) $, a distância Euclidiana é $sqrt{(4 - 1)^2 + (6 - 2)^2} = \sqrt{9 + 16} = 5$.

9) **Convolução e Correlação:**

   - **Convolução:** É uma operação entre uma imagem e um filtro (ou kernel) onde cada pixel é substituído pela soma ponderada de seus vizinhos, definida pelo filtro, usada em operações de suavização, detecção de bordas, etc.

   - **Correlação:** Similar à convolução, mas a aplicação do filtro ocorre sem reversão do kernel, sendo usada para detecção de padrões específicos em imagens.

![[Pasted image 20241105010040.png]]

---

## Filtros

### Como Aplicar o Filtro em uma Imagem

Para aplicar o filtro em uma imagem, usa-se a **convolução**. A convolução entre a matriz da imagem \( I \) e a máscara (kernel) \( K \) é feita pixel a pixel, deslocando o kernel sobre toda a imagem e calculando o valor de cada pixel filtrado com a fórmula:

$$
I'(x, y) = \sum_{i=-1}^{1} \sum_{j=-1}^{1} K(i, j) \cdot I(x+i, y+j)
$$

Onde:
- $I(x, y)$ é o valor do pixel original na posição $(x, y)$,
- $I'(x, y)$ é o valor do pixel após a aplicação do filtro,
- $K(i, j)$ é o valor do coeficiente da máscara na posição $(i, j)$.

### Resumo 

**-> Ou seja multiplica os valores respectivos de cada matriz, depois soma tudo**
-> **Posicionar a origem da matriz em cima do número**
**-> Nas bordas, preencher com 0**

### Média ou Passa Baixa

-> Construir uma matriz 3x3 com valores = 1, e dividir por um fator de normalização (Padrão =  9)

### Mediana

-> Consiste em substituir o pixel pela a mediana de sua vizinhança

### Filtro Passa Altas Básico

-> A matriz terá que ter valores positivos perto ao centro e negativos longe deles

### Filtros de Detecção de Bordas

- São filtros da primeira derivada

Imagem = [
  z1, z2, z3,
 z4, z5, z6,
z7, z8, z9
]

#### Filtro de Robert

Mascara Direção de X: [
   1, 0
   -1, 0
]

Mascara Direção de Y: [
     1, -1
     0, 0
]

### Filtro de Robert Cruzado

Mascara Direção de X: [
   1, 0
   -1, 0
]

Mascara Direção de Y: [
     1, -1
     0, 0
]

#### Filtro de Prewitt

Em direção a X: [
  -1, -1, -1
  0, 0, 0
  1, 1, 1
]

Em direção a Y: [
   -1, 0, 1
   -1, 0, 1
   -1, 0, 1
]

### Filtro de Sobel

Em X: [
  -1 -2 -1
  0 0 0
  1 2 1
]

Em Y: [
  -1 0 1 
  -2 0 2
  -1 0 1
]

As funções de transferência de intensidade são ferramentas essenciais no processamento de imagens, especialmente em áreas como realce de imagem, segmentação e ajuste de contraste. Elas mapeiam valores de intensidade de entrada em valores de intensidade de saída, ajustando a percepção e o destaque dos detalhes.

Aqui estão as principais funções de transferência de intensidade e suas fórmulas:

### 1. **Função de Probabilidade de Intensidade**
A função de probabilidade de intensidade (ou histograma) de uma imagem com níveis de intensidade \( L \) fornece a distribuição de frequência de cada valor de intensidade. O histograma de uma imagem é definido como:


$$p(r_k) = \frac{n_k}{n}$$

onde:
- \( p(r_k) \) é a probabilidade de um pixel ter a intensidade \( r_k \),
- \( n_k \) é o número de pixels com intensidade \( r_k \),
- \( n \) é o número total de pixels na imagem.

Essa função ajuda a identificar a distribuição de tons e é frequentemente usada para transformações de contraste e equalização de histograma.

### 2. **Transformação Linear**
A transformação linear é uma das mais simples, e estende os valores de intensidade para utilizar todo o intervalo possível de valores na imagem. O mapeamento de intensidade é dado por:


$$s = a \cdot r + b$$

onde:
- \( r \) é a intensidade de entrada,
- \( s \) é a intensidade de saída,
- \( a \) e \( b \) são constantes de ajuste (slope e intercept).

Essa transformação é útil para melhorar o contraste de imagens de baixo contraste.

### 3. **Transformação Logarítmica**
A transformação logarítmica amplia as intensidades de baixa amplitude e reduz a amplitude das intensidades mais altas. É definida por:


$$s = c \cdot \log(1 + r)$$

onde:
- \( c \) é uma constante que escala a transformação,
- \( r \) é a intensidade de entrada.

Essa transformação é particularmente útil para imagens onde detalhes nas sombras são mais importantes do que nos destaques.

### **Função de transformação de intensidade e faixa dinâmica**

![[Pasted image 20241105050507.png]]

### **Função Sigmoidal**
A função sigmoidal é uma transformação não-linear usada para melhorar o contraste em regiões específicas da imagem. Ela é dada por:

$$s = \frac{1}{1 + e^{-a(r - m)}}$$



---

## Morfologia

**Conceito básico:** consiste em extrair informações (componentes) de uma
imagem de geometria desconhecida pela transformação com uma outra imagem
completamente definida , denominada de **elemento estruturante.**

**Elemento Estruturante:** São pequenos padrões geométricos contidos na
imagem.

### Notação de Conjuntos
- **Conjunto vazio**: $\emptyset$
- **Subconjunto**: $A \subseteq B$
- **União**: $C = A \cup B$
- **Interseção**: $D = A \cap B$
- **Conjuntos disjuntos**: $A \cap B = \emptyset$
- **Especificação de conjunto**: $C = \{ w \mid w = -d, \text{ para } d \notin D \}$
- **Complemento**: $A^c = \{ w \mid w \notin A \}$
- **Diferença de conjuntos**: $A - B = \{ w \mid w \in A, w \notin B \} = A \cap B^c$

---

### Dilatação

A **dilatação** é uma operação que expande os objetos na imagem. No contexto matemático, a dilatação adiciona cada ponto do elemento estruturante BBB a cada ponto do conjunto AAA.

Ou seja p/ cada ponto de A somamos com todos os pontos de B, e ao final unimos em um conjunto.

### Erosão

-> Faz uma dilatação de cada elemento de A com a mascara B
-> os conjuntos resultante que estiverem contido em A, os valores de A será adicionado ao conjunto de A erodido B 

### Resumo das Operações com Exemplos

| Operador                  | Definição Formal                           | Exemplo                           | Efeito                             |
| ------------------------- | ------------------------------------------ | --------------------------------- | ---------------------------------- |
| **Dilatação**             | **$A \oplus B$**                           | Expande o objeto de \( A \)       | Preenche buracos, expande bordas   |
| **Erosão**                | **$A \ominus B$**                          | Reduz o objeto de \( A \)         | Remove bordas e ruídos             |
| **Abertura**              | **$A \circ B = (A \ominus B) \oplus B$**   | Remove ruídos, preserva estrutura | Elimina pixels isolados            |
| **Fechamento**            | **$A \bullet B = (A \oplus B) \ominus B$** | Preenche buracos internos         | Conecta regiões e preenche lacunas |
| **Gradiente Morfológico** | **(A ⊕ B) – (A θ B)**                      |                                   |                                    |
| **Contorno Externo**      | **(A ⊕ E) - A**                            |                                   |                                    |
| **Contorno Interno**      | **(A) = {A - (A θ E)}**                    |                                   |                                    |
## Morfologia em Nível de Cinza

-  **Dilatação:**  Pega cada pixel que a mascara pega, soma os elementos e pega o máximo
-  **Erosão:** Pega cada pixel que a mascara pega, soma os elementos e pega o miniimo
- **Abertura e Fechamento**
	- Abertura: Erosão depois dilatação
	- Fechamento: Dilatação depois erosão
- **Gradiente** Dilatação menos erosão
- **Top-Hat e Bottom-Hat** 
	- Top hat: Imagem - Abertura com W
	- Bottom hat: Fechamento - Imagem

Arredondar se passar dos limites 0 ou 255, arredonda p 0 ou 255

---
