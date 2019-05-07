# Documento de estudo da US7

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação.

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Métricas de Classificação

Avaliar o seu algoritmo de Machine Learning é uma parte essencial de qualquer projeto.Sua Model deve ter resultados satisfatórios quando avaliado usando a métrica Accuracy mas pode existir resultados ruins quando calculados contra outras métricas.
Na maioria das vezes,utilizamos a classificação Accuracy para medir a performace da Model,entretanto,não é possivel calcular perfeitamente e nesse documento,explicaremos alguns tipos de avaliação de métricas.

## Classificação Accuracy

Classificação Accuracy é a classificação da precisão do algoritmo de Machine Learning e é calculada pelo número total de predições certas dividido pelo número total de predições feitas.Só funciona bem se tiver um número igual de amostras pertencentes a cada classe

`Accuracy = Numero de predições certas/Numero total de predições feitas`

## Classificação F1

Classificação F1 é usada para media a precisão de um teste.F1 é a média harmônica entre a Precision e Recall.Ele fala o quão preciso é o seu classificador(quantas instâncias foram classificadas corretamente),assim como o quão robusto ele é(se não errou um número significativo de instâncias).Alta Precison e baixo Recall,oferece uma Accurate precisa mas em seguida perde um grande número de instâncias que são difíceis de classificar.Quanto maior a F1,melhor o desempenho da Model e matematicamente,pode ser expresso por:

`F1 = 2 * ( 1 / ( (1 / Precision) + (1/ Recall) ) )`

A f1 tenta achar o balanço entre a Precision e o Recall.

## Métricas de Classificação em Python

Utilizaremos o **Scikit Learn** e dentro dele há a biblioteca chamada **sklearn.metrics**,que é onde estão todas as funções necessárias para calcular as métricas de classificação.

### Clasificação Accuracy

Utilizaremos a função **accuracy_score()** :

```python
sklearn.metrics.accuracy_score(y_true, y_pred, normalize=True, sample_weight=None)
```

Seus parâmetros obrigatórios são:

**y_true**: 1d array-like ou matriz de indicador de rótulo / matriz esparsa,rótulos verdadeiros.

**y_pred**: 1d array-like ou matriz de indicador de rótulo / matriz esparsa
Rótulos previstos, conforme retornados por um classificador.

**normalize**: bool, opcional (padrão = True)
Se False, retorne o número de amostras classificadas corretamente. Caso contrário, retorne a fração de amostras classificadas corretamente.

A função tem como returno um **float**.Exemplo:

```python
>>> import numpy as np
>>> from sklearn.metrics import accuracy_score
>>> y_pred = [0, 2, 1, 3]
>>> y_true = [0, 1, 2, 3]
>>> accuracy_score(y_true, y_pred)
0.5
>>> accuracy_score(y_true, y_pred, normalize=False)
2
```

### Classificação F1

Utilizaremos a função **f1_score()**:

```python
sklearn.metrics.f1_score(y_true, y_pred, labels=None, pos_label=1, average=’binary’, sample_weight=None)
```

Seus parâmetros obrigatórios são:

**y_true**: 1d array-like ou matriz de indicador de rótulo / matriz esparsa,rótulos verdadeiros.

**y_pred**: 1d array-like ou matriz de indicador de rótulo / matriz esparsa
Rótulos previstos, conforme retornados por um classificador.

**pos_label**: str ou int, 1 por padrão
A classe a relatar se média = 'binária' e os dados forem binários. Se os dados forem multiclasse ou multilabel, isso será ignorado; setar rótulos = [pos_label] e média! = 'binary' informará as pontuações somente para esse rótulo.

**average** : string, [None, 'binary' (padrão), 'micro', 'macro', 'samples', 'weighted']
Este parâmetro é necessário para destinos multiclasse / multilabel. Se Nenhum, as pontuações para cada classe são retornadas. Caso contrário, isso determina o tipo de média executada nos dados:

_'binário'_ :
Apenas relatar resultados para a classe especificada por pos*label. Isso é aplicável somente se os destinos (y* {true, pred}) forem binários.

_'micro'_ :
Calcule as métricas globalmente contando o total de verdadeiros positivos, falsos negativos e falsos positivos.

_'macro'_ :
Calcule métricas para cada etiqueta e encontre a média não ponderada. Isso não leva em conta o desequilíbrio do rótulo.

_'weighted'_ :
Calcule métricas para cada etiqueta e encontre sua média ponderada pelo suporte (o número de instâncias verdadeiras para cada rótulo). Isso altera "macro" para explicar o desequilíbrio do rótulo; pode resultar em um F-score que não está entre precisão e recall.

_'samples'_ :
Calcule métricas para cada instância e encontre sua média (somente significativa para a classificação multilabel, onde isso difere de accuracy_score).

A função tem como retorno um **float**.Exemplo:

```python
>>> from sklearn.metrics import f1_score
>>> y_true = [0, 1, 2, 0, 1, 2]
>>> y_pred = [0, 2, 1, 0, 0, 1]
>>> f1_score(y_true, y_pred, average='macro')
0.26...
>>> f1_score(y_true, y_pred, average='micro')
0.33...
>>> f1_score(y_true, y_pred, average='weighted')
0.26...
>>> f1_score(y_true, y_pred, average=None)
array([0.8, 0. , 0. ])
```
