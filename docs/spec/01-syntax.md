_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 1. Sintaxe e Estrutura

A sintaxe do HMP (Human Machine Protocol) foi projetada para ser explícita, legível e estruturada. Cada script HMP é uma sequência de comandos executados de forma procedural pelo HMP Engine.

## Formato do Comando

Um comando HMP consiste em uma palavra-chave principal, seguida por argumentos e valores. A estrutura geral é:

```hmp
<COMANDO> <ARGUMENTO1> <VALOR1> [ARGUMENTO2 <VALOR2>...]
```

**Exemplo:**

```hmp
SET my_variable TO "Hello, HMP!"
```

Neste exemplo:
- `SET` é o comando.
- `my_variable` é o primeiro argumento (o nome da variável).
- `TO` é uma palavra-chave que conecta o nome da variável ao seu valor.
- `"Hello, HMP!"` é o valor atribuído.

## Comentários

Comentários são usados para adicionar notas explicativas ao código e são ignorados pelo HMP Engine. Comentários começam com o caractere `#`.

```hmp
# Este é um comentário de linha inteira.
SET counter TO 10 # Este é um comentário no final da linha.
```

## Blocos de Código

Estruturas de controle de fluxo, como `IF`, `LOOP`, `WHILE`, e `PARALLEL`, definem blocos de código. Esses blocos são delimitados por um comando de início e um comando de fim correspondente (por exemplo, `IF` e `ENDIF`).

```hmp
IF ${condition} THEN
    # Este é um bloco de código
    # que será executado se a condição for verdadeira.
    CALL log.print WITH message="Condition is true."
ENDIF
```

## Sensibilidade a Maiúsculas e Minúsculas (Case-Sensitivity)

- **Comandos e Palavras-chave:** Os comandos do HMP (ex: `SET`, `CALL`, `IF`) e palavras-chave (ex: `TO`, `WITH`, `THEN`) são **insensíveis a maiúsculas e minúsculas**. `SET` é o mesmo que `set`.
- **Nomes de Variáveis:** Os nomes das variáveis são **sensíveis a maiúsculas e minúsculas**. `my_var` é diferente de `My_Var`.
- **Nomes de Ferramentas (Tools) e Parâmetros:** Nomes de categorias de ferramentas, ferramentas e seus parâmetros são **sensíveis a maiúsculas e minúsculas**.

## Espaçamento

O HMP usa espaçamento (espaços e tabulações) para separar os componentes de um comando. Múltiplos espaços são tratados como um único. A indentação é recomendada para legibilidade dentro de blocos de código, mas não é sintaticamente obrigatória.
