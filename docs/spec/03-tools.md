_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 3. Chamada de Ferramentas (Tools)

As ferramentas (`tools`) são o principal mecanismo no HMP para interagir com o sistema, realizar cálculos, manipular dados e se conectar a serviços externos. O comando `CALL` é usado para invocar essas ferramentas.

## Sintaxe do `CALL`

A sintaxe para chamar uma ferramenta é estruturada para ser clara e legível.

**Sintaxe Básica:**

```hmp
CALL <category>.<tool_name>
```

**Com Parâmetros:**

```hmp
CALL <category>.<tool_name> WITH <param1>=<value1>, <param2>=<value2>
```

- `<category>`: O grupo ao qual a ferramenta pertence (ex: `log`, `math`, `http`).
- `<tool_name>`: O nome da ferramenta a ser executada.
- `WITH`: Palavra-chave que introduz a lista de parâmetros.
- `<param_name>=<value>`: Pares de nome e valor para os parâmetros que a ferramenta aceita.

## Manipulação de Resultados

O resultado da última ferramenta executada é armazenado automaticamente na variável especial `${last_result}`.

**Exemplo:**

```hmp
# Chama a ferramenta de soma
CALL math.sum WITH a=10, b=5

# O resultado (15) está agora em ${last_result}
SET sum_result TO ${last_result}
CALL log.print WITH message="O resultado da soma é: ${sum_result}"
```

### Rótulos de Resultado (`label`)

Para maior clareza, especialmente em operações complexas ou execuções paralelas, você pode atribuir um rótulo (`label`) ao resultado de uma chamada. O resultado será então armazenado como um campo dentro de `${last_result}`.

**Sintaxe com `label`:**

```hmp
CALL <category>.<tool_name> WITH <params>, label="<your_label>"
```

**Exemplo:**

```hmp
CALL math.sum WITH a=10, b=5, label="addition"
CALL math.subtract WITH a=20, b=3, label="subtraction"

# Acessa o resultado da soma
SET addition_result TO ${last_result['addition']}

# Acessa o resultado da subtração
SET subtraction_result TO ${last_result['subtraction']}

CALL log.print WITH message="Soma: ${addition_result}, Subtração: ${subtraction_result}"
```

## Catálogo de Ferramentas

O HMP vem com um rico conjunto de ferramentas nativas. A seguir, uma visão geral das categorias. A documentação completa de cada ferramenta, incluindo parâmetros e exemplos, estará disponível em um apêndice separado.

| Categoria | Descrição                                                                 |
| :-------- | :------------------------------------------------------------------------ |
| `log`     | Ferramentas para imprimir mensagens e depurar.                            |
| `math`    | Operações matemáticas (soma, subtração, etc.).                            |
| `string`  | Manipulação de strings (concatenar, dividir, etc.).                       |
| `list`    | Operações em listas (adicionar, obter, remover, etc.).                    |
| `json`    | Análise e serialização de dados no formato JSON.                          |
| `http`    | Realização de requisições HTTP (GET, POST, etc.).                         |
| `crypto`  | Funções criptográficas (geração de UUID, hashes, etc.).                   |
| `random`  | Geração de dados aleatórios (números, strings).                           |
| `system`  | Interação com o ambiente do sistema (variáveis de ambiente, etc.).        |
| `meta`    | Ferramentas para introspecção e manipulação do próprio script HMP.        |
