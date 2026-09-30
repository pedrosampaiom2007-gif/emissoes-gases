# Emissões de Gases de Efeito Estufa no Brasil 🌎

Análise exploratória das emissões de gases de efeito estufa dos estados brasileiros (1970–2021) usando **pandas**, com foco em **seleção, filtragem e agrupamento de dados**.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pedrosampaiom2007-gif/emissoes-gases/blob/main/pandas_selecao_e_agrupamento.ipynb)

## 📊 Fontes de dados

| Base | Descrição | Fonte |
|---|---|---|
| `1-SEEG10_GERAL-BR_UF_2022.10.27-FINAL-SITE.xlsx` (aba `GEE Estados`) | Emissões por estado, setor, gás e ano | [SEEG – Observatório do Clima](http://seeg.eco.br/download) |
| `POP2022_Municipios.xls` | População por município | [Censo IBGE 2022](https://www.ibge.gov.br/estatisticas/sociais/saude/22827-censo-demografico-2022.html) |

## 🗂️ Etapas do notebook

1. **Leitura dos dados** – `read_excel()` e `info()`.
2. **Ajuste da base** – uso de `unique()`, máscaras booleanas (`&`, `|`), `isin()`, `loc[]` e `drop()` para manter apenas as linhas de *Emissão*.
3. **Mudança de formato** – `melt()` transforma as colunas de anos (formato *wide*) em uma coluna `Ano` e outra `Emissão` (formato *long*).
4. **Análise dos gases** – `groupby()`, `groups`, `get_group()`, `sort_values()`, `iloc[]` e gráfico de barras; cálculo da participação do CO2 no total.
5. **Emissão por setor** – índice de vários níveis (MultiIndex), `xs()`, `max()`, `idxmax()`, `insert()` e `swaplevel()` para descobrir o setor que mais emite cada gás e o gás mais emitido em cada setor.
6. **Emissão ao longo dos anos** – agregação por ano, `reset_index()`, `pivot_table()` e gráficos por gás.
7. **População dos estados** – limpeza de texto com `str.contains()`, `replace()` com regex, `assign()` e `astype()`.
8. **Unindo os dados** – `merge()` entre emissões (2021) e população, gráficos de dispersão e cálculo da **emissão per capita** com Plotly.

Cada célula de código traz um comentário curto explicando o que a função do pandas faz.

## ▶️ Como executar

1. Abra o notebook no Google Colab (botão acima).
2. Salve as duas planilhas no Google Drive em `MyDrive/Colab Notebooks/`.
3. Execute as células em ordem — a primeira monta o Drive no Colab.

Para rodar localmente, instale as dependências e ajuste os caminhos dos arquivos no `read_excel()`:

```bash
pip install pandas openpyxl xlrd matplotlib plotly
```

## 🛠️ Tecnologias

- Python 3
- pandas
- Matplotlib
- Plotly Express
- Google Colab
