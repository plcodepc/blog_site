---
layout: post

---


<link rel="manifest" href="/manifest.json"/>

manifest .json


{
    "short_name": "codepc",
    "name": "codepc",
    "icons": [
        {
            "src": "/assets/images/me/piotr-kowalski-200x200.jpg",
            "sizes": "144x144",
            "type": "image/jpg"
        },
        {
            "src": "/assets/images/me/.jpg",
            "sizes": "192x192",
            "type": "image/jpg"
        },
        {
            "src": "/assets/images/me/.jpg",
            "sizes": "256x256",
            "type": "image/jpg"
        },
        {
            "src": "/assets/images/me/200x200.jpg",
            "sizes": "512x512",
            "type": "image/jpg"
        }
    ],
    "start_url": "/index.html",
    "background_color": "#000",
    "theme_color": "#2a6fa5",
    "display": "fullscreen"
}

service worker. js



const CACHE_NAME = 'piecioshka-1.1.6';
const CACHED_FILES = [
    '/',
    '/404/',
    '/blog/',
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
    return (/youtube|google|gstatic|twitter|codepen|cdn-cgi|disqus|github|twimg/).test(request.url);
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