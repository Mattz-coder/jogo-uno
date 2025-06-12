# Jogo de Cartas UNO (1x1):flower_playing_cards:
**UNO** é um jogo de cartas americano, do tipo "slides", jogado com um baralho impresso especialmente para esse fim. Os princípios gerais do jogo o colocam na família dos oitos malucos, e é semelhante ao tradicional jogo europeu mau-mau. É uma marca da Mattel desde 1992.

Tecnologias utilizadas: **HTML, CSS, JS**

<img src="head.png">

# Bem-vindo ao UNO!:peanuts:
[![forthebadge play-here-uno](play-here-uno.svg)](https://abhisheks008.github.io/UNO/) <img src="https://github.com/abhisheks008/UNO/blob/main/images/uno!.png" height="60px">

# Como funciona este jogo:hourglass:

- O jogo começará automaticamente ao carregar.

- O jogador e a CPU começarão com 7 cartas cada, e uma carta numerada iniciará a Pilha de Jogo. O jogador começará primeiro. O jogador pode clicar em uma carta de valor ou cor correspondente para jogá-la, jogar uma Carta de Ação (Reverter, Pular, Comprar 2, Comprar 4, Curinga) ou, se não houver cartas jogáveis ​​disponíveis, clicar na Pilha de Compra para obter uma nova carta e perder a vez.

- Em seguida, a CPU jogará, jogando uma carta apropriada ou pegando uma da Pilha de Compra.

- Comprar 2 (+2) e Comprar 4 (+4) cartas adicionarão automaticamente seu valor à mão da vítima e avançarão a vez. Cartas de Reverter e Pular pularão a vez da vítima (como há apenas dois jogadores, Reverter se torna essencialmente um Pular). Cartas Curinga podem ser jogadas a qualquer momento.

- O objetivo imediato é ser o primeiro a ficar sem cartas. Nesse momento, as cartas do adversário serão somadas e adicionadas à sua pontuação de acordo com as seguintes regras:
>cartas numeradas de 0 a 9 = valor nominal</br>
>Reverso, Pular, +2 = 20 pontos</br>
>Coringa, Coringa +4 = 50 pontos

- **O primeiro jogador a chegar a 100 perde o jogo.**

## Algoritmo e Fluxo de Trabalho :abacus:

Cartas Numeradas são simples:
```js
red8 = { <br>
    value: 8,<br>
    point: 8,<br>
    color: 'red',<br>
    changeTurn: true,<br>
    drawValue: 0<br>
}
```

As Cartas de Ação receberão um valor para fins de comparação lógica, em ordem crescente de perigo para a CPU em caso de derrota:
```js
greenReverse = {<br>
    value: 10,<br>
    point: 20,<br>
    color: 'green',<br>
    changeTurn: false,<br>
    drawValue: 0<br>
}

orangeSkip = {<br>
    value: 11,<br>
    point: 20,<br>
    color: 'yellow',<br>
    changeTurn: false,<br>
    drawValue: 0<br>
}

blueDraw2 = {<br>
    value: 12,<br>
    point: 20,<br>
    color: 'blue',<br>
    changeTurn: true,<br>
    drawValue: 2<br>
}

wild = {<br>
    value: 13,<br>
    point: 50,<br>
    color: 'any',<br>
    changeTurn: true,<br>
    drawValue: 0<br>
}

wild4 = {<br>
    value: 14,<br>
    point: 50,<br>
    color: 'any',<br>
    changeTurn: true,<br>
    drawValue: 4<br>
}
```
- O gameController usará as propriedades changeTurn e drawValue para determinar de quem é a vez e se alguma carta precisa ser comprada.

## Como a CPU está jogando!:computer:
A CPU terá dois arrays, dos quais ela monitora dois arrays:
```js
cpuHand = []
playableCards = []
```

Com base na última carta jogada e suas propriedades, a CPU percorrerá seu array cpuHand, e qualquer carta que corresponda ao valor ou à cor da última carta jogada será inserida no array playableCards, juntamente com quaisquer curingas que a CPU possa ter.

Como parte da diversão e da estratégia é saber quando jogar suas Cartas de Ação, a CPU randomizará sua estratégia a cada turno, determinada por uma variável Math.Random(). Se o randomizador estiver acima de 0,5, a CPU priorizará o jogo de Cartas de Ação, em um esforço para manter a pontuação de perdas baixa. Se o randomizador estiver abaixo de 0,5, a CPU manterá suas Cartas de Ação para um turno posterior e, em vez disso, jogará Cartas Numéricas. Também haverá lógica para pular o randomizador quando o jogador atingir um determinado número de cartas, momento em que a CPU priorizará apenas as Cartas de Ação.

## Como o Jogador se sente!:red_haired_woman::man:
Semelhante a como o computador controla quais cartas pode jogar, o mesmo acontece com o Controlador de Jogo para o jogador. Caso o jogador clique em uma carta inválida, uma mensagem aparecerá informando isso ao jogador.

Essas mensagens e a tela de Fim de Jogo serão os únicos avisos na tela, em um esforço para minimizar distrações e permitir que o fluxo do jogo seja o centro das atenções.

(Para evitar cliques indesejados, poderá haver uma mensagem "Tem certeza?" se o jogador clicar na Pilha de Compras enquanto segura cartas jogáveis.)

O objetivo é criar um loop de jogo esteticamente agradável, minimalista, porém satisfatório, que seja relaxante e divertido e que – com sorte – os usuários queiram jogar repetidamente.

---------------------------------------------

### ©️ código por , 2025 :link: <a href = "https://mattz-coder.github.io/jogo-uno/" </a>

