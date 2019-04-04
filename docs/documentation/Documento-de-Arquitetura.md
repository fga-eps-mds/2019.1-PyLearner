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

### 1. Introdução

### 2. Representação da Arquitetura

* **Jupyter Notebook**      

<p style="text-align:justify">&emsp;&emsp;O <i>Jupyter Notebook</i> é um aplicativo Web de código aberto que permite criar e compartilhar documentos que contêm código ativo, equações, visualizações e texto narrativo. Os usos   incluem: limpeza e transformação de dados, simulação numérica, modelagem estatística, visualização de dados, aprendizado de máquina e muito mais.</p> 

* **Rocket Chat**     

<p style="text-align:justify">&emsp;&emsp;<i>Rocket.Chat</i> é uma solução em software de chat de código aberto. Gratuito, ilimitado e totalmente personalizável com hospedagem em nuvem local. Excelente para a integração com chatbot.</p>

* **Rasa**     

<p style="text-align:justify">&emsp;&emsp;<i>Rasa</i> é um conjunto de ferramentas de aprendizado de máquina de código aberto para os desenvolvedores criarem chatbots e assistentes contextuais baseados em texto e voz.
Ele é dividido em duas principais ferramentas:

><i>Rasa NLU</i> que é uma ferramenta open source para processamento de linguagem natural, sendo focada em classificação de intenções e extração de identidades.

><i>Rasa Core</i> que é uma              ferramenta livre para construção de sistemas de conversação, como messengers e chat bots.</p>

* **Mongo DB**        

<p style="text-align:justify">&emsp;&emsp;<i>Mongo DB</i> é um programa de banco de dados orientado a documentos de plataforma cruzada gratuito e de código aberto. </p>


* **Docker**

<p style="text-align:justify">&emsp;&emsp;<i>Docker</i> é um projeto de código aberto que automatiza a implantação de aplicativos dentro de recipientes de software, fornecendo uma camada adicional de abstração e automação de virtualização de sistema de nível operacional em Linux, Mac OS e Windows.</p>

### 3. Metas e Restrições de Arquitetura
<p>&emsp;Restrições de arquitetura do projeto:</p>

<ul>

<li>Utilização da ferramenta <i>Jupyter Notebook</i> para computar os códigos gerados pelo usuário e tornar o ambiente mais propício a aprendizagem de forma mais interativa</li>
<li>Utilização da ferramenta <i>Docker</i> para a virtualização de ambientes, voltado para o desenvolvimento da arquitetura de microserviços do projeto</li>
<li>Necessário conexão com a internet por se tratar de uma aplicação web</li>

</ul>

<p>&emsp;Metas do projeto:</p>

<ul>

</ul>


### 4. Visão Lógica 