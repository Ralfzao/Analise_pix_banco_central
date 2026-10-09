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



Etapas do projeto

1. Extração e tratamento dos dados do Banco Central
   Os dados foram extraídos por meio da API pública do Banco Central utilizando
   a biblioteca requests.
   A resposta em JSON foi transformada em um DataFrame utilizando Pandas.
   Foram realizadas verificações de tipos, valores ausentes, registros duplicados
   e estrutura da base.
2. Preparação dos dados do IBGE
   A planilha de estimativa populacional de 2026 foi importada utilizando Pandas.
   O código completo do município foi criado a partir dos códigos da UF e do
   município fornecidos pelo IBGE.
3. Definição do período
   Foi utilizado setembro de 2026 como período de referência para a análise.
   Após uma nova consulta à API, foram obtidos dados de todos os 5.571 municípios
   presentes na base populacional.
   Um registro sem identificação municipal foi desconsiderado apenas na análise
   por município.
4. Integração das bases
   Os dados do Banco Central e do IBGE foram relacionados utilizando o código
   IBGE do município.
   O resultado final apresentou correspondência populacional para todos os
   5.571 municípios analisados.
5. Criação de indicadores
   Foram criados os seguintes indicadores:

- valor de PIX enviado por habitante;
- quantidade de transações PIX enviadas por habitante.
  Para evitar dupla contagem, foram consideradas as operações dos pagadores
  pessoa física e pessoa jurídica.

6. Análise de valores extremos
   Foram encontrados municípios com movimentações muito acima da maior parte
   da distribuição.
   Esses registros foram preservados na base, porém os municípios acima do
   percentil 99 do valor de PIX por habitante foram desconsiderados nos rankings
   principais para reduzir distorções.
7. Resultados
   Entre os municípios considerados no ranking sem os valores extremos:

- Porto Real (RJ) apresentou o maior valor de PIX enviado por habitante;
- Mamborê (PR) apresentou a maior quantidade de transações PIX por habitante.
  Os resultados mostram que valor financeiro movimentado e quantidade de
  transações representam comportamentos diferentes.
  Um município pode movimentar grandes valores sem necessariamente apresentar
  a maior quantidade de operações.
  Visualizações
  Foram criados gráficos com:
- os 10 municípios com maior valor de PIX por habitante;
- os 10 municípios com maior quantidade de transações PIX por habitante.
  Notebooks
  analise_pix_bcb.ipynb
  Extração, tratamento e validação inicial dos dados do Banco Central.
  analise_pix_populacao.ipynb
  Integração com os dados populacionais do IBGE, criação de indicadores,
  análise de outliers, rankings e visualizações.
  Possíveis evoluções
  O projeto pode ser expandido futuramente com:
- comparação entre diferentes meses;
- análise por estado e região;
- mapas geográficos;
- dashboard em Power BI;
- análise da evolução temporal do PIX.
  Autor
  Projeto desenvolvido como parte dos meus estudos e portfólio em Análise de Dados.
