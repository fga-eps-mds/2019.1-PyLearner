# Documento de estudo da US08

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.


## 1. Generalized Linear Models

Em estatística, o modelo linear generalizado é uma generalização flexível da regressão linear ordinária que permite variáveis de resposta que possuem modelos de distribuição de erro diferentes de uma distribuição normal. O GLM generaliza a regressão linear permitindo que o modelo linear seja relacionado à variável de resposta por meio de uma função de link e permitindo que a magnitude da variância de cada medida seja uma função de seu valor previsto.

### 1.1 Logistic regression

A regressão logística, apesar de seu nome, é um modelo linear para classificação em vez de regressão. A regressão logística também é conhecida na literatura como regressão logit, classificação de máxima entropia (MaxEnt) ou o classificador log-linear. Nesse modelo, as probabilidades que descrevem os resultados possíveis de um único teste são modeladas usando uma função logística.

```python
from sklearn import svm
X = [[0, 0], [1, 1]]
y = [0, 1]
clf = svm.SVC(gamma='scale')
clf.fit(X, y)

Output:

SVC(C=1.0, cache_size=200, class_weight=None, coef0=0.0,
    decision_function_shape='ovr', degree=3, gamma='scale', kernel='rbf',
    max_iter=-1, probability=False, random_state=None, shrinking=True,
    tol=0.001, verbose=False)

```

## 2. Support Vector Machines

A máquina de vetores de suporte (SVM) é um conjunto de métodos do aprendizado supervisionado que analisam os dados e reconhecem padrões, usado para classificação e análise de regressão. O SVM padrão toma como entrada um conjunto de dados e prediz, para cada entrada dada, qual de duas possíveis classes a entrada faz parte, o que faz do SVM um classificador linear binário não probabilístico. Um modelo SVM é uma representação de exemplos como pontos no espaço, mapeados de maneira que os exemplos de cada categoria sejam divididos por um espaço claro que seja tão amplo quanto possível.

### 2.1 Classificação

SVC, NuSVC e LinearSVC são classes capazes de executar classificações de várias classes em um conjunto de dados.

O SVC e o NuSVC são métodos semelhantes, mas aceitam conjuntos de parâmetros ligeiramente diferentes e têm diferentes formulações matemáticas. Por outro lado, o LinearSVC é outra implementação do Support Vector Classification para o caso de um kernel linear.

Como outros classificadores, SVC, NuSVC e LinearSVC tomam como entrada duas matrizes: uma matriz X de tamanho [n_samples, n_features] contendo as amostras de treinamento, e uma matriz y de rótulos de classe (strings ou inteiros), tamanho [n_samples]:


Depois de ajustado, o modelo pode ser usado para prever novos valores:

```python
clf.predict([[2., 2.]])

Output:

array([1])
```

A função de decisão de SVMs depende de algum subconjunto dos dados de treinamento, chamados de vetores de suporte. Algumas propriedades destes vetores de suporte podem ser encontradas nos membros support_vectors_, support_ e n_support:

```python
# get support vectors
clf.support_vectors_

Output:

array([[0., 0.],
       [1., 1.]])

```

```python
# get indices of support vectors
clf.support_

Output:

array([0, 1]...)
```
```python
# get number of support vectors for each class
clf.n_support_

Output:

array([1, 1]...)

```
### 2.1.1 Multi-class classification

O SVC e o NuSVC implementam a abordagem “um-contra-um” para classificação de várias classes. Se n_class é o número de classes, os classificadores n_class * (n_class - 1) / 2 são construídos e cada um treina os dados de duas classes. Para fornecer uma interface consistente com outros classificadores, a opção decision_function_shape permite agregar os resultados dos classificadores “um contra um” a uma função de decisão de forma (n_samples, n_classes):

```python
X = [[0], [1], [2], [3]]
Y = [0, 1, 2, 3]
clf = svm.SVC(gamma='scale', decision_function_shape='ovo')
clf.fit(X, Y)

Output:

SVC(C=1.0, cache_size=200, class_weight=None, coef0=0.0,
    decision_function_shape='ovo', degree=3, gamma='scale', kernel='rbf',
    max_iter=-1, probability=False, random_state=None, shrinking=True,
    tol=0.001, verbose=False)

```
```python
dec = clf.decision_function([[1]])
dec.shape[1] # 4 classes: 4*3/2 = 6

Output:
6
```
```python
clf.decision_function_shape = "ovr"
dec = clf.decision_function([[1]])
dec.shape[1] # 4 classes

Output:
4
```

Por outro lado, o LinearSVC implementa uma estratégia multi-classe “one to the rest”, treinando assim modelos n_class. Se houver apenas duas classes, apenas um modelo é treinado:

```python
lin_clf = svm.LinearSVC()
lin_clf.fit(X, Y)

Output:
LinearSVC(C=1.0, class_weight=None, dual=True, fit_intercept=True,
     intercept_scaling=1, loss='squared_hinge', max_iter=1000,
     multi_class='ovr', penalty='l2', random_state=None, tol=0.0001,
     verbose=0)
```
```python
dec = lin_clf.decision_function([[1]])
dec.shape[1]

Output:
4
```

### 2.1.2 Scores and probabilities

The decision_function method of SVC and NuSVC gives per-class scores for each sample (or a single score per sample in the binary case). When the constructor option probability is set to True, class membership probability estimates (from the methods predict_proba and predict_log_proba) are enabled. In the binary case, the probabilities are calibrated using Platt scaling: logistic regression on the SVM’s scores, fit by an additional cross-validation on the training data.

### 2.1.3 Unbalanced problems

Nos problemas em que se deseja dar mais importância a certas classes ou a determinadas amostras individuais, é possível usar as palavras-chave class_weight e sample_weight.

O SVC, o NuSVC, o SVR, o NuSVR e o OneClassSVM implementam também pesos para amostras individuais no ajuste do método através da palavra-chave sample_weight. Semelhante ao class_weight, eles definem o parâmetro C para o exemplo i-th como C * sample_weight [i].

## 3. Stochastic Gradient Descent

O Descentramento Estocástico de Gradiente (SGD) é uma abordagem simples, mas muito eficiente, para a aprendizagem discriminativa de classificadores lineares sob funções de perda convexa, como Máquinas de Vetores de Suporte (lineares) e Regressão Logística. O SGD tem sido aplicado com sucesso em problemas de aprendizado de máquina em grande escala e esparsos, freqüentemente encontrados na classificação de textos e processamento de linguagem natural.

### 3.1 Classification

A classe SGDClassifier implementa uma rotina de aprendizado de descida gradiente estocástica que suporta diferentes funções de perda e penalidades para classificação.

Como outros classificadores, o SGD deve ser equipado com duas matrizes: uma matriz X de tamanho [n_samples, n_features] contendo as amostras de treinamento e uma matriz Y de tamanho [n_samples] contendo os valores de destino (rótulos de classe) para as amostras de treinamento:

```python
from sklearn.linear_model import SGDClassifier
X = [[0., 0.], [1., 1.]]
y = [0, 1]
clf = SGDClassifier(loss="hinge", penalty="l2", max_iter=5)
clf.fit(X, y)

Output:
SGDClassifier(alpha=0.0001, average=False, class_weight=None,
           early_stopping=False, epsilon=0.1, eta0=0.0, fit_intercept=True,
           l1_ratio=0.15, learning_rate='optimal', loss='hinge', max_iter=5,
           n_iter=None, n_iter_no_change=5, n_jobs=None, penalty='l2',
           power_t=0.5, random_state=None, shuffle=True, tol=None,
           validation_fraction=0.1, verbose=0, warm_start=False)
```

Depois de ajustado, o modelo pode ser usado para prever novos valores:

```python
clf.predict([[2., 2.]])

Output:
array([1])
```

O SGD ajusta um modelo linear aos dados de treinamento. O membro coef_ contém os parâmetros do modelo:

```python
clf.coef_                                      

Output:
array([[9.9..., 9.9...]])
```

Membro intercept_ detém a interceptação (deslocamento ou polarização):

```python
clf.intercept_                                 

Output:
array([-9.9...])
```

Se o modelo deve ou não usar uma interceptação, ou seja, um hiperplano enviesado, é controlado pelo parâmetro fit_intercept.

Para obter a distância assinada para o hiperplano use SGDClassifier.decision_function:

```python
clf.decision_function([[2., 2.]])              

Output:
array([29.6...])
```

A função de perda de concreto pode ser definida através do parâmetro de perda. O SGDClassifier suporta as seguintes funções de perda:

> loss = "hinge": (soft-margin) linear Máquina de Vetores de Suporte

> loss = "modified_huber": perda da dobradiça alisada

> loss = "log": regressão logística

> E todas as perdas de regressão abaixo

Usando loss = "log" ou loss = "modified_huber" habilita o método predict_proba, que fornece um vetor de estimativas de probabilidade por amostra:

```python
clf = SGDClassifier(loss="log", max_iter=5).fit(X, y)
clf.predict_proba([[1., 1.]])                  

Output:
array([[0.00..., 0.99...]])
```

## 4. Nearest Neighbors

Nearest Neighbors e a base de muitos outros métodos de aprendizado. O pricípio por trás do método nearest neighbors é encontrar um número predefinido de amostras de treinamento mais próximas da distancia do novo ponto e prever a label a partir delas. O número de amostras pode ser uma constante definida pelo usuário (k-neighbor learning) ou variar com base na densidade local dos pontos (radius-based neighbor learning). A distancia pode ser qualquer medida métrica. Sendo um método não paramêtrico, é bem sucedido em situações de classificação em que os limites de decisão são muito irregulares.

### 4.1 Unsurpevised nearest neighbors

<a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.NearestNeighbors.html#sklearn.neighbors.NearestNeighbors>NearestNeighbors</a> atua como uma interface uniforme para três tipos de algoritmos nearest neighbors: <a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.BallTree.html#sklearn.neighbors.BallTree>BallTree</a>, <a href=https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KDTree.html#sklearn.neighbors.KDTree>KDTree</a>, e um algoritmo de força bruta baseado nas rotinas da <a href =https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics.pairwise>`sklearn.metrics.pairwise`</a>. A escolha dos algoritmos é controlada através do parâmetro `algorithm`, que deve ser `['auto', 'ball_tree', 'kd_tree', 'brute']`. Quando o valor default `'auto'` e passado, o algoritmo tenta determinar a melhor abordagem a partir dos dados de treinamento.

#### 4.1.1 Achando o Nearest Neighbors

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
#### 4.1.2 Classes KDTree e BallTree

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

### 4.2 Classisficação Nearest Neighbors

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

 ## 5. Naive Bayes

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

## 6. Decision Trees

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

