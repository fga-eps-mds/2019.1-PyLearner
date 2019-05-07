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
