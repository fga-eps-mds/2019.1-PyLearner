|Date|Version|Update|Author|
|:--:|:----:|:-------:|:---:|
|02/04/2019|0.1|Criação do documento|Gabriel Ziegler|
|02/04/2019|0.2|Adição definição para <i>Release</i> 1|Gabriel Ziegler|
|02/04/2019|0.3|Adição definição para <i>Release</i> 2|Gabriel Ziegler|

## _Release_ I  

<p align="justify">
A definição de <i>done</i> de <i>issues</i> abertas na primeira <i>release</i>é:
</p>
<ul>
    <li>Critérios de aceitação completos;</li>
    <li><i>Tasks</i>, se houverem, concluídas;</li>
</ul>

<p align="justify">
O <i>ZenHub</i> foi a ferramenta escolhida para auxiliar a equipe na condução do <i>scrum</i>, que utilizará sua funcionalidade de <i>pipelines</i> para fins rastreabilidade e transparência do trabalho a ser realizado na <i>sprint</i>.
</p>
As <i>pipelines</i> utilizadas serão:
<ul>
    <li><b><i>Backlog</i></b> - Todo o <i>Backlog</i> atualizado do produto.</li>
    <li><b><i>Sprint Backlog</i></b> - <i>Issues</i>/histórias que foram alocadas para a <i>Sprint.</i></li>
    <li><b><i>Ice Box</i></b> - <i>Issues</i>/histórias que foram retiradas da coluna <i>In Progress</i> numa <i>Sprint.</i>por algum motivo de força maior.</li>
    <li><b><i>In Progress</i></b> - <i>Issues</i>/Histórias sendo trabalhadas no momento.</li>
    <li><b><i>Review</i></b> - Necessário revisão de EPS.</li>
    <li><b><i>Done</i></b> - <i>Issue</i>/história concluída.</li>
</ul>  

<p align="justify">
Assim que uma história técnica ou de usuário respeitar a definição de pronto acordada, e, caso possua testes unitários, e a <i>build</i> esteja passando, o responsável por ela abrirá um <i>Pull Request</i>, e assim que for revisado por um membro de EPS, que, caso aceite a história, ela poderá ser movida para <i><b>done</b></i>.    

A cobertura de testes deverá estar em 30%.
</p>

## _Release_ II

<p align="justify">
Para a <i>Release II</i>, a definição de pronto sofrerá mudanças.
Os critérios de pronto corresponderão a:
<ul>
    <li>Critérios de aceitação completos;</li>
    <li><i>Tasks</i> concluídas;</li>
    <li>Testes unitários completos.</li>
</ul>

As <i>pipelines</i> utilizadas no <i>ZenHub</i> corresponderão a:
<ul>
    <li><b><i>Backlog</i></b> - Todo o <i>Backlog</i> atualizado do produto.</li>
    <li><b><i>Sprint Backlog</i></b> - <i>Issues</i>/histórias que foram alocadas para a <i>Sprint.</i></li>
    <li><b><i>Ice Box</i></b> - <i>Issues</i>/histórias que foram retiradas da coluna <i>In Progress</i> numa <i>Sprint.</i>por algum motivo de força maior.</li>
    <li><b><i>In Progress</i></b> - Histórias sendo trabalhadas no momento.</li>
    <li><b><i>Testing</i></b> - Com critérios de aceitação completos e <i>tasks</i> concluídas, a história agora deverá ser testada.</li>
    <li><b><i>Review</i></b> - Necessário revisão de EPS.</li>
    <li><b><i>Done</i></b> - <i>Issue</i>/história concluída.</li>
</ul> 

<p align="justify">
Assim que uma história técnica ou de usuário respeitar a definição de pronto, e a <i>build</i> esteja passando, o responsável por ela abrirá um <i>Pull Request</i></a>, e assim que for revisado por um membro de EPS, que, caso aceite a história, ela finalmente poderá ser dada como concluída.    

A cobertura de testes deverá estar em 90%.
</p>
