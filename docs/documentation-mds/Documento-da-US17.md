# Documento de estudo da US04

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


## Conceitos decorrentes da matriz

### Acurácia
Diz quanto o meu modelo acertou das previsões possíveis. Ou seja, é a razão entre o somatório das previsões corretas (TP + FP) sobre o somatório das previsões:

```
Acurácia = (TP+TN)/(TP+FP+TN+FN)
```
### Recall
Consiste a proporção de positivos que foram identificados corretamente. É definido como a razão entre verdadeiros positivos sobre a soma de verdadeiros positivos com negativos falsos.

```
Recall = TP/(TP+FN)
```

### Precisão
A precisão diz respeito a proporção de identificações positivas que foram corretas. Em outras palavras, o qual bem meu modelo trabalhou.

```
Precisão = TP/(TP+FP)
```

### F Score
Já o f-score nos mostra o balanço entre a precisão e o recall do modelo de classificação. É representado por:

```
F-score = 2*(precision+)
```

### Peguntas

1) O que é matriz de confusão?
2) Como saber se o modelo fez uma classificação correta?
3) Como avaliar a classificação?
4) Como é feita a avaliação do modelo?
5) Quais são as métricas usadas para avaliar a classificação?
6) O que é a acurácia?
7) O que é o recall?
8) O que é a precisão?
9) O que é o f-score? 

