## Histórico de Revisão

|    Data    | Versão |                             Alteração                             |                    Autor                    |
|:----------:|:------:|:-----------------------------------------------------------------:|:-------------------------------------------:|
| 08/04/2019 |   0.1  | Criação do documento  | Davi Alves |
| 10/05/2019 |   0.2  | Atualização do documento | Carlos Aragon |

---

### Elaboração da arquitetura da aplicação

- Elaborar uma arquitetura condizente com a nossa aplicação de forma com que ela possa suprir as necessidades do usuario.

### Elaboração do documento de arquitetura

- Esclarecer a estrutura, componentes e os usos das ferramentas utilizadas na aplicação.

### Treinamento de arquitetura de componentes

- Com o objetivo de mitigar um risco de nível técnico, será feito um treinamento para o time de desenvolvimento sobre a arquitetura utilizada pelo rasa para construção do chatbot.

### Adição de serviço de gerência de requisições(API Gateway)
- Responsável por gerenciar as requisições e a comunicação entre o pylearner e os serviços externos aos quais ele se conecta.

### Adição de serviços externos como microserviços

- Para melhor ajudar no aprendizado do usuario, sera integrado a aplicação alguns auxilios. Deixando assim a ferramenta mais completa.

### Criação de um banco de dados local

- Responsavel por armazenar os dialogos do chatbot para uma analise e melhorias.

### Testes de qualidade do bot

- Testes serão feito com o objetivo de saber se dado um questionamento ao chatbot ele esta respondendo corretamente.

---

### Análise da arquitetura

- Já possuindo boa parte da aplicação arquitetada e implementada, juntamente com o time de desenvolvimento o arquiteto fará análises para identificar possíveis problemas tendo como foco a expansibilidade e flexibilidade do software.
