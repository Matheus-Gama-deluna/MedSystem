# Especificação de Requisitos - MedSystem

## 1. Visão Geral
Este documento detalha os requisitos funcionais e não-funcionais do sistema MedSystem, derivados do PRD.

---

## 2. Requisitos Funcionais (RF)

### Módulo: Cadastros e Gestão (Core)
| ID | Descrição | Prioridade |
|---|---|---|
| **RF001** | O sistema deve permitir o cadastro de médicos (CRM, Especialidade, Dados Pessoais). | Alta |
| **RF002** | O sistema deve permitir o cadastro de pacientes (Dados Pessoais, Plano de Saúde). | Alta |
| **RF003** | O sistema deve permitir o gerenciamento de usuários (Admin, Médico, Recepcionista). | Alta |
| **RF004** | O sistema deve manter um histórico de pacientes com dados essenciais de atendimentos anteriores. | Média |

### Módulo: Agendamento
| ID | Descrição | Prioridade |
|---|---|---|
| **RF005** | O sistema deve permitir agendamento presencial por um atendente. | Alta |
| **RF006** | O sistema deve integrar com WhatsApp para permitir agendamento automatizado (Bot). | Alta |
| **RF007** | O sistema deve enviar confirmação automática via WhatsApp 1 dia útil antes da consulta. | Alta |
| **RF008** | O sistema deve permitir múltiplos agendamentos para o mesmo paciente no mesmo dia. | Média |
| **RF009** | O sistema deve permitir o bloqueio de agenda pelo médico, sujeito a aprovação do administrador. | Média |
| **RF010** | O sistema deve notificar automaticamente pacientes em caso de ausência do médico (cancelamento/reagendamento). | Média |

### Módulo: Gestão de Salas e Atendimento
| ID | Descrição | Prioridade |
|---|---|---|
| **RF011** | O sistema deve exibir um mapa de salas em tempo real (Disponível/Ocupada). | Alta |
| **RF012** | O sistema deve permitir designar a sala de atendimento antes do início da consulta. | Alta |
| **RF013** | O sistema deve exibir um painel de chamada com Nome do Paciente, Sala e Médico. | Alta |
| **RF014** | O sistema deve emitir aviso sonoro e realizar leitura de voz (TTS) do nome e sala ao chamar. | Alta |

### Módulo: Dashboard e Financeiro
| ID | Descrição | Prioridade |
|---|---|---|
| **RF015** | O sistema deve exibir dashboard com métricas de agendamentos (feitos, confirmados, realizados). | Média |
| **RF016** | O sistema deve permitir busca de cancelamentos por período. | Baixa |
| **RF017** | O sistema deve calcular o total de produção por médico (consultas x valor especialidade). | Alta |
| **RF018** | O sistema deve permitir exportação de relatórios para Excel/CSV. | Média |
| **RF019** | O sistema deve permitir configuração de valores de consultas por especialidade (Admin). | Alta |
| **RF020** | O sistema deve permitir atualização em lote (batch) de valores para múltiplas especialidades. | Baixa |

---

## 3. Regras de Negócio (RN)

| ID | Regra |
|---|---|
| **RN001** | **Bloqueio de Agenda:** Um médico só pode bloquear sua agenda se houver aprovação explícita de um perfil Administrador. |
| **RN002** | **Conflito de Salas:** Não é permitido agendar dois atendimentos na mesma sala no mesmo horário. |
| **RN003** | **Validação de Plano:** O cadastro de paciente deve validar se o plano de saúde informado é aceito pela clínica (lista configurável). |
| **RN004** | **Confirmação Antecipada:** A mensagem de confirmação deve ser enviada apenas em dias úteis (segunda a sexta). |
| **RN005** | **Privacidade:** Histórico deve ocultar dados sensíveis após 5 anos de inatividade, conforme LGPD. |

---

## 4. Requisitos Não Funcionais (RNF)

| ID | Categoria | Descrição | Critério de Aceite |
|---|---|---|---|
| **RNF001** | Segurança | Proteção de dados sensíveis | Dados de saúde e pessoais criptografados em repouso. |
| **RNF002** | Disponibilidade | Uptime do Bot de Agendamento | SLA de 99.9% para o serviço de agendamento via WhatsApp. |
| **RNF003** | Desempenho | Tempo de resposta do Mapa de Salas | Atualização do mapa de salas em < 1s. |
| **RNF004** | Acessibilidade | Leitura de voz no painel | Integração com API de TTS clara e audível em ambiente de espera. |
| **RNF005** | Usabilidade | Interface da Recepção | Design focado em "High Density" para reduzir scroll e cliques. |

---

## 5. Casos de Uso e Critérios de Aceite (Gherkin)

### UC01: Agendamento Automatizado via WhatsApp
**Ator:** Paciente
**Cenário:** Agendamento com Sucesso
```gherkin
Dado que o paciente envia uma mensagem "Quero marcar consulta" no WhatsApp
E o bot identifica o paciente pelo número de telefone
Quando o bot oferece os horários disponíveis para a especialidade "Cardiologia"
E o paciente seleciona "Quarta-feira, 14:00"
Então o sistema deve reservar provisoriamente o horário
E solicitar confirmação do paciente
E após confirmação, registrar o agendamento como "Agendado"
E enviar protocolo de agendamento.
```

### UC02: Chamada de Paciente no Painel
**Ator:** Médico ou Recepcionista
**Cenário:** Chamar paciente para sala
```gherkin
Dado que o paciente "João da Silva" está aguardando
E o médico seleciona "Chamar Paciente" no sistema
Quando o sistema processa a solicitação
Então o painel da sala de espera deve exibir "João da Silva - Sala 04 - Dr. Paulo"
E emitir um sinal sonoro
E reproduzir o áudio "João da Silva, comparecer à Sala 04".
```

### UC03: Fechamento de Agenda
**Ator:** Médico
**Cenário:** Solicitação de bloqueio de data
```gherkin
Dado que o médico precisa se ausentar no dia 25/12
Quando ele acessa "Bloquear Agenda" e seleciona a data
Então o sistema deve registrar a solicitação como "Pendente de Aprovação"
E notificar o administrador.

---

## 6. Matriz de Rastreabilidade (Iniciada)

| Requisito | Origem (PRD) | Casos de Uso/Teste | Status |
|---|---|---|---|
| RF001 | 3.1 CRUD | - | Implementar |
| RF002 | 3.1 CRUD | - | Implementar |
| RF006 | 3.2 Agendamento | UC01 | Implementar |
| RF013 | 3.3 Painel | UC02 | Implementar |
| RF009 | 3.2 Fechamento | UC03 | Implementar |

```
