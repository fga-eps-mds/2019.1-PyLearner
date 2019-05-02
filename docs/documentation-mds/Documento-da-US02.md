# Documento de estudo da US02

## Introdução

Antes da criação das intents, actions e stories de cada tema selecionado são gerados documentos pela equipe de desenvolvimento que possuem abrangentemente do que aquele ele se trata. Selecionamos um breve conhecimento do tema, possíveis bibliotecas e até mesmo a forma de implementação. 

## Objetivo

Tendo em vista que os dados passados para o treinamento do bot devem ser bem claros e ter uma quantidade reduzida de informação para não poluir a caixa de mensagens do usuário, o desenvolvedor responsável pelo tema tem como objetivo extrair o máximo de informação e simplifica-la antes de passar para o usuário final. Isso torna a criação das intents, actions e stories mais rápidas e objetivas.

# **JSON**

## O que é um arquivo JSON
&nbsp;&nbsp;&nbsp;&nbsp; Basicamente é um subconjunto da Linguagem JavaScript, cujo acrônimo remete a **J** *ava* **S** *cript* **O** *bject* **N** *otation*. É um padrão simples de comunicação de dados que possui uma facilidade de compreensão e criação tanto para humanos quanto para as máquinas.

## A Estrutura de um Arquivo .json
&nbsp;&nbsp;&nbsp;&nbsp;O arquivo JSON é iniciado e delimitado por colchetes. No seu escopo podemos encontrar objetos e seus atributos que estão restringidos por um par de chaves. Estes atributos consistem em pares de relação atributo-valor que possuem como consequência uma melhor transmissão e compreensão dos dados.

# **JSON e Python**
&nbsp;&nbsp;&nbsp;&nbsp; Existem várias abordagens de como se tratar arquivos JSON em Python! Entretanto todas possuem algumas etapas semelhantes. Irei abordar as mais simples, elaboradas e eficientes nos tópicos seguintes.
## Como Acessar um Arquivo JSON
&nbsp;&nbsp;&nbsp;&nbsp;Antes de extrair informações do arquivo é necessário importar a biblioteca do JSON diponível em Python, e claro, possuir um arquivo JSON. A importação da biblioteca pode ser realizada da seguinte forma:
```python
import json
```
&nbsp;&nbsp;&nbsp;&nbsp;A segunda etapa é *abrir* &nbsp;e *ler*&nbsp;o arquivo json desejado. Portanto é necessário conhecer seu diretório. Deve-se realizar esta etapa com o auxílio de uma variável que receberá todo o arquivo lido:
```python
conteudo = open('diretorio/arquivo.json').read()
```

&nbsp;&nbsp;&nbsp;&nbsp;Após o conteúdo do json está setado na variável auxiliar, podemos carregar todos os objetos e atributos como uma única chave, ou seja, o próximo passo irá linkar os objetos com os seus respectivos atributos. Um bom exemplo, para fugir da abstração, seria um arquivo json informando diversos tipos de Pokémons, cada um desses pokémons possui um grupo de informações e características pessoais como tipo, ataque, localidade, velocidade entre outras. O próximo passo irá tratar cada Pokémon com seu próprio conjunto de dados, ou seja, de forma unânime:
```python
objeto = json.loads(conteudo)
```
&nbsp;&nbsp;&nbsp;&nbsp;Agora podemos printar os dados adquiridos e manipulá-los da melhor maneira possível! Caso necessário, também é possível realizar *casting* e assim tratar os dados de modo mais eficaz, conforme a necessidade do problema. 

```python
for item in objeto:
        print (item)
```

## Acessar arquivos JSON utilizando Pandas
&nbsp;&nbsp;&nbsp;&nbsp;Pandas é uma biblioteca de análise de dados que utiliza uma estrutura de dados tabular eficiente chamada Dataframe para representar seus dados.<br />
&nbsp;&nbsp;&nbsp;&nbsp;Caso seja seu primeiro contato com esta biblioteca muito provavelmente será necessário fazer o *download*&nbsp; da biblioteca Pandas. Digite no terminal o seguinte comando: <br/>
```python
pip install pandas
```
&nbsp;&nbsp;&nbsp;&nbsp;Assim como no método anterior também será necessário importar as bibliotecas para realização da leitura do arquivo. Iremos precisar de três importações:
```python
import json
import pandas as pd
from pandas.io.json import json_normalize
```
&nbsp;&nbsp;&nbsp;&nbsp;De modo semelhante iremos ler o arquivo em questão para extrair as informações existentes:

```python
with open('diretorio/arquivo.json') as info:
        data = json.load(info)
```
&nbsp;&nbsp;&nbsp;&nbsp;Agora utilizaremos uma variável auxiliar que receberá um método de tabularização dos dados obtidos:
```python
aux = json_normalize(data)
```
&nbsp;&nbsp;&nbsp;&nbsp;Para visiualização dos resultados podemos utilizar a função print de forma direta:

```python
print(aux)
```
&nbsp;&nbsp;&nbsp;&nbsp;Também é possível manipular os dados de forma a adquirir as informações de uma única linha ou acessar diretamente os atributos de determinado objeto.
```python 
print (aux.loc[0]) #irá imprimir todas as informações do primeiro objeto.
print(aux['atributo_desejado'][5]) #irá imprimir o atributo especificado do objeto. 
```
## Conclusão
&nbsp;&nbsp;&nbsp;&nbsp;Diante do exposto, os métodos demonstrados são capazes de auxiliar o usuário na importação de dados de arquivos .json. <br/>
 &nbsp;&nbsp;&nbsp;&nbsp;O documento de estudo também oferece base e visão geral do comportamento de precedência do chatbot e auxilia na criação das intents, stories e actions.