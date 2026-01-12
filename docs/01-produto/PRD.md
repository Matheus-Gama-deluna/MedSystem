# PRD: MedSystem

**Versão:** 1.0  
**Data:** 2026-01-12  
**Autor:** Equipe MedSystem  
**Status:** Em Revisão

---

## 1. Sumário Executivo

MedSystem é um sistema de gestão de consultas médicas para clínicas, focado em agendamentos, controle de salas e acompanhamento de pacientes. Desenvolvido para ser operado por atendentes e médicos, com evolução planejada para automação via WhatsApp.

---

## 2. Problema

### 2.1 Contexto
Clínicas médicas de pequeno e médio porte frequentemente utilizam planilhas, agendas de papel ou sistemas complexos e caros para gerenciar consultas, resultando em erros, conflitos de horários e perda de informações de pacientes.

### 2.2 Problema Principal
- Dificuldade em gerenciar agendamentos de múltiplos médicos
- Falta de histórico organizado do paciente
- Comunicação ineficiente sobre chamada de pacientes para consulta
- Ausência de visão consolidada das operações da clínica

### 2.3 Impacto do Problema
- Conflitos de horários geram insatisfação de pacientes
- Médicos sem acesso rápido ao histórico do paciente
- Tempo perdido chamando pacientes manualmente
- Dificuldade em calcular produtividade e faturamento

---

## 3. Solução Proposta

### 3.1 Visão do Produto
Sistema web completo para gestão de consultas médicas com painel de chamada para TV e histórico integrado do paciente.

### 3.2 Proposta de Valor
- **Para a clínica**: Organização completa de agendamentos e salas
- **Para o médico**: Histórico do paciente acessível instantaneamente
- **Para o atendente**: Agendamento rápido e painel de chamada automatizado
- **Para o paciente**: Atendimento mais ágil e organizado

### 3.3 Diferencial Competitivo
- Painel de chamada com Text-to-Speech integrado
- Foco em simplicidade operacional
- Arquitetura pronta para evolução mobile
- Integração futura com WhatsApp para automação

---

## 4. Personas

### Persona 1: Dr. Carlos (Médico)
| Atributo | Descrição |
|---|---|
| Cargo/Papel | Médico especialista |
| Idade/Perfil | 35-55 anos, atende em múltiplas clínicas |
| Objetivos | Visualizar agenda, acessar histórico do paciente rapidamente |
| Dores principais | Não ter informações do paciente organizadas, perder tempo buscando prontuários |
| Jobs to be Done | "Quando um paciente entra na sala, quero ver seu histórico para dar continuidade ao tratamento" |

### Persona 2: Ana (Atendente)
| Atributo | Descrição |
|---|---|
| Cargo/Papel | Recepcionista/Atendente |
| Idade/Perfil | 25-45 anos, multitarefas |
| Objetivos | Agendar consultas rapidamente, chamar pacientes sem sair do lugar |
| Dores principais | Conflitos de horários, dificuldade em localizar salas disponíveis |
| Jobs to be Done | "Quando um paciente liga, quero encontrar o próximo horário disponível em segundos" |

### Persona 3: Roberto (Administrador)
| Atributo | Descrição |
|---|---|
| Cargo/Papel | Dono/Gestor da clínica |
| Idade/Perfil | 40-60 anos, foco em resultados |
| Objetivos | Visualizar produtividade, controlar valores, exportar relatórios |
| Dores principais | Falta de visão consolidada, dificuldade em calcular faturamento |
| Jobs to be Done | "No final do mês, quero saber quantas consultas cada médico realizou e o valor total" |

---

## 5. Escopo do MVP

### 5.1 Must-Have (P0) - MVP v1.0
- [x] **F001**: CRUD de Médicos (nome, especialidade, horários, valor consulta)
- [x] **F002**: CRUD de Pacientes (dados + histórico médico + anotações)
- [x] **F003**: Agendamento manual de consultas (atendente)
- [x] **F004**: Gestão de agenda (visualização, bloqueios, múltiplas consultas/dia)
- [x] **F005**: Gestão de salas (mapa, disponibilidade, designação)
- [x] **F006**: Painel de chamada para TV (nome, sala, médico + TTS)
- [x] **F007**: Sistema de perfis (Admin, Médico, Atendente)
- [x] **F008**: Dashboard básico (agendamentos do dia, status)

### 5.2 Should-Have (P1) - v1.1
- [ ] **F009**: Dashboard avançado (métricas, cancelamentos por período)
- [ ] **F010**: Totalizador financeiro por médico/especialidade
- [ ] **F011**: Exportação de dados para Excel
- [ ] **F012**: Fechamento de agenda com aprovação do admin
- [ ] **F013**: Reagendamento automático (ausência do médico)

