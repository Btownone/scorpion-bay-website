# CLAUDE.md — Scorpion Bay Baja site

Instructions for Claude Code when editing the **Scorpion Bay Baja** tourism site (for Zachary).

## What this is

A single-file tourism guide + local business directory + lead-gen site for **Scorpion Bay (San Juanico), Baja California Sur**. One HTML file (`index.html`) with inline CSS + JS. No build step, no framework, no package.json. Edit directly.

It's modeled on the **Blue Ocean Standard (BOS) premium layout** — cinematic full-bleed hero, fixed nav, stats bar, bento highlight grid, featured-business sections, parallax banners, and scroll-reveal — but adapted from fishing-charters to a whole-town tourism guide.

It is also a **reusable template**: the entire site is driven by one `SITE` config object near the top of the `<script>`. Copy the folder, edit only `SITE`, and you have a new town. (See "Spin up a new town" below.)

## The two businesses we feature

- **Scorpion Bay ATV Rentals** — `#atv` section. Fleet, pricing, safety, "Reserve Your ATV Today" form. Driven by `SITE.atv`.
- **Scorpion Bay Storage** — `#storage` section. Unit types, "Request Availability" form. Driven by `SITE.storage`.

## How to make changes

Almost everything lives in the `SITE` object — change data there, the page re-renders:

- **Business name / town / contact:** `SITE.name`, `SITE.town`, `SITE.contact`.
- **Hero video or photo:** `SITE.hero` — set `videoMp4` (hosted .mp4 URL), or `youtubeId`, or `image`. Leave all blank for the animated gradient hero. **Don't commit video files into the repo** — host them externally and reference by URL.
- **Stats bar:** `SITE.stats`.
- **Highlight cards:** `SITE.highlights`.
- **ATV fleet & pricing:** `SITE.atv.options` / `.includes` / `.image`.
- **Storage units & pricing:** `SITE.storage.options` / `.includes` / `.image`.
- **Directory listings:** `SITE.listings` (each has `cat`, `type`, `name`, `desc`, `img`, optional `featured`, `phone`, `web`). Filter tabs come from `SITE.dirCategories`.
- **Map pins:** `SITE.pins` + `SITE.map.center` / `.zoom`. Colors in `SITE.pinColors`.
- **Community copy / surf report / events:** edit the text in the `#community` section directly (marked `data-edit`).
- **Fishing seasons:** `SITE.fishSeasons`.

Static headline text (hero, section titles) is marked `data-edit="..."` in the HTML — find the words and change them, or use Edit Mode (below).

## Edit Mode (for Zachary, no code)

Add `?edit=1` to the URL (e.g. `scorpionbaybaja.com/?edit=1`). Click any text to edit it; click any featured photo to paste a new image URL. Hit **Save changes** — edits persist in that browser via localStorage. This mirrors the BOS v3 in-place editor. (For permanent edits that everyone sees, change `SITE` in `index.html`.)

## Lead forms

The three forms (ATV, Storage, List-your-business) POST to `SITE.formEndpoint`. Paste a [Formspree](https://formspree.io) (or similar) endpoint there. If it's blank, forms **fall back to opening the visitor's email client** pre-filled to `SITE.contact.email` — so they always work, even with no backend.

## Images

Placeholders use Unsplash CDN URLs and are clearly thematic (surf / desert / ATV / Baja). Replace `img:` URLs in `SITE` with Zachary's real photos. Every image sits on a gradient base, so a broken/missing URL still looks intentional. **Don't commit large photos/videos** — host on Cloudinary / R2 / Vimeo and reference by URL.

## Map

Leaflet + CARTO dark tiles — **free, no API key**. Centered on San Juanico (`26.2553, -112.4769`). Add/move pins in `SITE.pins`.

## Spin up a new town (the template play)

1. Copy this folder → `new-town-website/`.
2. In `index.html`, edit the `SITE` object: `name`, `town`, `contact`, `hero`, `stats`, `highlights`, the two featured businesses (or replace with that town's anchor businesses), `listings`, `map.center`, `pins`, `community` copy.
3. That's it — nothing else needs to change. Deploy.

This is the proof-of-concept for selling turnkey tourism sites to other Baja towns, surf/fishing destinations, and municipal tourism boards.

## Deploy

Static single file — host anywhere (Render static site, Netlify, Cloudflare Pages, GitHub Pages). Point a custom domain (e.g. `scorpionbaybaja.com`) at it; free SSL from the host. Suggested: same Render pattern as the other BOS client sites (commit to `main` → auto-deploy).

## Relationship to the BOS monorepo

This is a **standalone** site, deliberately decoupled from the `success-sportfishing` (Blue Ocean Standard) monorepo — same way josh-timpany-website and creative-legends-website started. Wiring it into the BOS website-builder as a first-class **tourism template/tenant** (so it gets the real BOS editor + builder) is the follow-up step and needs DB seeding / the platform team (Heenal). Until then, this standalone file is the live, editable, duplicatable deliverable.

## What NOT to do

- **Don't** add a build step, framework, or package.json. Simplicity is the feature.
- **Don't** commit video files or high-res photos. Reference by URL.
- **Don't** hardcode an API key into the map — CARTO/OSM tiles need none.

## Contacts

- Site owner: **Zachary** (Scorpion Bay ATV Rentals & Storage)
- Platform: **Bernardo** — bernardo8605@gmail.com — Blue Ocean Standard
