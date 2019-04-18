---
layout: post
title:  "Wartośc null vs undefined vs NaN"
date:   2019-04-18 08:35:33 +0200
category: zadania
author: "Admin"
description: "Porównanie wartości null, undefined, nan of number w JavaScript - różnice."

tags: [tablica , array, es5, es6, duplikaty, zadania, rekrutacja, algorytmy, js, javascript, spread, filter, metody, sposoby]
snipped: "Porównanie różnic pomiędzy wartościami pustymi, niezdefiniowanymi, nie będąca liczbą w języku JavaSCript"
full-image: 
comments: true
---

W pracy z JavaScript możemy napotkać problemy np. przy konwertowaniu zmiennych lub gdy niezdefiniowaliśmy tych zmiennych poprawnie. Poznanie różnic pomiędzy tymi wartościami będzie pomocne w debugowaniu kodu.

#### Not-A-Number

NaN - Wartość nie będąca liczbą. Wartość NaN nie jest równa żadnej liczbie nawet sobie. Aby sprawdzić czy jakaś wartość jest NaN musimy użyć funkcji `isNaN()` NaN możemy otrzymać w kilku przypadkach tj:
- dzieląc 0 przez 0
- dzieląc nieskonczone przez nieskonczone
- mnożąc nieskonczone przez 0
- wykonując operację z NaN
- konwersja jakiejś wartości która nie da się przekształcić na liczbę
NaN jest częscią obiektu globalnego, jest to typ numeryczny ale nie zdefiniowany jako liczba rzeczywista.

```js
NaN <1; // false 
NaN> 1; // false 
NaN == NaN; // false 
// Ale nadal możemy sprawdzić NaN: 
isNaN (NaN); // prawdziwe
```

#### Undefined 

Undefined w JS oznacza wartość niezdefiniowaną. Podobnie jak NaN nie jest przypisana do żadnego obiektu jest własnością najwyższego rzędu. Wartość tą otrzymamy jeżeli stworzymy zmienną ale nie przypiszemy jej żadnej wartości. Wtedy przy sprawdzeniu ta zmienna zwróci undefined.

```js
let zmienna;
console.log(typeof zmiena); //undefined

undefined === undefined // true

```
Jeżeli chcemy sprawdzić czy właściwość obiektu jest undefined możemy użyć operatora typeof który zwróci typ. 
Porównując undefined bez sprawdzania typu wartośc true otrzymamy jedynie w przypadku null oraz w porównaniu do siebie w porównaniu pełnym. W każdym innym przypadku otrzymamy false.

#### Null 

Null nie jest zmienną globalną a wyraża brak przypisania zmiennej do obiektu. Nie znaleziono identyfikacji. Typeof w przypadku null zwróci obiekt null Null jest wartością zdefiniowaną oznacza `nic`. 

```js
null === null // true
null + 1  // 1
```

#### Null vs undefinded w przykładach

```js
null == undefined // true
null === undefined // false

null  = 'wartosc' // ref error
undefined = 'wartosc' // wartosc

null == 0 //false
undefined == 0 // false

null + 1 // 1
undefined +1 //  NaN

undefined / 0 // NaN
null / 0 // NaN

null * 1 // 0
undefined * 1 // NaN

!null // ture
!undefined // true

typeof null // object
typeof undefined // undefined

```
Zrozumienie null, undefined i NaN nie jest skomplikowane ale działania z ich wykorzystaniem nie zawsze mogą wydawać się intuicyjne dlatego warto poświećić chwilę na ich zrozumienie. 

