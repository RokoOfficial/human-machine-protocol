_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 6. Funções

As funções permitem encapsular a lógica em blocos de código reutilizáveis. Isso promove a modularidade e a clareza nos scripts HMP.

## Definição de Função (`FUNCTION`)

**Sintaxe:**

```hmp
FUNCTION <function_name>(<param1>, <param2>, ...)
    # Corpo da função
ENDFUNCTION
```

## Chamada de Função (`CALL`)

As funções são chamadas usando o comando `CALL`.

**Sintaxe:**

```hmp
CALL <function_name> WITH <param1>=<value1>, <param2>=<value2>
```

## Retorno de Valores (`RETURN`)

As funções podem retornar valores usando o comando `RETURN`.

**Sintaxe:**

```hmp
RETURN <value>
```

**Exemplo Completo:**

```hmp
# Definição da função
FUNCTION calculate_total(price, quantity)
    SET total TO ${price * quantity}
    RETURN ${total}
ENDFUNCTION

# Chamada da função
CALL calculate_total WITH price=10, quantity=5, label="total_cost"

# Acessa o valor retornado
SET cost TO ${last_result["total_cost"]}
CALL log.print WITH message="O custo total é: ${cost}"
```
