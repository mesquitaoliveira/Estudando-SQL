# Estudando - SQL

# Índice
Dia 1
- Introdução ao SQL: o que é SQL, para que serve e como funciona;
- Comandos básicos: SELECT, FROM, WHERE, ORDER BY;
- Exercícios práticos com consultas simples em uma tabela.

Dia 2
- Operadores lógicos: AND, OR, NOT;
- Operadores de comparação: =, <>, >, >=, <, <=;
- Cláusulas LIKE e BETWEEN;
- Exercícios práticos com consultas mais complexas envolvendo vários operadores.

Dia 3
- Funções agregadas: COUNT, SUM, AVG, MAX, MIN;
- Agrupamento de dados: GROUP BY, HAVING;
- Joins: INNER JOIN, LEFT JOIN, RIGHT JOIN;
- Exercícios práticos com consultas envolvendo funções agregadas e junções.

# Dia 1

## Introdução ao SQL
### O que é SQL, para que serve e como funciona;

**O que é SQL?**
SQL é a sigla para *Structured Query Language*, que significa Linguagem de Consulta Estruturada. É uma linguagem de programação usada para gerenciar e manipular bancos de dados relacionais.

**Para que serve?**
SQL é usado para inserir, buscar, atualizar e deletar dados em um banco de dados relacional. Também pode ser usado para criar e modificar a estrutura do banco de dados.

**Como funciona?**
SQL funciona através de comandos que são enviados ao banco de dados. Esses comandos são escritos em uma sintaxe específica e podem ser usados para realizar diversas tarefas, como criar tabelas, inserir dados e fazer consultas.


### Comandos básicos: SELECT, FROM, WHERE, ORDER BY;

**SELECT**
O comando `SELECT` é usado para buscar dados de uma ou mais colunas de uma tabela. Por exemplo, para buscar todos os dados da coluna "nome" da tabela "clientes", o comando seria:
```SQL
SELECT nome FROM clientes;
```

**FROM**
O comando `FROM` é usado para especificar a tabela de onde os dados serão buscados. No exemplo acima, a tabela especificada é "clientes".

**WHERE**
O comando `WHERE` é usado para filtrar os resultados de uma consulta. Por exemplo, para buscar apenas os clientes com idade maior que 18 anos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE idade > 18;
```

**ORDER BY**
O comando `ORDER BY` é usado para ordenar os resultados de uma consulta. Por exemplo, para ordenar os clientes em ordem alfabética pelo nome, o comando seria:
```SQL
SELECT nome FROM clientes ORDER BY nome;
```

Esses são alguns dos comandos básicos do SQL.

### Exercícios práticos com consultas simples em uma tabela.

1. **Buscar todos os clientes:** Escreva uma consulta para buscar todos os dados da tabela "clientes".
```SQL
SELECT * FROM clientes;
```

2. **Buscar clientes por cidade:** Escreva uma consulta para buscar os nomes dos clientes que moram na cidade de "São Paulo".
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo';
```

3. **Ordenar clientes por idade:** Escreva uma consulta para buscar os nomes dos clientes ordenados por idade, do mais jovem para o mais velho.
```SQL
SELECT nome FROM clientes ORDER BY idade;
```

4. **Contar clientes por cidade:** Escreva uma consulta para contar o número de clientes em cada cidade.
```SQL
SELECT cidade, COUNT(*) FROM clientes GROUP BY cidade;
```

5. **Buscar clientes com desconto:** Escreva uma consulta para buscar os nomes dos clientes que têm um desconto maior que 10%.
```SQL
SELECT nome FROM clientes WHERE desconto > 10;
```

### Resolução Exercícios
Vamos supor que temos a seguinte tabela "clientes":

| **id** | **nome** | **cidade**       | **idade** | **desconto** |
|:------:|:--------:|:----------------:|:---------:|:------------:|
| 1      | Ana      | São Paulo        | 25        | 5            |
| 2      | Bruno    | Rio de Janeiro   | 32        | 15           | 
| 3      | Carla    | São Paulo        | 40        | 20           | 
| 4      | Diego    | Salvador         | 22        | 10           | 
| 5      | Elisa    | São Paulo        | 30        | 0            | 


