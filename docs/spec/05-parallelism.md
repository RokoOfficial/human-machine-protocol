_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 5. Execução Paralela

O HMP suporta a execução paralela de operações, o que pode melhorar significativamente o desempenho de scripts que executam tarefas independentes, como múltiplas chamadas de API.

## Bloco `PARALLEL`

A execução paralela é definida usando o bloco `PARALLEL`.

**Sintaxe:**

```hmp
PARALLEL
    # Comandos a serem executados em paralelo
ENDPARALLEL
```

Todos os comandos `CALL` dentro de um bloco `PARALLEL` são executados simultaneamente. O script aguardará a conclusão de todas as chamadas paralelas antes de prosseguir.

**Exemplo:**

```hmp
PARALLEL
    CALL http.get WITH url="https://api.service1.com/data", label="service1_data"
    CALL http.get WITH url="https://api.service2.com/data", label="service2_data"
    CALL http.get WITH url="https://api.service3.com/data", label="service3_data"
ENDPARALLEL

# Os resultados estão disponíveis em ${last_result}
SET data1 TO ${last_result['service1_data']}
SET data2 TO ${last_result['service2_data']}
```

> **Importante:** É altamente recomendável usar a opção `label` para cada chamada dentro de um bloco `PARALLEL` para distinguir seus resultados, que são todos coletados em `${last_result}`.
