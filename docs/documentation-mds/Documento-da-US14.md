# Documento de estudo da US14

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Matriz de Correlação

## O que é uma Matriz de Correlação?
Em Probabilidade e Estatística, correlação é qualquer relação estatística(causal ou não causal) entre um par de itens ou varíaveis dentro de uma ampla classe de relações estatísticas que envolva dependência entre esse par de itens ou variáveis. Existem diversas maneiras de definir correlação, sendo a <b>Correlação de Pearson</b> o mais clássico. Os valores de correlação podem variar de -1 a +1. Se os dois itens ou variáveis tendem a aumentar ou diminuir juntos, a correlação é positiva.
<br>
A matriz de correlação possibilita a análise simultânea entre os itens ou variavéis.

## Matriz de Correlação em Python

### Uso de dados
Pode ser feito a partir de leitura de arquivo(s) .csv, .xls ou dataset, por exemplo.

### Segmentação das variáveis
A segmentação serve como uma forma de organizar os dados em sub-grupos homogêneos, gerando grupos que se correlacionam.


### Cálculo da correlação
Será feito usando a biblioteca de manipulação e análise de dados <i>Pandas</i>, que possui o método <i>.corr()</i> que nos retorna a correlação daqueles valores.

### Estrutura do Código
Existem diversas maneiras de se calcular correlação em Python, e usando diversas bibliotecas e funcionalidades. Usaremos a biblioteca <i>Pandas</i> para manipulação dos dados, e a biblioteca <i>csv</i> para leitura de arquivos .csv.

```python
import csv
import pandas as pd
import pandas.io.data

# importando o CSV para o dataframe
headers = ['Key', 'Value']
dataframe = pd.read_csv['test.csv', index_col='Key', parse_dates = True, names = headers]
# carrega os valores
value = dataframe['Value']
# calcula a correlação na varíavel corr
corr = dataframe.corr()
```
Este trecho de código visa elucidar através de um exemplo simples o cálculo de uma Matriz de Correlação em Python.
