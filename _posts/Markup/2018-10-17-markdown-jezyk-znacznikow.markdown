---
layout: post
title:  "Markdown - język znaczników"
date:   2018-10-17 13:35:33 +0200
category: markup
description: "Język znaczników markdown Zalicza się do tej samej grupy co HTML. Posiada prostą składnię a jego rozszerzenie pliku to .md"
author: "Admin"
tags: [markdown, markup, znaczniki, md, jezyk, znaczników]
snipped: "Prosty język znaczników. Markdown język prostszy niż html?"
image: https://res.cloudinary.com/codepc/image/upload/v1539770982/posts/markdown/markdown-codepc-image-crop.jpg
full-image: https://res.cloudinary.com/codepc/image/upload/v1539770982/posts/markdown/markdown-codepc-image-intro.jpg
comments: true
---

Markdown - pochodzi z rodziny języków znaczników tz (markup language) który oprócz tekstu zawiera dodatkowe informacje tj. znaczenie tekstu czy chociażby wygląd. 
Markdown jest bardzo prostym językiem znaczników w porównaniu z HTML który, wymaga więcej do osiągnięcia podobnego efektu np: na stronie internetowej.
Pliki z rozszerzeniem md możemy spotkać na stronach takich jak github rownież ten blog używa plików md które są zamieniane na taki html i wyświetlane jako html (źródło strony Ctrl + U).

## Popularne języki znaczników:
- HTML
- MARKDOWN
- XML
- TEX 
- SGML

Oczywiście istnieją jeszcze inne ale skupiłem się na najpopularniejszych.

## Zalety Markdown i języków znaczników:
- prosty do nauczenia
- wystarczy niewiele aby zobaczyć efekt np na stronie 
- daje duże możliwości w formatowaniu tekstu
- istnieje możliwość używania znaczników HTML w plikach z rozszerzeniem markdown a tekst będzie poprawnie interpretowany.
- prostota

## Markdown vs HTML 

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code class="highlighter-rouge">Heading level 1<br>===============</code></td>
      <td><code class="highlighter-rouge">&lt;h1&gt;Heading level 1&lt;/h1&gt;</code></td>
      <td><h1 class="no-anchor" data-toc-skip="">Heading level 1</h1></td>
    </tr>
      <tr>
    <td>
      <code class="highlighter-rouge">
        1. First item<br>
        2. Second item<br>
        3. Third item<br>
        4. Fourth item
      </code>
    </td>
    <td>
      <code class="highlighter-rouge">
        &lt;ol&gt;<br>
          &lt;li&gt;First item&lt;/li&gt;<br>
          &lt;li&gt;Second item&lt;/li&gt;<br>
          &lt;li&gt;Third item&lt;/li&gt;<br>
          &lt;li&gt;Fourth item&lt;/li&gt;<br>
        &lt;/ol&gt;
      </code>
    </td>
    <td>
      <ol>
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
        <li>Fourth item</li>
      </ol>
    </td>
    </tr>
  </tbody>
</table>
Dla porównania przykład użycia markdown vs html w tym samym przykładzie.
W html do uzyskania nagłówka potrzebujemy znacznika `h1` otwierającego i zamykającego w markdown wystarczy znak `#` i tekst.
Stworzenie listy w html wymaga wpisania znacznika `ul` otwierającego i zamykającego. A potem dla każdego elemeentu znaczniki li otwierający i zamykający. Za to w markdown wystarczy myślnik `-' i spacja i tekst.

# Proste znaczniki:

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Element</th>
      <th>Składnia markdown</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Heading</td>
      <td><code># H1<br>
          ## H2<br>
          ### H3</code></td>
    </tr>
     <tr>
      <td><h1 class="no-anchor" data-toc-skip="">Heading level 1</h1></td>
      <td><code class="highlighter-rouge">Heading level 1<br>===============</code></td>
    </tr>
    <tr>
      <td><h2 class="no-anchor" data-toc-skip="">Heading level 2</h2></td>
       <td><code class="highlighter-rouge">Heading level 2<br>---------------</code></td>
    </tr>
    <tr>
      <td>Bold</td>
      <td><code>**bold text**</code></td>
    </tr>
    <tr>
      <td>Blockquote</td>
      <td><code>&gt; blockquote</code></td>
    </tr>
    <tr>
      <td>Ordered List</td>
      <td><code>
        1. First item<br>
        2. Second item<br>
        3. Third item<br>
      </code></td>
    </tr>
    <tr>
      <td>Unordered List</td>
      <td>
        <code>
          - First item<br>
          - Second item<br>
          - Third item<br>
        </code>
      </td>
    </tr>
    <tr>
      <td>Link</td>
      <td><code>[title](https://codepc.pl)</code></td>
    </tr>
    <tr>
      <td>Image</td>
      <td><code>![alt text](img.png)</code></td>
    </tr>
  </tbody>
</table>

## Podsumowanie

Jak widać powyżej składnia markdown jest bardzo przyjemna i nie wymaga dużo wysiłku. W zasadzie z biegu możemy go używać do formatowania tekstu na stronie itp. 
Wpis nie zawiera wszystkich znaczników a ma na celu przybliżenie i pokazanie jak wygląda taki plik i jego składnia. Jak już wspominałem jest to prosty język który jest używany coraz częściej, dlatego warto poznać jego podstawową składnię. Listę wszystkich znaczników markdown można znaleźć na tej stronie: <a target="_blank" href="https://www.markdownguide.org/basic-syntax"> Markdown syntax </a>.








