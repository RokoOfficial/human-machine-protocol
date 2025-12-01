_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 2. Variáveis e Tipos de Dados

Variáveis são usadas no HMP para armazenar e manipular dados durante a execução de um script. Elas são fundamentais para criar fluxos de trabalho dinâmicos e complexos.

## Definição de Variáveis (`SET`)

O comando `SET` é usado para criar uma nova variável ou para atualizar o valor de uma existente.

**Sintaxe:**

```hmp
SET <variable_name> TO <value>
```

- `<variable_name>`: O nome da variável. Deve começar com uma letra ou sublinhado (`_`) e pode conter letras, números e sublinhados.
- `<value>`: O valor a ser atribuído à variável.

**Exemplos:**

```hmp
# Atribui uma string
SET message TO "Hello, world!"

# Atribui um número inteiro
SET count TO 100

# Atribui um número de ponto flutuante
SET price TO 99.95

# Atribui um valor booleano
SET is_active TO true

# Atribui uma lista
SET users TO ["Alice", "Bob", "Charlie"]

# Atribui um valor nulo
SET data TO null
```

## Tipos de Dados

O HMP suporta os seguintes tipos de dados primitivos:

| Tipo      | Descrição                               | Exemplo Literal        |
| :-------- | :-------------------------------------- | :--------------------- |
| `String`  | Uma sequência de caracteres.            | `"Hello, HMP!"`        |
| `Number`  | Números inteiros ou de ponto flutuante. | `42`, `3.14159`        |
| `Boolean` | Um valor de verdadeiro ou falso.        | `true`, `false`        |
| `List`    | Uma coleção ordenada de valores.        | `[1, "apple", true]`   |
| `Null`    | Representa a ausência de um valor.      | `null`                 |

## Expressões e Interpolação

O HMP permite o uso de expressões para realizar cálculos e manipular dados dinamicamente. As expressões são colocadas dentro de `${...}`.

**Sintaxe de Interpolação:**

```hmp
SET greeting TO "Hello, ${user_name}!"
```

**Expressões Matemáticas:**

```hmp
SET base_price TO 100
SET tax_rate TO 0.07
SET total_price TO ${base_price * (1 + tax_rate)}
```

**Acesso a Itens de Lista:**

É possível acessar elementos de uma lista usando a notação de colchetes `[]` dentro de uma expressão.

```hmp
SET fruits TO ["apple", "banana", "orange"]

# Acessa o primeiro elemento (índice 0)
SET first_fruit TO ${fruits[0]} # Resulta em "apple"
```

As expressões são um recurso poderoso que será explorado com mais detalhes nas seções de ferramentas e controle de fluxo.
