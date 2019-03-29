# Estudo de Microserviços

## Introdução
> "Microsserviços" essa nomenclatura representa um estilo de arquitetura que é uma abordagem desenvolvida com a finalidade de criar um aplicativo único como uma suite de pequenos serviços, cada um executando seu próprio processo e se comunicando através de mecanismos leves, muitas vezes em uma API com recursos HTTP.
Esses serviços são construídos em torno de capacidades de negócios e funcionam através de mecanismos de deploy independentes totalmente automatizados. Há o mínimo possível de gerenciamento centralizado desses serviços, que podem ser escritos em diferentes linguagens de programação e utilizam diferentes tecnologias de armazenamento de dados.

* Uma imagem bastante explicativa relacionando sistemas monoliticos com sistemas microserviços:

![Imagem](!https://insights-images.thoughtworks.com/microservicos_nutshell_126263a3524c13ca2476c08a14af4943.jpg)


### Imagem adaptada de um post do blog do [Martin Fowler](https://martinfowler.com/articles/microservices.html)

## Possiveis problemas no uso de microserviços
> Já no inicio dos estudos dessa arquitetura é possivel notar algo que pode ser um grande problema, conhecida como performance. Por serviços dependerem de canais de comunicação como HTTP para conseguir tratar e responder as requisições. Exigem também uma coordenação entre os contratos de serviço para que os consumidores consigam “conversar” com os serviço da maneira que eles esperam, bem como receber as respostas que estão preparados.

>Esse problema é especialmente preocupante conforme você tenha muitas chamadas síncronas entre seus serviços, pois o tempo de espera total para seu sistema responder será igual à soma de todos os tempos de espera das chamadas síncronas. Neste momento você tem duas opções: mudar para uma abordagem assíncrona ou reduzir o máximo que puder o tempo de espera (e a quantidade) das requisições síncronas.

>A falha dos serviços também se torna algo com que deve-se preocupar, ou seja, a atenção para tolerancia de falhas terá de ser dobrada.

>"Qualquer chamado a um serviço pode **falhar** devido à indisponibilidade de um fornecedor e você tem de saber lidar com isso de maneira amigável com o restante do sistema". 

## Possiveis abordagens para iniciar uma arquitetura de microserviços

> A partir de uma ideia onde o serviço é monolitico, pode-se pensar em quebrar essa aplicação e assim montar serviços desacoplados. 

> Começando com a concepção da ideia em si, tambem é possivel projetar a aplicação de modo geral e ir dividindo em menores unidades.

> Separação de alguns tipos de componentes. como:
* Presentation layer – Componentes que lidam com requisições HTTP e implementam APIs ou UIs. Em uma aplicação que tenha uma interface de usuário muito sofisticada terá uma quantidade de código de front-end substancialmente grande.
* Business logic layer – Componentes que são o core da aplicação e implementam as regras de negócio.
* Data‑access layer – Componentes que acessam outros componentes de infraestrutura como bancos de dados e message brokers.


#### ***Referencias***:
[Microservices](https://martinfowler.com/articles/microservices.html)

[Dicas para refatorar um monolito em micro serviços](https://www.luiztools.com.br/post/dicas-para-refatorar-um-monolito-em-micro-servicos/)