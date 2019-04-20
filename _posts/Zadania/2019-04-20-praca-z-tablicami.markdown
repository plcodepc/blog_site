---
layout: post
title:  "Jak dodawać elementy do tablicy"
date:   2019-04-20 08:35:33 +0200
category: zadania
author: "Admin"
description: "Jak dodać element na początek tablicy a jak na koniec tablicy w jezyku JavaScript"

tags: [tablica , array,js, javascript, spread, rest, poczatek, koniec , metody, sposoby, dodawania ]
snipped: "Jak dodać element na początek a jak na koniec tablicy w języku JavaScript."
full-image: 
comments: true
---

#### Wstęp
We wcześniejszym wpisie pokazywałem jak usuwać elementy z tablicy w JS dzisiaj pokaże jak dodawać elementy do tablicy.
Wyświetlając dynamicznie listę w JS możemy chcieć dodać jakiś element na sam początek lub koniec tej listy. Istnieje wiele sposobów dodawania elementów do tablicy pokażę te najbardziej popularne. 

#### Dodawanie na początek tablicy
Dodać elementy do początku tablicy możemy na kilka sposobów najpopularniejsze to użycie:

- unshift
- spread operator

```js
let arr = [1, 2, 3, 4, 5, 6];
arr.unshift('start');
console.log(arr) // ['start', 1, 2, 3, 4, 5, 6]


let arr2 = [1, 2, 3, 4, 5];
console.log(['start', ...arr2]);
```

#### Dodawanie na koniec tablicy

Dodać element do tablicy na sam koniec możemy przy użyciu metody push lub operator spread.
- push
- spread operator

```js
let arr = [1, 2, 3, 4];
arr.push('end');
console.log(arr);

let arr2 = [1, 2, 3, 4];
console.log([...arr2, 'end']);

```

#### Podsumowanie

Teraz już wiesz jak dodać elementy do tablicy nie ważne czy to na koniec czy początek tablicy. Kolejny raz widać że ES6 wprowadził bardzo dużo ułatwień nie tylko w stosunku do czytelności kodu, ale usprawnień związanych z logiką.