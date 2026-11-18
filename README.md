# 24/7 Radio

Host this whole folder over HTTPS (GitHub Pages, Netlify, Cloudflare Pages…).

## Listener counter setup (free, ~3 minutes)
1. console.firebase.google.com → Add project (no Analytics needed).
2. Build → Realtime Database → Create database.
3. Rules tab → paste, then Publish:

```json
{
  "rules": {
    "radio": {
      "$list": {
        "$client": {
          ".read": true,
          ".write": true,
          ".validate": "newData.hasChildren(['t']) && newData.child('t').isNumber()"
        },
        ".read": true
      }
    }
  }
}
```
4. Copy the database URL (looks like `https://xxxx-default-rtdb.firebaseio.com`) into `const DB_URL = ""` in index.html.

The counter shows people currently tuned in to the same playlist (heartbeat every 20s, counted if seen in the last 60s).
