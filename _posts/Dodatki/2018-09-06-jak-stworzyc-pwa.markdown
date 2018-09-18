---
layout: post
title:  "Budowanie Progressive Web App"
date:   2018-09-17 05:35:33 +0200
category: dodatki
author: "Admin"
tags: [pwa , manifest, service, worker, icon, offline, web , service worker, aplikacja]
snipped: "Jak przerobić stronę na Progressive Web App."
image: https://res.cloudinary.com/codepc/image/upload/v1537300387/posts/pwa-create/pwa-aplikacja-progresywna-icon-pc-codepc.pl-hero.png
full-image: https://res.cloudinary.com/codepc/image/upload/v1537300387/posts/pwa-create/pwa-aplikacja-progresywna-icon-pc-codepc.pl.png
comments: true
---

Jak przerobić stronę na PWA?  We wcześniejszym wpisie napisałem co to jest Progressive Web App a teraz przyszła kolej za przerobienie strony na aplikację progresywną.

Okazuje się że budowa PWA nie zajmuje to wiele czasu a stworzenie prostej aplikacji progresywnej sprowadza się do kilku kroków.
Przypomnę co musimy zrobić aby strona działała w podobny sposób do aplikacji mobilnej. Oczywiście musimy posiadać stronę którą chcemy przerobić :)
- musimy stworzyć `manifest.json`
- stworzyć plik `service-worker.js`
- jeżeli nie posiadamy musimy stworzyć ikony naszej aplikacji w kilku rozmiarach
- hostować naszą stronę na https

Jeżeli stworzyliśmy stronę na jakimś generatorze czy to CMS-ie to zapewne istnieją wtyczki które stworzą za nas potrzebne pliki a my będziemy musieli je tylko zainstalować ale w tym wpisie pokażę jak zrobić to prawie od zera.


##### 1. Tworzenie Progressive Web App zaczniemy od stworzenia pliku `manifest.json` a wygląda on tak:

```json
{
   "name": "twoja-nazwa",
   "short_name": "Codepc",
   "icons": [
       {
           "src": "ścieżka do pliku",
           "sizes": "144x144",
           "type": "image/png"
       },
       {
           "src": "ścieżka do pliku",
           "sizes": "192x192",
           "type": "image/png"
       },
       {
           "src": "ścieżka do pliku",
           "sizes": "256x256",
           "type": "image/png"
       },
       {
           "src": "ścieżka do pliku",
           "sizes": "512x512",
           "type": "image/png"
       }
   ],
   "start_url": "/?utm_source=homescreen",
   "display": "fullscreen",
   "background_color": "#de0F",
   "theme_color": " #FFF"
 }
```


Opis:
- Pole name - będzie wyświetlane pod ikoną po zainstalowaniu aplikacji np: na komputerze.
- Pole icon - potrzebujesz kilku wielkości ikon w zależności od urządzenia.
- Pole start_url - po uruchomieniu aplikacji to będzie twój ekran główny.
- Pole display - 3 opcje fullscreen, standalone, minimalUI, browser.
- color - tło i theme naszej aplikacji jak ją zainstalujemy.

Link do generatora: <a href="https://app-manifest.firebaseapp.com/"> <button class="btn btn-info" >Generator MF </button></a>


### 2. Stworzyć ikony naszej aplikacji.

Ikonę musimy stworzyć ręcznie (np: w darmowym programie takim jak:Adobe XD, Figma) najlepiej w 512x512px a inne rozmiary wygenerować generatorem np: <a href="https://realfavicongenerator.net/"> <button class="btn btn-info" >Favicon</button></a>
A jest to ważne aby posiadać przynajmniej te rozmiary aby można było zainstalować naszą aplikację na urządzeniu.

Zalecane jest aby dodać do sekcji head naszej strony odnośnik do:
```html
  <meta name="theme-color" content="#FFF"/>
```
Ostatnim krokiem jest podpięcie pliku `manifest.json` do naszego projektu:
```html
<link rel="manifest" href="/manifest.json">
```


### 3. Stworzenie i dodanie do projektu service-worker.js


