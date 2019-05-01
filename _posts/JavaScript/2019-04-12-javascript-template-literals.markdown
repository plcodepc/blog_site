---
layout: post
title:  "Template literals"
date:   2019-04-12 12:58:11 +0200
category: javascript
author: "Admin"
description: "Szablony łańcuchów, stringów. JavaScript template literals nowe sposoby łaczenia napisów w JavaScript."

tags: [javascript, js, es6, es2015, template, literals, łańcuchy, lancuchy, napisy, szablony, string, interpolacja]
snipped: "Szablony łańcuchów, stringów. JavaScript template literals w akcji"
full-image: 
comments: true
---

Wprowadzenie template literals ( szablony łańcuchów ) znacznie uprościło pracę ze stringami w JavaScript. Dzieki użyciu template literals kod jest czytelniejszy i szybciej możemy osiągnąć zamierzony efekt. Szablony napisów wprowadzisz na klawiaturze używając  backtick, ( klawisz pod esc tzw odwrócony apostrof), znak otwierający i zamykający.



#### Interpolacja stringów

Interpolacja stringów ułatwia wyświetlanie zmiennych pomiędzy napisami. We wcześniejsze wersji es musieliśmy używać znaku `+` aby połączyć dwa napisy ze mnienną. 
##### es5 vs es6+
```js

let name = 'Jan';
let lastName = 'Kowalski';

let n = 1;
let n2 = 5;

//es5
const fullName = name + ' ' + lastName;
console.log(fullName);

//es6
const fullName2 = `${name} ${lastName}`;
console.log(fullName2);

//dodawanie liczb
const fullName2 = `${n + n2} ${lastName}`;
console.log(fullName2);
```
Oczywiście w powyższych przykładach nie widać od razu korzyści z użycia `backticka` ale jeżeli będziemy mieli łańcuchy kilku liniowe kilka zmiennych nie będziemy musieli dodatkowych składników aby np: załamać wyraz w wybranym miejscu. Przykład poniżej.

#### Dzielenie napisów

```js
let date = 2019;
let examp = 'Witaj w\n' + 'roku' + 
' ' + date + ' ' + ' przyjacielu.' ; 

//es6+
let examp2 = `Witaj roku
${date} przyjacielu.`;
```
W pierwszym przypadku trzeba dodać `\n` aby załamać napis w drugim wystarczy wcisnąć enter, podobnie jest z znakiem spacji. Nie musimy już doklejać odstępów.

#### Podsumowanie

Template literals pozwala na bardzo proste i "czyste" wyświetlanie kilku liniowych napisów. Dodatkowo w łatwiejszy sposób możemy wyświetlać zmienne z łańcuchami.

