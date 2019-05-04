# Documento de Estudo da US16

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Relatório de Classificação

### Como funciona o Relatório de Classificação

Após definir o que deseja que a máquina reconheça e passar os tipos de classificação,é necessário gerar o relatório de classificação,ou seja,como foi o desempenho da máquina.Por exemplo [Reconhecimento de digitos escritos à mão](https://scikit-learn.org/stable/auto_examples/classification/plot_digits_classification.html#sphx-glr-auto-examples-classification-plot-digits-classification-py), [Reconhecimento de faces](https://scikit-learn.org/stable/auto_examples/applications/plot_face_recognition.html#sphx-glr-auto-examples-applications-plot-face-recognition-py) e etc.
Após fazer esses reconhecimento,é necessário ver o relatório de classificação da máquina

## Como Checar os Resultados das Classificações

É necessário instalarmos o **sklearn**, e importaremos a biblioteca **classification_report**

```python
 from sklearn.metrics  import  classification_report
```

E após isso,podemos utilizar a função **classification_report** que é como visualizaremos as classificações

```python
classification_report(y_true, y_pred, labels=None, target_names=None, sample_weight=None, digits=2, output_dict=False)
```

Dentre todos esse paramêtros,existem paramêtros obrigatórios e opcionais::
**y_true** : matriz de indicador de rótulo / matriz esparsa
Realidade dos valores alvo.
**y_pred** : matriz de indicador de rótulo / matriz esparsa
Alvos estimados como retornados por um classificador.
**labels** : array, tamahnho = [n_labels],lista opcional de índices de etiquetas para incluir no relatório.

**target_names** : lista de strings,nomes de exibição opcionais correspondentes aos rótulos (mesma ordem).

**sample_weight** : array de tamanho = [n_samples], opcional,pesos de amostra

**dígitos**: int,número de dígitos para formatar valores de ponto flutuante de saída. Quando output_dict for True, isso será ignorado e os valores retornados não serão arredondados.

**output_dict** : bool (padrão = False)
Se for True, retorne a saída como dit
