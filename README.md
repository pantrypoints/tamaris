# Tamari's Steak and Seafood Restobar — Website

A SvelteKit 2.x + Svelte 5 website for Tamari's Steak and Seafood Restobar.

## Getting Started

```bash
npm install
npm run dev
```

Then open the printed local URL (usually `http://localhost:5173`).

To build for production:

```bash
npm run build
npm run preview
```

## ⚠️ Important: Add your video file

The jumbotron section plays a background video from `/static/v.mp4`.
**This file is not included** — please add your own video at:

```
static/v.mp4
```

Recommended: an MP4, H.264, under ~15MB, roughly 1920×1080 or 1280×720,
showing food being grilled/plated or the restaurant ambience. If the video
fails to load, the page automatically falls back to a static photo, so the
site won't break — it just won't autoplay a video.

## What's included

- **Jumbotron** — full-bleed background video (`/v.mp4`) with logo, tagline, and CTAs.
- **Promo section** (`src/lib/components/Promo.svelte`) — shows the current promo.
  Edit the `promo` object in that file whenever your promo changes.
- **Dish carousel** (`src/lib/components/DishCarousel.svelte`) — 4 best dishes with
  prices, autoplay + manual prev/next/dots. **Only the Baby Squid Kebab price
  (₱168) is confirmed from your source material** — the other three prices are
  placeholders marked "(approx.)" in the code. Update the `dishes` array with
  your real prices and swap in individual dish photos when you have them.
- **Facebook section** — links out to https://www.facebook.com/TamariGrills/
- **Contact/inquiry form** — client-side validated. It currently just shows a
  "sent" message after a short delay — **you'll need to wire it to a real
  backend** (a SvelteKit form action, an email service like Formspree/EmailJS,
  or your own API) for it to actually deliver messages. See the `TODO` comment
  in `src/lib/components/ContactForm.svelte`.

## Theme

Colors, fonts, and shared styles live in `src/app.css` as CSS variables
(`--color-yellow`, `--color-green`, `--color-black`, etc.) — change them there
to retheme the whole site at once.

## Images

Restaurant photos you provided are in `static/images/`:
- `logo.png` — Tamari's logo
- `promo-3some-tbone.jpg` — current "3-Some T-Bone Treat" promo
- `promo-mothers-day.jpg` — Mother's Day promo spread (used as sample dish photos in the carousel)
- `dish-baby-squid-kebab.jpg` — Baby Squid Kebab
- `team.jpg` — team/buffet photo (used as video poster/fallback)

Swap these out or add more as needed.
