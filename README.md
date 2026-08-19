# Treehaus — Virtual Experience

Standalone microsite for the Treehaus virtual walkthrough experience: a hero landing page (`index.html`) and a room-by-room video tour (`tour.html`).

Each file is a fully self-contained, single-file HTML bundle (fonts, images and styles inlined) — no build step, no dependencies, deploy as static files.

## Pages

- `index.html` — landing page with the rotating hero gallery and a link into the tour
- `tour.html` — five room walkthroughs: The Boardroom, The Private Lounge, The Training Room,
  Office and Library, and The Executive Lounge

## Videos

Rooms 01–04 are served from `videos/` as relative paths — committed with the site, no external
host needed. They are H.264 1080p/30, CRF 23, `+faststart` (moov atom first, so they begin
playing before the file finishes downloading).

| Room | File | Length |
| --- | --- | --- |
| 01 The Boardroom | `videos/boardroom.mp4` | 0:30 |
| 02 The Private Lounge | `videos/private-lounge.mp4` | 0:41 |
| 03 The Training Room | `videos/training-room.mp4` | 0:37 |
| 04 Office and Library | `videos/office-library.mp4` | 0:53 |
| 05 The Executive Lounge | Cloudflare R2 (`pub-7e5c5a58….r2.dev`) | 0:44 |

The uncompressed masters stay in the project root and are git-ignored. To re-encode one after
replacing a master:

```
ffmpeg -i "The Bordroom 2 .mp4" -c:v libx264 -preset medium -crf 23 -pix_fmt yuv420p -maxrate 5M -bufsize 10M -c:a aac -b:a 128k -movflags +faststart videos/boardroom.mp4
```

The chapter timestamps in `tour.html` are cut to each clip's runtime — re-time them if a
replacement clip has a different length.

## Booking

Every "BOOK" call-to-action links out to the main Treehaus website's facilities page:

- Header **BOOK** buttons → `https://dist-lemon-xi-43.vercel.app/facilities.html#spaces`
- **BOOK THE BOARDROOM** → `https://dist-lemon-xi-43.vercel.app/popups/boardroom.html`
- **BOOK THE LOUNGE** → `https://dist-lemon-xi-43.vercel.app/popups/private-dining.html`

The tour page's "BOOK A VIEWING" and footer "WHATSAPP" links remain direct WhatsApp contact links, since those are for scheduling an in-person viewing rather than a self-service room booking.

## Deploy

Static site, no framework. Any static host works:

```
vercel deploy --prod
```
