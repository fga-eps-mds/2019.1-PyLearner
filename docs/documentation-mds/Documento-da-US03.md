# Documento de Estudo da US03

## O que é excel?

Excel é um software de criação de planilhas eletrônicas.Foi criado pela Microsoft em 1987 para computadores que usam o sistema operacional da empresa.O Excel é a melhor plataforma eletrônica para criação de planilhas. Muitas empresas hoje sobrevivem com base em uso destas planilhas. Seus recursos incluem uma interface intuitiva e capacitadas ferramentas de cálculo e de construção de gráficos que, juntamente com marketing agressivo, tornaram o Excel um dos mais populares aplicativos de computador até hoje.E seus arquivos possuem formatos xlsx, xlsm, xltx, xltm.

## Arquivo excel e Python

### Como manipular arquivos excel?

A linguagem por si só nao faz essa manipulação,é necessário importamos a biblioteca **openpyxl**,uma biblitoeca para leitura e escrita de arquivos Excel 2010 xlsx/xlsm/xltx/xltm.
[Documentação da biblioteca](https://openpyxl.readthedocs.io/en/stable/index.html#module-openpyxl).

## Como abrir utilizar arquivos excel

Depois de importamos a biblioteca,é necessário importar de dentro da biblioteca o Workbook e utilizaremos a função load_workbook.

```python
from openpyxl import Workbook
wb = load_workbook(filename='arquivo.xlsx')
```

## Estrutura do Código

Segue um exemplo de como manipular arquivos excel em python:

```python
 from openpyxl import load_workbook
 wb = load_workbook(filename = 'empty_book.xlsx')
 sheet_ranges = wb['range names']
 print(sheet_ranges['D18'].value)
 # 3
```
