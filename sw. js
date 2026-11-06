const C='enz-v2';
const PRE=['./','./index.html','./manifest.webmanifest','./firebase-config.js','./icon-192.png','./icon-512.png','./icon-maskable-512.png'];
self.addEventListener('install',e=>{e.waitUntil(caches.open(C).then(c=>c.addAll(PRE)).then(()=>self.skipWaiting()))});
self.addEventListener('activate',e=>{e.waitUntil(caches.keys().then(k=>Promise.all(k.filter(x=>x!==C).map(x=>caches.delete(x)))).then(()=>self.clients.claim()))});
function ok(u){return u.origin===location.origin||u.hostname==='fonts.googleapis.com'||u.hostname==='fonts.gstatic.com'||(u.hostname==='www.gstatic.com'&&u.pathname.indexOf('/firebasejs/')===0)}
self.addEventListener('fetch',e=>{const r=e.request;if(r.method!=='GET'||!ok(new URL(r.url)))return;
e.respondWith(caches.open(C).then(c=>c.match(r,{ignoreSearch:true}).then(hit=>{const net=fetch(r).then(x=>{if(x&&(x.ok||x.type==='opaque'))c.put(r,x.clone());return x}).catch(()=>hit||c.match('./index.html'));return hit||net})))});
