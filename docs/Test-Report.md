## Relatório de qualidade do chatbot

|    Data    | Versão |             Alteração             |      Autor      |
|:----------:|:------:|:---------------------------------:|:---------------:|
| 24/05/2019 |  0.1   |       Criação do documento        | Bruno Henrique  |
| 24/05/2019 |  0.2   | Geração dos resultados dos testes | Bruno Henrique  |
| 26/05/2019 |  0.3   |      Análise dos resultados       | Gabriel Ziegler |

## Métricas

O desempenho do chatbot está sendo mensurado levando em consideração as seguintes métricas e visualizações:
- Precision: `tp / (tp + fp)`
- Recall: `tp / (tp + fn)`
- F1-Score: `2 * (precision * recall) / (precision + recall)`
- Support: Número de ocorrência de cada classe em `y_true`.
- Matriz de confusão: visualização gráfica dos tp, tn, fp, fn.

Onde:
- `tp` é verdadeiro positivo
- `tn` é verdadeiro negativo
- `fp` é falso positivo
- `fn` é falso negativo

Com todas essas métricas disponíveis o time decidiu por prezar mais a métrica **F1-Score** por essa ser uma métrica composta que leva em consideração tanto *precision* quanto *recall*, não gerando assim um viés de melhorar somente erros `type 1` ou `type 2`, mas sim melhorar os dois igualmente quando o F1-Score melhorar.

## Objetivo

O objetivo dos testes será manter a cobertura de testes das intents do chatbot com um **F1-Score**(weighted avg) acima de 75% sempre e com objetivo de antes da R2 essa cobertura estar acima de 90%.

## Baseline

### Classification Report
![Alt text](https://i.imgur.com/vnJdiYs.png)

### Matriz de Confusão
![Alt text](https://imgur.com/qMQKcHi.jpg)

## Análise

As métricas do desempenhos não são ruins, porém a amostragem ainda está muito desbalanceada e precisa aumentar para que possamos ter resultados de testes mais confiáveis.

## Referencial

[1] https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics
[2] https://www.stat.berkeley.edu/~hhuang/STAT141/Lecture-FDR.pdf
