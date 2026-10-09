# Análise de Transações PIX por Município

Projeto de portfólio em **Análise de Dados** desenvolvido em Python a partir de dados públicos do **Banco Central do Brasil** e de estimativas populacionais do **IBGE**.

O objetivo é comparar a utilização do PIX entre municípios brasileiros de diferentes tamanhos, transformando dados brutos em indicadores proporcionais à população e em insights mais comparáveis entre cidades.

## Visão geral

- **Período analisado:** setembro de 2026
- **Municípios analisados:** 5.571
- **Fontes:** Banco Central do Brasil + IBGE
- **Integração das bases:** código IBGE do município
- **Principais ferramentas:** Python, Pandas, Requests, Matplotlib e Jupyter Notebook

## Perguntas do projeto

O projeto foi desenvolvido para responder principalmente:

- Quais municípios movimentam mais valor de PIX por habitante?
- Quais municípios realizam mais transações de PIX por habitante?
- Valor financeiro movimentado e quantidade de transações apresentam o mesmo comportamento?
- Como valores extremos afetam os rankings municipais?

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

## Pipeline da análise

### 1. Extração dos dados do Banco Central

Os dados de transações PIX por município foram obtidos através da API pública do Banco Central do Brasil utilizando a biblioteca `requests`.

A resposta em JSON foi convertida em DataFrame com Pandas e passou por verificações de:

- tipos de dados;
- valores ausentes;
- registros duplicados;
- estrutura e consistência da base.

### 2. Preparação da base populacional

A estimativa populacional dos municípios brasileiros para 2026 foi importada com Pandas.

O código completo do município foi construído a partir dos códigos de UF e município fornecidos pelo IBGE, permitindo relacionar as duas fontes.

### 3. Integração das bases

As informações do Banco Central e do IBGE foram relacionadas pelo código IBGE.

A base final apresentou correspondência populacional para todos os **5.571 municípios** analisados.

### 4. Criação de indicadores

Foram construídos dois indicadores principais:

- **valor de PIX enviado por habitante**;
- **quantidade de transações PIX enviadas por habitante**.

Para evitar dupla contagem, foram consideradas as operações dos pagadores pessoa física e pessoa jurídica.

### 5. Tratamento de valores extremos

A análise identificou municípios com movimentações muito acima da maior parte da distribuição.

Esses registros foram preservados na base. Para os rankings principais, entretanto, municípios acima do **percentil 99 do valor de PIX por habitante** foram desconsiderados para reduzir distorções na comparação.

## Principais resultados

Entre os municípios considerados no ranking após o tratamento dos valores extremos:

- **Porto Real (RJ)** apresentou o maior valor de PIX enviado por habitante;
- **Mamborê (PR)** apresentou a maior quantidade de transações PIX por habitante.

O resultado mostra que **valor financeiro movimentado e quantidade de transações representam comportamentos diferentes**. Um município pode movimentar valores elevados sem necessariamente registrar a maior frequência de operações.

## Visualizações

Foram criados gráficos para comparar:

- os 10 municípios com maior valor de PIX por habitante;
- os 10 municípios com maior quantidade de transações PIX por habitante.

## Estrutura do repositório

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

## Notebooks

### `analise_pix_bcb.ipynb`

Extração, tratamento e validação inicial dos dados provenientes do Banco Central.

### `analise_pix_populacao.ipynb`

Integração com a base populacional do IBGE, criação dos indicadores, análise de outliers, rankings e visualizações.

## Como executar

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/Ralfzao/Analise_pix_banco_central.git
cd Analise_pix_banco_central
pip install -r requirements.txt
```

Em seguida, abra os notebooks da pasta `notebooks/` em Jupyter Notebook ou ambiente compatível.

## Possíveis evoluções

- comparação entre diferentes meses;
- análise por estado e região;
- mapas geográficos;
- dashboard em Power BI;
- análise da evolução temporal do PIX.

## Autor

**Matheus Opalenski**  
Em formação em Análise de Dados pela EBAC, com foco em SQL, Python, Pandas e visualização de dados.

Este projeto foi desenvolvido para fins de estudo e portfólio profissional em Análise de Dados.
