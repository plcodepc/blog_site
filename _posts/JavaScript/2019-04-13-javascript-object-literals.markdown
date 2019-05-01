---
layout: post
title:  "Object literals"
date:   2019-04-13 12:58:11 +0200
category: javascript
author: "Admin"
description: "Szablon obiektu. JavaScript object literals ułatwienia w pracy z obiektami"

tags: [javascript, js, es6, es2015, object, literals, obiekty, szablony]
snipped: "Szablony obiektów w JavaScript - łatwiejsza praca z obiektami"
full-image: 
comments: true
---

ES6 wprowadza wiele usprawnień dotyczących czytelności kodu, oraz lepszego jego zarządzania i debugowania. Jednym z nich jest `Object literal` który pozwala na uniknięcie redundancji (powtarzania). Dzieku temu mamy czystszy kod i bardziej czytelny.

###### Przykład
```js
function fullName(name, lastName) {
    const person = {
        newName:name, // key: value
        newlastName:lastName //key:value
    };

    console.log(person);
}
fullName('Jan', 'Kowalski');
```
Jak widać w powyższym przykładzie `key` jest newName a value będzie to wartość przekazana z name. Tak samo będzie z lastName.
Ale jeśli nadamy tę samą nazwę do klucza to unikniemy powtórzen, i nie będziemy musieli zapisywać dwa razy np: name: name Przykład poniżej:

###### Przykład es6
```js
function fullName(name, lastName) {
    const person = {
        name, // key: value  name:name
        lastName //key:value lastName:lastName
    };

    console.log(person);
}
fullName('Jan', 'Kowalski');
```
#### Podsumowanie
 
Oczywiście to prosty przykład demonstrujący ułatwienia dzięki object literal. Jeżeli będziesz pracować z API i dużą ilością danych to wykorzystanie object literal poprawi znacznie czytelność twojego kodu.
