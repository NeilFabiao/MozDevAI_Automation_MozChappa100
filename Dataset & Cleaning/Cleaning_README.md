## Part 1 MozChapa100

# 🎯 Objetivo

Mostrar, de forma prática e interativa, como podemos usar:

- Excel  
- Python (Jupyter Notebook)  
- SQL  
- Inteligência Artificial (Gemini ou Copilot)  

para automatizar processos de dados no contexto de transporte de trabalhadores.

---

# 🌍 Contexto da Empresa

## MozChappa100 Analytics

A MozChappa100 é uma empresa de transporte de trabalhadores em Moçambique.

Ela gere operações diárias como:

- Número de passageiros transportados  
- Rotas mais usadas  
- Tempo médio de viagem  
- Pagamentos por viagem ou por mês  
- Ocupação dos autocarros  
- Segmentos dos passageiros  

---

# 🔁 Fluxo do Projeto

```text
Excel (dados brutos + erros injectados)
        ↓
Python (geração + simulação de dados)
        ↓
SQL (limpeza + validação + agregação)
        ↓
Dataset Final (analytics-ready)
        ↓
Excel Dashboard (insights)
```

---

# ⚡ Conceito: Vibe Coding

> “Não vamos apenas escrever código — vamos construir soluções com IA, passo a passo, como um fluxo interativo.”

Os estudantes vão:
- completar código  
- corrigir erros  
- pensar como analistas  
- usar IA como assistente  

---

# 📊 1. Excel — Dados Brutos

O ponto de partida é um ficheiro Excel com dados operacionais da MozChapa100.

Este ficheiro representa o registo diário de operações de transporte de trabalhadores, usado para análise e tomada de decisão.

---

## 📁 Estrutura do Dataset (Final de Negócio)

| dia | segmento | rota | Tipo_Pagamento | Bilhetes_Vendidos | Preco_Unitario_MZN | viagens | passageiros | duracao_min | atrasos_min | receita |
|------|-------------|----------|----------------|-------------------|-------------------|----------|-------------|-------------|-------------|---------|
| 2026-03-01 | Trabalhadores | Maputo-A | Carteira Móvel | 480 | 50 | 12 | 480 | 35 | 5 | 24000 |
| 2026-03-02 | Estudantes | Maputo-B | Cartão | 360 | 50 | 10 | 350 | 40 | 8 | 18000 |
| 2026-03-03 | Turistas | Maputo-C | Dinheiro | 520 | 50 | 14 | 520 | 50 | 10 | 26000 |

---

# ⚠️ Problemas Introduzidos no Dataset (Simulação de Erros)

Durante a geração dos dados foram injectados 3 tipos de erros para simular problemas reais:

## 1. NEGATIVO
- Valores numéricos negativos em colunas como:
  - Bilhetes_Vendidos  
  - Preco_Unitario_MZN  
  - passageiros  
  - receita  

👉 Exemplo: `-480 → 480`

---

## 2. ESPAÇOS EXTRA
- Strings com espaços no início ou fim:

👉 Exemplo:
```
" M-Pesa "
```

---

## 3. DATA_ERRADA
- Datas convertidas para datetime com hora incluída:

👉 Exemplo:
```
2026-03-01 14:35:00
```

---

# 🐍 2. Python — Geração do Dataset

O dataset foi criado usando Python com:

- openpyxl para Excel
- random para simulação
- regras de negócio
- injecção controlada de erros

### Características:
- múltiplos segmentos (Trabalhadores, Estudantes, Turistas)
- múltiplas rotas
- diferentes métodos de pagamento
- simulação de operações reais

---

# 🧹 3. SQL — Limpeza e Transformação

Após carregar os dados no SQL, foram aplicadas transformações:

---

## ✔️ Limpeza aplicada

### 🔴 Remoção de valores negativos
```sql
ABS(column)
```

---

### 🔵 Remoção de espaços
```sql
TRIM(Forma_Pagamento)
```

---

### 🟢 Correção de datas
```sql
DATE(dia)
```

---

## ✔️ Criação do dataset limpo

```sql
CREATE TABLE MOZ_DEV_MOZCHAPPA100_CLEAN AS
SELECT
    DATE(dia) AS dia,
    segmento,
    rota,
    TRIM(Forma_Pagamento) AS Forma_Pagamento,
    ABS(Bilhetes_Vendidos) AS Bilhetes_Vendidos,
    ABS(Preco_Unitario_MZN) AS Preco_Unitario_MZN,
    ABS(viagens) AS viagens,
    ABS(passageiros) AS passageiros,
    ABS(duracao_min) AS duracao_min,
    ABS(receita) AS receita
FROM MOZ_DEV_MOZCHAPPA100_STELA_NEIL_ANALYSIS;
```

---

# 📊 4. Dataset Final — Analytics Ready

O dataset final já está pronto para análise:

- sem negativos  
- sem espaços  
- datas limpas  
- valores consistentes  
- pronto para Power BI / Excel  

---

# 📤 5. Exportação para Excel

O dataset final foi exportado para análise:

```python
df.to_excel("MozChapa100_CLEAN.xlsx", index=False)
```

---

# 📈 6. Casos de Uso

Com este dataset podemos responder:

- Quantos passageiros são transportados por dia  
- Quais segmentos usam mais o serviço  
- Quais rotas são mais rentáveis  
- Onde existem atrasos operacionais  
- Eficiência geral do sistema  

---

# 🚀 Resultado Final

Este projeto demonstra um pipeline completo:

✔ geração de dados  
✔ simulação de erros reais  
✔ limpeza com SQL  
✔ transformação de dados  
✔ exportação para análise  

---

# 💡 Conclusão

Este exercício simula um ambiente real de data engineering onde:

- dados nunca vêm perfeitos  
- limpeza é obrigatória  
- SQL é fundamental  
- Python automatiza geração  
- Excel é o output final para negócio  
```
