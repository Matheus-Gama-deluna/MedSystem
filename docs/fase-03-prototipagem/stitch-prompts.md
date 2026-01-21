# Prompts para Google Stitch - MedSystem

Use estes prompts no [Stitch](https://stitch.withgoogle.com) para gerar os protótipos da interface.

## 1. Dashboard Administrativo
**Objetivo:** Visão geral operacional e financeira da clínica.
**Prompt:**
> Crie um dashboard administrativo moderno para uma clínica médica (MedSystem).
> **Layout:** Sidebar de navegação à esquerda (Agenda, Pacientes, Salas, Financeiro, Configurações). Área principal com cards de resumo no topo.
> **Cards de Resumo:**
> - Consultas Hoje (Valor: 42 - ícone de calendário)
> - Faturamento Mensal (Valor: R$ 125.000 - ícone de cifrão, verde)
> - Taxa de Ocupação (Valor: 85% - gráfico de rosca)
> - Cancelamentos (Valor: 3 - vermelho)
> **Seção de Gráficos:**
> - Gráfico de barras: Atendimentos por Especialidade.
> - Gráfico de linha: Evolução do faturamento nos últimos 6 meses.
> **Tabela Recente:** Lista dos últimos 5 agendamentos (Paciente, Médico, Especialidade, Status, Valor).
> **Estilo:** Clean, profissional, uso de branco, cinza claro e detalhes em azul médico (Medical Blue #0077B6). Tipografia Inter.

## 2. Agenda do Médico (Calendário)
**Objetivo:** Gestão diária e semanal de consultas.
**Prompt:**
> Crie uma interface de calendário interativo para médicos.
> **Layout:** Cabeçalho com seletor de data, filtros por status (Confirmado, Pendente, Realizado) e botão "Novo Agendamento".
> **Visualização:** Grade de calendário semanal (TimeGrid).
> **Eventos:** Blocos coloridos representando consultas.
> - Azul: Agendado
> - Verde: Confirmado
> - Cinza: Realizado
> - Vermelho: Cancelado
> **Detalhes do Evento:** Ao clicar, mostrar modal com foto do paciente, nome, tipo de consulta e histórico breve.
> **Funcionalidade:** Drag-and-drop para reagendar. Indicador de "Sala 04" dentro do bloco do evento.
> **Estilo:** Minimalista, foco na legibilidade. Fundo branco, linhas de grade sutis.

## 3. Mapa de Salas em Tempo Real
**Objetivo:** Visualização da ocupação das salas físicas.
**Prompt:**
> Crie um painel de visualização de salas (Room Map).
> **Layout:** Grid de cards representando as salas da clínica.
> **Card de Sala:**
> - Título: "Sala 101 - Cardiologia"
> - Status atual: Badge "Ocupado" (Vermelho) ou "Livre" (Verde).
> - Ocupante atual: Foto e nome do Médico (Dr. Carlos) + Paciente em atendimento.
> - Próximo: Horário e nome do próximo paciente.
> - Ícones de recursos: Máquina de ECG, Maca, Computador.
> **Interação:** Botão "Designar Paciente" se livre.
> **Estilo:** Cards com sombra suave, bordas arredondadas. Uso claro de cores semânticas para status.

## 4. Painel de Chamada (Acessibilidade)
**Objetivo:** Tela de TV para sala de espera.
**Prompt:**
> Crie uma tela de TV para sala de espera (Digital Signage).
> **Destaque Principal:** Área central gigante mostrando a última chamada.
> - Texto enorme: "PEDRO ALVES"
> - Subtexto: "DIRIJA-SE À SALA 04"
> - Foto/Nome do médico ao lado.
> **Histórico:** Lista lateral direita com os últimos 3 chamados (menor destaque).
> **Rodapé:** Notícias ou mensagens institucionais em scroll horizontal (ticker).
> **Acessibilidade:** Alto contraste (Fundo azul escuro, texto branco/amarelo). Fontes grandes e legíveis.

---

## 5. Contexto de UX (Jornadas e Navegação)

### Mapa de Navegação
- **Login** -> **Dashboard Admin**
- **Dashboard Admin** -> **Agenda** | **Pacientes** | **Salas** | **Financeiro**
- **Agenda** -> **Novo Agendamento** (Modal) -> **Confirmação**
- **Pacientes** -> **Prontuário** -> **Histórico**

### Jornadas do Usuário (Wireframes via Stitch)
1.  **Recepcionista:** Login -> Visualiza Mapa de Salas -> Verifica Sala Livre -> Abre Agenda -> Marca Consulta -> Confirma.
2.  **Médico:** Login -> Visualiza Agenda do Dia -> Clica no Paciente -> Vê Histórico -> Chama Paciente (Painel).
3.  **Admin:** Login -> Dashboard -> Analisa Faturamento -> Ajusta Valores.

> *Obs: Os prompts acima geram os protótipos de alta fidelidade que validam estas jornadas.*

