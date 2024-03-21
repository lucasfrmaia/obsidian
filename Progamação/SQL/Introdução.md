
*  Para criar um database que ainda não existe

```sql
CREATE DATABASE IF NOT EXISTS nome_do_banco_de_dados;
```

---
### **Criando Tabelas**

**Exemplo:**

* O campo do tipo _numeric_ pode ser usado para representar quanto dinheiro o aluno tem, então **`dinhero NUMERIC(10,2),`**, onde o 10 representa o número de caracteres, que são **1234567890**, e 2 a quantidade de casas decimais, ou seja, **12345678,90**. E vamos utilizar o tipo _real_ para registrarmos a **altura** do aluno, com **`altura REAL`**, que pode ter entre 1 e 6 casas decimais.

```sql
CREATE TABLE aluno(
    id SERIAL,
	nome VARCHAR(255),
	cpf CHAR(11),
	observacao TEXT,
	idade INTEGER,
	dinheiro NUMERIC(10,2),
	altura REAL,
	ativo BOOLEAN,
	data_nascimento DATE,
	matriculado_em TIMESTAMP
);
```

---
### Tipos de Dados

**VARCHAR(n)**: Usado para armazenar strings de comprimento variável, com um limite máximo de caracteres definido por `n`. É útil quando se sabe aproximadamente o tamanho máximo do dado, como um nome de pessoa.
```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(255)
);
```

**CHAR(n)**: Armazena strings de comprimento fixo, com exatamente `n` caracteres. Útil para dados que sempre terão um comprimento específico, como um CPF.

```sql
CREATE TABLE users (
	id INT PRIMARY KEY,
	cpf CHAR(11)
);
```

**TEXT**: Usado para armazenar grandes quantidades de texto, sem um limite específico de caracteres. É apropriado quando o tamanho do texto pode variar muito, como em um campo de descrição.

```sql
CREATE TABLE articles (
    id INT PRIMARY KEY,
    title VARCHAR(255),
    content TEXT
);

```

* Outros tipos de dados

1. **INTEGER**: Armazena números inteiros, positivos ou negativos, com tamanho de 4 bytes. O intervalo de valores é de -2.147.483.648 a 2.147.483.647.
2. **REAL**: Armazena números de ponto flutuante de precisão simples (32 bits), usados para representar valores aproximados.
3. **SERIAL**: Um tipo especial de dado para criar uma coluna que se auto incrementa, geralmente usada para chaves primárias únicas.
4. **NUMERIC**: Armazena números decimais com precisão arbitrária, definida pelo usuário. É útil quando é necessário um alto grau de precisão
5. **BOOLEAN**: Armazena valores booleanos, que podem ser verdadeiro (`TRUE`), falso (`FALSE`) ou nulo (`NULL`).
6. **DATE**: Armazena uma data no formato "AAAA-MM-DD".
7. **TIME**: Armazena um horário no formato "HH:MM:SS".
8. **TIMESTAMP**: Armazena uma data e hora no formato "AAAA-MM-DD HH:MM:SS".

### **Inserção de Dados**

* Schema
```sql
INSERT INTO table [ ( column [, ...] ) ]
    { DEFAULT VALUES | VALUES ( { expression | DEFAULT } [, ...] ) | query }
```

* Exemplo de inserção na table aluno

```sql

INSERT INTO aluno (
	nome,
	cpf, 
	observacao,
	idade, 
	dinheiro, 
	altura, 
	ativo,
	data_nascimento,
	matriculado_em
)

VALUES (
	'João da Silva',
	'12345678901', 
	'Aluno dedicado e esforçado',
	20, 
	1500.50,
	1.75, 
	TRUE,
	'2004-03-15',
	'2024-03-20 10:00:00'
);
```

* Note que as strings devem está em aspas simples

--- 
---

### **Updates de Dados**

```sql
UPDATE aluno
    SET nome = 'Nico',
    cpf = '10987654321',
    observacao = 'Teste',
    idade = 38,
    dinheiro = 15.23,
    altura = 1.90,
    ativo = FALSE,
    data_nascimento = '1980-01-15',
    hora_aula = '13:00:00',
    matriculado_em = '2020-01-02 15:00:00'
WHERE id = 1;    
```

