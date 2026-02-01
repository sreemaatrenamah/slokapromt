const CACHE_NAME = 'sloka-reader-v1';
const urlsToCache = [
  './',
  './SlokaReader.html',
  './manifest.json',
  'https://fonts.googleapis.com/css2?family=NTR&display=swap',
  'https://fonts.gstatic.com/s/ntr/v10/tDRz9KDc0aZSFsmcAYzDTg.woff2'
];

// Install event - cache files
self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => {
      console.log('[Service Worker] Caching files');
      return cache.addAll(urlsToCache);
    }).catch((err) => {
      console.error('[Service Worker] Cache error:', err);
    })
  );
  self.skipWaiting();
});

// Activate event - clean up old caches
self.addEventListener('activate', (event) => {
  event.waitUntil(
    caches.keys().then((cacheNames) => {
      return Promise.all(
        cacheNames.map((cacheName) => {
          if (cacheName !== CACHE_NAME) {
            console.log('[Service Worker] Deleting old cache:', cacheName);
            return caches.delete(cacheName);
          }
        })
      );
    })
  );
  self.clients.claim();
});

// Fetch event - serve from cache, fallback to network
self.addEventListener('fetch', (event) => {
  // Skip non-GET requests
  if (event.request.method !== 'GET') {
    return;
  }

  event.respondWith(
    caches.match(event.request).then((response) => {
      // Return cached response if available
      if (response) {
        console.log('[Service Worker] Serving from cache:', event.request.url);
        return response;
      }

      // Otherwise fetch from network
      return fetch(event.request)
        .then((response) => {
          // Don't cache if not a successful response
          if (!response || response.status !== 200 || response.type === 'error') {
            return response;
          }

          // Clone the response for caching
          const responseClone = response.clone();
          caches.open(CACHE_NAME).then((cache) => {
            console.log('[Service Worker] Caching new resource:', event.request.url);
            cache.put(event.request, responseClone);
          });

          return response;
        })
        .catch(() => {
          // Offline fallback
          console.log('[Service Worker] Offline - using cached version:', event.request.url);
          return caches.match('./SlokaReader.html');
        });
    })
  );
});
