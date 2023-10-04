# Web to app
New web to app code, easy to install and **Free**
> [!IMPORTANT]\
> You need to have a website.
>
# Installing process

(1/3) In your **index.html** file, you need to paste this code: 

```html
<link rel="manifest" href="/manifest.json">
    <script>
        if('serviceWorker' in navigator) {
            navigator.serviceWorker.register('/sw.js')
                .then(function() { console.log("Service Worker activated"); });
        }
    </script>
```

(2/3) Then create a file named **manifest.json** and put this code: 

```json
{
    "short_name": "Your short app name",
    "name": "Your app name",
    "start_url": "/",
    "display": "standalone",
    "icons": [
        {
            "src": "your logo.png",
            "type": "image/png",
            "sizes": "192x192"
        },
        {
            "src": "your logo.png",
            "type": "image/png",
            "sizes": "512x512"
        }
    ]
}
```

(3/3) And finally create another file named **sw.js** and put this code:
```javascript
self.addEventListener('install', function(event) {
    event.waitUntil(
        caches.open('miapp').then(function(cache) {
            return cache.addAll([
                '/',
                '/index.html',
                '/styles.css',
                '/app.js' 
                
            ]);
        })
    );
});

self.addEventListener('fetch', function(event) {
    event.respondWith(
        caches.match(event.request).then(function(response) {
            return response || fetch(event.request);
        })
    );
});
```
- - - -
# Editing

> [!NOTE]\
> If you dont wan't to save your files into the user (**recommended for who update his web every day**), just delete the code of **sw.js** file.

(1/2) Your app name goes here: 
```json 
    "short_name": "Your short app name",
    "name": "Your app name",
```

(2/2) Your app logo goes here:
```json
"src": "your logo.png",
```
- - - -
# **Created by Javi17mod**
![javi17mod](https://raw.githubusercontent.com/Javi17mod/imagenes/2ec2c4d43adae20888f57989be249329191bcd6f/IMG_2220.png)
