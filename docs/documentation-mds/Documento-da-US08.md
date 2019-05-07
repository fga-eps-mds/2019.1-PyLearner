# Documento de estudo da US08

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.


## 1. Nearest Neighbors

Nearest Neighbors e a base de muitos outros métodos de aprendizado. O pricípio por trás do método nearest neighbors é encontrar um número predefinido de amostras de treinamento mais próximas da distancia do novo ponto e prever a label a partir delas. O número de amostras pode ser uma constante definida pelo usuário (k-neighbor learning) ou variar com base na densidade local dos pontos (radius-based neighbor learning). A distancia pode ser qualquer medida métrica. Sendo um método não paramêtrico, é bem sucedido em situações de classificação em que os limites de decisão são muito irregulares.

### 1.1 Unsurpevised nearest neighbors

<a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.NearestNeighbors.html#sklearn.neighbors.NearestNeighbors>NearestNeighbors</a> atua como uma interface uniforme para três tipos de algoritmos nearest neighbors: <a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.BallTree.html#sklearn.neighbors.BallTree>BallTree</a>, <a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KDTree.html#sklearn.neighbors.KDTree>KDTree</a>, e um algoritmo de força bruta baseado nas rotinas da <a href =https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics.pairwise>`sklearn.metrics.pairwise`</a>. A escolha dos algoritmos é controlada através do parâmetro `algorithm`, que deve ser `['auto', 'ball_tree', 'kd_tree', 'brute']`. Quando o valor default `'auto'` e passado, o algoritmo tenta determinar a melhor abordagem a partir dos dados de treinamento.

#### 1.1.1 Achando o Nearest Neighbors

Exemplo de como achar nearest neighbors entre dois conjuntos de dados:

```python
from sklearn.neighbors import NearestNeighbors
import numpy as np

X = np.array([[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]])

nbrs = NearestNeighbors(n_neighbors=2, algorithm='ball_tree').fit(X)
distances, indices = nbrs.kneighbors(X)

Out:
indices array([[0, 1],
               [1, 0],
               [2, 1],
               [3, 4],
               [4, 3],
               [5, 4]]...)

distances array([[0.        , 1.        ],
                 [0.        , 1.        ],
                 [0.        , 1.41421356],
                 [0.        , 1.        ],
                 [0.        , 1.        ],
                 [0.        , 1.41421356]])

```
#### 1.1.2 Classes KDTree e BallTree

Outra alternativa é usar diretamente as classes KDTree e BallTree para achar os nearest neighbors. As duas classes tem a mesma interface:

```python
from sklearn.neighbors import KDTree
import numpy as np
X = np.array([[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]])
kdt = KDTree(X, leaf_size=30, metric='euclidean')
kdt.query(X, k=2, return_distance=False)          
array([[0, 1],
       [1, 0],
       [2, 1],
       [3, 4],
       [4, 3],
       [5, 4]]...)
```

### 1.2 Classisficação Nearest Neighbors

A classificação usando nearest neighbors é calculada a partir de uma simples votação por maioria dos nearest neighbors mais próximos de cada ponto: um ponto de consulta é atribuido à classe de dados que possui mais representantes dentro dos nearest neighbors mais próximos.

