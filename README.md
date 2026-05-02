# Memory Palace Landing

Static landing page for Memory Palace. **Pure HTML/CSS/JS** — no build step, no framework, no node_modules in production. Vercel serves files as-is.

## Local preview

Open `index.html` in browser, or run a static server:

```bash
python -m http.server 5500
# → http://localhost:5500
```

## Deploy to Vercel

```bash
# First time
npm install -g vercel
vercel login
vercel        # follow prompts → connect to Git, choose project name

# Then on every push to main
git push      # Vercel auto-deploys
```

Or via dashboard: vercel.com → New Project → Import Git Repository → memory-palace-landing.

## Custom domain

1. Vercel dashboard → Project Settings → Domains
2. Add your domain (e.g. `memorypalace.app`)
3. Vercel shows DNS records to add at your registrar
4. Wait 5-30 minutes for propagation
5. SSL auto-provisioned

## Structure

```
memory-palace-landing/
├── index.html          ← Hero + 3 jobs + 4 personas + privacy + pricing + FAQ + buy CTA
├── personas.html       ← Full 8-persona deep dive (from JTBD analysis)
├── faq.html            ← (todo) Full 16-FAQ page
├── changelog.html      ← (todo) Public changelog mirror
├── quickstart.html     ← (todo) 3-step quick start guide
├── styles.css          ← Design tokens + components
├── vercel.json         ← Headers + redirects
└── public/             ← (todo) demo-90s.mp4, og-image.png, favicon.ico
```

## Design tokens

| Token | Light | Dark |
|-------|-------|------|
| `--bg` | `#fafaf9` | `#0c0c0c` |
| `--text` | `#1c1c1c` | `#f5f5f4` |
| `--accent` | `#0066ff` | `#4a8aff` |

Notion-inspired: warm off-white, single accent blue, whisper borders, no gradients except hero & buy CTA.

## Updating content

- **Hero copy** → `index.html` `<section class="hero">`
- **Pricing** → `index.html` `<section id="pricing">`
- **FAQ items** → `index.html` `<section id="faq">` (top 8) + `faq.html` (all 16)
- **Personas** → `personas.html` (synced manually from `../memory_palace/docs/audits/2026-05-01-JTBD-USER-STORIES.md`)

## TODOs after first deploy

- [ ] Record 90-second demo video → `public/demo-90s.mp4`
- [ ] Replace `<div class="demo-placeholder">` with `<video>` tag
- [ ] Wire `#buy-lifetime` button to LemonSqueezy checkout URL
- [ ] Wire `#download-trial` button to GitHub Release MSI URL
- [ ] Add Plausible analytics script to `<head>`
- [ ] Create OpenGraph image (`public/og-image.png`, 1200×630)
- [ ] Replace Discord placeholder link
- [ ] Add `faq.html`, `changelog.html`, `quickstart.html` pages
- [ ] Replace `Memory Palace 🧠` brand emoji with actual logo SVG

## Performance budget

- Total HTML+CSS shipped: < 50 KB (currently ~22 KB)
- No JS until analytics added (~5 KB Plausible)
- Lighthouse target: 100/100/100/100

## Connect to main repo

Source content for personas/FAQ lives at:
`../memory_palace/docs/audits/2026-05-01-JTBD-USER-STORIES.md`
`../memory_palace/docs/marketing/landing-faq.md`
`../memory_palace/docs/marketing/email-templates.md`

Sync manually when content changes (this repo is intentionally simpler than a content-driven CMS).

## License

(c) 2026 Sunny Ngô & Alex Tạ. Landing copy and design — all rights reserved. Brand "Memory Palace" is a trademark.