Agora, vamos resolver cada um dos exercícios anteriores baseado nesta tabela:

1. **Buscar todos os clientes:** Escreva uma consulta para buscar todos os dados da tabela "clientes".
```SQL
SELECT * FROM clientes;
```
Resultado:
| **id** | **nome** | **cidade**       | **idade** | **desconto** |
|:------:|:--------:|:----------------:|:---------:|:------------:|
| 1      | Ana      | São Paulo        | 25        | 5            |
| 2      | Bruno    | Rio de Janeiro   | 32        | 15           | 
| 3      | Carla    | São Paulo        | 40        | 20           | 
| 4      | Diego    | Salvador         | 22        | 10           | 
| 5      | Elisa    | São Paulo        | 30        | 0            | 

2. **Buscar clientes por cidade:** Escreva uma consulta para buscar os nomes dos clientes que moram na cidade de "São Paulo".
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo';
```
Resultado:
| **nome** |
|:------:|
| Ana |
| Carla |
| Elisa |

3. **Ordenar clientes por idade:** Escreva uma consulta para buscar os nomes dos clientes ordenados por idade, do mais jovem para o mais velho.
```SQL
SELECT nome FROM clientes ORDER BY idade;
```
Resultado:
| **nome** |
|:------:|
| Diego |
| Ana |
| Elisa |
| Bruno |
| Carla |

4. **Contar clientes por cidade:** Escreva uma consulta para contar o número de clientes em cada cidade.
```SQL
SELECT cidade, COUNT(*) FROM clientes GROUP BY cidade;
```
Resultado:
| **cidade**        | **COUNT(*)** |
|:-----------------:|:------------:|
| Rio de Janeiro    |        1     |
| Salvador          |        1     |
| São Paulo         |        3     |

5. **Buscar clientes com desconto:** Escreva uma consulta para buscar os nomes dos clientes que têm um desconto maior que 10%.
```SQL
SELECT nome FROM clientes WHERE desconto >10;
```
Resultado:
| nome |
|:------:|
| Bruno|
| Carla|

# Dia 2

### Operadores lógicos: AND, OR, NOT;

Os operadores lógicos são usados para combinar ou modificar condições em uma consulta SQL. Eles permitem que você crie consultas mais complexas e flexíveis, filtrando os resultados de acordo com suas necessidades. Os operadores lógicos básicos do SQL são `AND`, `OR` e `NOT`.

**AND** é usado para combinar duas ou mais condições, retornando apenas os resultados que atendem a todas as condições especificadas.

**OR** é usado para buscar resultados que atendam a pelo menos uma das condições especificadas.

**NOT** é usado para inverter o resultado de uma condição, retornando apenas os resultados que **não** atendem à condição especificada.

Agora que você tem uma introdução sobre os operadores lógicos do SQL, vamos ver como eles funcionam na prática:

**AND**
O operador `AND` é usado para combinar duas ou mais condições em uma consulta. Por exemplo, para buscar os clientes que moram na cidade de "São Paulo" e têm mais de 30 anos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo' AND idade > 30;
```

