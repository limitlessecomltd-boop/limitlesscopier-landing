# Limitless landing page

Single-page static site for **limitlesscopier.com**.

## What's in this repo

- `index.html` — entire page in one file (HTML + inline CSS + inline SVG + minimal JS)
- `robots.txt` — search crawler permissions
- `sitemap.xml` — single-page sitemap, expand when blog posts ship

## Deploy to Vercel

### Option A — drag and drop (fastest)
1. Go to https://vercel.com/new
2. Drag this folder onto the upload area
3. Project name: `limitlesscopier-landing`
4. Click **Deploy**
5. Once live, in Project Settings → Domains, add `limitlesscopier.com`
6. Follow Vercel's DNS instructions (CNAME or A record at your registrar)

### Option B — Git-based deploy (recommended for iteration)
```bash
cd landing
git init
git add .
git commit -m "Initial landing page"
git branch -M main
git remote add origin https://github.com/limitlessecomltd-boop/limitlesscopier-landing.git
git push -u origin main
```
Then in Vercel: **Add New Project → Import Git Repository → pick the landing repo → Deploy.**

Every `git push` redeploys automatically.

## Before going live — checklist

The page is production-quality but has placeholders you should fill before launch:

- [ ] Replace `https://buy.stripe.com/REPLACE_1MONTH` / `_3MONTH` / `_YEARLY` with real Stripe Payment Links
- [ ] Add real screenshots of Copier / Journal / Protector — the SVG mockups are stylized placeholders
- [ ] Add real `og-image.png` (1200×630 PNG used when the page is shared on Twitter/LinkedIn/Discord)
- [ ] Create the legal pages: `/terms`, `/privacy`, `/refund` (Stripe will check these)
- [ ] Build a `/docs` and `/blog` (good for long-tail SEO; can wait until launch +1)
- [ ] Verify `support@limitlesscopier.com` email is set up (Google Workspace or similar)
- [ ] Add Google Search Console verification meta tag once domain is live
- [ ] Add Plausible or Fathom analytics snippet (privacy-friendly, no cookie banner needed)
- [ ] Confirm bank-transfer and crypto payment instructions are documented somewhere reachable (the page advertises both)

## SEO notes

The page targets these primary keywords in title/H1/body:
- `mt5 trade copier`
- `trade copier prop firm`
- `metatrader 5 trade copier`
- `prop firm journal`
- `ftmo trade copier`
- `multi account copier`

Schema.org JSON-LD is included for `SoftwareApplication`, `Organization`, and `FAQPage` — Google should pick up rich snippets within ~1-2 weeks of indexing.

Average TTFB on Vercel ~50ms (US), single HTML file, no external JS dependencies, no render-blocking. Should score 95-100 on Lighthouse Performance/SEO/Accessibility.

## Design system

- **Bebas Neue** (display) — uppercase headlines, balances, stat numbers
- **DM Sans** (body) — body copy at 300/400/500/600/700
- **DM Mono** (mono) — license keys, tickers, table cells, captions

Palette: gold/amber (`#FFD700` → `#FFA500`) primary, deep navy base (`#030508`), green for master/OK states, red for slave/warning states, cyan accent used sparingly.

All fonts loaded from Google Fonts with preconnect for speed.

## Hero animation

The hero shows a 3-splash rotating preview of the product:

1. **Copier** — master node fanning out trade pulses to four slave accounts (FTMO, MFF, FundedNext, E8) along dashed paths.
2. **Journal** — profit-target ring filling toward 68%, daily-loss bar growing toward threshold, P&L stat tiles, and a 14-day trading heatmap.
3. **Protector** — daily-loss meter rising to its threshold, then a green shield slamming in with "PROTECTED · AUTO-PAUSED", followed by pre-trade-block + profit-target-met alerts.

Auto-cycles every 5 seconds. Pauses on hover. Three clickable tabs below let visitors jump between splashes. Respects `prefers-reduced-motion` — falls back to a static first splash with no animation.

Pure inline SVG + CSS + ~40 lines of JS. No external libraries, no images.

## Compliance note

The page includes a **Risk Disclosure** block in the footer covering:
- Trading risk and leverage warning
- Limitless is a copier/journal utility, not a signal provider or advisor
- User responsibility for every trade placed on every connected account
- No liability for losses or prop-firm rule breaches
- User's responsibility to verify that copy-trading complies with each broker's / firm's terms

Keep this in place even if you redesign — it is essential cover when shipping trade-copying software.
