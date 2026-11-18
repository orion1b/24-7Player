# 24/7 Radio

Host this whole folder over HTTPS (GitHub Pages, Netlify, Cloudflare Pages…).

## Listener counter setup (Supabase, free, ~2 minutes, no SQL)
1. supabase.com → New project.
2. Project Settings → API → copy **Project URL** and the **anon public** key.
3. Paste them into `SUPABASE_URL` and `SUPABASE_KEY` at the top of the script in `index.html`.
4. If the counter stays at 0, open Project Settings → Realtime and make sure public access to channels is allowed (Realtime "Allow public access").

The counter uses Realtime presence: each page that is tuned in to the same playlist is counted, and people disappear automatically when they close the tab or lose connection. The anon key is meant to be public; don't use the service_role key.

## Floating window
In desktop Chrome / Edge, the **⧉ Float** button opens a small always-on-top window with the song, progress and Tune in/out. Keep the main tab open — the audio plays there. (Not available on phones.)
