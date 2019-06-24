## Relatório de qualidade do chatbot

|    Data    | Versão |             Alteração             |      Autor      |
|:----------:|:------:|:---------------------------------:|:---------------:|
| 24/05/2019 |  0.1   |       Criação do documento        | Bruno Henrique  |
| 24/05/2019 |  0.2   | Geração dos resultados dos testes | Bruno Henrique  |
| 26/05/2019 |  0.3   |      Análise dos resultados       | Gabriel Ziegler |
| 23/06/2019 |  0.4   |  Análises e Conclusões            | Bruno Henrique  |

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

## Conclusões e Análises

Os Testes fornecidos pelo RASA resultaram em Matrizes de Confusão nos temas abordados pelo ChatBot. Estes mesmos resultados foram usados como base para refatoração de intents e actions, visando assim, um aperfeiçoamento no fluxo de conversação do bot.
Como exemplificação da utilidade dos testes, temos que essa matriz foi gerada como resultado inicial

![Alt Text](https://imgur.com/J6ghvVF.png)

Como podemos observar este tópico necessitava de ajustes em seu fluxo, visto que não atendia as respostas esperadas. Portanto após alguns ajustes e refatorações, este mesmo teste foi realizado para comparação de melhoria e o resultado foi

![Alt Text](https://imgur.com/TJvhvXO.png)

Importante ressaltar que este teste é limitado a um input específico e generalizado, a partir destes inputs observamos que caracteres acentuados necessitam estar declarados em intenções de usuário para captação de mensagens também torna-se necessário adicionar as palavras chaves de cada tópico em suas intents.

Algumas mesclas de conversas mostraram-se bastante satifatórias cobrindo uma margem considerável de acertos, como por exemplo:
![Alt Text](https://imgur.com/xwORnWX.png)

Estes Testes forneceram um recurso relevante para detecção de falhas no bot, servindo como parâmetro de checagem do desempenho geral do projeto.

## Referencial

[1] https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics
[2] https://www.stat.berkeley.edu/~hhuang/STAT141/Lecture-FDR.pdf
