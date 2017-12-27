---
title: "Flutter: modularizando o código"
date: 2017-12-26T11:06:36-02:00
draft: false
---

No post anterior, chegamos ao ponto de fazer a navegação pela barra inferior funcionar muito bem, porém você deve ter percebido que criar as páginas todas dentro do `body` do Scaffold não seria nada interessante. No exemplo era bastante prático, já que só estávamos escrevendo uma frase em cada tela. Observe o código abaixo:

<script src="https://gist.github.com/mnaegeler/571dc23039566f019add82aba8b8b4e6.js"></script>

> O que eu alterei neste código?

Veja a linha do body no Scaffold, alteramos todo o código inline que tinha para escrever as frases para a criação de dois widgets (`ListBody` e `FormBody`) que estão definidos logo abaixo. Eles também retornam somente um texto centralizado, mas dessa forma estamos modularizando o código, então poderíamos criar um arquivo para cada uma dessas classes e importá-los no arquivo principal.

Caso queira fazer isso, crie um arquivo para cada módulo na mesma pasta `lib` (alguma subpasta também, se desejar) e importe no arquivo onde usará. A sintaxe da importação é `import './list-body.dart';` e deve ser adicionada no início do seu código. Dentro do arquivo coloque a definição do widget (e todo o código que pertença a ele).

Os widgets que criamos são `Stateless`, já que não precisaremos alterar seu estado. O estado que alteraremos será do widget pai pois **quando um estado é alterado no Flutter, o framework irá destruir e reconstruir todos os widgets pertencentes àquele estado**.

---

Tem alguma dúvida ou comentário? Deixe-o abaixo:
