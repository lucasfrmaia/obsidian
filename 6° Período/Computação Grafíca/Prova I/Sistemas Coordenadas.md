### Resolução Gráfica

Quatro parâmetros definem a resolução gráfica

- **ndh** - o número de posições endereçáveis horizontalmente
- **ndv** - o número de posições endereçáveis verticalmente.
- **width** - a largura do retângulo de visualização em mm.
- **height** - a altura do retângulo de visualização em mm.

A partir dos 4 parâmetros as seguintes medidas são
definidas:

- **resolução horizontal**: horiz_res = ndh / width
- **resolução vertical**: vert_res = ndv / height
- **tamanho do ponto horizontal**: horiz_dot_size = width / ndh
- **tamanho do ponto vertical**: vert_dot_size = height / ndv
- **total de pontos endereçáveis**: total_nr_dots = ndh * ndv
- **resolução de área**: area_res = total_nr_dots / (width * height)
- **razão de aspecto gráfica**: aspect_ratio = vert_dot_size / horiz_dot_ size
- **razão de aspecto físico**: physical_aspect_ratio = width /height

### Sistemas de Coordenadas

De forma geral são definidos três sistemas de coordenadas:
##### 1. Sistemas de coordenadas do mundo

É um conjunto de coordenadas cartesianas em um
intervalo qualquer definido pelo usuário.

* Coordenadas:  x-min <= x <= x-max
			 y-min <= y <= y-max	
##### 2. Sistemas de coordenadas do dispositivo

É um conjunto de pixels endereçáveis pelo dispositivo. Os
pixels são endereçados por dois números inteiros que dão
suas coordenadas horizontal e vertical.

**Coordenadas**:  0 <= dcx <= ndh -1
			 0 <= dcy <= ndv - 1

##### 3. Sistema de coordenadas normalizadas do dispositivo (NDC).

Este sistema é intermediário entre os dois anteriores,
definido de tal forma que todo conteúdo da janela de
visualização possua as coordenadas variando no
intervalo [0,1] X [0,1]

**Coordenadas**:  0 <= ndcx <= 1
			 0 <= ndcy <= 1
