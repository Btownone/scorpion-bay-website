# Scorpion Bay Baja 🦂🌊

The definitive online guide to **Scorpion Bay (San Juanico), Baja California Sur** —
surfing, fishing, ATV adventures, places to stay, local food, and the businesses that make the town run.

Built on the **Blue Ocean Standard** tourism platform, designed to be a repeatable template for other destinations.

## Quick start

It's a single static file — just open it:

```bash
open index.html
# or serve it:
python3 -m http.server 8080   # then visit http://localhost:8080
```

## What's inside

- **Cinematic hero** (drop in Zachary's surf/ATV video or a photo)
- **Local Highlights** — Surfing · Fishing · ATV · Food · Stay
- **Featured businesses** — Scorpion Bay ATV Rentals + Scorpion Bay Storage (with booking/inquiry forms)
- **Tourism Directory** — filterable: Stay · Food & Drink · Activities · Services
- **Interactive map** — surf spots, our locations, hotels, restaurants, boat launches (free, no API key)
- **Community** — San Juanico history, surf report, fishing seasons, events
- **List-your-business** lead form (marketplace / featured-listing groundwork)
- **Inline Edit Mode** — `?edit=1` to edit text & photos in the browser

## Make it your own / spin up a new town

Everything is driven by the `SITE` config object near the top of the `<script>` in `index.html`.
Copy the folder, edit `SITE`, deploy. See **CLAUDE.md** for the full playbook.

## Deploy

Static — host on Render / Netlify / Cloudflare Pages / GitHub Pages and point a custom domain at it (free SSL).
Suggested domain: **scorpionbaybaja.com**.
