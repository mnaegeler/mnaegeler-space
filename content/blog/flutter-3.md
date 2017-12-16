---
title: "Flutter: o que vamos contruir?"
date: 2017-12-16T09:52:52-02:00
draft: false
---

Vamos construir uma aplicação bastante simples para salvar links _(como os favoritos do navegador)_ demonstrar alguns princípios básicos dos components Flutter.

A aplicação consiste basicamente em uma tela para salvar link e uma tela para listá-los. Não usaremos banco de dados ainda pelo fato da simplicidade do artigo. Até fiz um sketch para mostrar como ficaria o produto final _(admirem minha habilidade com o pencil)_:

![Sketch](/img/sketch-app.png)

**Claro que por fins de usabilidade um aplicativo não deveria ser estruturado dessa forma, gostaria de fazê-lo nesta estrutura para conseguir demonstrar alguns conceitos como: a navegação pela barra inferior, listas, inputs, botões e o gerenciamento de estados da aplicação.**

Em um post próximo trataremos essa questão melhorando a usabilidade e usando novos recursos.

## Começando

Vamos iniciar pela estrutura básica: o esqueleto. O código abaixo cria somente um texto no centro da tela.

<script src="https://gist.github.com/mnaegeler/26783cc17abef47b5992d6719761e32c.js"></script>

Após isso, vamos separar nosso código para que fique mais limpo e fácil de entender:

<script src="https://gist.github.com/mnaegeler/3cf91d3fc7f1886d32a85c136f973b3b.js"></script>

Note que criamos duas novas `classes`:

  * `LinkSaverApp` que contém a configuração básica do aplicativo;
  * `HomePage` que o `Scaffold` e os elementos da página.

Com isso chegamos ao mesmo resultado que tínhamos porém com uma nova habilidade: **podemos separar essas classes em arquivos diferentes** quando eles começarem a ficar extensos.

As duas novas classes que criamos estendem de `StatelessWidget`, mas o que é isso?

StatelessWidget é um widget que _não terá estado_ (stateless), ou seja, as informações que são contidas nele não serão observadas por alterações, serão computadas e renderizadas e nada mais acontece após isso.

> Então Marcelo, como eu posso observar alterar variáveis e isso ser apresentado na tela?

Para isso precisamos que nossa aplicação tenha um controle de estado. É nesse ponto que usamos um `StatefulWidget`, que como o próprio nome diz, é um _widget com estado_.

Altere a class `HomePage` para que seja um `StatefulWidget` e crie mais uma classe que seja `State` para receber o estado.

Veja o código abaixo e altere a class `HomePage` e adicione ao seu código a classe `LinkSaverState`.

<script src="https://gist.github.com/mnaegeler/c8e2b1901813565f0a856da2365a96ae.js"></script>

Classes que estedem da `State` devem conter o link com uma `StatefulWidget` que em no nosso caso é a HomePage passada na definição da classe (`State<HomePage>` diz que esse estado é referente à HomePage).

No corpo da classe temos uma variável inteira `_counter` que será nosso contador para demonstração de como funcionam estados. Também há a declaração da função `_increment` que quando chamada fará a alteração do valor de `_counter` e fará o `setState` que aplica a alteração.

> Repare em `setState` a sintaxe para função anônima `() { ... }`.

> Falando em sintaxe, você percebeu que muitos lugares o código termina com vírgula? Uma boa prática do Flutter quando se usam várias propriedades em objetos é terminar a linha com vírgula. Isso é chamado de **trailing comma**.

Continuando com a análise, o restante do conteúdo da `LinkSaverState` será basicamente o widget que no código anterior estava em `HomePage`. A diferença está no body do widget que agora substituímos por uma `Column` (veja abaixo o que é) e dentro um texto que informará o valor da variável `_counter` e um botão para chamar a função `_increment` que vimos antes.

`Column` é um widget que faz com que seus filhos seja alinhados em coluna, ou seja, um abaixo do outro. Os filhos são definidos na propriedade `children` que recebe uma lista de widgets `children: <Widget>[]`. A `mainAxisAlignment` faz o alinhamento dos filhos, aqui usamos `center`, mas mude para `start` ou `end` e veja o que acontece. É bastante similar ao flexbox do CSS.

Quando você clicar no botão (`MaterialButton`), a função `onPressed` será chamada que por sua vez é definida como a `_increment`.

No botão você pode brincar também com as cores, troque `Theme.of(context).buttonColor` por `Colors.blue` por exemplo.

Muito bem, até aqui aprendemos como podemos modularizar nosso código, como funciona o state e um pouco de como estilizar nossa tela. Aguarde continuação.

---

Tem alguma dúvida ou comentário? Deixe-o abaixo:
