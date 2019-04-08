---
layout: post
title:  "Operator Spread i Rest"
date:   2019-04-08 11:35:33 +0200
category: javascript
author: "Admin"
description: "Operator spread i rest. Trzy kropki w JavaScript, najważniejsze informacje, przykłady użycia oraz krótka charakterystyka."

tags: [spread , rest, operator, operatory, trzy kropki, javascript, es6, rozszerzenia, reszta]
snipped: "Operatory spread i rest. Trzy kropki w JS najważniejsze informacje, różnice, przykłady zastosowania."
full-image: https://res.cloudinary.com/codepc/image/upload/c_scale,h_550,w_825/v1554719841/posts/Operators/spread-operator-rest-operator.jpg
comments: true
---

Operator spread i rest zostały wprowadzone w specyfikacji ES6. Mogą być używanie z elementami iterującymi takimi jak napisy, tablice oraz obiekty. Operator spread/rest wygląda tak samo `... ` Ale  w zależności od kontekstu (jak i gdzie) został użyty możemy powiedzieć czy używamy spread czy rest. 

## Rest 
Rest/Collector/Gather - reszta, zbiera pozostałe elementy w jedną tablicę. Jako że zbiera pojedyncze elementy musi występować jako ostatni np (a,b, ... , z) zwróci błąd a (a,b , ...) będzie już poprawne.


#### Przekazywanie n argumentów do funkcji
```js
function dodaj(...args) {
  let wynik = 0;
  for (let arg of args) wynik = wynik + arg;
  return wynik
}
console.log(dodaj(1)); // -> 1
console.log(dodaj(1, 2)); // -> 3
console.log(dodaj(1, 2, 3, 4, 5, 6)); // -> 21
```
W powyższym przykładzie przekazaliśmy argumenty do funkcji przy użyciu operatora rest dzięki czemu mamy dostęp do natywnych metod tj. map, forEach itp. Gdybyśmy użyli starej metody przekazywania agrumentów musielibyśmy odwoływać się od prototypu funkcji aby mieć dostęp do tych metod.

#### Destrukturyzacja tablic 
W poniższym przykładzie jak można przypisać do każdego elementu tablicy pojedynczą zmienną.
```js
const games = ["Assassin Creed 2", 8.5, 2008, "Ezio Auditore",
 "Rodrigo Borgia", "Desmond Miles"];
const [title, rate, year, ...characters] = games;
console.log(title, rate, year, characters);
```

## Spread 
Spread rozwija/rozszerza dane na wejściu. W operatorze rest zbieraliśmy elementy w tablice. Natomiast w spread rozbijamy elementy tablicy na pojedyncze argumenty.

#### Przekazanie tablicy do funkcji.
Przykładu możemy użyć jeżeli chcemy przekazać listę argumentów opakowaną jako tablica. 
```js
const arrayOfData = [1, 2, 3, 4]
function test(a, b, c, d) {
  // a = 1
  // b = 2
  // c = 3
  // d = 4
  return a + b + c + d;
}
test(...arrayOfData)
```
W powyższym przykładzie przekazaliśmy elementy tablicy do funkcji jako pojedyncze argumenty nie jako cała tablica. Operator spread rozbił tablicę na pojedyncze elementy.

#### Łączenie dwóch tablic w jedną.
```js
const arraySpread = [
  ...[1, 2, 3],
  ...[4, 5, 6]
]
// [1, 2, 3, 4, 5, 6]
```
#### Kopiowanie i rozszerzanie tablic obiektów
```js
  arr = [1, 2, 3];
  arr2 = [...arr]
  console.log(arr2);
```

```js
const toSpread = { key: 'value' }
const objectSpread = {
   ...toSpread,
  secondKey: 'secondValue'
}
console.log(objectSpread);
```
Rozszerzenie obiektu często wykorzystywanie  w redux , tworzy kopię obiektu i dodaje zdefiniowane nowe wartości.

#### Destrukturyzacja
```js
const objekt = {
    imie : "Michał",
    wiek : 21
    zwierze : "kot"
}
const {pet, ...objektbezZwierzaka} = objekt;

console.log(objekt); //kot
console.log(objektbezZwierzaka); // Michał, 21
```
Wyciąganie pojedynczych elementów z obiektu

## Podsumowanie

Operatory spread i rest są bardzo użyteczne i dokładne ich zrozumienie jest bardzo pomocne w pracy. Wprowadzenie `... ` uprościło sposoby kopiowania, przekazywania argumentów itp.
Nie musimy już używać metod takich jak splice, odwoływać sie do prototypu aby skorzystać z metod tablicy itp. 