---
layout: post
title:  "Display grid"
date:   2019-05-02 05:35:33 +0200
category: css
author: "Admin"
description: "Właściwość grid - css display grid w praktyce"
tags: [grid, css, area, center, align, items, grid-area, fr ]
snipped: "Właściwość grid - css display grid w praktyce"
full-image:
comments: true
---

#### Wstęp
Na wstępie zaznaczę że nie jest to tutorial, ale mój własny skrót dla css grid. Małe przypomnienie właściwości css grid. Jeżeli szukasz wyjaśnień dla poszczególnych właściwości grid - odwiedz: 

- https://css-tricks.com/snippets/css/complete-guide-grid/
- https://www.w3schools.com/css/css_grid.asp
- google


Display: grid to 2 wymiarowy system, oznacza to że możemy ustawiać elementy w dwóch wymiarach w przeciwieństwie do display flex.
W grid mamy możliwość ustawienia wierszy i kolumn dla naszego layoutu. Obecnie css grid jest już standardem wspieranym przez najważniejsze przeglądarki.

```css
.container{
    display: grid; // blok level grid
    display: inline-grid; // inline level grid
}
```
#### Layout

- grid-template-columns
- grid-template-rows
- grid-template-areas 

```css
.item-a {
  grid-area: header;
}
.item-b {
  grid-area: main;
}
.item-c {
  grid-area: sidebar;
}
.item-d {
  grid-area: footer;
}

.container {
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: auto;
  grid-template-areas: 
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer";
}
```
#### Odstępy i centerowanie

- align-items - os Y
- justify-items os X
- place-items - align-items+justify-items
- align-self
- align-content
- justify-content
- place-content = align-content+ justify-content
- grid-gap - grid-column-gap+ grid-row-gap
- . 
- grid-column 1/span2


#### Obszary 

- grid-area
- grid-column-start
- grid-column-end
- grid-column - grid-column: 1/3
- grid-row - grid-row:1/3


#### Rozmiary

- fr
- auto
- px
- minmax(300px 500px)
- repeat(10, fr)
- auto-fill
- auto-fit

#### Auto

- grid-auto-flow
- auto
- fr

#### Podsumowanie
Właściwość display: grid jest bardzo użyteczna. Dzieki niej mamy możliwość zaprojektowania dowolnego layoutu. Poprzez wprowadzenie display grid zmalała potrzeba wykorzystywania frameworków css takich jak np: Bootstrap w który wykorzystuje siatkę tzw grid do rozmieszczania elementów. Dzieki grid pozycjonowanie elementów layoutu jest teraz znacznie łatwiejsze. 