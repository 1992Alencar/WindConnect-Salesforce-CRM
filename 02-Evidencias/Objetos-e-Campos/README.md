# Evidências – Objetos e Campos

## Módulo Contas

O módulo Contas permite cadastrar, consultar e gerenciar as empresas clientes do WindConnect.

### 01 – Listagem de Contas

Apresenta a relação de empresas cadastradas, permitindo consultar informações e acessar os registros.

### 02 – Detalhes da Conta

Apresenta a estrutura individual do cadastro, incluindo informações comerciais, dados de contato, classificação e proprietário da conta.

## Objetivo

Demonstrar a organização e a modelagem das informações utilizadas no CRM WindConnect.

### 03 - Módulo: Detalhamento de Contatos

A tela de detalhes permite consultar e gerenciar as informações individuais dos contatos cadastrados no WindConnect.

O registro apresenta dados pessoais e profissionais, informações de comunicação, endereço, departamento, cargo e relacionamento com a empresa vinculada.

Também permite visualizar o proprietário do contato e seu relacionamento hierárquico com outros registros.

**Objetivo:** centralizar as informações dos contatos e facilitar o gerenciamento do relacionamento comercial entre clientes e empresas.

### 04 - Módulo: Detalhamento de Parques Eólicos

O cadastro individual de parques eólicos permite centralizar informações operacionais e administrativas de cada empreendimento.

O registro apresenta nome do parque, localização, capacidade instalada em MW, status operacional, data de início da operação, observações e proprietário do registro.

**Objetivo:** organizar as informações dos empreendimentos e facilitar o acompanhamento operacional por meio da plataforma Salesforce.

### 05 - Módulo: Detalhamento de Contratos de Energia

A tela de detalhes apresenta as principais informações dos contratos cadastrados no WindConnect, incluindo número do contrato, cliente relacionado, parque eólico, status, datas de vigência e valor contratual.

**Monitoramento de vencimento:**

Foi implementado um alerta visual para identificar contratos cuja data de vencimento foi ultrapassada.

O campo Dias para Vencer permite acompanhar o prazo contratual, enquanto o indicador de vencimento auxilia na identificação de situações que exigem atenção.

**Objetivo:** facilitar o acompanhamento dos contratos e apoiar a gestão dos prazos por meio de recursos de automação e regras de negócio do Salesforce.

### Monitoramento de Contratos Próximos do Vencimento

O WindConnect possui um indicador para identificar contratos com vencimento previsto dentro dos próximos 30 dias.

No exemplo apresentado, o contrato CE-0001 possui 15 dias restantes até o vencimento, apresentando o campo "Vence em 30 dias" marcado.

**Objetivo:** facilitar a identificação antecipada de contratos que necessitam de acompanhamento, permitindo que os responsáveis tomem providências antes do vencimento.

### 06 - Módulo: Solicitações de Atendimento

O módulo permite registrar, consultar e gerenciar solicitações de atendimento relacionadas às operações do WindConnect.

A interface apresenta a listagem dos registros, com identificação individual por número de solicitação e recursos para criação, importação e gerenciamento.

**Objetivo:** centralizar as solicitações de atendimento e facilitar o acompanhamento das demandas relacionadas aos clientes e às operações.

### Módulo: Detalhamento de Solicitações de Atendimento

A tela de detalhes permite consultar e gerenciar as solicitações de atendimento registradas no WindConnect.

O cadastro contempla número da solicitação, prioridade, categoria, status, descrição, data limite e data de resolução.

Também apresenta relacionamentos com Contas, Parques Eólicos e Contratos de Energia.

**Objetivo:** centralizar o gerenciamento das demandas de atendimento, permitindo acompanhar prioridades, responsáveis e situações das solicitações.
