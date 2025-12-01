_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# Guia de Início Rápido

Este guia fornecerá um tutorial passo a passo para você começar a usar o HMP (Human Machine Protocol).

## Pré-requisitos

Antes de começar, você precisará de um ambiente com o HMP Engine instalado. (Nota: O HMP Engine ainda não está disponível publicamente. Esta documentação serve como uma referência técnica para o protocolo em si).

## Seu Primeiro Script HMP

Vamos criar um script HMP simples que define uma variável e a imprime no console.

Crie um arquivo chamado `hello.hmp` com o seguinte conteúdo:

```hmp
# Define uma variável com o nome de um usuário
SET user_name TO "World"

# Imprime uma mensagem de saudação usando a variável
CALL log.print WITH message="Hello, ${user_name}!"
```

### Executando o Script

Para executar este script, você usaria o HMP Engine da seguinte forma:

```bash
$ hmp_engine execute hello.hmp
```

### Saída Esperada

A saída no console seria:

```
Hello, World!
```

## Próximos Passos

Agora que você executou seu primeiro script, explore a **[Especificação Técnica](./spec/)** para aprender sobre todos os recursos poderosos que o HMP oferece, incluindo:

*   **Tipos de Variáveis:** Aprenda sobre os diferentes tipos de dados que você pode usar.
*   **Controle de Fluxo:** Domine o uso de `IF`, `LOOP`, `WHILE` e `FOR EACH`.
*   **Catálogo de Ferramentas:** Descubra todas as ferramentas (`tools`) nativas disponíveis para interagir com sistemas, manipular dados e muito mais.
