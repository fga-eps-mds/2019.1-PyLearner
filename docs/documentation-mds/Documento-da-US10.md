# Documento de Estudo da US10

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação.

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# Regressão Polinomial

Um padrão comum em machine learning é usar modelos lineares treinados em funções não-lineares dos dados. Essa abordagem mantém o desempenho geralmente rápido de métodos lineares, permitindo que eles se ajustem a uma faixa muito maior de dados.

Por exemplo, uma regressão linear simples pode ser estendida construindo recursos polinomiais a partir dos coeficientes. No caso de regressão linear padrão, você pode ter um modelo assim para dados bidimensionais:

`ŷ(W, X) = W0 + W1 * X1 + W2 * X2`

Se quisermos ajustar um parabolóide aos dados em vez de um plano, podemos combinar os recursos em polinômios de segunda ordem, para que o modelo se pareça com isso:

`ŷ(W, X) = W0 + W1 * X1 + W2 * X2 + W3 * X1 * X2 + W4 * X1 * x1 + W5 * X2 * X2`

A observação (às vezes surpreendente) é que este ainda é um modelo linear: para ver isso, imagine criar um novo conjunto de recursos

`z = [X1,X2,X1 * X2,X1 * X1,X2 * X2]`

Com esta nova rotulagem dos dados, nosso problema pode ser escrito

`ŷ(W, Z) = W0 + W1 * Z1 + W2 * Z2 + W3 * Z3 + W4 * Z4 + W5 * Z5`

Vemos que a regressão polinomial resultante está na mesma classe de modelos lineares que consideramos acima (ou seja, o modelo é linear em) e pode ser resolvida pelas mesmas técnicas. Considerando-se os ajustes lineares dentro de um espaço de dimensões superiores construído com essas funções de base, o modelo tem a flexibilidade de ajustar um intervalo de dados muito mais amplo.

## Regrassão Polinomial em Python

Utilizamos o transformador **PolynomialFeatures**, que transforma uma matriz de dados de entrada em uma nova matriz de dados de um determinado grau. Pode ser usado da seguinte forma:

```python
>>> from sklearn.preprocessing import PolynomialFeatures
>>> import numpy as np
>>> X = np.arange(6).reshape(3, 2)
>>> X
array([[0, 1],
       [2, 3],
       [4, 5]])
>>> poly = PolynomialFeatures(degree=2)
>>> poly.fit_transform(X)
array([[ 1.,  0.,  1.,  0.,  0.,  1.],
       [ 1.,  2.,  3.,  4.,  6.,  9.],
       [ 1.,  4.,  5., 16., 20., 25.]])
```

Os recursos do X foram transformados de `[X1,X2]` para `[1,X1,X2,X1*X1,X1*X2,X2*X2]` e agora podem ser usados ​​em qualquer modelo linear.

Esse tipo de pré-processamento pode ser otimizado com as ferramentas do **Pipeline**. Um único objeto representando uma regressão polinomial simples pode ser criado e usado da seguinte maneira:

```python
>>> from sklearn.preprocessing import PolynomialFeatures
>>> from sklearn.linear_model import LinearRegression
>>> from sklearn.pipeline import Pipeline
>>> import numpy as np
>>> model = Pipeline([('poly', PolynomialFeatures(degree=3)),
...                   ('linear', LinearRegression(fit_intercept=False))])
>>> # fit to an order-3 polynomial data
>>> x = np.arange(5)
>>> y = 3 - 2 * x + x ** 2 - x ** 3
>>> model = model.fit(x[:, np.newaxis], y)
>>> model.named_steps['linear'].coef_
array([ 3., -2.,  1., -1.])
```

O modelo linear treinado em características polinomiais é capaz de recuperar exatamente os coeficientes polinomiais de entrada.

Em alguns casos, não é necessário incluir poderes superiores de qualquer recurso único, mas apenas os chamados recursos de interação que se multiplicam no máximo em recursos distintos. Estes podem ser obtidos em **PolynomialFeatures** com a configuração `interaction_only = True`.

Por exemplo, ao lidar com recursos booleanos,`(Xi ** n) = Xi` para todos `n` e, portanto, é inútil; mas `XiXj` representa a conjunção de dois booleanos. Desta forma, podemos resolver o problema XOR com um classificador linear:

```python
>>> from sklearn.linear_model import Perceptron
>>> from sklearn.preprocessing import PolynomialFeatures
>>> import numpy as np
>>> X = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])
>>> y = X[:, 0] ^ X[:, 1]
>>> y
array([0, 1, 1, 0])
>>> X = PolynomialFeatures(interaction_only=True).fit_transform(X).astype(int)
>>> X
array([[1, 0, 0, 0],
       [1, 0, 1, 0],
       [1, 1, 0, 0],
       [1, 1, 1, 1]])
>>> clf = Perceptron(fit_intercept=False, max_iter=10, tol=None,
...                  shuffle=False).fit(X, y)
```

E as "previsões" do classificador são perfeitas:

```python
>>> clf.predict(X)
array([0, 1, 1, 0])
>>> clf.score(X, y)
1.0
```

# Regressão Bayesiana

Tecnicas de regressão bayesianas podem ser usadas para incluir parâmetros regulares no processo de estimativa.
Isso é feito ao introduzir uma distribuição, chamada de distribuição a priori, ao conjunto de parâmetros desconhecidos quantificando a sua crença sobre esse conjunto e a estimação dos parâmetros é dada através da distribuição à posteriori, que é proporcional ao produto da função de verossimilhança com a distribuição a priori.

## Regressão de Ridge Bayesiana

BayesianRidge estima um modelo de probabilidade do problema de regressão. O coeficiente &alpha; e &lambda; são escolhidos para serem distribuições gamma, o conjugado para a precisão Gaussiana. O resultado do modelo é chamado de Bayesian Ridge Regression.
Os parâmetros &omega;, &alpha; e &lambda; sao estimados durante o ajuste do modelo. Os parâmetros de regularização &alpha; e &lambda; são estimados maximizando a probabilidade marginal do log.

```python
>>> from sklearn import linear_model
>>> X = [[0., 0.], [1., 1.], [2., 2.], [3., 3.]]
>>> Y = [0., 1., 2., 3.]
>>> reg = linear_model.BayesianRidge()
>>> reg.fit(X, Y)  
BayesianRidge(alpha_1=1e-06, alpha_2=1e-06, compute_score=False, copy_X=True,
       fit_intercept=True, lambda_1=1e-06, lambda_2=1e-06, n_iter=300,
       normalize=False, tol=0.001, verbose=False)
```

Depois de ajustado, o modelo pode ser usado para prever novos valores:

```python
>>> reg.predict([[1, 0.]])
array([0.50000013])
```
Para acessar o coeficiente &omega;:

```python
>>> reg.coef_
array([0.49999993, 0.49999993])
```