---
layout: post
title:  "Właściwość css transition"
date:   2018-10-15 05:35:33 +0200
category: css
author: "Admin"
description: "Css transition jak używać i jak poruszać elementem."
tags: [animation, css, keyframes, transition, ease, click, hover]
snipped: "Stworzenie prostej interakcji użytkownika ze stroną."
image: https://res.cloudinary.com/codepc/image/upload/v1539615151/posts/css-animation/animation-css-codepcpl.jpg
full-image: https://res.cloudinary.com/codepc/image/upload/v1539615151/posts/css-animation/animation-css-codepc.pl.jpg
comments: true
---

Jak wiadomo aby sprawić aby element poruszał się na stronie, reagował na działanie użytkownika np: najechanie myszą lub kliknięcie nie trzeba używać właściwości animation Wystarczy użyć css transition który stworzy efekt animacji.

Css transition musi zostać wywołane przez najechanie na element lub kliknięcie użytkownika w dany element. Nie jest wywoływanie automatycznie po załadowaniu strony, jak w przypadku css animation.
Efekt najechania myszy możemy uzyskać przy użyciu tylko CSS co w połączeniu z właściwością transiton jest bardzo często wykorzystywanie na stronach do tworzenia prostych efektów.

## Na co pozwala CSS transition:
- animowanie elementu poprzez np zmianę jednego stylu na inny.
- można obsłużyć dowolną ilość stylów css
- pozwala na animowanie grafiki svg
- daje możliwość określenia czasu trwania animacji.
- zdefiniowanie krzywej poruszania obiektu.

## Jak używać css transition aby działał poprawnie: 
- ustalamy style dla naszego elementu 
- definiujemy style jakie ma przypisać nasz element po interakcji użytkownika.
- ustawić czas trwania przejścia

Ważne jest aby zdefiniować `transition` w pierwszej fazie wtedy animowany będzie również efekt powrotu do bazowych stylów.
Przykład:
<div class="button"> Hover </div>

```css
.button{
    background:red;
    transition: all 3s ease;
}
.button:hover{
    background:blue;
}
```
W pierwszym przypadku widać jak animacja przejścia z jednego stylu na inny jest płynna w obu kierunkach. Z kolei w drugim przykładzie animacja w jedną stronę jest płynna a powrót następuje natychmiastowo, co już nie wygląda dobrze. 
<div class="button2"> Hover </div>

```css
.button2{
    background:rgb(255, 0, 0);
    text-align: center;
}
.button2:hover{
    background:rgb(11, 2, 92);
    transition: all 3s ease; 
}
```
Transition możemy ustawić dla wszystkich właściwości naszego elementu jak i dla pojedynczej.
W przykładzie powyżej ustawiłem wartość `all` a mogłem wybrać pojedynczą właściwość css i dla niej tylko zdefiniować efekt przejścia.

## CSS Transition właściwości: 

- transition: zdefiniowanie wszystkich poniższych właściwości w jednej linijce.
- transition-delay: 1s 2s
- transition-duration: 1s, 2s
- transition-property: all, background, transform , itp..
- transition-timing-function:linear, ease , ease-in, ease-in-out, cubic(n,n,n,n);

We właściwościach musimy ustawić transition: (property duration timing-function) aby efekt przejścia zadziałał.

## Podsumowanie:
CSS transition jest bardzo często wykorzystywane na stronach. Wg strony CanIUse wsparcie jest prawie 100% więc nie ma żadnych przeszkód aby zastosować tą właściwość css. Tworzenie efektu przejścia jest bardzo szybkie i nie zajmuje dużo czasu. Listę właściwości css które mogą być wykorzystane przy transition znajdziesz tutaj: <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties"><button class="btn btn-info"> Css transition </button></a>