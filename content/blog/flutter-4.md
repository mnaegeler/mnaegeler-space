---
title: "Flutter: barra de navegação inferior"
date: 2017-12-22T12:50:48-02:00
draft: false
---

Agora que aprendemos (sim, também estou aprendendo ainda) como funcionam os `states` no Flutter podemos avançar um passo me nossa aplicação: a `BottomNavigationBar`.

Aproveitando o código já existente da aplicação, altere o conteúdo da classe `LinkSaverState` para que fique como o código a seguir:

<script src="https://gist.github.com/mnaegeler/0e842b19798b1b43ae45edf0f6ad02fd.js"></script>

Veja o que foi feito:

No início da classe declaramos a variável `_activeScreen` iniciada com `0`, mais tarde você entenderá que está variável será o controle da tela a ser exibida. Logo abaixo criamos uma função `_showScreen` que não tem retorno (`void`) que fará a alteração da variável `_activeScreen`. Como vimos no artigo anterior, para que as alterações que fazemos nas variáveis sejam propagadas precisamos fazer a alteração do estado que é feita pela `setState`.

Após isso trocamos o conteúdo do `body` em Scaffold para que receba uma condicional: se a variável `_activeScreen` for igual a `0`, exibirá o texto "tela 1" centralizado na tela, senão exibirá "tela 2", também centralizado. não é uma forma elegante de se fazer essa condicional, porém é funcional neste exemplo. Veremos como limpar esse código e melhorar sua leitura em um próximo artigo, por momento vamos focar na navegação.

Logo abaixo do body temos a tão desejada propriedade `bottomNavigationBar`. Acredito que ela seja autoexplicativa no que acontece com ela. A propriedade `currentIndex` deve receber um inteiro que será o controle do item (da navegação) ativo. Se você ignorar essa propriedade, quando você clicar em algum item nada acontecerá. Veja que usamos o `_activeScreen` para fazer o controle de index aqui, sendo assim, quando essa tela for carregada o item `0` será exibido. O próximo item, `onTap` é um _event handler_, ou seja, um parâmetro que receba uma função a ser executada em determinado evento, nesse caso um _tap_. O valor da propriedade será o nome da função a ser executada (`_showScreen`). Como alternativa essa função poderia ser passada como anônima (caso tenha interesse, deixe um comentário que explico).

Resumindo: quando clicarmos em algum item da navegação chamará a função `_showScreen` que por sua vez alterará o estado da aplicação.

> **Conceito importante:** A cada mudança de estado, o Flutter fará um novo build do widget, por esse motivo, não temos a necessidade de chamar alguma função que mude a tela a ser exibida (no body).

Tendo  completado isso, nosso aplicativo já começa a ganhar a estrutura que pensei no início.

---

Tem alguma dúvida ou comentário? Deixe-o abaixo:
