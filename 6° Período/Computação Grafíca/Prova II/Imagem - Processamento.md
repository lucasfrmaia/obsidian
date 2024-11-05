
![[Pasted image 20241027205546.png]]

**Aquisição de imagem:**
Sensor –Converterá a informação ótica em sinais elétricos

**Digitalizador –** Transformará a imagem analógica em imagem digital.

**Pré-processamento**
*  A imagem resultante pode apresentar diversas imperfeições:
	- Presença de pixels ruidosos
	- Contraste ou brilho inadequado
	- Caracteres interrompidos ou indevidamente conectados
	- As operações envolvidas nesta etapa são ditas de baixo nível.
	- Trabalham diretamente com os valores de intensidades dos pixels

--- 

**Fenômeno**: Variação da pressão do ar por efeito da propagação de ondas sonoras
-> 
**Microfone**: mede os valores do fenômeno e transforma em valores de tensão elétrica
->
**Tensão elétrica:** variável física dependente do tempo que varia de forma análoga à variação do ar

Processo de digitalização

PCM - Modulação de Código por Pulsos

Processa em duas fases

Amostragem: retenção de um conjunto finito de valores
ou amplitudes assumido pelo sinal analógico.

Quantização: Discretização dos valores ou amplitude
dos sinais amostrados.

--- 

Aqui está a organização do conteúdo em tópicos para o formato Obsidian:

---

# Imagens Digitais

## Definição

- Uma **imagem monocromática** é uma função de intensidade luminosa: 
  - $$f(x, y) = i(x, y) \cdot r(x, y) $$
  - Onde:
    - \( i(x, y) \): quantidade de luz que incide sobre o objeto
    - \( r(x, y) \): quantidade de luz refletida do objeto no ponto espacial \((x, y)\)
  
---

## Exemplos de Valores para Iluminância e Refletância

### Iluminância
| Valor (lux) | Condição de Iluminação           |
|-------------|----------------------------------|
| 900         | Dia ensolarado                   |
| 100         | Dia nublado                      |
| 10          | Iluminação média de escritório   |
| 0,001       | Noite clara de lua cheia         |

### Refletância
| Valor | Material                  |
|-------|----------------------------|
| 0,93  | Neve                       |
| 0,80  | Parede branco-fosca        |
| 0,65  | Aço inoxidável             |
| 0,01  | Veludo preto               |

---
## Observações

- A intensidade luminosa de uma imagem monocromática é denominada **nível de cinza** (L) no ponto espacial \((x, y)\).
- O intervalo \([L_{min}, L_{max}]\) é denominado **escala de cinza** da imagem.
- Para ser adequada ao processamento, a imagem \( f(x, y) \) precisa ser digitalizada em:
  - **Espaço** (amostragem)
  - **Amplitude** (quantização)

---

## Digitalização de Imagens

### Amostragem
- Processo de **discretização** em coordenadas espaciais \((x, y)\).

### Quantização
- Processo de **discretização em amplitude**.

### Parâmetros para Digitalização
- No processo de digitalização, definem-se:
  - Valores de \( M \) e \( N \) (dimensões da imagem)
  - **Nível de cinza discreto** permitido para cada pixel.
- Em processamento de imagens, assume-se que esses valores são potências de 2, com \( n \), \( k \) e \( m \) inteiros.

#### Número de níveis de cinza \( k \)
- Representado pelo **número de bits por pixel**.

---

## 1. Filtro da Média (Filtro Passa-Baixas)

**Descrição**  
O filtro da média é um filtro passa-baixas que suaviza a imagem, reduzindo ruídos. Ele utiliza uma máscara de convolução 3x3, onde todos os coeficientes são iguais a 1, e o resultado é dividido por um fator de normalização (neste caso, 9). Esse processo substitui cada pixel pela média dos valores dos pixels na sua vizinhança.

**Máscara de Filtro da Média 3x3**  
```
1/9 * 
| 1  1  1 |
| 1  1  1 |
| 1  1  1 |
```

**Exemplo**  
Imagine uma imagem com ruído (pequenos pontos esparsos com variação de cor ou luminosidade). Aplicar o filtro da média suavizará esses pontos, tornando a imagem mais homogênea e com menos variação abrupta de tonalidade.

---

## 2. Filtro da Mediana (Filtro Não Linear)

**Descrição**  
O filtro da mediana é um filtro não linear, utilizado para reduzir ruídos impulsivos (como o ruído "sal e pimenta") na imagem. Ele substitui o valor do pixel central da janela pela mediana dos pixels em sua vizinhança, em vez de utilizar a média. A mediana é uma estatística de ordem, sendo mais resistente a valores extremos.

**Exemplo**  
Se tivermos uma imagem com ruído de "sal e pimenta" (pixels brancos e pretos aleatórios), aplicar o filtro da mediana substituirá cada pixel central por um valor que representa a mediana dos pixels ao seu redor, reduzindo a presença de pontos brancos e pretos isolados e mantendo as bordas das figuras mais nítidas.

---

## 3. Filtro de Realce de Imagem: Detecção de Bordas (Filtro Passa-Altas)

