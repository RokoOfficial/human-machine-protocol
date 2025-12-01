_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 7. Tratamento de Erros

O HMP fornece um mecanismo de tratamento de erros para gerenciar exceções de forma controlada, garantindo que os scripts possam lidar com falhas sem interromper abruptamente.

## Bloco `TRY`/`CATCH`

**Sintaxe:**

```hmp
TRY
    # Bloco de código que pode gerar um erro
CATCH
    # Bloco de código a ser executado se ocorrer um erro
ENDTRY
```

Se ocorrer um erro dentro do bloco `TRY`, a execução desse bloco é interrompida e o controle é transferido para o bloco `CATCH`. Se nenhum erro ocorrer, o bloco `CATCH` é ignorado.

Dentro do bloco `CATCH`, a variável especial `${last_error}` está disponível, contendo informações sobre o erro que ocorreu.

**Exemplo:**

```hmp
TRY
    # Esta chamada falhará porque a URL é inválida
    CALL http.get WITH url="invalid-url"
CATCH
    CALL log.print WITH message="Ocorreu um erro: ${last_error["message"]}"
ENDTRY
```