--- 
### Delete de Dados

```sql
DELETE FROM films WHERE kind <> 'Musical';
DELETE FROM films WHERE producer_id IN (SELECT id FROM producers WHERE name = 'foo');
```
1. `DELETE FROM films WHERE kind <> 'Musical';`
    Esta query DELETE remove todas as linhas da tabela `films` onde o valor da coluna `kind` não é igual a `'Musical'`. O operador `<>` é usado para verificar a desigualdade. Ou seja, esta query vai excluir todos os filmes que não são do tipo 'Musical'.
    
2. `DELETE FROM films WHERE producer_id IN (SELECT id FROM producers WHERE name = 'foo');`
    Nesta query DELETE, o `WHERE` contém uma subquery. Ela primeiro seleciona o `id` dos produtores com o nome 'foo' da tabela `producers` e, em seguida, utiliza esses `id`'s para excluir todas as linhas da tabela `films` onde `producer_id` corresponde a um dos `id`'s selecionados pela subquery. Em resumo, esta query exclui todos os filmes cujo produtor tem o nome 'foo'.

---

### **Select de Dados**

* Para retornar apenas os dados da coluna "nome", executamos o comando `SELECT nome FROM aluno;`, e assim veremos só os registros de nome. Se quisermos os resultados de mais campos, como "nome", "idade" e "matriculado_em", informamos esses campos, separados por vírgula, após o `SELECT`.
```sql
SELECT nome,
       idade,
       matriculado_em
    FROM aluno;
```

--- 

### **Filtros de Querys**

```sql
SELECT *
    FROM aluno
 WHERE nome = 'Diogo';
```

* Ao executar esse código, notamos que `WHERE nome = 'Diogo;'` retorna apenas os dados do "Diogo". Se pesquisássemos, por exemplo, `WHERE nome = 'Diogo Oliveira'` , não acharíamos nenhum resultado, pois o único "Diogo" na nossa tabela não tem sobrenome.

```sql
SELECT * 
    FROM aluno
 WHERE nome LIKE 'Di_go';
```

* Nesse caso, o filtro ignora o terceiro caractere entre o "**Di**" e o "**go**", ou seja, a tabela retornará tanto o "Diego", quanto o "Diogo". Em resumo, o **`_`** , que pode estar no começo, meio ou final de uma palavra, ocupa o espaço específico de um caractere, que será ignorado na busca.

```sql
SELECT * 
    FROM aluno
 WHERE nome LIKE 'D%';
```

* Novamente aparecem os resultados do "Diogo" e do "Diego", que são os nomes da nossa tabela que começam dom D.

```sql
SELECT * 
    FROM aluno
 WHERE nome LIKE '% %';
```

* Outro exemplo, para filtrar os nomes compostos, utilizamos o comando `WHERE nome LIKE % %';` . Assim aparecerão os dados do "Vinícius Dias". Outra possibilidade é recuperar todos os nomes que tenham espaço:

```sql
SELECT * 
    FROM aluno
 WHERE nome LIKE '%i%a%';
```

* Esse comando apresenta os dados que tenham "**i**", em alguma parte do texto, seguido por "**a**", em outra parte do texto. No nosso banco de dados retorna os nomes "Vinícius Dias", devido ao "**i**" em "V**i**nícius" e o "**a**" em "Di**a**s", e o "Nico Steppat", devido ao "**i**" em "N**i**co" e o "**a**" em "Stepp**a**t".

---
### **Filtros compostos e de outros tipos**

```sql
SELECT *
    FROM aluno
 WHERE cpf IS NULL;
```

* Executando esse código, o programa irá retornar todos os registros cujo CPF é nulo
	
* O `IS NOT` é o comando oposto, ou seja, mostra todos os registros cujo campo selecionado está preenchido. Sendo assim, o comando `WHERE cpf IS NOT NULL` retorna os dados de alunos onde o cpf não é nulo.

```sql
SELECT *
    FROM aluno
 WHERE idade BETWEEN 10 AND 20;
```

*  Pegando todos os alunos entre 10 e 20 anos

