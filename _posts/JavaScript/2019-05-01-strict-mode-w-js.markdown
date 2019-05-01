---
layout: post
title:  "Strict mode w JavaScript"
date:   2019-05-01 11:35:33 +0200
category: javascript
author: "Admin"
description: "Do czego służy tryb strict mode w JavaScript"

tags: [sluzy, javascript, es6, strict, mode, es2015, es2018, tryb, kontekst]
snipped: "Do czego służy tryb strict mode w JavaScript, po co używać strict mode."
full-image: https://res.cloudinary.com/codepc/image/upload/c_scale,h_550,w_825/v1556721549/posts/js-logo-codepc-pl.png
comments: true
---

### Wprowadzenie

Strict mode to funkcjonalność wprowadzona w es5, umożliwia tworzenie kodu js w specjalnym kontekscie. Tryb ten kontroluje jakość kodu źródłowego nie pozwalając na błędy które mogą zostać pominięte w trybie domyślnym. 

Możemy użyć tryby ścisłego dla całego pliku lub tylko dla danej funkcji. Aby użyć `strict mode` wystarczy wpisać `use strict` na początku dokumentu lub wewnątrz funkcji w której chcemy bardziej restrykcyjnych warunków w procesie analizy i interpretacji kodu przez silnik JavaScript. Tryb ten będzie poprawnie interpretowany jeżeli użyjemy go na początku dokumentu lub funkcji.

```js
"use strict";
//code 


function fo() {
  "use strict";  
  //code
}
```
#### Po co używać strict mode 

- Strict mode pozwala na tworzenie bardziej bezpiecznego kodu 
- poprzez zastosowanie bardziej restrykcyjnych zasad nie pozwala na strorzenie przypadkowych globalnych zmiennych
- nie pozwala na przypisanie wartości do niezadeklarowanej zmiennej
- nie dozwolone jest wykorzystywanie tej samej nazwy we właściwościach obiektów
- bardziej restrykcyjne zasady mają pomóc w natychmistwowym wyłapaniu potencjalnych błędów, które mogły by zostać niezauważone

#### Niedozwolone operacje w Strict mode

Usuwanie nieusuwalnych właściwości

```js
"use strict";
delete Object.prototype; // This will cause an error
```

Przypisanie wartości do niezadeklarowanej zmiennej

```js
"use strict";
zmienna = 3.14;
```
Nadpisywanie lub używanie słów kluczowych eval i arguments nazw

```js
"use strict";
var eval = 3.14; 
var arguments = 3.14;

```

Przypisanie wartości do nienadpisywalnych obiektów globalnych

```js
"use strict";
var undefined = 5;
var NaN = 4;
```
Ponowne użycie nazwy właściwości w obiektach

```js
function fo() {
    "use strict";

    var test = {
        a: 1,
        b: 2,
        a: 3 // error
    };
}
```

#### Słowa kluczowe zarezerwowane dla js

- mplements
- interface
- let
- package
- private
- protected
- public
- static
- yield

Próba użycia któregoś ze słów jako nazwa, zakończy się błędem.

### Dodatkowo strict mode nie pozwala na:

- nadpisywanie nienadpisywalnych obiektów globalnych tj. NaN, Infinity
- kasowanie zmiennej lub funkcji za pomocą „delete”
- używanie składni ósemkowej (var x = 010)
- nadpisywanie właściwości tylko do odczytu
- użycie zmiennej „eval” jako zmiennej (var eval = „test”)


#### Podsumowanie 

Strict mode w JavaScript nie wybacza błędów ale dzięki temu, że natychmiast zwraca błąd chroni nas od trudnych do zidentyfikowania błędów. 
Jest łatwiejsze naprawienie błędu w części kodu który właśnie stworzyliśmy niż lokalizowanie błędu dla całej aplikacji.