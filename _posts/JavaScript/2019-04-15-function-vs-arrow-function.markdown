---
layout: post
title:  "Funkcja strzałkowa vs zwykła funkcja"
date:   2019-04-15 11:35:33 +0200
category: javascript
author: "Admin"
description: "Fat arrow function kontra regular function w JavaScript różnice"

tags: [return, strzałkowa, funkcja, javascript, es6, arrow, fat, js, es2015, nowa funkcja]
snipped: "Fat arrow konta regular function porównanie. Kiedy użyć funkcji strzałkowej a kiedy zwykłej funkcji."
full-image: https://res.cloudinary.com/codepc/image/upload/c_scale,h_550,w_825/v1555338233/posts/arrow-fn/hello-i-m-nik-281498-unsplash.jpg
comments: true
---

Obecnie w JavaScript istnieją dwa sposoby tworzenia funkcji. Stara metoda używająca słowa kluczowego `function` oraz nowa metoda wykorzystująca `=>` tzw. grubą strzałkę. Zasadniczo obie są jak najbardziej użyteczne. Ale posiadają drobne różnice  które możemy wykorzystać do osiągnięcia zamierzonych efektów.
Definiowanie funkcji
```js
    const głos = function(){ //function expression - brak hoistingu fn
        ...
        return;
    }
    function głos(){ // function declaration  -> hoisting
        ...
        return; 
    };
```
Podobnie możemy zrobić z nowym sposobem definiowania funkcji.
##### Funkcja ES5 VS ES6
```js
function dajGłos(){
    console.log("Woof Wooof");
}
//es6
const dajGłos = () => console.log("Woof Woof");

```

### Zwykła funkcja przed ES6
Sposób  zapisu funkcji:

```js
const red = function(test) {
    // ...
     console.log(test);
}
function() {  // fn anonimowa
  console.log(test);
}

//iife function
(function(test){
  console.log("Test");
})()
```
Regularna fukncja ze słowem kluczowym function jest może mniej czytelna ale nadal ma swoje zastosowanie (objekty, argumenty, this, new target). Najważniejsze to iż definiowanie funkcji w ten sposób:

- zmienia kontekst słowa kluczowego this na siebie.


### Funkcja strzałkowa
Funkcja strzałkowa została w wprowadzona w specyfikacji es6, pozwala na definiowanie funkcji w krótszy i bardziej przejrzysty sposób.
- nie zmienia kontekstu słowa kluczowego  `this`
- krótsza i bardziej czytelna

```js
const red = (test) => {
    // ...
}
const red = test =>  console.log(test);
red(5);

//iife fat arrow
(test => {
  console.log("Test");
})()

```

### this w function vs =>
Pierwszą różnicę widać deklarując metody (funckja w obiekcie).

```js
const car = {
  brand: 'BMW',
  model: '316',
  start: function() {
    console.log(`Driving ${this.brand} ${this.model}`) //ex1
  },
  stop: () => {
    console.log(`Stopped ${this.brand} ${this.model}`) //ex2
  }
}
```
W pierwszym przypadku  przy użyciu słowa kluczowego function consola wyświetli się bez błędu, ponieważ odniesienie do właściwości przy użyciu słowa kluczowego this będzie wskazywało tą funkcję.
W przypdaku funkcji strzałkowej słowo this nie będzie wskazywać na swój kontekst ale na fn rodzica, czyli na zewnątrz. W powyższym przykładzie będzie to obiekt window.

Funkcja strzałkowa nie powiązuje słowa kluczowego `this` w swoim zakresie. Arrow function podniesie zakres i odniesienia do this,  tam gdzie zostało zdefiniowane.


#### Callback ze zmieniającym się kontekstem
W pierwszym przpadku this będzie wskazywać na konteks funkcji nadrzędnej czyli counter funkcja strzałkowa nie zmieni odwołania do `this`.
```js
// ES6 
var obiekt = { 
  id: 10, 
  counter: function counter () { 
    setTimeout (() => { 
      console.log (this.id); 
    }, 1000); 
  } 
};

// ex 2
class Counter {
  counter = 0;
  handleClick() {
    this.counter++;
  }
  constructor() {
    this.handleClick = this.handleClick.bind(this);
  }
}
//vs ES fn

var obiekt = { 
  id: 10, 
  counter: function counter () { 
    setTimeout (function () { 
      console.log (this.id);  
    } .bind (this), 1000);  // zmiana kontekstu this
  } 
};
```
W drugim przypadku gdybyśmy nie zmienili kontekstu this otrzymalibyśmy błąd undefined.

### Arguments  super new.target  w  funkcji strzałkowej
```js
var a = function() {
  return () => console.log(arguments);
};

a(1,2,3)(4,5,6);  // [1,2,3]
```
Funkcja strzałkowa nie definiuje swojego lokalnego konteksu dla arguments, this, super, oraz new.target.

### Podsumowanie

Funkcji z użyciem słowa kluczowego `function` lepiej używać:
- metody obiektów
- zmieniający się kontekst w callback fn

Za to funkcji strzałkowej możemy używać  gdy:
- nie chcemy zmieniać konteksu na który będzie wskazywać słowo kluczowe `this`
- gdy chcemy uczynić nasz kod bardzie czytelny np. funkcje takie jak map, reduce itp.