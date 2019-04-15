---
id: doc_arquitetura
title: Documento de Arquitetura
---

# Documento de Arquitetura

## Histórico de Revisão

| **Data** | **Versão** | **Modificação** | **Autor** |
| :------: | :--------: | :-------------: | :-------: |
| 03/04/2019 | 0.1 | Criação do documento e Metas e Restrições de Arquitetura | Ernando |
| 04/04/2019 | 0.2 | Tópico 2 | Davi Alves |
| 05/04/2019 | 0.3 | Tópico 3 | Ernando |
| 06/04/2019 | 0.3.1 | Finalização topico 2, revisão topico 3 | Davi Alves |
| 06/04/2019 | 0.4 | Tópico 1 | Álex Porto 
| 07/04/2019 | 0.5 | Tópico 4 | Eugênio Sales
| 14/04/2019 | 0.5.1 | Revisão de ortografia e correção do diretório da imagem | Álex Porto 

## 1. Introdução
Este documento apresenta a arquitetura de software utilizada no desenvolvimento do ChatBot PyLearner, visando uma visualização dos requisitos e da estrutura com os desenvolvedores.
#### 1.1 Finalidade
Este documento tem como objetivo esboçar uma visão ampla da arquitetura do PyLearner e porque cada decisão arquitetural foi tomada 
### 1.2 Escopo
o Pylearner propõe-se a ajudar programadores a aprender de uma maneira mais interativa e dinâmica, através de uma plataforma que integra tutoriais e chatbot,sobre Machine Learning,podendo tirar dúvidas e orientar a direção em que se deve seguir no assunto .  

### 1.3 Referências
>2018.2-Lino: Documento de Arquitetura. 2018. Disponível em: <a href='https://github.com/fga-eps-mds/2018.2-Lino/blob/master/docs/documento-de-arquitetura.md'><https://github.com/fga-eps-mds/2018.2-Lino/blob/master/docs/documento-de-arquitetura.md></a>. Acesso em: 6 de abril de 2019;

>2018.2-IncluCare_API: Documento de Arquitetura. 2018. Disponível em: <a href='https://github.com/fga-eps-mds/2018.1-IncluCare_API/blob/master/docs/ARCHITECTURE_DOCUMENT.md'><https://github.com/fga-eps-mds/2018.1-IncluCare_API/blob/master/docs/ARCHITECTURE_DOCUMENT.md></a>. Acesso em: 6 de abril de 2019;
### 1.4  Definições, Acrônimos e Abreviações
<li> API: Application Programming Interface </li>
<li> DB: Banco de Dados, <i>DataBase</i> </li>
<li> Front-end: Trabalha com a parte da aplicação que interage diretamente com o usuário </li>
<li> Back-end:  Trabalha na parte de “trás” da aplicação. Ele é o responsável, em termos gerais, pela implementação da regra de negócio. </li>

## 2. Representação da Arquitetura

* **Jupyter Notebook**      

<p style="text-align:justify">&emsp;&emsp;O <i>Jupyter Notebook</i> é um aplicativo Web de código aberto que permite criar e compartilhar documentos que contêm código ativo, equações, visualizações e texto narrativo. Os usos   incluem: limpeza e transformação de dados, simulação numérica, modelagem estatística, visualização de dados, aprendizado de máquina e muito mais.</p> 

* **Rocket Chat**     

<p style="text-align:justify">&emsp;&emsp;<i>Rocket.Chat</i> é uma solução em software de chat de código aberto. Gratuito, ilimitado e totalmente personalizável com hospedagem em nuvem local. Excelente para a integração com chatbot.</p>

* **Rasa**     

<p style="text-align:justify">&emsp;&emsp;<i>Rasa</i> é um conjunto de ferramentas de aprendizado de máquina de código aberto para os desenvolvedores criarem chatbots e assistentes contextuais baseados em texto e voz.
Ele é dividido em duas principais ferramentas:

><i>Rasa NLU</i> que é uma ferramenta open source para processamento de linguagem natural, sendo focada em classificação de intenções e extração de identidades.

><i>Rasa Core</i> que é uma ferramenta livre para construção de sistemas de conversação, como messengers e chat bots.</p>

* **Mongo DB**        

<p style="text-align:justify">&emsp;&emsp;<i>Mongo DB</i> é um programa de banco de dados orientado a documentos de plataforma cruzada gratuito e de código aberto. </p>


* **Docker**

<p style="text-align:justify">&emsp;&emsp;<i>Docker</i> é um projeto de código aberto que automatiza a implantação de aplicativos dentro de recipientes de software, fornecendo uma camada adicional de abstração e automação de virtualização de sistema de nível operacional em Linux, Mac OS e Windows.</p>

* **Microserviços**

<p style="text-align:justify">&emsp;&emsp;A arquitetura de microserviços representa um estilo de arquitetura que é uma abordagem desenvolvida com a finalidade de criar um aplicativo único como uma suite de pequenos serviços, cada um executando seu próprio processo e se comunicando através de mecanismos leves, muitas vezes em uma API com recursos HTTP.</p>

<p style="text-align:justify">&emsp;&emsp;No software descrito neste documento a arquitetura de microsserviços será bastante utilizada. Os módulos serão:</p>

* **Busca no StackOverflow**:
Módulo responsável por efetuar uma busca de uma mensagem de erro gerado na output da celula executada no jupyter.

* **Sugestões para exercicios**: 
Módulo responsável por propor exercicios de plataforma externa.

* **Busca de Datasets**:
Módulo responsavel por efetuar busca de datasets especificos na area de machine learning.

* **Gateway**: Módulo responsável por intermediar a comunicação entre o Back-end e o Front-end.

* **Comunicação entre os serviços**

<p style="text-align:justify">&emsp;&emsp;Comunicação entre os serviços será feita por meio de uma API Gateway, a qual será responsável por fazer o intermédio entre os microsserviços por meio de métodos do protocolo HTTP.</p>

* **Amazon API Gateway**: O Amazon API Gateway é um serviço totalmente gerenciado que facilita para os desenvolvedores criar, publicar, manter, monitorar e proteger APIs em qualquer escala.



## 3. Metas e Restrições de Arquitetura
<p>&emsp;Restrições de arquitetura do projeto:</p>

<ul>

<li>Utilização da ferramenta <i>Jupyter Notebook</i> para computar os códigos gerados pelo usuário e tornar o ambiente mais propício a aprendizagem de forma mais interativa.</li>
<li>Utilização da ferramenta <i>Docker</i> para a virtualização de ambientes, voltado para o desenvolvimento da arquitetura de microserviços do projeto.</li>
<li>Utilização do <i>Mongo DB</i> para criação de um banco de dados relacional.</li>
<li>Utilização do <i>Rasa</i> para a criação e contextualização do <i>Chatbot.</i></li>
<li>Necessário conexão com a internet por se tratar de uma aplicação web.</li>


</ul>

<p>&emsp;Metas do projeto:</p>

<ul>

<li>Tirar duvidas de Machine Learning com o intuito de  aprimorar conhecimento nessa área e auxiliar o usuario com tutoriais.</li>

</ul>


## 4. Visão Lógica 

### Arquitetura do Backend

![](/img/diagramaPacotesBackend.png)


