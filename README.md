# Análise de Dados de Transações PIX

# Análise de Dados de Transações PIX

Projeto de análise de dados desenvolvido em Python utilizando dados públicos disponibilizados pelo Banco Central do Brasil.

## Objetivo

O objetivo deste projeto é praticar um fluxo básico de análise de dados, desde a extração das informações por meio de uma API pública até o tratamento, validação e armazenamento dos dados.

## Fonte dos dados

Os dados foram obtidos por meio da API pública do Banco Central do Brasil, utilizando a base de transações PIX por município.

## Tecnologias utilizadas

- Python
- Pandas
- Requests
- Jupyter Notebook
- API REST
- JSON
- CSV
- Apache Parquet

## Etapas do projeto

### 1. Extração dos dados

Foi utilizada a biblioteca `requests` para realizar uma requisição HTTP à API pública do Banco Central.

Os dados retornados pela API foram recebidos em formato JSON.

### 2. Conversão para DataFrame

Os registros retornados foram transformados em um DataFrame com a biblioteca Pandas.

A base utilizada possui:

- 100.000 registros
- 19 colunas

### 3. Análise inicial

Foram realizadas verificações de:

- tipos das variáveis;
- valores ausentes;
- registros duplicados;
- estrutura do conjunto de dados.

### 4. Tratamento dos dados

Foram realizados os seguintes tratamentos:

- remoção de espaços extras dos nomes das colunas;
- limpeza dos campos de texto;
- conversão dos códigos IBGE para números inteiros.

### 5. Validação

Após os tratamentos, os dados foram novamente verificados.

Foram identificados alguns valores ausentes relacionados aos códigos de localização. Esses registros foram mantidos para evitar a exclusão de informações sem uma análise mais detalhada sobre sua origem.

Não foram identificados registros duplicados.

### 6. Armazenamento

Os dados tratados foram exportados nos formatos:

- CSV
- Apache Parquet

O arquivo Parquet também foi validado por meio de uma nova leitura utilizando Pandas.

## Estrutura do projeto

```text
Analise_pix_banco_central/
├── data/
│   ├── raw/
│   │   ├── bcb_tabela.csv
│   │   └── estimativa_dou_2026.xlsx
│   └── processed/
│       ├── dados_tratados.csv
│       └── dados_tratados.parquet
├── notebooks/
│   └── analise_pix_bcb.ipynb
├── README.md
└── requirements.txt
```

Projeto de análise de dados desenvolvido em Python utilizando dados públicos disponibilizados pelo Banco Central do Brasil.

## Objetivo

O objetivo deste projeto é praticar um fluxo básico de engenharia e análise de dados, desde a extração das informações por meio de uma API pública até o tratamento, validação e armazenamento dos dados.

## Fonte dos dados

Os dados foram obtidos através da API pública do Banco Central do Brasil, utilizando a base de transações PIX por município.

## Tecnologias utilizadas

- Python
- Pandas
- Requests
- Jupyter Notebook
- API REST
- JSON
- CSV
- Apache Parquet

## Etapas do projeto

### 1. Extração

A biblioteca `requests` foi utilizada para realizar uma requisição HTTP à API pública do Banco Central.

Os dados retornados pela API foram recebidos em formato JSON.

### 2. Conversão dos dados

Os registros retornados foram transformados em um DataFrame utilizando a biblioteca Pandas.

A extração utilizada no projeto possui:

- 100.000 registros
- 19 colunas

### 3. Análise inicial

Foram realizadas verificações de:

- tipos das variáveis;
- valores ausentes;
- registros duplicados;
- estrutura do conjunto de dados.

### 4. Tratamento dos dados

Entre os tratamentos realizados estão:

- remoção de espaços extras dos nomes das colunas;
- limpeza dos campos de texto;
- conversão dos códigos IBGE para números inteiros.

### 5. Validação

Após os tratamentos, foram verificadas novamente:

- tipagem das colunas;
- existência de valores nulos;
- existência de registros duplicados.

Foram identificados alguns valores ausentes relacionados aos códigos de localização. Esses registros foram mantidos para evitar a exclusão de informações sem uma análise mais detalhada sobre sua origem.

### 6. Armazenamento

Os dados tratados foram exportados nos formatos:

- CSV
- Apache Parquet

O formato Parquet também foi testado através de uma nova leitura utilizando Pandas.

## Estrutura do projeto

```text
analise-pix-banco-central/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   └── analise_pix_bcb.ipynb
├── README.md
└── requirements.txt
```
