# Fluxo 03 — Definição Automática de Prioridade

## 1. Visão geral

Automação desenvolvida no Salesforce Flow Builder para definir automaticamente a prioridade das Solicitações de Atendimento conforme a categoria selecionada.

| Propriedade | Configuração |
|---|---|
| Projeto | WindConnect |
| Nome do fluxo | WF_Solicitacao_Definir_Prioridade |
| Versão analisada | V12 |
| Tipo | Fluxo acionado por registro |
| Objeto | Solicitação de Atendimento |
| Gatilho | Registro criado ou atualizado |
| Otimização | Atualizações de campo rápidas |

## 2. Objetivo

Automatizar a classificação das solicitações, atribuindo prioridades de acordo com a categoria informada pelo usuário.

## 3. Condições de entrada

O fluxo verifica se a categoria da solicitação corresponde a uma das seguintes opções:

- Cadastro
- Contrato
- Dúvida
- Operação
- Outro

O requisito de condição utiliza a opção **Qualquer condição é atendida (OR)**.

## 4. Estrutura do fluxo

O fluxo possui uma decisão chamada `Verificar Categoria`, responsável por direcionar a execução para cinco caminhos.

| Categoria | Elemento de atribuição | Prioridade definida |
|---|---|---|
| Contrato | Definir Prioridade Crítica | Crítica |
| Operação | Definir Prioridade Alta | Alta |
| Cadastro | Definir Prioridade Normal - Cadastro | Normal |
| Dúvida | Definir Prioridade Normal - Dúvida | Normal |
| Outro | Definir Prioridade Baixa | Baixa |

## 5. Funcionamento

1. Uma Solicitação de Atendimento é criada ou atualizada.
2. O fluxo verifica a categoria informada.
3. A decisão `Verificar Categoria` identifica o caminho correspondente.
4. O elemento de atribuição define o campo Prioridade.
5. A execução é finalizada.

## 6. Testes de depuração

Foram realizados testes de depuração para verificar os cinco caminhos da decisão.

| Categoria testada | Resultado da decisão | Resultado da atribuição |
|---|---|---|
| Operação | Operação | Prioridade Alta |
| Contrato | Contrato | Prioridade Crítica |
| Cadastro | Cadastro | Prioridade Normal |
| Dúvida | Dúvida | Prioridade Normal |
| Outro | Resultado padrão | Prioridade Baixa |

**Resultado:** os cinco caminhos foram identificados e os respectivos elementos de atribuição foram executados nas depurações apresentadas.

## 7. Integração com regra de validação

O fluxo trabalha em conjunto com a regra de validação `Prioridade_critica`.

Quando a categoria é Contrato, o fluxo define a prioridade como Crítica.

Nesse cenário, a regra de validação exige o preenchimento da Descrição antes de permitir o salvamento do registro.

Mensagem apresentada:

**ATENÇÃO, CRÍTICO!!**

## 8. Evidências

As capturas de tela da configuração do fluxo e das execuções de depuração devem ser armazenadas na pasta `evidencias`.

## 9. Resultado

Automação configurada para classificar automaticamente as Solicitações de Atendimento conforme sua categoria.

**Status:** Testes de depuração realizados com sucesso.
