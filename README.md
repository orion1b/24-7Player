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

## Chat
Uses the same Supabase connection (Realtime broadcast). Messages are never stored anywhere — they only live in the open pages, and everyone's copy is wiped 15 seconds after the last listener tunes out.

## Keeping everyone in sync
The playlist is re-read from YouTube every time the app opens. If the playlist changes while someone has the app open, tap **↻ Refresh list** (a banner offers it automatically when other listeners are on a different version). The "Station xxxxxx" code under the buttons is the playlist version: listeners with the same code hear the same song at the same moment.
