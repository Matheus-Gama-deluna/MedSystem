# Product Requirements Document (PRD) - MedSystem

**Versão:** 1.1
**Data:** 2026-01-21
**Autor:** MedSystem Team (AI & User)
**Status:** Em Revisão

---

## 1. Sumário Executivo

O MedSystem é uma plataforma de gestão para clínicas médicas focada na otimização do fluxo de atendimento presencial e agendamento. Ele resolve a desorganização de agendas e salas físicas, integrando confirmações automáticas via WhatsApp para reduzir o absenteísmo (no-show) e garantindo eficiência operacional para médicos e recepcionistas.

---

## 2. Problema

### 2.1 Contexto
Atualmente, clínicas de médio porte sofrem com a desconexão entre o agendamento (telefone/whatsapp manual) e a realidade física (salas disponíveis, médicos presentes). O uso de planilhas ou sistemas genéricos (Google Agenda) não cobre o fluxo de "chegada do paciente" e "liberação de sala".

### 2.2 Problema Principal
Desorganização no agendamento que gera conflitos de sala, alta taxa de não comparecimento (no-show) por falta de confirmação eficiente e dificuldade de gestores em visualizar a produtividade real da clínica.

### 2.3 Impacto do Problema
- **Financeiro:** Salas ociosas e médicos parados devido a faltas não notificadas.
- **Operacional:** Estresse na recepção com choques de horário.
- **Paciente:** Experiência ruim com atrasos e desinformação.

---

## 3. Solução Proposta

### 3.1 Visão do Produto
Ser o "sistema operacional" da clínica, orquestrando desde a mensagem no WhatsApp do paciente até o momento em que ele entra na sala do médico.

### 3.2 Proposta de Valor
- **Reduce No-Shows:** Confirmação ativa automática via WhatsApp.
- **Gestão Física:** Controle real de qual sala está ocupada e por quem.
- **Simplicidade:** Foco no fluxo da clínica, sem a complexidade desnecessária de ERPs hospitalares gigantes.

### 3.3 Diferencial Competitivo
Ao contrário de agendas simples (Google Calendar) ou sistemas focados apenas em telemedicina, o MedSystem prioriza a **logística física** da clínica (Salas) integrada à comunicação (WhatsApp), preenchendo a lacuna de sistemas legados caros e complexos.

---

## 4. Personas

### Persona 1: Dra. Ana (Médica)
| Atributo | Descrição |
|---|---|
| Perfil | Focada no atendimento, pouco tempo para burocracia. |
| Dores | Pacientes que faltam sem avisar; Sala não preparada quando chega. |
| Jobs to be Done | "Quando chego na clínica, quero saber minha sala e lista de pacientes confirmados para começar a atender sem atrasos." |

### Persona 2: Carla (Recepcionista)
| Atributo | Descrição |
|---|---|
| Perfil | Multitarefa, lida com telefone, balcão e WhatsApp simultaneamente. |
| Dores | Responder centenas de "tem horário?"; Gerenciar conflitos de sala manualmente. |
| Jobs to be Done | "Quando um paciente pede horário, quero visualizar rapidamente as vagas e confirmar o agendamento em segundos." |

### Persona 3: Roberto (Gestor)
| Atributo | Descrição |
|---|---|
| Perfil | Busca eficiência financeira e controle. |
| Dores | Não saber quanto cada médico produziu; Falta de visibilidade sobre cancelamentos. |
| Jobs to be Done | "No fim do mês, quero um relatório automático de produção para realizar os pagamentos corretos." |

---

## 5. Escopo do MVP

### 5.1 Must-Have (P0) - Essencial
- [ ] **Gestão de Agendas:** Visualização diária/semanal por médico.
- [ ] **Cadastro de Pacientes:** Prontuário básico (Dados pessoais, contato).
- [ ] **Gestão de Salas:** Mapa de disponibilidade de salas físicas.
- [ ] **Integração WhatsApp:** Envio de lembretes automáticos D-1.
- [ ] **Painel de Recepção:** Check-in do paciente e status de espera.
- [ ] **Painel de Chamada:** TV na espera chamando paciente/sala (Acessibilidade).
- [ ] **Relatórios Financeiros:** Totalizado básico por médico.
- [ ] **Bloqueio de Agenda:** Médico poder solicitar bloqueio de datas.

### 5.2 Nice-to-Have (P2) - Futuro
- [ ] **Chatbot IA:** Agendamento 100% autônomo via NLP no WhatsApp.
- [ ] **Prontuário Eletrônico Avançado:** Prescrição digital, integração MEMED.

### 5.4 Won't Have (v1) - Fora do Escopo
- **Telemedicina:** Foco inicial é atendimento presencial e gestão física.
- **Faturamento TISS:** Integração complexa com convênios fica para v2.

---

## 6. Métricas de Sucesso

### North Star Metric
⭐ **Consultas Confirmadas e Realizadas** (Foco em reduzir a diferença entre agendado vs realizado).

### Métricas de Suporte
| Métrica | Baseline (Estimado) | Target (3 meses) | Como Medir |
|---|---|---|---|
| Taxa de No-Show | 20-30% (Mercado) | < 10% | % de agendamentos não realizados sem aviso |
| Tempo de Agendamento | 5-10 min (Tel) | < 2 min | Tempo médio de operação no sistema |
| Consultas/Mês | 0 | 500+ | Total de registros de atendimento |

---

## 7. Concorrência

| Concorrente | Pontos Fortes | Pontos Fracos | Nosso Diferencial |
|---|---|---|---|
| **Google Agenda + Excel** | Grátis, familiar. | Sem gestão de salas, sem confirmação auto, dados descentralizados. | Centralização e automação específica para fluxo médico. |
| **Doctoralia** | Ótimo para aquisição de pacientes (marketing). | Caro, focado em agendamento online, fraco gestão interna de salas. | Foco na operação interna e custo-benefício para gestão física. |
| **Feegow/ERPs** | Completos (estoque, fiscal). | Complexos, caros, curva de aprendizado alta. | UX simples e foco no problema principal (Agenda/Sala). |

---

## 8. Riscos e Mitigações

| ID | Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|---|
| R1 | **Bloqueio do WhatsApp** | Média | Alto | Usar API oficial (BSP) ou rotação inteligente; Ter fallback para SMS/Email. |
| R2 | **Resistência Médica** | Média | Médio | Interface do médico deve ser "zero clique" (apenas visualização/chamada). |
| R3 | **LGPD/Vazamento** | Baixa | Crítico | Criptografia de dados sensíveis; Logs de acesso rigorosos desde o D0. |

---

## 9. Cronograma Estimado
- **Fase 1 (Atual):** Definição Produto/Requisitos.
- **Fase 2 (Dev Core):** Estrutura de Salas, Agendas e Pacientes.
- **Fase 3 (Integr.):** Bot WhatsApp e Notificações.
- **Fase 4 (Frontend):** Painéis de Recepção e Médico.
- **Fase 5 (Valid.):** Testes em ambiente controlado.
