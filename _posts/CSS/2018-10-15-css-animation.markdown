---
layout: post
title:  "Animowanie elementu w css"
date:   2018-10-15 05:35:33 +0200
category: css
author: "Admin"
description: "Jak stworzyć animację w css. Animacja diva przy użyciu css"
tags: [animation, css, keyframes, transition ]
snipped: "Css animation i @keyframes"
image: https://res.cloudinary.com/codepc/image/upload/v1539615151/posts/css-animation/animation-css-codepcpl.jpg
full-image: https://res.cloudinary.com/codepc/image/upload/v1539615151/posts/css-animation/animation-css-codepc.pl.jpg
comments: true
---

Jak animować dowolny element przy użyciu CSS?

Użycie animation css pozwala na poruszanie elementem HTML bez użycia JavaScript.
Css animation jest wspierane przez prawie wszystkie przeglądarki właściwości potrzebne do animowania elementu to @keyframes i animation.

Na co pozwala CSS animation:
- animowanie elementu poprzez np zmianę jednego stylu na inny.
- można obsłużyć dowolną ilość stylów css
- pozwala na animowanie grafiki svg
- daje możliwość określenia czasu trwania animacji oraz ilości powtórzeń.
- ustawienie opóźnienia animacji
- ustalenie własnej nazwy dla animacji
- wybranie kierunku animacji
- zdefiniowanie krzywej animacji

@keyframes - pozwala na ustalenie przejścia z jednego stylu na inny od początku do końca lub procentowo od 0 do 100%. Przy czym możemy ustawić zachowanie animacji dla dowolnej wartości i tak do 100.

Aby stworzyć animację powinniśmy zdefiniować właściwości dla animacji jak czas trwania, ilość powtórzeń, opóźnienie itp następnie w @keyframes ustawić jak ma się zachowywać i wyglądać element w pozycji wyjściowej. W pozycji od np: 50% i w pozycji końcowej. Oczywiście istnieje też możliwość ustawienia animacji tylko w pozycji środkowej jak na przykładzie poniżej.

## Przykład animacji

<div class="jumbotron anim-wrap" >
<div class="square"></div>
</div>

```css
@keyframes animation {
    50%{
        border-radius:50%;
        transform: translateX(70%) rotate(180deg);
        background: rgb(72, 10, 153);   
    } 
}
.square{
    background: rgb(192, 53, 53);
    width:90px;
    height: 90px;
    border-radius:10px;
    animation-name: animation;
    animation-duration: 5s;
    animation-delay: 1s;
    animation-timing-function: ease-in-out;
    animation-iteration-count: 4;  
}

```

W powyższym przykładzie właściwości animacji definiowane były osobno ale nie jest to wymagane. Możemy oczywiście zdefiniować wszystko w jednej linijce.

```css
div{
   animation: example 5s linear 2s infinite alternate;
}
```

Ta prosta animacja pokazuje jak łatwo i przyjemnie można stworzyć poruszający się div, który dodatkowo zmienia kształt i kolor. Jeżeli zdefiniujemy kroki naszej animacji to dodanie kolejnych właściwości css jest bardzo proste, dzięki czemu możemy stworzyć zaawansowanie animacje.

## Animation :
-  animation-name: example_name
-  animation-duration: 1s, 3s...
-  animation-delay: -1s , 1s..
-  animation-fill-mode: none, forwards, backwards, both
-  animation-direction: normal, reverse, alternate, alternate-reverse
-  animation-iteration-count 2,3... , infinite
-  animation-timing-function: ease, linear, ease-in, ease-out, ease-in-out, cubic-bezier(n,n,n,n) // chrome devtools i właściwości naszej animacji możemy wybrać krzywą.
-  animation-fill-mode: none, forwards, backwards, both

Co do właściwości które możemy animować jest ich bardzo dużo dlatego nie będę wypisywać wszystkich listę można znaleźć pod tym linkiem <a target='_blank' href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties"> <button class="btn btn-info">CSS Animate Property </button></a>

## Podsumowanie

To już wszystko jak widać stworzenie prostej animacji div nie jest zbyt skomplikowanie i pozwala na bardzo dużo. Podobna sprawa ma się z animowaniem grafiki SVG ale ona musi być importowana bezpośrednio do pliku HTML nie jako link. Należy też dodać że do płynnego poruszania elementu na stronie możemy wykorzystać właściwość transition. Ale w tym wpisie skupiłem się tylko na jednym. Powodzenia!