* Todos esses filtros que aprendemos agora funcionam para os campos **INTERGER**, **REAL**, **SERIAL**, **NUMERIC**, **DATE**, **TIME** e **TIMESTAMP**.

```sql
SELECT *
    FROM aluno
  WHERE nome LIKE 'D%'
    AND cpf IS NOT NULL;
```

* Imaginemos a situação em que precisássemos resgatar todos os nomes que comecem com a letra "D" **e** tenham o CPF preenchido. Para isso, usamos o operador `AND` , que funciona como uma soma de condições, apresentando apenas os resultados que atendam às duas exigências que colocamos.
*
```sql
SELECT *
    FROM aluno
  WHERE nome LIKE 'Thiago'
     OR nome LIKE 'Miguel';
```
* Operador OR para buscar todos os Thiago ou Miguel.

---
### Keys

#### **Primary Key**

* A principal função de uma chave primária é garantir a unicidade e a integridade dos dados em uma tabela. Sem uma chave primária, seria difícil garantir que cada registro seja único e que não ocorram duplicatas na tabela. Além disso, a chave primária é frequentemente usada como um ponto de referência em relacionamentos entre tabelas (chamados de chaves estrangeiras), permitindo a criação de associações entre diferentes conjuntos de dados dentro do banco de dados.

```sql
CREATE TABLE curso (
    id INTEGER PRIMARY KEY,
    nome VARCHAR(255) NOT NULL
);
```

Aprendemos, então, que uma chave primária não pode ser nula e precisa ser única. É possível criar chaves primárias **compostas**, juntando dois campos, mas isso veremos em outro momento. Agora você precisa entender apenas como funciona a chave primária em uma única coluna.

#### **Foreign Key**

```sql
CREATE TABLE aluno_curso (
    aluno_id INTEGER,
    curso_id INTEGER,
    PRIMARY KEY (aluno_id, curso_id)
);
```

* Reparem que, ao criarmos nossa tabela, codamos uma chave primária com dois campos, ou seja, uma **chave primária composta**. Dessa forma, declaramos que tanto o id do aluno, quanto o id do curso é um campo único que não pode ser nulo. Faremos um novo registro para testarmos o funcionamento da chave.

* O problema da ausência da **chave estrangeira** na tabela "aluno_curso" é que poderíamos matricular um aluno com "id = 3" no curso de "HTML" sem restrição, porém esse id não existe na tabela "aluno". Isso gera uma inconsistência no nosso banco de dados. Para impedir que isso aconteça, vamos aprender como criamos uma chave estrangeira, a partir da fórmula base abaixo.

```sql
CREATE TABLE aluno_curso (
    aluno_id INTEGER,
	curso_id INTEGER,
	
	PRIMARY KEY (aluno_id, curso_id),
	
	FOREIGN KEY (aluno_id) REFERENCES aluno (id),
	
	FOREIGN KEY (curso_id) REFERENCES curso (id)
);
```

### Consultas com relacionamentos

* Até o momento, para sabermos em qual o curso o aluno está matriculado, usamos o `SELECT * FROM nome_da_tabela WHERE id =` para consultar individualmente o id do aluno e do curso em cada tabela. Contudo, essa não é uma boa forma para visualizarmos os dados, então aprenderemos como fazer essa consulta em uma única _query_.

```sql
SELECT *
  FROM aluno
  JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id
```

* `JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id`: Realiza uma junção entre as tabelas `aluno` e `aluno_curso` com base em uma condição. O `ON` especifica a condição de junção, onde `aluno_curso.aluno_id` deve ser igual a `aluno.id`. Isso significa que a junção será feita usando a coluna `aluno_id` da tabela `aluno_curso` e a coluna `id` da tabela `aluno`.

* Em resumo, esta consulta retorna todas as colunas das tabelas `aluno` e `aluno_curso` para os registros que têm um `aluno_id` correspondente na tabela `aluno`. Isso é útil para combinar informações de ambas as tabelas com base em uma chave estrangeira (`aluno_id` na tabela `aluno_curso`) que referencia a chave primária (`id` na tabela `aluno`) na tabela `aluno`.