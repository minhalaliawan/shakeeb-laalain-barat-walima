# Barat &amp; Walima — Ahmed Shakeeb &amp; Dr. Laalain Fatima

A standalone invitation covering the **Barat and Walima only**. Single static
file, no build step, no dependencies, no backend. Open `index.html` in a browser
and it works.

This is a **separate project** with its own repository and its own deployment,
independent of the full three-event site and of the Walima-only site.

---

## The events

| Event  | Day      | Date            | Time    | Venue |
|--------|----------|-----------------|---------|-------|
| Barat  | Saturday | 24 October 2026 | 5:30 PM | Fortress Events Complex, Islamabad Expressway, opposite PWD |
| Walima | Sunday   | 25 October 2026 | 5:30 PM | Aura Grande Event Complex, 2 Service Road E, Golra NPF, E-11/4 |

RSVPs are sent to WhatsApp **+92 333 5101170**.

The countdown targets the **Barat — 24 October 2026, 5:30 PM PKT**.

---

## What it does

- Ornate gate intro — twin gold-lattice doors that swing open from a wax seal
- Background music, starting on the tap, with a floating toggle
- Bismillah header, animated gold mandala, drawn Mughal arch
- Live countdown to the Barat
- Both events on a gold timeline that fills as you scroll, each with
  **Location** and **Add to Calendar** buttons
- RSVP form that composes a WhatsApp message — no backend needed
- Falling rose petals and gold dust on canvas, scroll reveals, card tilt

---

## Personalised links

Add a query string and the page adapts, then **wipes it from the address bar**
so the guest never sees the code.

```
https://your-site.com/?to=Kamran%20Uncle&event=b
```

### `to=` — the guest's name
Greets them in the hero and pre-fills the RSVP form.

### `event=` — narrow it to one event

| Code | Shows | Countdown targets |
|------|-------|-------------------|
| *(omitted)* | Barat + Walima | Barat |
| `b` | Barat only | Barat |
| `w` | Walima only | Walima |

With a single event the RSVP form drops the "which events" dropdown and the
WhatsApp message names that event directly.

Both values are remembered in `sessionStorage`, so a refresh keeps them.

### Examples

```
?to=Ahsan%20Bhai              → both events, greeted by name
?to=Dr%20Sana&event=w         → Walima only
?event=b                      → Barat only, no name
```

Spaces must be written as `%20`.

---

## Optional files

Drop these into `assets/` — each is optional and the site degrades cleanly
without it:

- `music.mp3` — replaces the online background track
- `barat.jpg`, `walima.jpg` — the printed cards. When present, a **View Card**
  button appears on that event and opens the image full screen. When absent the
  button removes itself.

---

## Editing content

Everything lives in `index.html`.

- **Dates, times, venues** — in the `<article class="ev">` blocks
- **WhatsApp number** — `var PHONE = '923335101170';` near the bottom of the script
- **Countdown target** — `var target = new Date('2026-10-24T17:30:00+05:00')`,
  plus the per-event targets in the `evKey` branches
- **Colours** — the `:root` block at the top of the `<style>`
- **Map links** — the `Location` buttons use Google Maps *search* queries, which
  resolve to the right venues. Swap in exact `maps.app.goo.gl/...` pins if you
  prefer.

---

## Deploying

Static hosting, nothing to build.

**Vercel**

```bash
npx vercel --prod
```

Or drag the folder onto [vercel.com/new](https://vercel.com/new). `vercel.json`
is already set up.

**Netlify** — drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop).

---

## Local preview

```bash
npx --yes serve -l 4323 .
```

Then open `http://localhost:4323`.