### 5.3 Nice-to-Have (P2) - v2.0
- [ ] **F014**: Integração WhatsApp (Z-API/Evolution)
- [ ] **F015**: Chatbot para agendamento automatizado
- [ ] **F016**: Lembretes automáticos (1 dia antes)
- [ ] **F017**: Confirmação de presença via WhatsApp

### 5.4 Won't Have (v1)
- **Portal do Paciente** - Paciente interage apenas via WhatsApp (v2.0)
- **Prontuário Eletrônico Completo (PEP)** - Foco em anotações simples, não conformidade com CFM
- **Integração com convênios/ANS** - Complexidade fora do escopo inicial
- **Telemedicina** - Fora do escopo

---

## 6. Métricas de Sucesso

### North Star Metric
**Consultas Realizadas por Mês**: Quantidade de consultas que passaram do status "agendada" para "realizada"

### Métricas de Suporte

| Métrica | Baseline | Target (3 meses) | Como Medir |
|---|---|---|---|
| Tempo médio para agendar | N/A | < 30 segundos | Timestamp no sistema |
| Taxa de no-show | N/A | < 15% | Agendadas vs Realizadas |
| Consultas/dia/médico | N/A | Definir após 1 mês | Dashboard |
| Erros de conflito de sala | N/A | 0 | Logs do sistema |

---

## 7. Concorrência

| Concorrente | Pontos Fortes | Pontos Fracos | Nosso Diferencial |
|---|---|---|---|
| iClinic | Completo, integração convênios | Caro, complexo | Simplicidade e preço |
| Doctoralia | Marketplace de pacientes | Foco em marketing, não gestão | Foco operacional |
| Planilhas Excel | Familiar, gratuito | Sem automação, propenso a erros | Automação e histórico |
| Agenda de papel | Simples | Não escalável, sem backup | Digital e seguro |

---

## 8. Riscos e Mitigações

| ID | Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|---|
| R1 | TTS não funcionar bem em todos navegadores | Média | Alto | Usar Web Speech API com fallback |
| R2 | Performance do painel TV em hardware antigo | Média | Médio | Otimização e modo lite |
| R3 | Complexidade do histórico médico | Baixa | Alto | Manter campos simples e objetivos |
| R4 | Integração WhatsApp complexa | Alta | Médio | Deixar para v2.0, focar no core |

---

## 9. Stack Tecnológica Recomendada

### Critério: Fácil evolução para Mobile

| Camada | Tecnologia | Justificativa |
|---|---|---|
| **Frontend** | React + Next.js | SSR, PWA ready, compartilha lógica com React Native |
| **Estilo** | Tailwind CSS | Produtividade, design system consistente |
| **Backend** | Node.js + Fastify | Performance, TypeScript compartilhado |
| **Banco** | PostgreSQL | Robusto, suporte a JSON para flexibilidade |
| **ORM** | Prisma | Type-safe, migrations fáceis |
| **Auth** | NextAuth.js | Sessões, múltiplos providers |
| **TTS** | Web Speech API | Nativo do browser, sem custo |
| **Deploy** | Vercel + Railway | Simplicidade, baixo custo inicial |

### Evolução Mobile (v3.0+)
- **React Native** com Expo compartilhando componentes e lógica do Next.js
- API já estará pronta em Node.js

---

## 10. Histórico do Paciente - Campos

### Dados Básicos (não sensíveis)
- Nome completo
- Data de nascimento (para cálculo de idade)
- Telefone de contato
- Plano de saúde (nome + número da carteira)

### Dados Médicos (controlados por perfil)
- Alergias conhecidas
- Medicamentos em uso contínuo
- Condições crônicas relevantes (diabetes, hipertensão, etc.)
- Observações gerais

### Por Consulta
- Data e hora
- Médico responsável
- Especialidade
- Anotações do médico (texto livre)
- Status (agendada, realizada, cancelada, no-show)

---

## 11. Timeline Preliminar

| Marco | Data Estimada | Dependências |
|---|---|---|
| PRD Aprovado | Semana 1 | - |
| Requisitos Completos | Semana 2 | PRD |
| Arquitetura Definida | Semana 3 | Requisitos |
| Design/Protótipo | Semana 4-5 | Arquitetura |
| MVP Funcional | Semana 10-12 | Design |
| Testes e Ajustes | Semana 13-14 | MVP |
| v1.0 Produção | Semana 15 | Testes |

---

## 12. Restrições e Premissas

### Restrições
- **Equipe**: Desenvolvimento com IA (1-2 pessoas + assistentes IA)
- **Orçamento**: Bootstrap (infraestrutura < $50/mês inicial)
- **Prazo MVP**: ~3-4 meses

### Premissas
- Clínica possui TV/monitor para painel de chamada
- Navegador moderno com suporte a Web Speech API
- Conexão internet estável na clínica

---

## Changelog

| Versão | Data | Autor | Mudanças |
|---|---|---|---|
| 1.0 | 2026-01-12 | Equipe | Versão inicial |
