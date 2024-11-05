  

1) **Passos fundamentais de um sistema de visão artificial:**

   - **Aquisição de Imagem:** Captura da imagem através de dispositivos como câmeras e sensores.
   - **Pré-Processamento:** Realização de operações como remoção de ruído e ajuste de contraste para melhorar a qualidade da imagem.
   - **Segmentação:** Separação da imagem em regiões de interesse, facilitando a análise de objetos específicos.
   - **Extração de Características:** Identificação de características importantes, como bordas, formas e texturas.
   - **Classificação e Interpretação:** Uso de algoritmos para classificar objetos e interpretar o conteúdo da imagem.
   - **Decisão:** Com base nos resultados da classificação, é feita uma decisão sobre a ação a ser tomada.

2) **Imagem Monocromática:**

   - Uma imagem monocromática é uma imagem em tons de cinza, composta por diferentes níveis de intensidade de um único canal de cor (geralmente em escalas de cinza). Cada pixel apresenta uma intensidade variando do preto ao branco.

3) **Elementos do processamento de imagens digitais:**

   - **Aquisição:** Captura da imagem a partir de dispositivos como câmeras digitais ou scanners.
   - **Armazenamento:** Salva a imagem em uma mídia digital (disco rígido, memória RAM), onde poderá ser recuperada e manipulada.
   - **Processamento:** Aplicação de algoritmos para melhorar a qualidade, segmentar, analisar ou modificar a imagem.
   - **Comunicação:** Transferência de imagens e dados para outros sistemas ou dispositivos por redes ou cabos.
   - **Exibição:** Exibição da imagem em um monitor ou dispositivo de saída para interpretação visual.

4) **Modelo simples de imagem digital:**
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