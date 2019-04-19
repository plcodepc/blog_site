---
layout: post
title:  "Domknięcia w JS. Clousure w akcji"
date:   2019-04-19 10:35:33 +0200
category: javascript
author: "Admin"
description: "Mechanizm domknięcia w JavaScript, o co chodzi z clousure i jak możemy go wykorzystać."

tags: [spread , rest, dostęp, funkcja w funkcji, inner, private, javascript, es6, domkniecia, clousure, js, es2015]
snipped: "Mechanizm domknięcia w JavaScript, o co chodzi z clousure i jak możemy go wykorzystać."
full-image:
comments: true
---

W tym posicie pokażę Ci na przykładzie jak działa Clousure w JavaScript i jak łatwo zrozumieć ten mechanizm na przykładach.

#### Clousure definicja
Clousure w JavaScript jest to zbiór wszystkich zmiennych funkcji otaczającej do których ma dostęp funkcja wewnętrzna, podczas tworzenia się. Trzy zasięgi zmiennych dla clousure to 
- własny (zmienna zdefiniowana wewnątrz tej funkcji);
- zasięg funkcji otaczającej funkcję wewnętrzną.
- zasięg globalny (zdef poza funkcją zewnętrzną)

Funkcja `inner` ma dostęp do zmiennej `b` która znajduje się poza nią, jak również do zmiennej c. W momęcie tworzenia funkcji wszystkie te zmienne do których ma dostep funkcja inner to clousure (domknięcie).

```js
var c = 30;  // zasięg globalny
function outer() {
   var b = 10; // zasięg funkcji outer
   function inner() {
         var a = 20; // zasieg własny
         console.log(a+b);
    }
   return inner;
}
var X = outer() // zwracamy funkcje inner()
```
A i należy wspomnieć w powyższym przykładzie funkcja outer zwraca całą funkcje inner tzn. ciało tej funkcji. Wywołanie funkcji zawsze ma nazwa + ().

#### Clousure przykłady.

Ok już wiesz mniej więcej co oznacza termin domknięcie ale jak zobaczyć jak działa? Już pomagam :)

```js
function outer() {
var b = 10;
var c = 100;
   function inner() {
         var a = 20; 
         console.log("a=" + a + " |" + " b=" + b);
         a++;
         b++;
    }
   return inner;
}
var X = outer();  // outer() wywołana pierszy raz
var Y = outer();  // outer() wywołana drugi raz


X(); // X() wywolanie pierszy raz  -> a=20 b=10
X(); // X() wywolanie drugi raz  -> a=20 b=11
X(); // X() wywolanie trzeci raz  -> a=20 b=12
Y(); // Y() wywolanie pierszy raz  -> a=20 b=10

```
Ok o co tu chodzi 

Wywołanie X() po raz pierszy.

- w momęcie wywołania X() ma dostęp do trzech zmiennych
- następuje pierwsze wywołanie a=20 potem odczytujemy b=10 i c=100 
- następnie dodajemy po 1 do zmiennych a=21 i b=11
- koniec wywołania

Wywołanie  X() po raz drugi

- funkcja inner ma dostep znowu do 3 zmiennych  zmienna a tworzona jest od nowa, c tak samo  natomiast zmienna b już istnieje jako clousure dla funkcji inner().
- wynika z tego że a=20, c=100 ale b w pierwszym wywołaniu została zmieniona o 1 a że nie jest tworzona od nowa będzie mieć wartośc 11

Wywołanie X() po raz trzeci

- funkcja inner ma dostep znowu do 3 zmiennych
- a i c zostaną znowu nadpisane a b znowu bedzie z dopełnienia czyli już 12
- nastepuje trzecie wywołanie a = 20 b=12 c=100;

Teraz wywołamy  po raz pierszy Y()
- następuje pobranie przez funkcje inner() a=20 b=10(clousure pierszy raz) c=100;



### Podsumowanie

Clousure to jeden z głównych konceptów JS które warto poznać. W momęcie tworzenia funkcji ustawiamy jakby worek (clousure) na zmienne do których ma dostęp funkcja wewnętrzna. Ustawiamy je raz w momęcie tworzenia każdej z instancji. X(), Y() w powyższym przykładzie. 
