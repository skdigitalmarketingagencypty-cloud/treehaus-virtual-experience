# Treehaus — Virtual Experience

Standalone microsite for the Treehaus virtual walkthrough experience: a hero landing page (`index.html`) and a room-by-room video tour (`tour.html`).

Each file is a fully self-contained, single-file HTML bundle (fonts, images and styles inlined) — no build step, no dependencies, deploy as static files.

## Pages

- `index.html` — landing page with the rotating hero gallery and a link into the tour
- `tour.html` — video walkthroughs of The Boardroom and The Private Lounge

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
