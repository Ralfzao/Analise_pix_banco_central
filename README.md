# Análise de Transações PIX por Município

Projeto de análise de dados desenvolvido em Python utilizando dados públicos
do Banco Central do Brasil e estimativas populacionais do IBGE.

O projeto realiza desde a extração dos dados por API até a criação de indicadores
de utilização do PIX por habitante.

## Objetivo

Analisar a utilização do PIX nos municípios brasileiros e comparar municípios
de diferentes tamanhos populacionais utilizando indicadores proporcionais à população.

## Fontes dos dados

### Banco Central do Brasil

Dados de transações PIX por município obtidos por meio da API pública do
Banco Central do Brasil.

### IBGE

Estimativa populacional dos municípios brasileiros para 2026.

As duas bases foram relacionadas utilizando o código IBGE do município.

## Tecnologias utilizadas

- Python
- Pandas
- Requests
- Matplotlib
- Jupyter Notebook
- OpenPyXL
- API REST
- JSON
- CSV
- Apache Parquet

## Estrutura do projeto

```text
Analise_pix_banco_central/
├── data/
│   ├── raw/
│   │   ├── bcb_tabela.csv
│   │   └── estimativa_dou_2026.xlsx
│   └── processed/
│       ├── dados_tratados.csv
│       ├── dados_tratados.parquet
│       ├── pix_populacao_2026.csv
│       └── pix_populacao_2026.parquet
├── notebooks/
│   ├── analise_pix_bcb.ipynb
│   └── analise_pix_populacao.ipynb
├── README.md
└── requirements.txt
```
