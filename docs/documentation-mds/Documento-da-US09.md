# Documento de estudo da US09

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

## R<sup>2</sup> score

A função r2_score calcula o coeficiente de determinação R<sup>2</sup>. Esse coeficiente fornece uma métrica de quão bem as amostras futuras provavelmente serão previstas pelo modelo. A melhor pontuação possível é 1.0 e pode ser negativa (porque o modelo pode ser arbitrariamente pior). Essa métrica não é bem definida para amostras únicas e retornará um valor NaN se o número de amostras(n_samples) for menor que dois.

O valor R<sup>2</sup> estimado em n<sub>samples</sub> é definido como: 

![](https://i.imgur.com/PfmVLyM.png)

Exemplo de uso da função r2_score:

```python
from sklearn.metrics import r2_score
y_true = [3, -0.5, 2, 7]
y_pred = [2.5, 0.0, 2, 8]
r2_score(y_true, y_pred)  

y_true = [[0.5, 1], [-1, 1], [7, -6]]
y_pred = [[0, 2], [-1, 2], [8, -5]]
r2_score(y_true, y_pred, multioutput='variance_weighted')


y_true = [[0.5, 1], [-1, 1], [7, -6]]
y_pred = [[0, 2], [-1, 2], [8, -5]]
r2_score(y_true, y_pred, multioutput='uniform_average')


r2_score(y_true, y_pred, multioutput='raw_values')


r2_score(y_true, y_pred, multioutput=[0.3, 0.7])
```