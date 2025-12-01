_**Atenção, esta documentação está em desenvolvimento e pode sofrer alterações.**_

# 9. Modelo de Segurança

O HMP foi projetado com a segurança como um pilar fundamental. O HMP Engine implementa várias camadas de proteção para garantir que os scripts sejam executados de forma segura e controlada.

## Execução em Sandbox

Cada script HMP é executado em um ambiente de sandbox isolado. Isso significa que um script não pode acessar o sistema de arquivos, a rede ou outros recursos do sistema, a menos que seja explicitamente permitido através de `tools` configuradas.

## Limites de Recursos

O HMP Engine impõe limites estritos sobre os recursos que um script pode consumir:

- **Limite de Tempo de Execução:** Um script não pode ser executado por mais tempo do que o tempo máximo configurado.
- **Limite de Iterações de Loop:** Os loops `WHILE` têm um número máximo de iterações para prevenir loops infinitos.
- **Limite de Profundidade de Pilha:** Limita a profundidade das chamadas de função para evitar estouro de pilha.
- **Limite de Uso de Memória:** Um script não pode alocar mais memória do que o limite configurado.

## Validação de Expressões

As expressões dentro de `${...}` são avaliadas usando um interpretador seguro de Abstract Syntax Tree (AST), não uma função `eval()`, o que previne a execução de código arbitrário.