**OR**
O operador `OR` é usado para buscar resultados que atendam a pelo menos uma das condições especificadas. Por exemplo, para buscar os clientes que moram na cidade de "São Paulo" ou têm mais de 30 anos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo' OR idade > 30;
```

**NOT**
O operador `NOT` é usado para inverter o resultado de uma condição. Por exemplo, para buscar os clientes que **não** moram na cidade de "São Paulo", o comando seria:
```SQL
SELECT nome FROM clientes WHERE NOT cidade = 'São Paulo';
```

Esses são os operadores lógicos básicos do SQL. Você pode combiná-los para criar consultas mais complexas e filtrar os resultados de acordo com suas necessidades.

### Operadores de comparação: =, <>, >, >=, <, <=;

Os operadores de comparação são usados para comparar valores em uma consulta SQL. Eles permitem que você crie condições para filtrar os resultados de acordo com suas necessidades. Os operadores de comparação básicos do SQL são `=`, `<>`, `>`, `>=`, `<` e `<=`.

`=` é usado para verificar se dois valores são iguais.

`<>` é usado para verificar se dois valores são diferentes.

`>` é usado para verificar se um valor é maior que outro.

`>=` é usado para verificar se um valor é maior ou igual a outro.

`<` é usado para verificar se um valor é menor que outro.

`<=` é usado para verificar se um valor é menor ou igual a outro.

Agora que você tem uma introdução sobre os operadores de comparação do SQL, vamos ver como eles funcionam na prática:

**=**
O operador `=` é usado para verificar se dois valores são iguais. Por exemplo, para buscar os clientes que moram na cidade de "São Paulo", o comando seria:
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo';
```

**<>**
O operador `<>` é usado para verificar se dois valores são diferentes. Por exemplo, para buscar os clientes que **não** moram na cidade de "São Paulo", o comando seria:
```SQL
SELECT nome FROM clientes WHERE cidade <> 'São Paulo';
```

**>**
O operador `>` é usado para verificar se um valor é maior que outro. Por exemplo, para buscar os clientes com mais de 30 anos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE idade > 30;
```

**>=**
O operador `>=` é usado para verificar se um valor é maior ou igual a outro. Por exemplo, para buscar os clientes com 30 anos ou mais, o comando seria:
```SQL
SELECT nome FROM clientes WHERE idade >= 30;
```

**<**
O operador `<` é usado para verificar se um valor é menor que outro. Por exemplo, para buscar os clientes com menos de 30 anos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE idade < 30;
```

**<=**
O operador `<=` é usado para verificar se um valor é menor ou igual a outro. Por exemplo, para buscar os clientes com 30 anos ou menos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE idade <= 30;
```

Esses são exemplos de como os operadores de comparação funcionam na prática. Você pode usá-los para criar consultas mais flexíveis e filtrar os resultados de acordo com suas necessidades.

### Cláusulas LIKE e BETWEEN;

As cláusulas `LIKE` e `BETWEEN` são usadas para filtrar os resultados de uma consulta de maneira mais flexível. Elas permitem que você busque resultados que correspondam a padrões específicos ou que estejam dentro de um intervalo de valores.

A cláusula `LIKE` é usada para buscar resultados que correspondam a um padrão especificado. Ela é útil para buscar valores que contenham um determinado texto ou que comecem ou terminem com um determinado caractere.

A cláusula `BETWEEN` é usada para buscar resultados que estejam dentro de um intervalo de valores. Ela é útil para buscar valores que estejam entre dois valores especificados, como datas ou números.

Agora que você tem uma introdução sobre as cláusulas `LIKE` e `BETWEEN`, vamos ver como elas funcionam na prática:

**LIKE**
A cláusula `LIKE` é usada com o operador `WHERE` para buscar resultados que correspondam a um padrão especificado. Por exemplo, para buscar os clientes cujos nomes começam com a letra "A", o comando seria:
```SQL
SELECT nome FROM clientes WHERE nome LIKE 'A%';
```
O caractere `%` é um curinga que representa qualquer sequência de caracteres. Neste caso, ele é usado para representar qualquer sequência de caracteres após a letra "A".

**BETWEEN**
A cláusula `BETWEEN` também é usada com o operador `WHERE` para buscar resultados que estejam dentro de um intervalo de valores. Por exemplo, para buscar os clientes com idade entre 20 e 30 anos, o comando seria:
```SQL
SELECT nome FROM clientes WHERE idade BETWEEN 20 AND 30;
```

Esses são exemplos de como as cláusulas `LIKE` e `BETWEEN` funcionam na prática. Você pode usá-las para criar consultas mais flexíveis e filtrar os resultados de acordo com suas necessidades.

## Exercícios:

Supondo que temos a seguinte tabela "clientes":

| **id** | **nome** | **cidade**       | **idade** | **desconto** |
|:------:|:--------:|:----------------:|:---------:|:------------:|
| 1      | Ana      | São Paulo        | 25        | 5            |
| 2      | Bruno    | Rio de Janeiro   | 32        | 15           | 
| 3      | Carla    | São Paulo        | 40        | 20           | 
| 4      | Diego    | Salvador         | 22        | 10           | 
| 5      | Elisa    | São Paulo        | 30        | 0            | 

Agora, vamos resolver alguns exercícios usando os operadores lógicos, operadores de comparação e cláusulas `LIKE` e `BETWEEN`:

1. **Buscar clientes por cidade e idade:** Escreva uma consulta para buscar os nomes dos clientes que moram na cidade de "São Paulo" e têm mais de 30 anos.
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo' AND idade > 30;
```
Resultado:
| nome |
|------|
| Carla |

