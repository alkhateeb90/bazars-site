# Bazars.io — static site

Plain HTML/CSS, no framework and no build step. Deploy the repository root to Vercel.

## Structure

- `index.html` + `zh/ tr/ vi/ pl/` — public landing (indexed), hreflang-linked
- `manufacturers/` + `zh/ tr/ vi/ pl/manufacturers/` — unlisted (noindex meta + `X-Robots-Tag` in `vercel.json`)
- `buyers/`, `partners/`, `investors/` — unlisted, English only
- `assets/style.css` — one stylesheet; hero motion is a dependency-free canvas globe (`assets/globe.js`): gentle rotation, staggered city pulses; pauses offscreen and under `prefers-reduced-motion`
- `robots.txt` — allows everything, lists nothing
- `vercel.json` — `cleanUrls` + noindex headers for the unlisted routes

No page links to the unlisted pages. Visitors reach them only via a link you send.

## Deploy

1. Create a **private** GitHub repository and push this folder (see "Honest limitations").
2. In Vercel: Add New Project → import the repo → Framework Preset: **Other** → no build command → output directory: `./` (root).
3. After deploy, check `https://yourdomain/manufacturers` returns the `X-Robots-Tag: noindex, nofollow` header.
4. Point `bazars.io` at the project in Vercel → Settings → Domains.

## Before you send any link — open items

1. **Mailboxes.** Pages use `manufacturers@`, `buyers@`, `partnerships@`, `investors@bazars.io`. Create the ones you will use (the earlier draft used `suppliers@` — pick one convention for manufacturers).
2. **WeChat QR / WhatsApp number.** The dashed QR box on the manufacturers pages is a placeholder. Replace with your real QR image and add the WhatsApp line (commented in the HTML).
3. **Trust line and logos.** Comments in `index.html` (landing band) and the manufacturers page show where partner names go. Publish names **only** with written permission; otherwise leave them out entirely.
4. **Translations are drafts.** The zh/tr/vi/pl pages carry a visible "draft — needs native review" note in the footer area. Get a native read before sending, then delete that line.
5. **Registered entity line.** Footer placeholders are commented in each page; add the line once incorporated.
6. **Meta descriptions** are generated from the page copy; sanity-check them before launch.

## Honest limitations

- **noindex is not security.** The unlisted pages are in this repository. If the repo is public, anyone can find them. Use a private GitHub repo (Vercel deploys from private repos on the free plan), and keep nothing sensitive on these pages.
- **Fonts load from Google Fonts**, which is unreliable from mainland China. For Chinese recipients, self-host the font files later (download woff2 into `assets/` and replace the `<link>` tags) or accept the fallback to system fonts.
- **Vercel can be slow inside China.** Test `/zh` and `/zh/manufacturers` from a mainland connection before the first WeChat campaign; if too slow, mirror on a China-friendly static host.
- **The route map is schematic**, and the site intentionally says so — it is an illustration, not a geographic claim.
- **No analytics** is included. If you add any, avoid Google Analytics for the China reason above (Plausible or Vercel Analytics are safer choices).
