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
Por conta de tudo aqui escrito,considero que este trecho de código acima é suficiente para manipular arquivos .csv em Python e atenderá as demandas da US01.
