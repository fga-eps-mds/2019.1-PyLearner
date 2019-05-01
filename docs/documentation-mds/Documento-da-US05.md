# Transformar Dados Categóricos

## Dados Categóricos 

### O que são Dados Categóricos
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dados Categóricos podem ser tipos de dados nominais ou ordinais decorrentes de determinada situação a ser tratada.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Um exemplo de dados nominais seria a variável cor, que pode assumir os valores "azul" ou "vermelho".<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Já um exemplo de dados ordinais inferiria a variável escolaridade que pode assumir os valores "1º Grau" ou "2º Grau".<br/>
### Dados Categóricos No Contexto de Machine Learning
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Em Machine Learning geralmente os algoritmos não trabalham com esses tipos de dados por não expressarem valor numérico. Diante do exposto, a solução de tal problemática seria uma conversão destes dados para então realizar uma abordagem congruente aos algoritmos utilizados. <br/>
### Como Tratar os Dados Categóricos
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O primeiro passo, talvez seja a instalação da biblioteca scikit-learn pelo terminal:<br/>
```
pip install -U scikit-learn
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
O segundo passo é a importação do módulo de pré-processamento:
```python
from sklearn.preprocessing import LabelEncoder
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Para melhor entendimento dos processos relacionados ao tratamento de dados categóricos considere a seguinte situação de exemplo, utilizando a variável _mes_<br/>
```python
mes = ['Janeiro','Fevereiro','Março','Abril','Maio','Junho','Julho','Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro']
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Como dito anteriormente para tratarmos estes tipos de dados, devemos convertê-los, em uma forma legível a ser trabalhada pelos algoritmos. Para isso, o próximo passo é instanciar um objeto da classe LabelEncoder()
```python
label_encoder = LabelEncoder()
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O próximo passo irá tranformar estes dados em chaves numéricas, que é o principal objetivo desta seção. No caso teremos o auxílio do método **fit_transform()**:
```python
valores_numericos = label_encoder.fit_transform(mes)
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Agora a variável _valores_numericos_ detêm os respectivos valores a serem tratados pelos algoritmos de maneira correta. Em nosso caso cada mês recebeu uma codificação numérica distinta para ser tratada, essa codificação não estará necessariamente na ordem de precedência dos dados.
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Importante ressaltar que caso hajam dados categóricos repetidos, a função irá retornar uma única chave de codificação independente da quantidade de ocorrências deste dado. Nestes casos é possível utilizar o comando set para confirmar e visualizar as chaves geradas sem repetições e ordenadas:
```python
set(valores_numericos)
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Assim como foi realizado um mapeamento dos dados, é possível decodificar as chaves geradas atráves do método **inverse_transform()**. Da seguinte maneira: 
```python
valor_real = label_encoder.inverse_transform([1])
print (valor_real)
```
Neste caso ao passar o valor 1 como parâmetro, o retorno foi o valor "Agosto".











