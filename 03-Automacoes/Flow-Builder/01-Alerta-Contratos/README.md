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

## Atualização automática – Não Vence em 30 dias

O elemento Update Records atualiza o registro de Contrato de Energia utilizando a variável global `$Record`.

### Configuração

- Objeto: Contrato de Energia.
- Registro: `$Record`.
- Campo atualizado: Vence em 30 dias.
- Valor atribuído: Falso.

### Resultado esperado

Quando o registro não atende a todas as condições estabelecidas na decisão Verificar Vencimento, o indicador é atualizado automaticamente para Falso.

Essa configuração mantém o campo atualizado conforme os critérios definidos na automação.

### Resultado esperado

Quando o contrato atende às condições estabelecidas na decisão Verificar Vencimento, o Flow atualiza automaticamente o indicador para Verdadeiro.

Essa configuração permite identificar contratos ativos cujo vencimento ocorrerá dentro dos próximos 30 dias.

## Teste funcional – Contrato CE-0001

Foi realizada uma execução de depuração (Debug) no Salesforce Flow Builder para validar a automação de monitoramento de contratos próximos do vencimento.

### Registro utilizado
- Contrato: CE-0001.
- Data de vencimento: 02/12/2026.
- Dias restantes na data do teste: 15 dias.

### Resultado obtido

A execução foi concluída com sucesso.

O elemento Decision direcionou o registro para o resultado "Dentro dos 30 dias".

Na sequência, o Flow executou a atribuição e a atualização do registro, utilizando o elemento Update Records.

### Conclusão

O teste demonstrou que a automação identifica corretamente um contrato ativo com vencimento dentro do período de 30 dias e executa a atualização do indicador correspondente.

**Observação:** a depuração foi realizada com o modo de reversão ativado, portanto, o teste não representa uma alteração permanente no registro.

## Teste funcional – Contrato CE-0002

Foi realizada uma segunda execução de depuração (Debug) para validar o comportamento da automação diante de um contrato vencido.

### Registro utilizado
- Contrato: CE-0002.
- Data de vencimento: 10/11/2026.
- Status: Ativo.

### Resultado obtido

A execução foi concluída com sucesso.

O elemento Decision direcionou o registro para o resultado padrão "Fora dos 30 dias".

Na sequência, o fluxo executou a atribuição e a atualização do campo "Vence em 30 dias" para Falso.

### Conclusão

O teste demonstrou o funcionamento do segundo caminho da automação, validando a atualização do indicador para contratos que não atendem às condições de vencimento dentro dos próximos 30 dias.

A depuração foi realizada com o modo de reversão ativado, evitando alterações permanentes no registro.
