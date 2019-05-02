# Documento de estudo da US04

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Dados Faltantes

## O que são dados faltantes?
Consiste em valores vazios ou inesperados encontrados em um dataset antes da fase de pré processamento. Dentro do tratamento de dados para pré-processamento, a correção de dados faltantes é uma das tarefas que demandam maior tempo para preparação do modelo. Depois de coletado o dataset, é necessário essa limpeza de dados para que as predições sejam corretas posteriormente.
## Motivos para que haja valores faltantes
1) Houve esquecimento no preenchimento de um campo por um usuário

2) Dados perdidos quando transferidos manualmente de uma base de dados

3) Erro no programa

## Iniciando a detecção

Antes de limpar os dados, é recomendável agrupar os dados e responder perguntas como:

1) Quais são as features?

2) Quais são os tipos de dados esperados? (int, float, double, boolean e etc.)

3) Há dados faltantes facilmente detectáveis?

### Checar o dataset através da biblioteca Pandas

```python
import pandas as pd
arquivo = pd.read_csv("data property.csv")
print (arquivo.head())
```


```python
Exemplo de dataset:
   ST_NUM    ST_NAME OWN_OCCUPIED  NUM_BEDROOMS
0   104.0     PUTNAM            Y           3.0
1   197.0  LEXINGTON            N           3.0
2     NaN  LEXINGTON            N           3.0
3   201.0   BERKELEY          NaN           1.0
4   203.0   BERKELEY            Y           3.0
```

Então podemos ver o csv sendo importado para dentro do dataframe da biblioteca pandas.

### Features do dataset

>ST_NUM: Número da rua

>ST_NAME: Nome da rua

>OWN_OCCUPIED: Residência ocupada

>NUM_BEDROOMS: Número de banheiros

### Tipos esperados para cada feature

>ST_NUM: float or int

>ST_NAME: string

>OWN_OCCUPIED: string

>NUM_BEDROOMS: float or int

## Padrão de valores faltantes

Estes são os valores que o Pandas pode detectar. O Pandas quando imprime datasets com valores faltantes preenche com "NA" indicando que estes lugares estão vazios.

Com a função isnull(), é retornado verdadeiro caso haja um valor faltante e falso caso esteja de acordo para o valor.

```python
# Looking at the ST_NUM column
print df['ST_NUM']
print df['ST_NUM'].isnull()
Out:
0    104.0
1    197.0
2      NaN
3    201.0
4    203.0
5    207.0
6      NaN
7    213.0
8    215.0

Out:
0    False
1    False
2     True
3    False
4    False
5    False
6     True
7    False
8    False
```



## Valores faltantes não padronizados
É o caso onde há valores faltantes em diferente formatos.

```python
# Looking at the NUM_BEDROOMS column
print df['NUM_BEDROOMS']
print df['NUM_BEDROOMS'].isnull()
Out:
0      3
1      3
2    n/a
3      1
4      3
5    NaN
6      2
7     --
8     na

Out:
0    False
1    False
2    False
3    False
4    False
5     True
6    False
7    False
8    False
```
Como observa-se, não foram reconhecidos todos os valores faltantes pelo pandas.

Para corrigir o problema, é necessário criar uma lista com tipos de valores faltantes

```python
missing_values = ["n/a", "na", "--"]
df = pd.read_csv("property data.csv", na_values = missing_values)
```

## Corrigindo dados faltantes

### Substituindo por uma constante

```python
df['ST_NUM'].fillna(125, inplace = True)
```

### Imputação baseada no lugar

```python
df.loc[2,'ST_NUM'] = 125
```

### Subtituindo por mediana

```python
median = df['NUM_BEDROOMS'].median()
df['NUM_BEDROOMS'].fillna(median, inplace=True)
```
