---
layout: post
title:  "Hoisting: var, let, const"
date:   2019-04-08 11:35:33 +0200
category: javascript
author: "Admin"
description: "Hoisting w javascript. Słowa kluczowe var, let, const. Zasięg zmiennych w js"

tags: [hoisting , wynoszenie, zmienne, let, var, const, js, zasięg, funkcyjny, blokowy]
snipped: "Hoisting w javascript. Słowa kluczowe var, let, const. Zasięg zmiennych w js"
full-image: https://res.cloudinary.com/codepc/image/upload/c_scale,w_825/v1554803036/posts/hoisting/hoisting-let-var-const-codepc.jpg
comments: true
---

#### Hoisting
W JavaScript istnieje mechanizm zwany hoistingiem który wynosi automatycznie na początek zasięgu tylko deklaracje zmiennej. 
```js
var zmienna; // deklaracja
var zmienna = 2; // definicja = deklaracja + inicjalizacja

z = 5; //inicjalizacja
var z; // deklaracja

let zmienna = 2; 
zmienna = 5; //przypisanie nowej wartości
```
```js
    function fn() {
        alert(x); // x jest undefined
        alert(z)  // var z

            let x = 111;
            var z = 333;   
    }
    fn();
```
W pierwszym przypadku kompilator nie wie nic o zmiennej X i wyświetla błąd, w drugim przypadku wie już że istnieje zmienna z ale nie ma ona jeszcze przypisanej żadnej wartości.
Hoisting zmiennych występuje tylko przy deklaracji var.

#### Zasięgi(Scope)
- zasięg blokowy np: warunki, pętle
- zasięg funkcyjny np deklaracje funkcji
- zasięg globalny dostępny wszędzie


#### Var
Użycie słowa kluczowego var pozwala na przypisanie wartości do zmiennej a potem jej deklarację.
```js
auto = "Fiat";
console.log(auto);
var auto;
```
Var posiada zasięg funkcyjny oznacza to że zmienna zostanie wyniesiona na początek funkcji nie ważne czy została zadeklarowana w zasięgu blokowym.
```js
var x = "NAPIS"
function fn() { // zasieg funkcyjny
    var x;
    x = 5;
    console.log("X przed redeklaracja", x);
    for(let i = 0; i < 5; i++){ // zasięg blokowy
        x++;
    }
    console.log("Po redeklaracji " , x);
}
fn();
console.log("X poza zasięgiem funkcji ", x);
```

Dlatego też istnieje możliwośc redeklaracji zmiennej w innym miejscu co powoduje problem gdy używamy var
```js
var x = 10; //  x = 10
{ 
  var x = 2; // x = 2
}
// od teraz x = 2 /  nadpisaliśmy wartość 10
//Przykład 2

var x = 10; // x = 10
{ 
  let x = 2; // x = 2
}
```
#### Let

Zmienna `let ` nie może być redeklarowana 
```js
let x = 999;
let x = "Napis";
console.log(x); // Identifier 'x' has already been declared
```
Let posiada zasięg blokowy jest widoczna tylko w bloku w którym jest zadeklarowana.
```js
let x = 5; // x =5
if(true) {
    let x = 7; // x = 7
}
//x = 5;
```

#### Const 
Zmnienna z użyciem `const ` oznacza stałą,  oraz posiada jak let zasięg blokowy.
```js
const name = "Janusz";
name = "Michał"; // przypisanie nowej wartości niedozwolone

let n = 5;
n = 2; // przypisanie nowej wartości dozwolone
```
Jak widać na powyższym przykładzie do zmiennej `const ` nie możemy przypisać innej wartości.
Zabroniona jest również redefinicja zmiennej tak samo jak w let.
```js
const name; 
```
Jako że const jest stałą którą nie może zostać zmieniona nie możemy zadeklarować samej nazwy bez przypisania wartości.

```js
const cars = ["Fiat", "Audi", "BMW"];
cars[1] = "Ford";
console.log(cars); // ["Fiat", "Ford", "BMW"];

cars.push("Mazda");
console.log(cars); // ["Fiat", "Ford", "BMW", "Mazda"];

```
<br/>
Jak widać tablica zadeklarowana przez const dalej wskazuje na ten sam adres w pamięci ale rozmiar jej został zwiększony.

Za  to w tym przypdaku gdy chcemy zmienić referencje z jednej tablicy na inną wyskoczy błąd.
```js
const cars = ["Fiat", "Audi", "BMW"];
const names = ["Mateusz", "Janusz", "Tomasz"];
cars = names; // nie dozwolone 
```

## Podsumowanie
W celu uniknięcia błędów zalezane jest używanie let/const a całkowite pominięcie var, chociaż są przypadki kiedy użycie var będzie miało taki sam efekt jak let ( bez bloków);
- var (zasięg funkcyjny, mechanizm hoistingu)
- let (zasięg blokowy, brak redeklaracji)
- const (zasięg blokowy, brak redeklaracji, stałość referencji w przypadku tablic i obiektów, stałość wartości dla pojedynczej zmiennej).

