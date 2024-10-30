
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
  - \( f(x, y) = i(x, y) \cdot r(x, y) \)
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