2. **Buscar clientes por cidade ou desconto:** Escreva uma consulta para buscar os nomes dos clientes que moram na cidade de "São Paulo" ou têm um desconto maior que 10%.
```SQL
SELECT nome FROM clientes WHERE cidade = 'São Paulo' OR desconto >10;
```
Resultado:
| nome |
|------|
| Ana |
| Bruno|
| Carla|
| Elisa|

3. **Buscar clientes que não têm desconto:** Escreva uma consulta para buscar os nomes dos clientes que não têm desconto.
```SQL
SELECT nome FROM clientes WHERE NOT desconto >0;
```
Resultado:
| nome |
|------|
| Elisa|

4. **Buscar clientes com idade entre dois valores:** Escreva uma consulta para buscar os nomes dos clientes com idade entre 25 e 35 anos.
```SQL
SELECT nome FROM clientes WHERE idade BETWEEN 25 AND 35;
```
Resultado:
| nome |
|------|
| Ana |
| Bruno|
| Elisa|

5. **Buscar clientes cujos nomes começam com a letra "A":** Escreva uma consulta para buscar os nomes dos clientes cujos nomes começam com a letra "A".
```SQL
SELECT nome FROM clientes WHERE nome LIKE 'A%';
```
Resultado:
| nome |
|------|
| Ana |

6. **Contar clientes por cidade e idade:** Escreva uma consulta para contar o número de clientes em cada cidade que têm mais de 30 anos.
```SQL
SELECT cidade, COUNT(*) FROM clientes WHERE idade >30 GROUP BY cidade;
```
Resultado:
| cidade          | COUNT(*) |
|-----------------|----------|
| Rio de Janeiro    |        1 |
| São Paulo         |        1 |

7. **Buscar clientes com desconto diferente de zero:** Escreva uma consulta para buscar os nomes dos clientes que têm um desconto diferente de zero.
```SQL
SELECT nome FROM clientes WHERE desconto <>0;
```
Resultado:
| nome |
|------|
| Ana |
| Bruno|
| Carla|
| Diego|

8. **Buscar clientes com idade maior ou igual a um valor:** Escreva uma consulta para buscar os nomes dos clientes com idade maior ou igual a 30 anos.
```SQL
SELECT nome FROM clientes WHERE idade >=30;
```
Resultado:
| nome |
|------|
| Bruno|
| Carla|
| Elisa|

9. **Buscar clientes cujos nomes terminam com a letra "a":** Escreva uma consulta para buscar os nomes dos clientes cujos nomes terminam com a letra "a".
```SQL
SELECT nome FROM clientes WHERE nome LIKE '%a';
```
Resultado:
| nome |
|------|
| Ana |
| Carla |
| Elisa |

Agora vamos continuar com o exercício 10:

10. **Buscar clientes com idade menor ou igual a um valor:** Escreva uma consulta para buscar os nomes dos clientes com idade menor ou igual a 30 anos.
```SQL
SELECT nome FROM clientes WHERE idade <=30;
```
Resultado:
| nome |
|------|
| Ana |
| Diego|
| Elisa|
