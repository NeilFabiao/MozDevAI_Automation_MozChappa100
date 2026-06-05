# 🚀 Automação de Processos com IA e Scripts
## Do Excel ao Dashboard Inteligente — MozChapa100 · MozBikes
![Pipeline](Dataset%20%26%20Cleaning/img1.png)

---

## 🎯 Pitch da Sessão

A sessão começa com o **Excel como ponto de entrada dos dados**, explicando que na vida real os dados chegam de várias fontes e formatos, muitas vezes desorganizados.

Fazemos a **ingestão de 3 ficheiros diferentes**, simulando um cenário real de operação da **MozChapa100** — a unidade de transporte de passageiros (chapas) do grupo MozBikes — e construímos um pipeline completo até ao dashboard.

---

## 🗂️ Estrutura do Repositório

```
📦 mozchapa100-pipeline
 ┣ 📓 Exercício_Criar_Dataset_COM_PROMPT.ipynb   ← Part 0: Geração de dados com erros
 ┣ 📓 Exercício_of_MozDev_Cleaning.ipynb         ← Part 1: Ingestão, SQL e limpeza
 ┗ 📁 Dataset & Cleaning/
 ┣ 📊 MozChapa100_Tutorial-Main.xlsx             ← Dashboard analítico final (STELA)
 ┗ 📁 Dashboard & Insight/
    ┗ img1.png
```

---

## 🛠️ Ferramentas Utilizadas

| Ferramenta | Papel no pipeline |
|---|---|
| **Excel** | Ponto de entrada dos dados e dashboard final |
| **Python (Jupyter / Colab)** | Geração, manipulação e automação |
| **pandas + openpyxl** | Leitura de ficheiros `.xlsx` e criação de DataFrames |
| **sqlite3 / JupySQL** | Base de dados local, JOINs, limpeza com SQL |
| **IA (Gemini / Claude)** | Copiloto de programação — *Vibe Coding* |

---

## 🗺️ Pipeline Completo

```
  📊 EXCEL            🐍 PYTHON            🗄️ SQL              📊 EXCEL
  (3 ficheiros)  ──►  (pandas)       ──►  (SQLite)      ──►  (Dashboard)

  Segmentos.xlsx      pd.read_excel()      CREATE TABLE        Tabela limpa
  Vendas.xlsx    ──►  .to_sql()       ──►  JOIN + GROUP  ──►  Gráficos
  Rotas.xlsx          limpeza              BY agregação        Insights

  [ENTRADA]           [INGESTÃO]           [ANÁLISE]           [SAÍDA]
```

---

## 📓 Notebooks — Guia de Conteúdo

### Part 0 — `Exercício_Criar_Dataset_COM_PROMPT.ipynb`
**Geração de dados simulados com erros propositados**

Este notebook cria os 3 ficheiros Excel que alimentam o pipeline, injectando 3 tipos de erros para simular dados reais de sistemas POS, ERP ou formulários manuais.

| # | Tipo de Erro | Exemplo errado | Exemplo correcto |
|---|---|---|---|
| 1 | **NEGATIVO** | `-15` bilhetes | `15` bilhetes |
| 2 | **ESPAÇOS** | `" M-Pesa "` | `"M-Pesa"` |
| 3 | **DATA ERRADA** | `2026-03-01 07:23:00` | `2026-03-01` |

As 3 tabelas geradas seguem o seguinte esquema relacional:

```
┌──────────────────┐     ┌───────────────────────────┐     ┌──────────────────┐
│    SEGMENTOS     │     │          VENDAS            │     │      ROTAS       │
├──────────────────┤     ├───────────────────────────┤     ├──────────────────┤
│ ID_Segmento (PK) │◄────│ ID_Segmento (FK)          │     │ ID_Rota (PK)     │
│ Tipo_Passageiro  │     │ ID_Rota (FK) ─────────────┼────►│ Origem           │
│ Genero           │     │ Data                      │     │ Destino          │
│ Faixa_Etaria     │     │ Forma_Pagamento ⚠️         │     │ Distancia_KM     │
│ Total_Passageiros│     │ Bilhetes_Vendidos ⚠️       │     │ Viagens_Realizadas│
│ Hora_Pico        │     │ Preco_Unitario_MZN ⚠️      │     │ Passageiros_Total │
└──────────────────┘     └───────────────────────────┘     └──────────────────┘
                                          ⚠️ = contém erros injectados
```

