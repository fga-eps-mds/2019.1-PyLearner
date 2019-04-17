# Histograma

## **1. O que é**

<p style="text-align:justify">&emsp;&emsp;Histograma é uma representação gráfica de dados quantitativos. Esses dados são agrupados em classes de frequências de modo que é possivel ilustrar e representar uma amostra de dados e como ela está distribuida.</p>
<p style="text-align:justify">&emsp;&emsp;Para contruir um histograma é necessario que os dados estejam organizados em uma tabela de frequência na qual esta listados os dados e suas respectivas quantidades.</p>

## **2. Como fazer um histograma**

<p style="text-align:justify">&emsp;&emsp;Primeiro é necessário preparar o notebook, importando as bibliotecas necessarias: </p>

```python
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
```
<p style="text-align:justify">&emsp;&emsp;Depois é preciso selecionar e carregar um dataset(amostra):</p>

```python
#caminho do arquivo para carregar
file_path = "../file.csv"

#ler o arquivo e salvar em uma variavel
file_data = pd.read_csv(file_path, index_col="Id")
```

<p style="text-align:justify">&emsp;&emsp;Para criar o histograma podemos usar o comando <code>sns.distplot</code>:</p>

```python
#a = escolhe a coluna que quer plotar
#kde = False usa sempre que for criar um histograma
sns.distplot(a=file_path['column'],kde=False)
```

<p style="text-align:justify">&emsp;&emsp;Ou também o comando <code>sns.kdeplot</code> para criar um histograma com curvas mais suaves:</p>

```python
#a = escolhe a coluna que quer plotar
#shade = True preenche a area abaixo da curva
sns.kdeplot(a=file_path['column'],shade=True)
```

<p style="text-align:justify">&emsp;&emsp;Podemos usar o comando <code>input.plot.hist</code> do pandas também:</p>

```python
#gera dados nos tempos de deslocamento
size, scale = 1000, 10
commutes = pd.Series(np.random.gamma(scale, size=size) ** 1.5)

#plota o histograma
commutes.plot.hist(grid=True, bins=20, rwidth=0.9,
                   color='#607c8e')
```