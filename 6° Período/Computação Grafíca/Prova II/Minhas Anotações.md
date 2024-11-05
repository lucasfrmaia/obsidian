
## Exercício

**Imagem Monocromática:** é uma imagem de tons de cinza, composta de diferentes níveis de intensidade em um único canal de cor

**Passos fundamentais de um sistema de visão artificial:**

- **Aquisição:** Captura de imagem a partir de dispositivos
- **Pré-Processamento:** Realiza remoções de ruídos e outros ajustes como contrastes.
- **Segmentação:** Separação da imagem em regiões de interesse.
- **Extração de Características:** Extração de bordas, formas e texturas
- **Classificação e Interpretação**: Classificar/Interpretar o conteúdo da imagem
- **Decisão:** Com base na classificação, uma decisão é tomada

**Sistema de Processamento de Imagem**

   - **Aquisição:** Captura da imagem a partir de dispositivos como câmeras digitais. **Armazenamento:** Salva a imagem em uma mídia digital.
   - **Processamento:** Aplicação de algoritmos para melhorar a qualidade, segmentar, analisar ou modificar a imagem.
   - **Comunicação:** Transferência de imagens e dados para outros sistemas ou dispositivos por redes ou cabos.
   - **Exibição:** Exibição da imagem em um monitor ou dispositivo de saída para interpretação visual.
   
 **Modelo simples de imagem digital:**
   - Uma imagem digital é representada como uma matriz de pixels, onde cada elemento possui um valor correspondente à intensidade (para imagens monocromáticas) ou valores para cada canal de cor (para imagens coloridas). Cada pixel é um ponto da imagem com uma posição e intensidade definidas.

5) **Amostragem e Quantização:**

   - **Amostragem:** Processo de converter uma imagem contínua em uma imagem discreta ao selecionar pontos específicos (pixels) para representá-la.

   - **Quantização:** Processo de reduzir a precisão dos valores de intensidade para um número finito de níveis, associando cada intensidade de pixel a um valor discreto.

   - **Exemplo:** Em uma foto, a amostragem define a quantidade de pixels, enquanto a quantização determina os níveis de cinza ou cor que cada pixel pode assumir.

6) **Vizinhança de um pixel:**

   - Refere-se ao conjunto de pixels ao redor de um pixel central. A vizinhança pode ser definida de várias formas, como:

     - **Vizinhança de 4:** Inclui os pixels acima, abaixo, à esquerda e à direita.
     - **Vizinhança de 8:** Inclui os pixels acima, abaixo, à esquerda, à direita e os quatro diagonais.

7) **Medida de distância entre pixels:**

   - **Distância Euclidiana:** A distância entre dois pixels $p(x_1, y_1)$ e$ q(x_2, y_2)$ é dada pela fórmula $d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$. Por exemplo, entre $p(1, 2)$ e$ q(4, 6) $, a distância Euclidiana é $sqrt{(4 - 1)^2 + (6 - 2)^2} = \sqrt{9 + 16} = 5$.

8) **Convolução e Correlação:**

   - **Convolução:** É uma operação entre uma imagem e um filtro (ou kernel) onde cada pixel é substituído pela soma ponderada de seus vizinhos, definida pelo filtro, usada em operações de suavização, detecção de bordas, etc.

   - **Correlação:** Similar à convolução, mas a aplicação do filtro ocorre sem reversão do kernel, sendo usada para detecção de padrões específicos em imagens.

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