---

### Part 1 — `Exercício_of_MozDev_Cleaning.ipynb`
**Ingestão → SQL → Detecção → Limpeza**

Este notebook é o núcleo técnico do pipeline, estruturado em fases progressivas:

**1. Ingestão** — carregar os 3 Excel para SQLite (`header=1` para ignorar título decorativo na linha 0)

**2. JOIN analítico** — criar `MOZ_DEV_MOZCHAPPA100_STELA_NEIL_ANALYSIS` com `CREATE TABLE AS SELECT` agregando por data, segmento, rota e forma de pagamento

**3. Detecção de erros** — 3 queries SQL para identificar registos problemáticos antes de corrigir:

```sql
-- Erro 1: negativos
WHERE Bilhetes_Vendidos < 0 OR Preco_Unitario_MZN < 0

-- Erro 2: espaços
WHERE Forma_Pagamento != TRIM(Forma_Pagamento)

-- Erro 3: datas com timestamp
WHERE Data != DATE(Data)
```

**4. Correcção** — `ABS()` para negativos, `TRIM()` para espaços, `DATE()` para timestamps

**5. Exportação** — tabela limpa exportada para Excel para STELA

---

### Dashboard — `MozChapa100_Tutorial-Main.xlsx`
**Análise final em Excel — componente STELA**

O ficheiro Excel contém os dados operacionais limpos de Março 2026, com as seguintes dimensões:

- **Segmentos:** Estudante · Trabalhador · Turista
- **Rotas:** Maputo Centro–Matola · Matola–Boane · Machava–Marracuene · Maputo Centro–KaMavota · Maputo Centro–Machava
- **Métricas:** Bilhetes vendidos · Preço unitário (MZN) · Viagens · Passageiros · Duração (min) · Receita (MZN)
- **Pagamentos:** M-Pesa · e-Mola · Numerário

> 🎨 Convenção de cores: **Azul** = inputs · **Preto** = fórmulas · **Verde** = ligações entre folhas

---

## 🧠 Personas do Projecto

### NEIL — Pipeline Engineer
Responsável pela construção técnica: ingestão, SQL, limpeza, automação e exportação dos dados.

### STELA — Data Analyst
Responsável pela análise de negócio: dashboard Excel, análises Month-on-Month, top/bottom performers e insights estratégicos.

---

## ⚡ Desafios Vibe Coding

Os estudantes têm 2 desafios cronometrados onde usam IA como copiloto:

| Desafio | Tempo | Objectivo |
|---|---|---|
| Script de ingestão | 10 min | Carregar 3 Excel para SQLite com regras de qualidade |
| Queries de limpeza | 5 min | Detectar e corrigir os 3 tipos de erros com SQL |

---

## 💡 Resultado Esperado

No final, NEIL e STELA conduzem a fase de insights conjunta. Os estudantes devem interpretar os dados e apresentar:

- **Insights de negócio** — qual segmento e rota geram mais receita?
- **Problemas operacionais** — onde estão os atrasos e ineficiências?
- **Recomendações estratégicas** — acções concretas para MozChapa100 / MozBikes

---

## 🚀 Como Correr

```bash
# 1. Instalar dependências
pip install jupysql pandas openpyxl

# 2. Correr no Google Colab ou Jupyter
# Abrir Exercício_Criar_Dataset_COM_PROMPT.ipynb  → gera os ficheiros Excel
# Abrir Exercício_of_MozDev_Cleaning.ipynb        → pipeline completo

# 3. Abrir MozChapa100_Tutorial-Main.xlsx para o dashboard STELA
```

---

## 👤 Contacto

Repo owner: **Neil Fabião** → [@neilfabiao](https://github.com/neilfabiao) ✌🏾

![](https://komarev.com/ghpvc/?username=mozdevsfinalaiautomation&color=blue)
