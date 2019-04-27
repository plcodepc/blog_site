---
layout: post
title:  "Rozwiązwyanie zadan cz.1"
date:   2019-04-27 08:35:33 +0200
category: zadania
author: "Admin"
description: "Co wyswietli konsola w następujących zadaniach."

tags: [tablica , array, es5, es6, duplikaty, rekrutacja, consola, popularne]
snipped: "Co wyświetli konsola w poniższych zadaniach - przykłady i odpowiedzi"
full-image:
comments: true
---

#### Wstęp
W tej serii będę pokazywał popularne zadania z JavaScriptu znalezione w sieci z przykładami ich rozwiązań.

#### Zadanie #1
Co wyświetli konsola w poniższym zadaniu?
```js
console.log(false == '0')
console.log(false === '0')
```
Odp:
- true
- false

W pierszym przypadku false jest traktowane jak 0 czyli będzie 0==0 i to jest prawda. W drugim przypdaku też będzie 0 ale operator === porówna typ z `false` który będzie  boolean, natomiast z 0 będzie number, dlatego też konsola wyświetli false.

#### Zadanie #2
Jaki będzie wynik w konsoli?
```js
typeof undefined == typeof NULL

```
Odp: true
Język JavaScript jest `case-sensitive` zapisanie małymi literami różni się od zapisu dużymi literami. Dlatego też w powyższym przypadku typ `NULL` będzie niezdefiniowany (`null` = object). Typeof undefined również będzie undefined, dlatego też konsola zwróci prawdę.

#### Zadanie #3
Co pokaże konsola?
```js
console.log(typeof typeof 1);
```
Odp: string

Idąc od prawej typeof 1 będzie number a typeof number będzie napisem.

#### Zadanie #4

Jaki będzie wynik następującego działania.
```js
for (let i = 0; i < 5; i++) {
  setTimeout(function() { console.log(i); }, i * 1000 );
}
```
Odp: 0, 1, 2, 3, 4
Poprzez użycie let, zmienna i jest wydoczna tylko w zasięgu pętli for. Gdybyśmy użyli var wynik był by 5 5razy.

#### Zadanie #5
Wynik w konsoli będzie?
```js
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);
```
Odp: 
- true
- false 

W drugim przypadku idąc od lewej `3>2` będzie true. True będzie zamienione na 1 co w rezultacie da `1>1` czyli false.

#### Podsumowanie
To już tyle na początek 5 krótki zadań z JavaScript na rozgrzewkę.