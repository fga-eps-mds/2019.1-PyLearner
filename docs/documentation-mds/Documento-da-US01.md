# Documento de estudo da US1
## O que é um CSV?
Comma-separated values (ou CSV) é um formato de arquivo que armazena dados tabelados, cujo grande uso data da época dos mainframes.Por serem bastante simples, arquivos .csv são comuns em todas as plataformas de computador.
## Como é a estrutura de um arquivo .csv?
O CSV é um implementação particular de arquivos de texto separados por um delimitador, que usa a vírgula e a quebra de linha para separar os valores. O formato também usa as aspas em campos no qual são usados os caracteres reservados (vírgula e quebra de linha). Essa robustez no formato torna o CSV mais amplo que outros formatos digitais do mesmo segmento.

## Arquivo .csv e Python

### Como Manipular Arquivo .csv?
Primeiro é necessário importar uma biblioteca chamada csv e com isso temos acesso a algumas funções necessarias para fazer a importação.
[Documentação da biblioteca](https://docs.python.org/3/library/csv.html)


### Como Abrir um Arquivo .csv?
Utilizaremos a função nativa open(),que pode ser usada para manipular arquivos em Python. Sua sintaxe básica é:

file_object = open(filename, mode)

Onde filename é, obviamente, o nome do arquivo a ser manipulado.

mode é o modo como o arquivo será aberto,existem alguns modos em como esse arquivo pode ser aberto mas utilizaremos o modo 'rb' que significa Read in Binary mode,que vai se aplicar pra maioria dos casos.

### Como Manipular um Arquivo .csv?
Após abrir o arquivo,é necessário lê-lo,então usaremos a função reader(),presente na biblioteca csv.Essa função retorna um objeto,por isso,atribuiremos esse objeto a uma variavel.
### Estrutura do Código
Existe mais de um jeito de ler arquivos csv em python,por exemplo,a forma mais simples é:

```python
import csv
ficheiro = open('arquivo.csv', 'rb')
reader = csv.reader(ficheiro)
for linha in reader:
    print linha
```
No entanto,é boa prática abrir o arquivo de outro modo:
```python
import csv
with open('ficheiro_csv.csv', 'rb') as ficheiro:
    reader = csv.reader(ficheiro)
    for linha in reader:
        print linha
```
## Pandas e Python
### O que é Pandas
Outra forma de manipularmos arquivos em Python é utilizando o Pandas,uma biblioteca de software open-source escrita para a linguagem Python com a finalidade de manipulação e análise de dados.Pandas é muito utilizado em Deep Learning,Data Science e Machine Learning.

## Pandas na Manipulação de Arquivo CSV
Em pandas,é até mais simples,utilizamos basicamente apenas a função read_csv da biblioteca pandas.
### Função read_csv()
Essa função é muito poderosa e recebe como parametros:
```python
pandas.read_csv( filepath_or_buffer , sep = ' , ' , delimitador = Nenhum , cabeçalho = 'infer' , nomes = Nenhum , index_col = Nenhum , usecols = Nenhum , squeeze = False , prefixo = Nenhum , mangle_dupe_cols = True , dtype = Nenhum , engine = Nenhum , conversores = Nenhum , true_values ​​= Nenhum , false_values ​​= Nenhum , skipinitialspace = False , skiprows = Nenhum , skipfooter = 0 , nrows = Nenhum , na_values ​​= Nenhum, keep_default_na = Verdadeiro , na_filter = Verdadeiro , verbose = Falso , skip_blank_lines = Verdadeiro , parse_dates = Falso , infer_datetime_format = Falso , keep_date_col = Falso , date_parser = Nenhum , dayfirst = Falso , iterador = Falso , chunksize = Nenhum , compactação = 'inferir' , milhares = nenhum , decimal = b '.' , lineterminator = None , quotechar = '"' , citando = 0 , doublequote = True , escapechar = None ,comment = Nenhum , codificação = None , dialect = None , tupleize_cols = Nenhum , error_bad_lines = True , warn_bad_lines = Verdadeiro , delim_whitespace = Falso , low_memory = Verdadeiro , memory_map = Falso , float_precision = Nenhum )
```
Mas apenas o primeiro parâmetro é obrigatório,o filepath_or_buffer, que é objeto de caminho ou objeto semelhante a arquivo
Qualquer caminho de string válido é aceitável. A string pode ser um URL. Esquemas de URL válidos incluem http, ftp, s3 e file. Para URLs de arquivos, um host é esperado.

Por objeto tipo arquivo, nos referimos a objetos com um read() método, como um manipulador de arquivos (por exemplo, via openfunção interna ) ou StringIO.Como são muitos parâmetros e apenas um deles é obrigatório e atenderá a maioria dos casos da US01,não vou detalhar todos os parâmetros mas segue a documentação da função read_csv().
[Documentação da função](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html)

### Exemplo de código com Pandas
O exemlo abaixo printa todos os nomes contidos no arquivo.csv
```python
import pand as pd
ex = pd.read_csv('arquivo.csv')
nome = df[['nome']].values
print(nome)
```