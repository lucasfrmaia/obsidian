
## **1° Caso**

![[Pasted image 20240430000945.png]]
![[Pasted image 20240430001124.png]]

---

Peço desculpas pela formatação inadequada anterior. Vou reformatar a resposta para que fique mais legível:

Dado:

- Tamanho da amostra ((n)): 85 mancais.
- Número de mancais com acabamento superficial mais rugoso ((x)): 10.

Primeiro, vamos calcular a proporção amostral: $\hat{p} = \frac{x}{n} ]$

$hat{p} = \frac{10}{85}$
\hat{p} \approx 0.1176 

Agora, vamos encontrar o erro padrão da proporção: [ SE(\hat{p}) = \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}} ]

$$SE(\hat{p}) = \sqrt{\frac{0.1176 \cdot (1 - 0.1176)}{85}} $$

$SE(\hat{p}) \approx 0.0335$

Para um intervalo de confiança de 95%, usaremos o valor crítico (z) correspondente. O valor crítico (z) para um intervalo de confiança de 95% é aproximadamente 1.96.

Agora, podemos calcular o intervalo de confiança: [ \text{Limite inferior} = \hat{p} - z \cdot SE(\hat{p}) ] [ \text{Limite superior} = \hat{p} + z \cdot SE(\hat{p}) ]

Substituindo os valores: $$\text{Limite inferior} \approx 0.0516 ] [ \text{Limite superior} \approx 0.1836 $$

Portanto, o intervalo de confiança de 95% para a proporção é aproximadamente **5.16% a 18.36%**.

Isso significa que estamos 95% confiantes de que a proporção de mancais com acabamento superficial mais rugoso está entre 5.16% e 18.36%

---

Análise da Nova Espécie de Trigo com Base no Intervalo de Confiança:

Dado:

Média amostral observada (x̄) = 28 ton/ha
Variância amostral observada = 12 (ton/ha)²
Tamanho da amostra (n) = 16
Média da produtividade da espécie tradicional (μ) = 25 ton/ha
Erro Padrão da Média (SEM):

O erro padrão da média é dado por: SEM = √(variância amostral / n)
Calculando: SEM = √(12 / 16) = 1.732 ton/ha
Intervalo de Confiança:

Para um nível de confiança de 95%, o valor crítico (Z-score) é aproximadamente 1.96.
Margem de erro = Z-score * SEM = 1.96 * 1.732 ≈ 3.40
Intervalo de confiança = (x̄ - Margem de erro, x̄ + Margem de erro)

Calculando:
Limite inferior = 28 - 3.40 ≈ 24.60
Limite superior = 28 + 3.40 ≈ 31.40
Conclusão:

Com 95% de confiança, espera-se que a média real de produtividade da nova espécie de trigo esteja dentro do intervalo de (24.60, 31.40) ton/ha.
Como o intervalo inclui a média da espécie tradicional (25 ton/ha), não há evidência significativa de que a nova espécie seja mais produtiva.

Portanto, com base no intervalo de confiança, não podemos afirmar com certeza que a nova espécie de trigo é mais produtiva do que a espécie tradicional