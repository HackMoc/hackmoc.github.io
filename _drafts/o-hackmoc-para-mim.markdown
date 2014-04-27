---
layout: post
title:  "O Hackmoc para mim"
date:   2014-04-26 22:31:10
author: mbodock
categories: blog
---

Ainda me lembro no inicio, quando comecei a participar do Hackmoc eu dizia a
mim mesmo que seria um bom motivo para acordar cedo aos sábados, não tinha
qualquer pretensão de me divertir fazendo o que faço como trabalho regular.

Hoje foi o dia que descobrir está completamente enganado, há muito tempo não
me divertia e aprendia tanto em um dia como hoje, cheio de altos e baixos.

O projeto do [LegendasTvMirror][legendastvmirror] começava a parecer desnecessário, 
e foi justamente durante a discussão da manhã que novamente o site saiu fora do ar,
interessante como coisas simples são suficientes para impulsionar ainda o
desenvolvimento.

Após algumas horas de modelagem, planejamento e muitas hipótesis, afinal planejar
um _Crawler_ com um site fora do ar é muito difícil, conseguimos criar um projeto
mais conciso que o do encontro passado. Afim de não deixar que as idéias se 
esfriassem partimos logo para a documentação de como cada arquivo deveria funcionar.

Após muito escreve e a todos interromper, sim essa é a atmosfera que eu falei no inicio
poder perguntar a qualquer momento, não ter a pressão de um prazo, não precisar agradar
ninguem que ali não estivesse presente. Isso que eu chamo de diversão... mas voltando,
após muito descrever como tudo funcionaria, sim no subjuntivo, algumas coisas começaram
a não funcionar, o primeiro foi nosso modelo de persistência de dados, o [CouchDB][couchdb], nada
contra o mesmo, de fato gostei muito da idéia, mas para o nosso mirror precisavamos de
algo relacional foi então que fechamos com o [Dataset][dataset] e o Postgres.

Como ninguém é de ferro fizemos aquela pausa para o almoço, algo bem leve, uma
feijoada e meia com aquela cerveja gelada para acompanhar. Passado esse momento
de sacrifício voltamos a frente dos computadores e dalhe códigos!

Tudo ia muito bem até algo inédito acontecer na cidade, chuva, e não foi pouca água não.
Dentro de minutos a copa de onde estávamos já estava toda enxarcada e tivemos que 
fazer outra pausa para dar uma enxugada. Relendo este texto nem parece que escrevemos uma
linha sequer de código, mas já chego lá.

No nosso final de tarde, do que foi hoje o mais longo dos Hackmocs da história, recebemos a
visita de um novo membro, aproveito a ocasião para desejá-lo as boas vindas.

E então finalmente começamos a códificar, mas só um pouco. Iniciamos o desenvolvivendo do 
`magro.py` em um arranjo completamente diferente, programação orientada a palpites. Um volante
e outros 4 olhando e cada um dando sua opinião, em minha visão foi o melhor momento do dia
ter a possibilidade de acompanhar o raciocínio distinto de tantas pessoas e analisar as 
ferramentas que cada um usava enquanto opinavam ou codificavam. Realmente foi uma experiência
inigualável.

Acabou-se então sendo um bom sábado para ser acordar cedo.

[legendastvmirror]: https://github.com/HackMoc/legendastvmirror
[couchdb]: https://pythonhosted.org/CouchDB/
[Dataset]: https://dataset.readthedocs.org/en/latest/
