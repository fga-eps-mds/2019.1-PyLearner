# Documento de estudo da US08

## Introdução

&nbsp;&nbsp;&nbsp;&nbsp;Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

&nbsp;&nbsp;&nbsp;&nbsp;Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

## K-means
&nbsp;&nbsp;&nbsp;&nbsp;K-means possui por finalidade agrupar um conjunto de dados semelhantes ou que não apresentam grande discrepância entre si descobrindo assim padrões subjacentes.

```python
KMeans(n_clusters=8, init=’k-means++’, n_init=10, max_iter=300, tol=0.0001, precompute_distances=’auto’, verbose=0, random_state=None, copy_x=True, n_jobs=None, algorithm=’auto’)
```
### Parâmetros relevantes:
**n_clusters**: Refere-se ao número de clusters(agrupamentos) em que serão alocados os dados, o número 8 é o padrão da função caso não seja especificado no parâmetro.

**init**: Refere-se ao modo como o algoritmo será inicializado. 'k-means++' é o método padrão para criação dos clusters.

**random**: Se refere ao modo de inicialização de forma aleatória, ou seja, os centróides iniciais serão gerados de forma totalmente aleatória sem um critério para seleção.

**max_iter**: A quantidade de vezes em que o algoritmo irá ser executado.

**n_jobs**: Podemos especificar a quantidade de CPU´s ou optar por não utilizar computação paralela.

**algorithm**:  A versão do algoritmo K-Means a ser utilizada.

## Implementação

&nbsp;&nbsp;&nbsp;&nbsp;Para entender melhor o conceito iremos ter por base uma matriz de valores aleatórios de apenas duas dimensões.

```python
import numpy as np
import matplotlib.pyplot as plt

valores_aleatorios = np.random.rand(100,2)
```
&nbsp;&nbsp;&nbsp;&nbsp;Esta função irá gerar 100 valores aleatores para cada dimensão (x,y) setada. Importante ressaltar as quantidades podem ser expandidas de acordo com a necessidade da situação.

&nbsp;&nbsp;&nbsp;&nbsp;A Clusterização dos dados necessita da biblioteca do KMeans. A importação desta biblioteca é feita da seguinte forma:
```python
    from sklearn.cluster import KMeans
```
&nbsp;&nbsp;&nbsp;&nbsp;Agora iremos setar os dados e agrupa-los utilizando KMeans
```python
    kmeans = KMeans(n_clusters=2).fit(valores_aleatorios)
```
&nbsp;&nbsp;&nbsp;&nbsp;Agora os dados e suas particularidades encontradas no processo de KMeans estão setados na variável kmeans! Note que temos dois clusters, ou seja, teremos dois agrupamentos de dados.
&nbsp;&nbsp;&nbsp;&nbsp;Podemos utilizar agora uma função que ira mostrar a que cluster cada par, ou conjunto, de dados se encontra. Resumindo é onde cada dado está situado, qual o endereço do agrupamento em que foi armazenado.
```python
    print (kmeans.labels_)
```
&nbsp;&nbsp;&nbsp;&nbsp;     Com isso teremos os dados agrupados e em que endereço se encontram. De certa forma os endereços, ou chaves de agrupamento, dos clusters são nomeados de acordo com o range de _0 à n-1_ onde n corresponde a quantidade de cluster definidos no parâmetro inicial (n_clusters=n). Neste caso, em específico, teremos um cluster que atende pela codificação 0 e o outro cluster atenderá por 1<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Caso seja necessário podemos achar os pontos centrais de cada cluster com o comando:
```python
    kmeans.cluster_centers_
```
&nbsp;&nbsp;&nbsp;&nbsp;Que irá retornar a posição do ponto central de cada cluster. 

&nbsp;&nbsp;&nbsp;&nbsp;Para plotarmos o gráfico devemos iterar sobre cada par encontrado e plotar no gráfico, da seguinte forma

```python
i = 0

while(i < len(valores_aleatorios)):

    if (kmeans.labels_[i] == 0): plt.plot(valores_aleatorios[i][1],valores_aleatorios[i][0], 'go' ,color = 'green')
    
    else: plt.plot(valores_aleatorios[i][1],valores_aleatorios[i][0], 'go' ,color = 'orange')

    i+=1

    # Mapeando ponto a ponto no gráfico 

plt.plot(kmeans.cluster_centers_[0][1], kmeans.cluster_centers_[0][0], 'go', color = 'black')
    
plt.plot(kmeans.cluster_centers_[1][1], kmeans.cluster_centers_[1][0], 'go', color = 'black')

# Mapeando o centróide de cada cluster

plt.title('Exemplo K-Means - Pyter')

plt.show()


```
&nbsp;&nbsp;&nbsp;&nbsp;Cada Cluster foi mapeado com cores distintas e seu centróides são pontos negros em seus respectivos endereços. Por serem valores aleatórios gerados em cada execução do código teremos, na maioria das vezes, gráficos e pontos distintos. Entretanto para exemplificar esses conjuntos de códigos em funcionamento deixo esta exemplificação: <br/>

 ![Exemplo](https://i.imgur.com/c3GFjeD.png)
