---
layout: post
title:  "Ideias e argumentos"
date:   2014-05-10 17:53:43
author: myhro
categories: blog
---

Acordei mais cedo do que gostaria, ainda durante a madrugada deste sábado. Não consegui dormir em seguida, mas isto não importava: meu maior compromisso pela manhã era comparecer às 8h ao HackMoc. Acompanhado por [Marcus Bodock][mbodock], cheguei à sede da [Sisqualis][sisqualis] exatamente no mesmo momento em que [Herberth Amaral][bertoca], para minha primeira participação.

Enquanto esperávamos a limpeza da sala ser terminada, fui apresentado ao projeto do [Legendas TV Mirror][ltvmirror], onde me explicaram seus desafios e ideias para abordá-los. Discutimos sobre recuperação da informação, bancos de dados não-relacionais, [_Levenshtein distance_][levenshtein] e alguns outros tópicos por volta de meia hora. Em seguida, fomos para sala, onde a mão começou a ser colocada na massa.

Como qualquer novato, comecei meio perdido, sem saber no que poderia começar a contribuir. Marcus me ajudou a melhorar a interface do Vim com o [vim-airline][vim-airline] (com a dica valiosíssima da instalação das fontes, a partir [deste tutorial][powerline-font-tutorial]) e em seguida [Fernando Marcio][fernando] chegou. Ajudei-o, da mesma forma que Marcus o fez comigo, a configurar alguns detalhes de seu Vim. Uma aplicação imediata do ditado "[_Today you... Tomorrow me_][todayyou-tomorrowme]."

No restante da manhã, adicionei ao projeto testes de estilo de código com o [flake8][flake8], onde trocamos apenas o limite de 80 caracteres por linha da [PEP8][pep8] por 110, e realizei as primeiras modificações no caminho para que o projeto seja tratado como um módulo Python "de verdade". Foi neste momento que aprendi a utilizar a biblioteca [argparse][argparse], uma vez que ninguém mais verifica as combinações dos argumentos do `sys.argv` "na mão".

Ao final, fomos convidados a almoçar um saboroso feijão tropeiro na casa de Herberth (e ainda dizem que não existe "almoço grátis"). Saí de lá com um gostinho de "quero mais", mas de trocas de experiências e conhecimento, não do feijão. É uma pena que os encontros sejam realizados apenas quinzenalmente pois, como disse Marcus, "ainda que não escrevêssemos uma linha de código, só vir aqui discutir estas ideias já valeria a pena".


[argparse]: https://docs.python.org/2/howto/argparse.html
[bertoca]: https://github.com/herberthamaral
[fernando]: https://github.com/fernandomrm
[flake8]: https://flake8.readthedocs.org/
[levenshtein]: https://en.wikipedia.org/wiki/Levenshtein_distance
[ltvmirror]: https://github.com/HackMoc/legendastvmirror
[mbodock]: https://github.com/mbodock
[pep8]: http://legacy.python.org/dev/peps/pep-0008/
[powerline-font-tutorial]: http://powerline.readthedocs.org/en/latest/installation/linux.html#fontconfig
[sisqualis]: http://sisqualis.com.br/
[todayyou-tomorrowme]: http://www.reddit.com/r/AskReddit/comments/elal2/have_you_ever_picked_up_a_hitchhiker/c18z0z2
[vim-airline]: https://github.com/bling/vim-airline
