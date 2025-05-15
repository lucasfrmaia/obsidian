
- Recebe uma sequencia de tokens do lexico e determina se a string pode ser gerada atraves da gramatica da linguagem forte

- Se o programa for bem formado, constroi uma arvore de derivação

- Deve se recuperar de erros comuns


### Papel do Sintático

- Coletar informações sobre os tokens na tabela de símbolo
- Verificação de tipos
- Geração do código intermediário


### Sintaxe de uma Linguagem


Define construções estruturalmente validas de uma linguagem

- Pode não passar em checagem de tipos por exemplo

ERs são boas para definir a estrutura lexica, mas não tão boas para a estrutura sintatica.

Exemplos:

digito: [0-9]+
sum digito "+" digito

Implementação: o analisador substituiu as abreviações antes da tradução em um automato

As abreviações não acresetam a ERs o poder de recursão

####  Solução para o problema acima

- Usar gramatica livres de contextos realizado por automato finitos com pilha
- Reconhecimento realziados por algorimos recursivos descedentes.

#### Gramaticas

Descrevem a sintaxe de construções de uma linguagem de programação como expressões e comandos

Exemplo: 

**stmt** -> if (expr) stmt else stmt
**stmt** representa comandos
**expr** representa expressões


Formalmente, uma gramática livre de contexto possui quatro componentes:
1. **Elementos terminais**: símbolos do alfabeto da linguagem. Ex.: if, (, ), else
2. **Elemento não-terminais**: variáveis que representam sequências de terminais (e/ou não-terminais).
3. Designação de um símbolo inicial da gramática;
4. Um conjunto de produções, que especificam a forma como os terminais e os não-terminais podem ser combinados para forma cadeias. Cada produção consiste em:
5. Um **não-terminal** (cabeça ou lado esquerdo da produção) 
6. Um símbolo -> ou ::=;
7. Um corpo ou lado direito da produção, que consiste em zero ou mais terminais e não-terminais



