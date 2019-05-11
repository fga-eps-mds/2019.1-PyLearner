# Documento de estudo da US06

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Feature Scaling

## O que é Feature Scaling?
O Feature Scaling é uma técnica para padronizar os recursos independentes presentes nos dados em um intervalo fixo. Ele é executado durante o pré-processamento de dados para lidar com magnitudes, valores ou unidades altamente variáveis. Se o dimensionamento de recurso não for feito, um algoritmo de aprendizado de máquina tende a pesar valores maiores, maiores e considera valores menores como os valores mais baixos, independentemente da unidade dos valores.

## Técnicas para execução do Feature Scaling

Min-Max Normalização: Esta técnica redimensiona um recurso ou valor de observação com valor de distribuição entre 0 e 1.

```
X = (Xi - min(x)) / (max(x) - min(x))
```

Padronização: É uma técnica muito eficaz que reescala um valor de recurso para que ele tenha distribuição com valor médio 0 e variância igual a 1.


```
X = (Xi - média) / desvio padrão 
```


### Implementação da normalização

```python
from sklearn import preprocessing
min_max_scaler = preprocessing.MinMaxScaler(feature_range =(0, 1))
x_after_min_max_scaler = min_max_scaler.fit_transform(dataSet) 
print ("\nAfter min max Scaling : \n", x_after_min_max_scaler)
```

### Implementação da padronização

```python
from sklearn import preprocessing
Standardisation = preprocessing.StandardScaler() 
x_after_Standardisation = Standardisation.fit_transform(x) 
print ("\nAfter Standardisation : \n", x_after_Standardisation) 
```


Perguntas:

1) O que é Feature Scaling?
2) Para que serve Feature Scaling?
3) O que ocorre caso não seja feito Feature Scaling?
4) O que é Min-Max Normalisation?
5) O que é Standardisation?
6) Quais são as técnicas utilizadas para Feature Scaling?
7) Qual a biblioteca mais comum para Feature Scaling?