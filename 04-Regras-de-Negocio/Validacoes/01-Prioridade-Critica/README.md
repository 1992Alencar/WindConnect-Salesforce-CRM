# Validação 01 — Prioridade Crítica

## 1. Visão geral

Regra de validação desenvolvida no Salesforce para garantir que toda Solicitação de Atendimento classificada com prioridade Crítica possua uma descrição preenchida.

| Propriedade | Configuração |
|---|---|
| Projeto | WindConnect |
| Objeto | Solicitação de Atendimento |
| Nome da regra | Prioridade_critica |
| Status | Ativada |
| Mensagem de erro | ATENÇÃO, CRÍTICO!! |
| Local do erro | Parte superior da página |

## 2. Campos utilizados

| Campo | API Name | Finalidade |
|---|---|---|
| Prioridade | Prioridade__c | Identificar solicitações críticas |
| Descrição | Descricao__c | Exigir detalhamento da solicitação |

## 3. Fórmula da regra

```salesforce
AND(
    ISPICKVAL(Prioridade__c, "Crítica"),
    ISBLANK(Descricao__c)
)
```

## 4. Funcionamento

A regra verifica duas condições simultaneamente:

1. A prioridade da solicitação deve ser Crítica.
2. O campo Descrição deve estar vazio.

Quando ambas as condições são verdadeiras, o Salesforce bloqueia o salvamento do registro e apresenta a mensagem:

**ATENÇÃO, CRÍTICO!!**

## 5. Cenários de teste

| Prioridade | Descrição | Resultado esperado |
|---|---|---|
| Crítica | Vazia | Bloquear salvamento |
| Crítica | Preenchida | Permitir salvamento |
| Alta | Vazia | Não bloquear por esta regra |
| Normal | Vazia | Não bloquear por esta regra |
| Baixa | Vazia | Não bloquear por esta regra |

## 6. Integração com Flow Builder

Esta validação possui relação direta com o fluxo:

`WF_Solicitacao_Definir_Prioridade`

O fluxo identifica a categoria da solicitação e atribui automaticamente a prioridade correspondente.

Quando a categoria é Contrato, a prioridade definida é Crítica.

Nesse cenário, a regra de validação exige que a descrição esteja preenchida antes de permitir o salvamento.

## 7. Evidências

As capturas de tela da configuração da regra e dos testes devem ser armazenadas na pasta de evidências correspondente.

## 8. Resultado

Regra de validação identificada e analisada no Salesforce.

A fórmula está ativa e protege a qualidade das informações das solicitações classificadas como críticas.

**Status da documentação:** Registrada.  
**Status dos testes funcionais:** Pendente de validação dos cenários de salvamento.
