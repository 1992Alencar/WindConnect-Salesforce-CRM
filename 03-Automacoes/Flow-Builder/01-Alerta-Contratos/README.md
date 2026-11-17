# Alerta de Contratos Próximos do Vencimento

Documentação da automação desenvolvida no Salesforce Flow Builder para monitoramento dos contratos de energia do WindConnect.

## Configuração da decisão – Verificar Vencimento

O elemento Decision foi configurado para identificar contratos ativos cujo vencimento esteja dentro dos próximos 30 dias.

### Condições estabelecidas

A decisão utiliza três critérios:

1. Data de Vencimento maior ou igual à Data_Atual.
2. Data de Vencimento menor ou igual à Mais30dias.
3. Status do Contrato igual a Ativo.

### Lógica de avaliação

Foi utilizada a condição lógica AND (E), exigindo que todos os critérios sejam atendidos simultaneamente.

### Resultados

- Dentro dos 30 dias: direciona o registro para a atualização do indicador de vencimento.
- Fora dos 30 dias: direciona o registro para a atualização do indicador correspondente.

### Conhecimentos aplicados

Salesforce Flow Builder, elemento Decision, operadores de comparação, condições AND e regras de negócio.

## Atualização automática – Vence em 30 dias

O elemento Update Records foi configurado para atualizar o próprio registro de Contrato de Energia que iniciou o fluxo, utilizando a variável global `$Record`.

### Configuração

- Objeto: Contrato de Energia.
- Registro: `$Record`.
- Campo atualizado: Vence em 30 dias.
- Valor atribuído: Verdadeiro.

### Resultado esperado

Quando o contrato atende às condições estabelecidas na decisão Verificar Vencimento, o Flow atualiza automaticamente o indicador para Verdadeiro.

Essa configuração permite identificar contratos ativos cujo vencimento ocorrerá dentro dos próximos 30 dias.