```javascript

const CACHE_NAME = 'codepc';
const CACHED_FILES = [
   '/',
   'plik.txt'
];
self.addEventListener('install', (evt) => {
   evt.waitUntil(
       Promise.resolve()
           .then(() => {
               return caches.open(CACHE_NAME);
           })
           .then((cache) => {
               return cache.addAll(CACHED_FILES);
           })
           .then(() => {
               self.skipWaiting();
           })
   );
});
self.addEventListener('activate', (event) => {
   event.waitUntil(
       caches.keys()
           .then((keys) => {
               return Promise.all(keys
                   .filter((key) => {
                       return key !== CACHE_NAME;
                   })
                   .map((key) => {
                       return caches.delete(key);
                   })
               );
           })
   );
});
function isForeignRequest(request) {
   return (/youtube|google|gstatic|twitter|codepen|cdn-cgi|disqus|github|twimg/)
   .test(request.url);
}

function fetchAndCache(request, cache) {
   return fetch(request)
       .then((response) => {
           cache.put(request, response.clone());
           // console.log('fetch (online)', request.url);
           return response;
       })
       .catch(() => {
           // console.log('fetch (cache)', request.url);
           return cache.match(request);
       });
}
function networkFirst(evt) {
   evt.respondWith(
       caches.open(CACHE_NAME)
           .then((cache) => {
               return fetchAndCache(evt.request, cache);
           })
   );
}
self.addEventListener('fetch', (evt) => {
   if (isForeignRequest(evt.request)) {
       return;
   }
   networkFirst(evt);
});
```
W powyższym kodzie wystarczy zmienić jakie pliki chcemy aby były cachowane.
Co do `Service-Worker-a istnieje kilka strategii jak ma się zachowywać. Oto kilka z nich:
- Cache Only
- Network only
- Cache First
- Network First
- Fastest

Po więcej oraz wyjaśnienie o co dokładnie chodzi zachęcam do przeczytania: <a href="https://jakearchibald.com/2014/offline-cookbook/" > Link </a>

Jeżeli już posiadasz plik service-worker.js musisz poinformować stronę gdzie się znajduje: Umieść poniższy kod w sekcji footer w tagach script wskazując ścieżkę do pliku w którym znajduje się plik.

```javascript
      
   const PATH = '/service-worker.js';
  
   let isServiceWorkersSupport = ('serviceWorker' in navigator);
  
   if (isServiceWorkersSupport) {
       console.log('Will service worker register?');
       navigator.serviceWorker.register(PATH).then(function () {
           console.log("SW registered");
       }).catch(function (err) {
           console.log("SW failed: ", err)
       });
   }
```

###### Info

Gdzie możemy sprawdzić nasz service-worker, manifest, ikony, oraz index pkt naszej aplikacji?
- Chrome CTRL+SHIFT+I zakładka Application mamy Manifest ( tutaj też znajduje się link do instalacji naszej aplikacji jako natywnej), Service-worker, oraz nasze ikony.
Wspomnę aby chwilę poczekać po dodaniu wszystkiego aby sprawdzać czy wszystko działa.
W zakładce Audits możemy sprawdzić również na ile pkt nasza aplikacja spełnia założenia PWA.

#### 4. Hostować naszą stronę przez HTTPS
Używamy protokołu HTTPS dla naszej strony oraz dla wszystkich źródeł (np:zdjęcia) które wykorzystujemy.

### Podsumowanie

Jeżeli wszystko poszło sprawnie powinniśmy mieć w zakładce Audits wysoki wynik PWA. Teraz też powinniśmy mieć możliwość instalacji naszej aplikacji na np: Windows lub telefonie. Chrome CTRL+SHIFT+I zakładka Application > Manifest i po prawej Add to homescreen. Powodzenia.

Pomocne linki:

<a href="https://jakearchibald.com/2014/offline-cookbook/" > https://jakearchibald.com/2014/offline-cookbook/ </a>
<a href="https://codelabs.developers.google.com/codelabs/your-first-pwapp/#0" > https://codelabs.developers.google.com/codelabs/your-first-pwapp/#0</a>
<a href="https://developers.google.com/web/fundamentals/web-app-manifest/" >https://developers.google.com/web/fundamentals/web-app-manifest/ </a>
<a href="https://realfavicongenerator.net/" >https://realfavicongenerator.net/</a>
<a href="https://app-manifest.firebaseapp.com/" > https://app-manifest.firebaseapp.com/ </a>
