**Descrição**  
Filtros de detecção de bordas são utilizados para destacar detalhes finos em uma imagem, como linhas e contornos. Esse filtro utiliza uma máscara onde os coeficientes próximos do centro são positivos, e os coeficientes distantes do centro são negativos. A soma algébrica dos coeficientes da máscara é igual a zero, o que significa que regiões homogêneas tendem a resultar em valores próximos de zero, enquanto regiões com variações acentuadas (bordas) são destacadas.

**Máscara de Exemplo (Filtro de Sobel)**  
```
| -1  0  +1 |
| -2  0  +2 |
| -1  0  +1 |
```

**Exemplo**  
Em uma imagem de uma folha de papel com texto, aplicar um filtro passa-altas realçará as bordas das letras, tornando o texto mais definido e separando as letras do fundo. O filtro passa-altas é essencial para sistemas de visão computacional que precisam detectar contornos de objetos.

---

Aqui está a explicação das operações entre duas imagens na área de computação gráfica, com exemplos reais e formatado para o padrão do Obsidian Notes.

---

# Operações Entre Duas Imagens em Computação Gráfica

Na computação gráfica, operações aritméticas entre imagens podem ser realizadas para combinar, ajustar ou extrair informações visuais. Essas operações são aplicadas **pixel a pixel**, usando os valores de intensidade de cada imagem nas mesmas coordenadas.

---

## 1. Soma de Imagens

**Descrição**  
A operação de soma entre duas imagens consiste em adicionar os valores dos pixels correspondentes em cada imagem. Essa operação é útil para combinar imagens ou para aumentar a intensidade de regiões específicas. A soma pixel a pixel entre duas imagens $A$ e $B$ com valores de pixels $A(x, y)$ e $B(x, y)$ é dada por:

$$
C(x, y) = A(x, y) + B(x, y)
$$

**Exemplo**  
Imagine duas imagens, uma com uma paisagem diurna (Imagem A) e outra com uma paisagem noturna (Imagem B). Somando os pixels das duas, você pode obter uma imagem intermediária, com elementos visíveis de ambas as cenas.

Se em uma posição o pixel da Imagem A tem valor 120 e o da Imagem B tem valor 100, o resultado será:

$$
C(x, y) = 120 + 100 = 220
$$

**Observação**  
Se o valor ultrapassar o máximo permitido (por exemplo, 255 em uma imagem de 8 bits), o valor é limitado a 255.

---

## 2. Subtração de Imagens

**Descrição**  
A operação de subtração entre duas imagens é utilizada para destacar diferenças entre elas. A subtração é realizada pixel a pixel, subtraindo o valor do pixel da imagem B do valor do pixel correspondente na imagem A:

$$
C(x, y) = A(x, y) - B(x, y)
$$

**Exemplo**  
Em sistemas de vigilância, se você tiver uma imagem de fundo (Imagem A) e uma imagem com uma pessoa na cena (Imagem B), subtrair as duas destacará apenas a pessoa. 

Se um pixel da Imagem A tiver valor 200 e o pixel correspondente da Imagem B tiver valor 180, o resultado será:

$$
C(x, y) = 200 - 180 = 20
$$

**Observação**  
Se o valor da subtração for negativo, ele é geralmente limitado a zero (em imagens de 8 bits).

---

## 3. Multiplicação de Imagens

**Descrição**  
A operação de multiplicação entre duas imagens permite misturar informações e é frequentemente usada para aplicar máscaras ou modificar o contraste de uma imagem. A multiplicação pixel a pixel é realizada como:

$$
C(x, y) = A(x, y) \times B(x, y)
$$

**Exemplo**  
Imagine que a Imagem A seja uma fotografia e a Imagem B seja uma máscara binária (com valores 0 ou 1) que delimita uma área de interesse. Multiplicar essas imagens faz com que apenas a área marcada pela máscara permaneça visível na imagem resultante.

Se em uma posição o pixel da Imagem A tem valor 150 e o da Imagem B (máscara) tem valor 1, o resultado será:

$$
C(x, y) = 150 \times 1 = 150
$$

Para uma região fora da área de interesse, onde a máscara é 0:

$$
C(x, y) = 150 \times 0 = 0
$$

---

## 4. Divisão de Imagens

**Descrição**  
A operação de divisão entre imagens pode ser usada para normalizar ou destacar detalhes onde uma imagem serve como um divisor, atuando como uma forma de ajuste de intensidade. A divisão pixel a pixel é dada por:

$$
C(x, y) = \frac{A(x, y)}{B(x, y) + \epsilon}
$$

**Observação**  
Para evitar divisões por zero, adiciona-se um valor muito pequeno ($\epsilon$) ao denominador.

**Exemplo**  
Em processamento médico, uma imagem com contraste pode ser dividida por uma imagem de referência para ajustar o brilho em regiões específicas. 

Se em uma posição o pixel da Imagem A tiver valor 180 e o da Imagem B tiver valor 2, o resultado será:

$$
C(x, y) = \frac{180}{2} = 90
$$

---

