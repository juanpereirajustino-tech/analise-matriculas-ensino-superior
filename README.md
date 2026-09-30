# Análise de Matrículas no Ensino Superior --- 2019 a 2024

## Sobre o projeto

Este projeto foi desenvolvido como atividade universitária de análise de
dados utilizando dados abertos governamentais e o Power BI.

O objetivo é analisar a evolução das matrículas no ensino superior
brasileiro entre **2019 e 2024**, considerando modalidade de ensino,
rede de ensino, grau acadêmico e sexo.

## Fonte dos dados

Os dados utilizados são provenientes do **Censo da Educação Superior**,
disponibilizado pelo **Instituto Nacional de Estudos e Pesquisas
Educacionais Anísio Teixeira (INEP)**.

-   Órgão responsável: INEP
-   Tema: Educação Superior
-   Período analisado: 2019 a 2024
-   Formato: CSV

O arquivo CSV utilizado está na pasta `dados/`.

## Ferramentas utilizadas

-   **Power BI Desktop** --- análise e visualização
-   **DAX** --- criação de medidas
-   **GitHub** --- documentação e armazenamento
-   **CSV** --- conjunto de dados

## Perguntas da análise

### 1. Como evoluiu o número total de matrículas no ensino superior entre 2019 e 2024?

Foi criado um gráfico de linha com o total de matrículas por ano.

O resultado mostra uma tendência de crescimento no total de matrículas
durante o período, especialmente nos anos finais.

### 2. Qual foi a participação das matrículas EAD entre 2019 e 2024?

Foi calculado o percentual de matrículas EAD em relação ao total.

A análise mostra crescimento contínuo da participação do ensino a
distância, passando de aproximadamente **24% em 2019 para mais de 50% em
2024**.

### 3. Como evoluiu a participação da rede pública nas matrículas?

Foi calculado o percentual de matrículas da rede pública em relação ao
total.

A visualização indica oscilações no início da série e redução da
participação nos anos finais, chegando a aproximadamente **15% em
2024**.

### 4. Como as matrículas estão distribuídas por grau acadêmico?

Foi utilizado um gráfico de barras para comparar o total de matrículas
por grau acadêmico.

As categorias encontradas são:

-   Bacharelado
-   Tecnólogo
-   Licenciatura
-   Não se aplica

O **bacharelado** concentra a maior quantidade de matrículas, seguido
por **tecnólogo** e **licenciatura**.

### 5. Qual foi a participação das mulheres nas matrículas entre 2019 e 2024?

Foi criada uma medida para calcular o percentual de matrículas femininas
em relação ao total.

Também foi utilizado um gráfico de matrículas por sexo e ano para
complementar a análise.

## Medidas DAX

### Total de Matrículas

``` dax
Total Matrículas =
SUM(matriculas_inep[n_matricula])
```

### Percentual de Matrículas EAD

``` dax
% Matrículas EAD =
DIVIDE(
    [Matrículas EAD],
    [Total Matrículas],
    0
)
```

### Percentual de Matrículas Públicas

``` dax
% Matrículas Públicas =
DIVIDE(
    CALCULATE(
        [Total Matrículas],
        matriculas_inep[tp_rede] = "Pública"
    ),
    [Total Matrículas],
    0
)
```

### Percentual de Matrículas Femininas

``` dax
% Matrículas Femininas =
DIVIDE(
    CALCULATE(
        [Total Matrículas],
        matriculas_inep[sexo] = "Feminino"
    ),
    [Total Matrículas],
    0
)
```

## Visualizações

O dashboard contém:

1.  Evolução das matrículas no ensino superior;
2.  Participação das matrículas EAD;
3.  Participação das matrículas da rede pública;
4.  Matrículas por grau acadêmico;
5.  Participação das matrículas femininas;
6.  Indicador de total de matrículas.

## Estrutura do repositório

``` text
analise-matriculas-ensino-superior/
├── README.md
├── dados/
│   └── matriculas_inep.csv
├── imagens/
│   └── dashboard.png
└── powerbi/
    └── analise_matriculas_ensino_superior.pbix
```

## Conclusão

A análise de 2019 a 2024 evidencia crescimento do número total de
matrículas e forte expansão da participação do ensino a distância.
Também foi observada redução da participação relativa da rede pública
nos anos finais da série.

Na análise por grau acadêmico, o bacharelado apresenta a maior
quantidade de matrículas. A análise por sexo complementa o estudo ao
mostrar a participação feminina ao longo do período.

## Arquivos do projeto

-   `dados/` --- conjunto de dados em CSV.
-   `powerbi/` --- relatório desenvolvido no Power BI.
-   `imagens/` --- imagem do dashboard.

------------------------------------------------------------------------

**Projeto acadêmico --- Análise de Dados com Power BI e Dados Abertos
Governamentais**
