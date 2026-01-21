# Contexto do Projeto: MedSystem

## 1. O que é
Sistema de gestão para clínicas médicas de médio porte, focado em **atendimento presencial**, **gestão de salas físicas** e **confirmação via WhatsApp**.

## 2. Principal Diferencial
Orquestração da logística física (Sala/Médico) + Redução de No-Show (WhatsApp). Resolve o gap entre agenda simples (Google) e ERPs hospitalares complexos.

## 3. Stack Tecnológico (Preliminar)
- **Frontend**: React (Vite) ou Next.js (Dashboard administrativo e Painéis).
- **Backend**: Node.js (API REST ou GraphQL).
- **Banco de Dados**: PostgreSQL (Relacional para agendamentos e estrutura).
- **Infra**: Docker.

## 4. Glossário do Domínio
- **No-Show**: Paciente que agenda mas não comparece e não avisa.
- **D-1**: Dia anterior à consulta (momento chave da confirmação).
- **Sala Ociosa**: Sala física vazia gerando custo.
- **Produção Médica**: Valor gerado pelo médico com base nas consultas realizadas.

## 5. Diretrizes de Design
- **Prioridade 0**: Velocidade operacional (Recepcionista precisa agendar em segundos).
- **Visual**: Limpo, "Clean Medical", alto contraste para leitura rápida.
- **Mobile**: Foco na visualização do Médico e mensagens do Paciente.
