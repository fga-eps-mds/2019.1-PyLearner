# Documento de estudo da US17

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Matriz de confusão

## O que é a matriz de confusão?
A Matriz de confusão consiste em uma mensuração da performance de classificação de um modelo em machine learning. 

## Representação da matriz de confusão
Consiste em uma tabela que mostra as frequências de classificação para cada classe do modelo, que são:

> True Positive (TP): ocorre quando no conjunto real, a classe que estamos buscando foi prevista corretamente.

> False Positive (FP): ocorre quando no conjunto real, a classe que estamos buscando prever foi prevista incorretamente.

> True Negative (TN): ocorre quando no conjunto real, a classe que não estamos buscando prever foi prevista corretamente.

> False Negative (FN): ocorre quando no conjunto real, a classe que não estamos buscando prever foi prevista incorretamente.

## Implementação da matriz de confusão

O Scikit-Learn fornece uma função confusion_matrix:

```python
from sklearn.metrics import confusion_matrix
y_actu = [2, 0, 2, 2, 0, 1, 1, 2, 2, 0, 1, 2]
y_pred = [0, 0, 2, 1, 0, 2, 1, 0, 2, 0, 2, 2]
confusion_matrix(y_actu, y_pred)

Output:

array([[3, 0, 0],
       [0, 1, 2],
       [2, 1, 3]])
```

Mas  também pode ser criado uma matriz de confusão usando Pandas:

```python
import pandas as pd
y_actu = pd.Series([2, 0, 2, 2, 0, 1, 1, 2, 2, 0, 1, 2], name='Actual')
y_pred = pd.Series([0, 0, 2, 1, 0, 2, 1, 0, 2, 0, 2, 2], name='Predicted')
df_confusion = pd.crosstab(y_actu, y_pred)

Output:

Predicted  0  1  2
Actual
0          3  0  0
1          0  1  2
2          2  1  3
```

### Peguntas

1) O que é matriz de confusão?
2) O que é verdadeiro positivo?
3) O que é verdadeiro negativo?
4) O que é falso positivo?
5) O que é falso negativo?
6) Como implementar a matriz de confusão?
7) Quais bibliotecas são usadas para gerar a matriz de confusão?

