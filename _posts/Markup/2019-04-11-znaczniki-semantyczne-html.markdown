---
layout: post
title:  "Znaczniki semantyczne w HTML"
date:   2019-04-11 11:35:33 +0200
category: markup
description: "Znaczniki semantyczne w HTML5 - nav,article, section, footer, aside, main, header"
author: "Admin"
tags: [markup, html, html5, znaczniki, semantyczne, nav, article, stopka, footer, section, md, jezyk, znaczników]
snipped: "Nowe znaczniki semantyczne w HTML5 - po co, gdzie i jak ich używać"
full-image: https://res.cloudinary.com/codepc/image/upload/v1554995782/posts/html-semantic/semantic_html.png
comments: true
---
#### Wstęp

Semantyczne znaczniki HTML zostały wprowadzone aby poprawić czytelność od strony robotów indeksujących oraz poozwalają na określenie przeznaczenia określonym treścią na stronie. Dzięki temu nasza strona będzie łatwiej pozycjonowana, lepiej odbierana przez roboty indeksujące. Co przełoży się na lepszą pozycje w wyszukiwarce.

List nowych znaczników HTML5
- header (nagłówek)
- nav (nawigacja)
- article (artykuł)
- section (sekcja)
- main (główna zawartość)
- aside (poboczna zawartość)
- footer (stopka)

#### Header

Znacznik header oznacza nagłówek w której umieszczamy zawartość wstępną, wprowadzającą treść do semantycznego rodzica tego tagu w którym został użyty np(artice, aside, section itp). Lub jako wstęp do całego znacznika body. Jako że header przeważnie umieszczany jest na początku względem swego rodzica, często w nim umieszczamy elementy nawigacyjne.

#### Nav 
 
Znacznik nav jak sama nazwa wskazuje powinniej zawierać w sobie elementy nawigacyjne ( listy z linkami do podstron witryny lub innych stron). Dzięki zastosowaniu znacznika nav roboty czytające mogą przeskoczyć do głównej zawartości strony, zamiast każdorazowo czytać listę nawigacji. Oczywiście nie wszystkie listy z linkami muszą znajdować się w tym znaczniku (jeżeli nie jest to np. główna nawigacja).

#### Article

Znacznika article używamy w celu oddzielenia całościowego, kompletnego pewnej odrębnej częsci strony, jak pojedynczy artykuł, wpis na stronie. Ale jako że na stronie może znajdować się kilka artykułów, wpisów znacznik article często jest powtarzalny (występuje kilka razy na stronie). Ponadto warto dodać że w znaczniku article może znajdować się również znacznik article jeżeli wewnątrz pierwszego mamy kilka odrębnych części (wątki, komentarze np na forum).

#### Section
Zawartość która umieścimy wewnątrz tagów section powinna być częscią większej całości. Treść wewnątrz tagów section oznacza tematycznie zgrupowaną zawartość. W każdej sekcji powinna znaleźć się część nagłówkowa która będzie wzkazywać na tematykę treści umieszczonej w tym tagu. Tag section jest podobny do tagu article  i może być użyty w podobnym miejscu z tą różnicą, iż sekcja powinna być częścią jakiejś całości a  artykuł powinien stanowić odrębną całość. W praktyce użycie tagów section/article zależy od programisty.

#### Main

Główna część strony, rózni się od pozostałych znaczników tym że możemy go użyć tylko raz na podstronie. Wewnątrz tego tagu powninniśmy umieścić najważniejszą treść całej podstrony. Znacznik main musi być znacznikiem semantycznie zewnętrznym oznacza to że nie może znajdować się wewnątrz innego znacznika semantycznego np Nie możemy umieśćić main w znaczniku article.

#### Aside

Zawartość boczna, treści powiązane z główną częścią strony, ale nie tak ważne jak treść główna. Wewnątrz znacznika aside może znaleźć się np boczna nawigacja, social-media, reklamy itp.

#### Footer

Stopka oznacza treść końcową nie tylko dla całej podstrony ale tak samo jak header dla innych semantycznych rodziców np section. Znaczników footer na podstronie może znaleźć się kilka.

### Podsumowanie

Znaczniki semantyczne są bardzo pomocne w nadawaniu znaczenia określonym treścią witryny. Używanie ich napewno zwiększy ranking twojej strony. Oprócz znaczników semantycznych możemy używać zwykłych znaczników jak np div ale one powinny być używane do nadawania wyglądu, układu strony. 