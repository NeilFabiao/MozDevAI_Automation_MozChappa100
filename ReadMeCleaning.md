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

## MozBus Analytics

A MozBus é uma empresa de transporte de trabalhadores em Moçambique.

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
Excel (dados brutos)
        ↓
Jupyter Notebook (Python)
        ↓
SQL (limpeza e validação)
        ↓
Excel Dashboard (insights finais)
```
# 📊 1. Excel — Dados Brutos

O ponto de partida é um ficheiro Excel com dados operacionais da MozChapa100.

Este ficheiro representa o **registo diário de operações de transporte de trabalhadores**, usado para análise e tomada de decisão.

---

# ⚡ Conceito: Vibe Coding

> “Não vamos apenas escrever código — vamos construir soluções com IA, passo a passo, como um fluxo interativo.”

Os estudantes vão:
- completar código  
- corrigir erros  
- pensar como analistas  
- usar IA como assistente  


## 📁 Estrutura do Dataset

| dia | segmento | rota | Tipo_Pagamento | Bilhetes_Vendidos | Preco_Unitario_MZN | viagens | passageiros | duracao_min | atrasos_min | receita |
|------|-------------|----------|----------------|-------------------|-------------------|----------|-------------|-------------|-------------|---------|
| 1 | Trabalhadores | Maputo-A | Carteira Móvel | 480 | 50 | 12 | 480 | 35 | 5 | 24000 |
| 2 | Estudantes | Maputo-B | Cartão | 360 | 50 | 10 | 350 | 40 | 8 | 18000 |
| 3 | Turistas | Maputo-C | Dinheiro | 520 | 50 | 14 | 520 | 50 | 10 | 26000 |

## 📖 Valores Possíveis por Coluna

| Coluna | Exemplos de Valores |
|---------|-------------------|
| dia | 2025-01-01, 2025-01-02, 2025-01-03 |
| segmento | Trabalhadores, Estudantes, Turistas |
| rota | Maputo-A, Maputo-B, Maputo-C, Maputo-Xai-Xai, Maputo-Matola |
| Tipo_Pagamento | Dinheiro, Cartão, Carteira Móvel |
| Bilhetes_Vendidos | 120, 250, 480, 1000 |
| Preco_Unitario_MZN | 20, 30, 50 |
| viagens | 1, 5, 10, 20 |
| passageiros | 100, 350, 480, 1000 |
| duracao_min | 20, 35, 45, 60 |
| atrasos_min | 0, 5, 10, 20 |
| receita | 2400, 12000, 24000, 50000 |

## 📖 Descrição das Colunas

| Coluna | Descrição |
|---------|------------|
| dia | Data da operação |
| segmento | Tipo de passageiro (Trabalhadores, Estudantes ou Turistas) |
| rota | Rota utilizada pelo passageiro |
| Tipo_Pagamento | Método de pagamento utilizado |
| Bilhetes_Vendidos | Quantidade total de bilhetes vendidos |
| Preco_Unitario_MZN | Preço unitário do bilhete em Meticais |
| viagens | Número de viagens realizadas na rota |
| passageiros | Número total de passageiros transportados |
| duracao_min | Duração média da viagem em minutos |
| atrasos_min | Atraso médio registado em minutos |
| receita | Receita total gerada pela venda de bilhetes |


