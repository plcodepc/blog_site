---
layout: post
title:  "Sytnezator mowy"
date:   2018-09-20 05:35:33 +0200
category: javascript
author: "Admin"
description: "Speech Synthesis API - jest to narzędzie udostępnione w nowoczesnych przeglądarkach.
Zaprezentowane w 2014 roku a obecnie wspierane przez prawie wszystkie przeglądarki desktopowe- bez IE."

tags: [Synthesis , Speech, api, generator, mowy, przegladarka, aplikacja]
snipped: "Speech Synthesis API - jest to narzędzie udostępnione w nowoczesnych przeglądarkach."
image: https://res.cloudinary.com/codepc/image/upload/v1537455091/posts/synthesis%20api/SpeechSynthesis-syntezator_mowy_w_przegladarce-codepc.png
full-image: https://res.cloudinary.com/codepc/image/upload/v1537520247/posts/synthesis%20api/syntezator-mody-w-przegladarce-codepc.pl.jpg
comments: true
---


**Speech Synthesis API** - jest to narzędzie udostępnione w nowoczesnych przeglądarkach.

Zaprezentowane w 2014 roku a obecnie wspierane przez prawie wszystkie przeglądarki desktopowe- bez IE.
Według strony Can I Use dostępność wynosi ponad 80% czyli dużo, dlatego też narzędzie to może być wykorzystywane bez większej obawy o kompatybilność.


## 1. Jak zacząć?
Najprostszym przykładem jak możemy wypróbować Synthesis APi jest wpisanie w konsoli przeglądarki następujący kod a twój mikrofon przemówi.


`speechSynthesis.speak(new SpeechSynthesisUtterance('Wpisz tu co chcesz usłyszeć'));`

Z kolei jeżeli stworzysz plik HTML i umieścisz w nim następujący kod powinieneś mieć już możliwość wpisania w pole tekstowe tekstu i wysłuchania go. 
```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8"> 
    <style>
        body{
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            padding-top: 10%;
            align-items: center;
        }
    #text{
        height: 200px;
        width: 400px;
    }
    .button{
        height: 50px;
        width: 406px;
        margin-top:5px;
        color:white;
        background: rgb(38, 153, 173);
        
        cursor:pointer;
    }
    </style>

    </head>
    <body>
    <h1>Syntesis Speech API</h1>
    <input type="text" id="text">
    <button class="button">Speak</button>

    <script>
    const button = document.querySelector('.button');
    const text = document.querySelector('#text');
    button.addEventListener('click', function() {
    myText = text.value;
    speechSynthesis.speak(new SpeechSynthesisUtterance(myText));
    });
    </script>
    </body>
    </html>
```
Kod można wykorzystać do słuchania artykułów jeżeli nie mamy ochoty czytać :)
Oczywiście prezentowany do tej pory przykład jest najprostszą wersją jaką można stworzyć, ale już widać że ma potencjał.

## 2. Interfejs aplikacji
<br/>
  **SPEECHSYNTHESISUTTERANCE** - odpowiada za zapytanie głosowe, jeżeli przekażemy do niego tekst, usłyszymy go w głośnikach naszego komputera.

Aby to zadziałało musimy stworzyć obiekt utterence.
const utterance = new SpeechSynthesisUtterance(“Nasz tekst”);
A przez to będziemy mieć możliwość zmiany pewnych właściwości tego obiektu.
jak np:

- utterance.rate: prędkość mowy zakres od [0.1 - 10], domyślnie to 1
- utterance.volume: głośność głosu zakres [0 - 1], domyślnie również 1
- utterance.pitch: wysokość głosu  [0 - 2], domyślny to 1
- utterance.lang: jezyk mowy ( BCP 47 language tag, jak en-US or it-Es)
- utterance.text:  wcześniej tekst przekazaliśmy w konstruktorze a możemy ustawić właściwość tekst naszego obiektu. Wielkość 32767 znaków.
- utterance.voice: ustawienie głosu (każda przeglądarka ma inną liczbę dostępnych głosów np: "Microsoft Paulina Desktop - Polish", lub name: "Microsoft Zira Desktop - English (United States).
Jeżeli chcesz zobaczyć listę głosów dostępnych u Ciebie wystarczy wpisać wkleić w konsolę Chrome następujący kod: 

```javascript
const voiceschanged = () => {
  console.log(`Voices #: ${speechSynthesis.getVoices().length}`)
  speechSynthesis.getVoices().forEach(voice => {
    console.log(voice.name, voice.lang)
  })
}

speechSynthesis.onvoiceschanged = voiceschanged

```
<br/>
Gdy już to zrobiłeś możesz wyświetlić listę tym: 
speechSynthesis.getVoices()
Mac posiada większą ilość dostępnych głosów niż Windows.
Po dodaniu większej ilości inputów jest możliwość sterowania szybkością mowy itp - oto prosty przykład na koniec. 

```javascript
<!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Speech Syntesis</title>
    <!-- <link rel="stylesheet" href="style.css"> -->
    <style>
        body{
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            padding-top: 10%;
            align-items: center;
        }
    #text{
        height: 200px;
        width: 400px;
    }
    .button{
        height: 50px;
        width: 406px;
        margin-top:5px;
        color:white;
        background: rgb(38, 153, 173);
        
        cursor:pointer;
    }
    </style>
    </head>
    <body>
    <h1>Syntesis Speech API</h1>
    <input type="range" name="pitch" id="pitchV" min="0.1" max="10" step="1" value="1" >
    <input type="range" name="volume" id="volume" min="0" max="1" step="0.1"  value="0.5">
    <input type="range" name="rate" id="rate" min="0" max="2" step="0.1" value="1" >
    <textarea type="text" id="text"> </textarea>
    <button class="button">Speak</button>

    <script>
        
        const button = document.querySelector('.button');
        const text = document.querySelector('#text');
        const pitch = document.querySelector('#pitchV');
        const volume = document.querySelector('#volume');
        const rate = document.querySelector('#rate');
        
        button.addEventListener('click', function() {
            const utterance = new SpeechSynthesisUtterance(text.value);
            utterance.pitch = pitch.value;
            utterance.volume = volume.value;
            utterance.rate = rate.value;
            speechSynthesis.speak(utterance);
        });
    </script>
    </body>
</html>

```
<br/>
To zaledwie prosta aplikacja po więcej zachęcam do odwiedzenia strony MDN jest tam przykład między innymi z wyborem języka.  A w dokumentacji znajdziesz między innymi jak ustawić zatrzymywanie mowy, wybór głosów i wiele innych funkcjonalności. 
[MDN](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis)