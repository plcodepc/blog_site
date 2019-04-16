---
layout: post
title:  "Usuwanie duplikatów w tablicach JS"
date:   2019-04-16 08:35:33 +0200
category: zadania
author: "Admin"
description: "Jak usunąć powtarzające się elementy w tablicy w języku JavaScript."

tags: [tablica , array, es5, es6, duplikaty, zadania, rekrutacja, algorytmy, js, javascript, spread, filter, metody, sposoby]
snipped: "Sposoby usuwania duplikatów z tablcy w jezyku JavaScipt"
full-image: https://res.cloudinary.com/codepc/image/upload/c_scale,h_550,w_825/v1555397387/posts/array/antonio-garcia-339626-unsplash.jpg
comments: true
---

### Tablice w JavaScript
W JavaScript praca na tablicach jest bardzo ważna. Poznanie metod i sposobów kopiowania, sortowania, modyfikacji tablic będzie bardzo użyteczne w codziennej pracy. Dzisiaj przedstawię dwa sposoby pozbycia się duplikatów z tablicy.

#### Przykład 1. Usuwanie duplikatów z tablicy przy użyciu filter
Istnieje wiele sposobów usuwania duplikató w JS, możmy użyć metod tablicy i porównywać elementy, użyć metod z zewnętrznych bibliotek (lodash). Ale ja pokażę 2 moim zdaniem najprostsze.
```js
var a = [2, 3, 4, 5, 5, 4, 33, "j", "j"];
let arr = a.filter(function(value, index) {
  console.log(index, value); // 0 2 , 1 3, 2 4, ...

  //                          0              =      2
  //                          1              =      3
  //                          2              =      4
  //                          3              =      5
  //                          3              =      5  false
  console.log("Index of", a.indexOf(value), " = ", value, ":::", a.indexOf(value)==index);
  //                                                               true/ false
  return a.indexOf(value) == index;
});
console.log(arr);
```
W przykładzie tym użyliśmy metody filter która iteruje po każdym elemencie tablicy i sprawdza wartość elementu i zwraca nową tablicę jeżeli elemnent spełnia zdefiniowany warunek. W naszym przypadku z tablicy a pobiera wartość elementu i index każdego elementu. W callbacku sprawdzamy czy index dla danej wartości jest taki sam jak index iterowanego elementu. Jeżeli nie zwróci false.
Dzięki temu pozbywamy się duplikatów i możem uzyskać tablicę bez powtórzeń.

#### Przykład 2. Set i spread operator
 Drugi sposob przy użyciu obiektu set i operatora spread.

```js
let names = ['Janusz','Marek','Tomasz','Grzesiek','Tomasz',3 , 3 , 'Janusz', 'Marek', 3];
let setObj = new Set(names);
console.log(arr);
let arr = [...setObj];

//let short =  [...new Set(names)];  // krótka wersja
console.log(arr);
```
W powyższym przykładzie stworzyliśmy nowy obiekt Set i przekazaliśmy do niego naszą tablicę. Jako że set nie posiada duplikatów otrzymaliśmy obiekt tablico-podobny bez powtarzających się elementów. Następnie przy pomocy operatora spread uzyskaliśmy tablicę elementów bez powtórzeń.




