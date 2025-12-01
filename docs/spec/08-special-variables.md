_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 8. Variáveis Especiais

O HMP Engine fornece um conjunto de variáveis especiais que dão acesso a informações de estado e resultados durante a execução do script.

| Variável | Contexto | Descrição |
|---|---|---|
| `${last_result}` | Global | Armazena o resultado da última operação `CALL` bem-sucedida. |
| `${last_error}` | Bloco `CATCH` | Contém informações sobre o erro capturado em um bloco `TRY`/`CATCH`. |
| `${loop_index}` | Blocos `LOOP` e `FOR EACH` | O índice da iteração atual (base 0). |
