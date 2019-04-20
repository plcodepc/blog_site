---
layout: post
title:  "Kopiowanie tablic w JS"
date:   2019-04-17 08:35:33 +0200
category: zadania
author: "Admin"
description: "Jak utworzyć kopię tablicy w jezyku JavaScript."

tags: [tablica , array, es5, es6, kopiowanie, zadania, rekrutacja, algorytmy, js, javascript, spread, kopia, metody, sposoby,slice]
snipped: "Sposoby na utworzenie kopi tablicy w języku JavaScript"
full-image: 
comments: true
---

Jednym z wyzwan które można napotkać w pracy z tablicami jest utworzenie kopi danej tablicy. Jak to zrobić, pokażę kilka sposobów na utworznie takiej kopi tablicy. Istnieje wiele sposobów tworzenia kopi ale nie możemy użyć poprostu znaku równości ponieważ w JS tablice wskazują na miejsce w pamięci i gdybyśmy użyli znaku równości skopowalibyśmy tylko referencje do oryginalnej tablicy. Zatem!

#### Kopiowanie tablcy - Array.slice
Zgodnie z definicją slice() wydobywa fragment tablicy i zwraca go jako nową tablicę. Jeżeli nie podamy punktu początkowego i końcowego. Zwróci kopię całej tablicy. Jest to zarazem jeden z najszybszych sposobów kopiowania tablicy.
```js
var arr = [1, 2, 3, 4, 5];
console.log(arr);

let arrCopy = arr.slice();
console.log(arrCopy);
```

#### Array.concat
```js
var arr = [1, 2, 3, 4, 5];

let arrCopy = arr.concat();
```
#### Array from
```js
let arr = [1,2,3,4];
let copy = Array.from(arr);
```
#### Spread operator

Użycie spread operatora jest obecnie najszybszą metodą kopiowania tablicy w JavaScript sposób wygląda bardzo prosto i jest dodatkowo bardzo czytelny.
```js
let arr = [1, 2, 3, 4, 5];

arr2 = [...arr];
```

### Tablice wielowymiarowe 
Inna sprawa ma się z tablicami wielowymiarowymi. Jeżeli chcemy stworzyć kopię tablicy 1 lub wiecej poziomów w dół musimy użyć innych metod. Tablica wielowymiarowe to:
```js
let demArray= [[1,2], [1,2,3], [1, [1,2], [2,3]]];
let copy = [...demArray];  // kopia tablicy

copy[0][1] = "B";  // nauszamy oryginał tablicy 
```
Jeżeli chcemy skopiować taką tablicę musimy użyć innego sposobu niż powyższe.
#### Json.parse
```js
let dArray= [[1,2], [1,2,3], [1, [1,2], [2,3]]];

copy = JSON.parse(JSON.stringify(dArray));
copy[0][1] = "B";   // oryginał zostanie nienaruszony
```
Metoda ta oferuje kopiowanie tablicy kilu wymiarowej.

### Podsumowanie

Kopiowanie tablicy w JavaScript jest sprawą prostą. Ważne przy dobraniu sposobu będzie szybkość wykonania takiej operacji, co przełoży się na wydajność, oraz czy kopiujemy tablicę 1 czy kilku wymiarową. Dodatkowo do kopiowania tablic zwykłych czy wielowymiarowych możemy użyć zewnętrznych funkcji np (_.cloneDeep) z biblioteki loadsh.