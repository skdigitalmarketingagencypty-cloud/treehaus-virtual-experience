# Treehaus — Virtual Experience

Standalone microsite for the Treehaus virtual walkthrough experience: a hero landing page (`index.html`) and a room-by-room video tour (`tour.html`).

Each file is a fully self-contained, single-file HTML bundle (fonts, images and styles inlined) — no build step, no dependencies, deploy as static files.

## Pages

- `index.html` — landing page with the rotating hero gallery and a link into the tour
- `tour.html` — five room walkthroughs: The Boardroom, The Private Lounge, The Training Room,
  Office and Library, and The Executive Lounge

## Videos

All five room walkthroughs are served from Cloudflare R2 (`pub-7e5c5a58….r2.dev`) — nothing
video-related is committed with the site. They are H.264 1080p masters with the moov atom up
front, so they begin playing before the file finishes downloading.

| Room | R2 object | Length |
| --- | --- | --- |
| 01 The Boardroom | `The Bordroom 2 .mp4` | 0:30 |
| 02 The Private Lounge | `The Private Meeting Room & Lounge .mp4` | 0:41 |
| 03 The Training Room | `The Training Room 2 .mp4` | 0:37 |
| 04 Office and Library | `The Office&Library 2 .mp4` | 0:53 |
| 05 The Executive Lounge | `Executive lounge 2 .mp4` | 0:44 |

To swap a clip, upload the new file to the R2 bucket and point that room's `src` in `tour.html`
at its public URL (URL-encode the spaces and `&`). The chapter timestamps in `tour.html` are cut
to each clip's runtime — re-time them if a replacement clip has a different length.

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
