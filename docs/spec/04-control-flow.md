_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 4. Controle de Fluxo

O HMP fornece um conjunto robusto de estruturas de controle de fluxo para gerenciar a lógica de execução de um script. Isso permite a criação de fluxos de trabalho condicionais e repetitivos.

## Condicional (`IF`/`THEN`/`ELSE`/`ENDIF`)

A estrutura `IF` permite que um bloco de código seja executado apenas se uma determinada condição for atendida.

**Sintaxe:**

```hmp
IF <condition> THEN
    # Bloco de código a ser executado se a condição for verdadeira
ENDIF
```

**Com um bloco `ELSE`:**

```hmp
IF <condition> THEN
    # Bloco de código se for verdadeiro
ELSE
    # Bloco de código se for falso
ENDIF
```

- `<condition>`: Uma expressão que avalia como `true` ou `false`.

**Operadores de Comparação:**

| Operador | Descrição        |
| :------- | :--------------- |
| `==`     | Igual            |
| `!=`     | Diferente        |
| `>`      | Maior que        |
| `<`      | Menor que        |
| `>=`     | Maior ou igual a |
| `<=`     | Menor ou igual a |
| `AND`    | E lógico         |
| `OR`     | Ou lógico        |

**Exemplo:**

```hmp
SET user_role TO "admin"
IF ${user_role} == "admin" THEN
    CALL log.print WITH message="Acesso de administrador concedido."
ELSE
    CALL log.print WITH message="Acesso negado."
ENDIF
```

## Loop Fixo (`LOOP N TIMES`)

Executa um bloco de código um número fixo de vezes.

**Sintaxe:**

```hmp
LOOP <number> TIMES
    # Bloco de código a ser repetido
ENDLOOP
```

Dentro de um `LOOP`, a variável especial `${loop_index}` está disponível, contendo o índice da iteração atual (começando em 0).

**Exemplo:**

```hmp
LOOP 3 TIMES
    CALL log.print WITH message="Esta é a iteração número ${loop_index}."
ENDLOOP
```

## Loop Condicional (`WHILE`)

Executa um bloco de código repetidamente enquanto uma condição for verdadeira.

**Sintaxe:**

```hmp
WHILE <condition>
    # Bloco de código a ser repetido
ENDWHILE
```

**Exemplo:**

```hmp
SET counter TO 0
WHILE ${counter} < 3
    CALL log.print WITH message="O contador é ${counter}."
    SET counter TO ${counter + 1}
ENDWHILE
```

> **Nota de Segurança:** Para prevenir loops infinitos, o HMP Engine impõe um limite máximo de iterações para cada bloco `WHILE`.

## Iteração de Lista (`FOR EACH`)

Itera sobre cada item de uma lista, executando um bloco de código para cada item.

**Sintaxe:**

```hmp
FOR EACH <item_variable> IN <list_variable>
    # Bloco de código a ser executado para cada item
ENDFOR
```

- `<item_variable>`: Uma variável que conterá o item da lista na iteração atual.
- `<list_variable>`: A variável de lista a ser iterada.

Dentro do loop, as variáveis `${item_variable}` e `${loop_index}` estão disponíveis.

**Exemplo:**

```hmp
SET users TO ['Alice', 'Bob', 'Charlie']
FOR EACH user IN ${users}
    CALL log.print WITH message="Processando usuário ${user} no índice ${loop_index}."
ENDFOR
```