O scikit-learn implementa dois classificadores de nearest neighbors: <a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier>KNeighborsClassifier</a> implementa o aprendizado baseado no *k* nearest neighbors de cada ponto de consulta,onde *k* é um valor inteiro especificado pelo usuário. <a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.RadiusNeighborsClassifier.html#sklearn.neighbors.RadiusNeighborsClassifier>RadiusNeighborsClassifier</a> implementa a aprendizagem com base no número de neighbors dentro de um raio fixo *r* de cada ponto de treinamento, onde *r* é um valor de ponto flutuante especificado pelo usuário.

 A classificação de vizinhos KNeighborsClassifier é a técnica mais usada. A escolha ideal do valor *k* é altamente dependente dos dados: em geral, um *k* muito grande suprime os efeitos do ruído, mas torna os limites de classificação menos distintos.

 Nos casos em que os dados não são uniformemente amostrados, a classificação dos neighbors baseados no raio RadiusNeighborsClassifierpode ser uma escolha melhor. O usuário especifica um raio fixo *r*, de modo que pontos em vizinhanças mais esparsas usem menos vizinhos mais próximos para a classificação.

 A classificação básica de vizinhos mais próximos usa pesos uniformes: isto é, o valor atribuído a um ponto de consulta é calculado a partir de uma votação por maioria simples dos vizinhos mais próximos. Em algumas circunstâncias, é melhor ponderar os vizinhos de tal forma que os vizinhos mais próximos contribuam mais para o ajuste. Isso pode ser feito através do parametro `weights`. O valor padrão `weights = 'uniform'`, atribui pesos uniformes a cada vizinho.`weights = 'distance'` atribui pesos proporcionais ao inverso da distância do ponto de consulta. Alternativamente, uma função definida pelo usuário da distância pode ser fornecida para calcular os pesos.

 Exemplo:

 ```python

import numpy as np
import matplotlib.pyplot as plt
from matplotlib.colors import ListedColormap
from sklearn import neighbors, datasets

n_neighbors = 15

# import some data to play with
iris = datasets.load_iris()

# we only take the first two features. We could avoid this ugly
# slicing by using a two-dim dataset
X = iris.data[:, :2]
y = iris.target

h = .02  # step size in the mesh

# Create color maps
cmap_light = ListedColormap(['#FFAAAA', '#AAFFAA', '#AAAAFF'])
cmap_bold = ListedColormap(['#FF0000', '#00FF00', '#0000FF'])

for weights in ['uniform', 'distance']:
    # we create an instance of Neighbours Classifier and fit the data.
    clf = neighbors.KNeighborsClassifier(n_neighbors, weights=weights)
    clf.fit(X, y)

    # Plot the decision boundary. For that, we will assign a color to each
    # point in the mesh [x_min, x_max]x[y_min, y_max].
    x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
    y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
    xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                         np.arange(y_min, y_max, h))
    Z = clf.predict(np.c_[xx.ravel(), yy.ravel()])

    # Put the result into a color plot
    Z = Z.reshape(xx.shape)
    plt.figure()
    plt.pcolormesh(xx, yy, Z, cmap=cmap_light)

    # Plot also the training points
    plt.scatter(X[:, 0], X[:, 1], c=y, cmap=cmap_bold,
                edgecolor='k', s=20)
    plt.xlim(xx.min(), xx.max())
    plt.ylim(yy.min(), yy.max())
    plt.title("3-Class classification (k = %i, weights = '%s')"
              % (n_neighbors, weights))

plt.show()
 ```

 ## 2. Naive Bayes

<a href=https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.GaussianNB.html#sklearn.naive_bayes.GaussianNB>GaussianNB</a> implementa o algoritmo Gaussian Naive Bayes para classificação. A probabilidade das features assume ser gaussiana:

![](img/gaussin-naive-bayes.png)

Os parâmetros &sigma;<sub>y</sub> e &mu;<sub>y</sub> são estimados usando a maior probabilidade.

```python
from sklearn import datasets
iris = datasets.load_iris()
from sklearn.naive_bayes import GaussianNB
gnb = GaussianNB()
y_pred = gnb.fit(iris.data, iris.target).predict(iris.data)
print("Number of mislabeled points out of a total %d points : %d"
      % (iris.data.shape[0],(iris.target != y_pred).sum()))
```

## 3. Decision Trees

<a href=https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html#sklearn.tree.DecisionTreeClassifier>DecisionTreeClassifier</a> e a classe capaz de realizar classificações de varias classes em um dataset.

O parâmetro de entrada são dois arrays: um array X, esparso ou denso, de tamanho <code>[n_samples, n_features]</code> contendo os dados de treino; e um array Y de valores inteiros de tamanho <code>[n_samples]</code>, contendo as labels de classes para os dados de treino:

```python
from sklearn import tree
X = [[0, 0], [1, 1]]
Y = [0, 1]
clf = tree.DecisionTreeClassifier()
clf = clf.fit(X, Y)
```

Depois de ajustada, a model pode ser usada para prever os dados:

```python
clf.predict([[2., 2.]])

Saida:
array([1])
```

