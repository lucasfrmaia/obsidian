

## Operadores Morfológicos

### Dilatação
- A dilatação expande uma imagem.
- Sendo $A$ e $B$ conjuntos de $\mathbb{Z}^2$ e $\emptyset$ o conjunto vazio, a dilatação de $A$ por $B$, denotada por $A \oplus B$, é definida como:
  - $A \oplus B = \{ z \mid (\hat{B})_x \cap A \neq \emptyset \}$
  - $A \oplus B = \bigcup_{b \in B} (A + b)$ (adição de Minkowski)

- O processo de dilatação envolve:
  - A obtenção da reflexão de $B$ em torno de sua origem.
  - A translação dessa reflexão por $x$.

- Em termos matemáticos:
  - $A \oplus B = \{ c \mid c = a + b, a \in A, b \in B \}$

### Conceitos Fundamentais
- **Elemento Estruturante**: 
  - Padrões geométricos pequenos contidos na imagem que definem a transformação morfológica.

- **Imagens Binárias**:
  - Os conjuntos em questão são membros do espaço bidimensional de números inteiros, onde cada elemento é um vetor bidimensional com coordenadas $(x, y)$ dos pixels pretos.

### Notação de Conjuntos
- **Conjunto vazio**: $\emptyset$
- **Subconjunto**: $A \subseteq B$
- **União**: $C = A \cup B$
- **Interseção**: $D = A \cap B$
- **Conjuntos disjuntos**: $A \cap B = \emptyset$
- **Especificação de conjunto**: $C = \{ w \mid w = -d, \text{ para } d \notin D \}$
- **Complemento**: $A^c = \{ w \mid w \notin A \}$
- **Diferença de conjuntos**: $A - B = \{ w \mid w \in A, w \notin B \} = A \cap B^c$

### Operações com Conjuntos
- **Reflexão de $B$**: 
  - $\hat{B} = \{ w \mid w = -b, b \in B \}$

- **Translação de $A$ por $z = (z_1, z_2)$**: 
  - $(A)_z = \{ c \mid c = a + z, a \in A \}$

---
