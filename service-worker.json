// service-worker.js
const CACHE_NAME = 'timetable-talk-v5';
const ASSETS = [
  './',
  './index.html',
  './manifest.json',
  './icons/ttt-192.png',
  './icons/ttt-512.png'
  // add your CSS/JS if you have them, e.g., './styles.css'
];

self.addEventListener('install', (event) => {
  event.waitUntil(caches.open(CACHE_NAME).then(cache => cache.addAll(ASSETS)));
});

self.addEventListener('activate', (event) => {
  event.waitUntil(
    caches.keys().then(keys =>
      Promise.all(keys.map(k => (k !== CACHE_NAME ? caches.delete(k) : null)))
    )
  );
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request, { ignoreSearch: true }).then(cached => {
      return cached || fetch(event.request);
    })
  );
});



