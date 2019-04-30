# Documento de Estudo da US16

## Relatório de Classificação

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

Dentre todos esse paramêtros,existem paramêtros obrigatórios e opcionais,os obrigatórios sao:
**y_true** : 1d array-like ou matriz de indicador de rótulo / matriz esparsa
Realidade dos valores alvo.
