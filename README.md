# IA_ML_processo_ETL_para_WEKA

## Contexto
Esse processo de etl foi desenvolvido para tratar uma amostra de base de dados (PNAD) a fim de preparar o arquivo qeu irá ser carregado no software WEKA e repsonder algumas questões sobre alguns algoritmos (Apriori, J48 e LinearProgression).

## Requisitos para execução
Pra executar o código é necessário ter:
- Python 3
    - Biblioteca Pandas
    - Biblioteca psycopg2
- Banco de dados Postgre

## Linha de desenvolvimento
O processo de ETL foi realizado em **Python** em um notebook **Jupyter** e utilizando as bibliotecas **pandas** e **psycopg2**.
Inicialmente a ideia do código era realizar o processo ETL em pandas e realizar uma conexão com o banco de dados Postgre, subir um arquivo csv para esse banco e coenctar o WEKA no Postgre através da conexão JDBC, no momento de desenovolvimento não consegui realizar a conexão do banco com o weka, por esse motivo o código contém todo o código de conexão com o banco de dados, criação das tabelas e inserção dos dados, mas a execução dessos métodos referente a essa etapa estão comentados (porém funcionando corretamente).

Visto isso foi feito uma etapada alternativa para utilizar os arquivos no weka, sendo, dois métodos que pegamo os arquivos csv's e eles são tratados e salvos em um pasta como arquivo csv's para serem utilizados no weka.

No final para cada arquivo csv selecionado 2 novos arquivos são criados, isso porque para utilizar o algoritmio apriori o weka exige que os dados sejam do tipo nominal, então é criado um arquivo csv onde somente dados do tipo nominal estão incluídos, e um outro arquivo é criado para executar o algoritmo linear regression que exige dados do tipo numeric.

O processo de ETL consiste em 5 etapas, sendo elas:
- Exclusão da coluna índice ("Unnamed: 0").
- Coreção de uma quebra de linha da coluna "RM_RIDE".
- Exclusão de todas as colunas onde só tenham valores nulos.
- Filtro de apenas 5 estados da coluna "UF".
- Separa em dois arquivos csv um com dados do tipo "NOMINAL" e outra com tipo "NUMERIC" (Essa ultima tem impacto ao importar para o weka)
