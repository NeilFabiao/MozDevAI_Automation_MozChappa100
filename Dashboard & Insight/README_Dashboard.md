# 📊 Part 2 — MozChapa100 Dashboard

# 🎯 Objetivo

Mostrar, de forma prática e interativa, como transformar dados limpos em **insights estratégicos** através de um dashboard analítico em Excel.

A STELA assume a componente de visualização e análise, construindo um dashboard que responde a perguntas reais de negócio da MozChapa100.

---

# 🌍 Contexto

## MozChapa100 — Dashboard Operacional

Com o dataset já limpo e validado pelo NEIL, a STELA constrói o dashboard que serve como **output final para o negócio**.

O dashboard cobre **3 meses de operação** (Março, Abril e Maio de 2026) e responde a:

- Como evoluiu a receita mês a mês?
- Quais os segmentos de passageiros mais rentáveis?
- Quais as rotas de melhor e pior desempenho?
- Como se compara a performance diária ao longo dos meses?

---

# 🔁 Posição no Pipeline

```text
Excel (dados brutos + erros injectados)
        ↓
Python (geração + simulação de dados)
        ↓
SQL (limpeza + validação + agregação)
        ↓
Dataset Final (analytics-ready)
        ↓
Excel Dashboard ← ESTAMOS AQUI
```

---

# ⚡ Conceito: Dashboard Inteligente

> "Não é só um gráfico bonito — é uma ferramenta de decisão."

A STELA constrói análises que permitem aos estudantes:

- interpretar tendências operacionais
- identificar top e bottom performers
- calcular variações mês a mês
- apresentar recomendações estratégicas

---

# 📁 Estrutura do Dashboard

O ficheiro `MozChapa100_Dashboard.xlsx` contém **4 folhas** independentes:

---

## 📊 Folha 1 — Dashboard Principal

Vista executiva com todos os KPIs num único ecrã.

| Secção | Conteúdo |
|--------|----------|
| KPI Cards | Receita total, Viagens, Passageiros, Bilhetes vendidos (Mar–Mai) |
| Tabela MoM | Performance mês a mês para todas as métricas |
| Segmentos | Receita por Estudante / Trabalhador / Turista |
| Rotas | Ranking e quota de mercado por rota |
| Pagamentos | Mix de receita por M-Pesa / e-Mola / Numerário |

---

## 📅 Folha 2 — MoM Analysis

Análise aprofundada de variação mês a mês para cada métrica.

### Colunas presentes em cada bloco:

| Coluna | Descrição |
|--------|-----------|
| Maio (M3) | Valor absoluto do mês mais recente |
| Abril (M2) | Valor do mês anterior |
| Março (M1) | Valor do mês base |
| M3 vs M2 % | Variação percentual Maio vs Abril |
| M2 vs M1 % | Variação percentual Abril vs Março |
| M3 vs M2 Abs | Diferença absoluta Maio vs Abril |
| M2 vs M1 Abs | Diferença absoluta Abril vs Março |
| Daily Avg M3 | Média diária de Maio |
| Daily Avg M2 | Média diária de Abril |

### Métricas analisadas:
- Receita (MZN)
- Viagens
- Passageiros
- Bilhetes Vendidos

Cada bloco inclui desagregação por **segmento** (Estudante, Trabalhador, Turista).

---

## 📈 Folha 3 — Daily Trends

Evolução diária de todas as métricas ao longo dos 92 dias de operação.

### Tabela de dados (Colunas B–F):

| Coluna | Conteúdo |
|--------|----------|
| B | Data (formato DD MMM YYYY) |
| C | Receita (MZN) |
| D | Viagens |
| E | Passageiros |
| F | Bilhetes Vendidos |

### Gráficos incluídos:

| Gráfico | Tipo | Cor |
|---------|------|-----|
| Daily Revenue | Linha | 🟠 Laranja |
| Daily Trips | Linha | 🔵 Ciano |
| Daily Passengers | Linha | 🟢 Verde |
| Daily Tickets Sold | Barras | 🟡 Dourado |

> Todos os gráficos cobrem o período de **1 Março a 31 Maio 2026**.

---

## 🏆 Folha 4 — Performers

Identificação de rotas com melhor e pior desempenho.

| Tabela | Critério |
|--------|----------|
| Top Performers | Rotas com maior receita em Maio |
| Bottom Performers | Rotas com menor receita em Maio |
| Maior Declínio MoM | Rotas com maior queda Maio vs Abril |
| Maior Crescimento MoM | Rotas com maior crescimento Maio vs Abril |

Cada tabela inclui receita dos 3 meses + variação % + variação absoluta.

---

# 📖 Descrição das Métricas

| Métrica | Descrição |
|---------|-----------|
| Receita (MZN) | Receita total gerada pela venda de bilhetes |
| Viagens | Número de viagens realizadas |
| Passageiros | Total de passageiros transportados |
| Bilhetes Vendidos | Quantidade total de bilhetes emitidos |
| Daily Avg | Média diária calculada com base nos dias reais do mês |
| M3 vs M2 % | `(M3 / M2) - 1` — variação relativa |
| Abs Diff | `M3 - M2` — variação absoluta |

---

# ⚠️ Notas de Interpretação

## Dados do Período

| Mês | Dias | Receita Total (MZN) |
|-----|------|---------------------|
| Março 2026 (M1) | 31 | 10.397.840 |
| Abril 2026 (M2) | 30 | 10.089.640 |
| Maio 2026 (M3) | 31 | 9.609.400 |

> 📉 Tendência de declínio mês a mês — ponto de análise estratégica para a sessão.

## Segmentos

| Segmento | Perfil |
|----------|--------|
| Estudante | Passageiros com tarifas reduzidas |
| Trabalhador | Principal segmento operacional |
| Turista | Segmento de maior variabilidade |

## Rotas

| Rota | Característica |
|------|----------------|
| Matola – Boane | Rota mais longa, alta receita em Março |
| Maputo Centro – KaMavota | Rota urbana, crescimento em Abril |
| Maputo Centro – Machava | Volume consistente |
| Maputo Centro – Matola | Alta frequência |
| Machava – Marracuene | Rota periférica |

---

# 🚀 Resultado Final

Este dashboard demonstra a fase final do pipeline de dados da MozChapa100:

✔ dados limpos prontos para análise  
✔ KPIs executivos numa vista única  
✔ análise Month-on-Month completa  
✔ tendências diárias com gráficos  
✔ identificação de top e bottom performers  

---

# 💡 Questões para Discussão (NEIL & STELA)

Com base no dashboard, os estudantes devem ser capazes de responder:

1. **Qual o mês com maior receita? E o de menor?**
2. **Qual o segmento mais rentável em Maio?**
3. **Qual a rota com maior declínio MoM?**
4. **Qual o dia com pico de receita? O que pode ter acontecido?**
5. **A receita por viagem está a aumentar ou a diminuir?**
6. **Que recomendações farias à gestão da MozChapa100?**

---

# 📤 Ficheiro

```
MozChapa100_Dashboard.xlsx
├── 📊 Dashboard       → Vista executiva + KPIs
├── 📅 MoM Analysis    → Variação mês a mês detalhada
├── 📈 Daily Trends    → Evolução diária + 4 gráficos
└── 🏆 Performers      → Top & bottom performers por rota
```

---

# 🔗 Pipeline Completo

```text
Excel → Python → SQL → IA → Excel Dashboard
```

> Transformando dados brutos da MozChapa100 em **decisões inteligentes** para o grupo MozBikes através de IA e automação.
