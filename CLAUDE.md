# CLAUDE.md — muneebarshad.com portfolio

## What this is
Multi-page static portfolio for Muneeb Arshad (mobile app dev + growth marketing).
**No build system** — every page is a fully self-contained HTML file (inline CSS/JS,
no external JS libraries). Deployed on **Vercel** from `muneeb117/portfolio` main branch;
folder pages give clean URLs (`/revenuecat/` → `revenuecat/index.html`).

## Pages
- `index.html` — homepage (hero, services, apps grid w/ filters, growth, about, tech, footer)
- `apps/` — complete portfolio, all apps + filter tabs
- `ai-apps/` — AI development service page (mobile + web)
- `growth/` — performance marketing (Meta / TikTok / Google Ads / ASA + ASO)
- `revenuecat/` — subscriptions & monetization (animated RC dashboard mockup)
- `appsflyer/` — attribution & analytics (animated AF dashboard mockup)
- `beauty/` `wellness/` `finance/` `productivity/` — niche solution pages

**Purpose of subpages:** client-specific links. Muneeb sends the matching page to each
prospect (e.g. trading-app client → `/finance/`). Therefore subpages contain
**NO contact info** (no email/phone/socials/forms) — only capability + app proof.
Keep it that way.

## Design system (v4 — MIXPANEL theme; APPROVED 2026-07-11)
Client rejected 3 earlier looks (warm serif+orange; glowing indigo→cyan "too much AI";
minimal-corporate got redirected). FINAL = **Mixpanel design language** (from mixpanel.com).
`index.html` is the canonical reference — match it on every page.
- Fonts: **Hanken Grotesk** (headings 700/800, free Garnett substitute) + **Inter** (body).
- **Page-wide gradient field:** `body::before` fixed multi-radial (lilac/peach/mint/purple,
  low opacity). Light sections are `background:transparent` so the field flows through the
  whole page; white cards float on it. Dark sections + footer are opaque anchors.
- Palette: purple **#7856ff** (`--accent`), deep purple **#150040** (`--navy`, dark bands +
  footer), ink `#1f2023`, lilac panel `#f0edff`. BLACK pill buttons (`--ink`, radius 100px);
  lilac icon tiles w/ purple stroke; lilac `.sec-tag` w/ purple text; purple review stars;
  `.accent` = ink + lilac highlighter underline. Rounded (radius 12–20). Footer + dark
  sections have rounded-top corners. `.cta-band` = white→lilac→purple gradient before footer.
- Headline proof (NO exact live-app count — "selection of 100+"): **100+ apps · 20M+
  downloads · 180K+ ratings** (subscription-apps stat was REMOVED). Reviews section = 9 real
  Fiverr/Upwork testimonials. Photo: nav `.logo-mark` img `/assets/muneeb.jpg` w/ "M" fallback.
- **Dashboards = REAL screenshots** (`/assets/screenshots/*.png`) in a browser frame with an
  onerror fallback to clean stat tiles — NOT fake mockups (user: "looks fake"). User drops
  the PNGs (+ `assets/muneeb.jpg` photo, `assets/reviews/*` screenshots).
- Shared nav (6 links) + footer (Pages + Solutions) in sync across ALL pages.
- Animations (restrained): `.reveal` staggers + count-up `.count` (keep runCount setTimeout
  safety net — rAF stalls in bg tabs). Full spec + base.css/base.js in session scratchpad.
  **count-up `runCount` MUST keep its `setTimeout` safety net** — rAF stalls in background
  tabs and freezes counters mid-count without it. `prefers-reduced-motion` respected.
- Full spec + extracted base.css/base.js live in the session scratchpad `design-spec.md`.

## Data rules
- App cards: real App Store / Play Store URLs + mzstatic icon URLs. US storefront links.
- Rating badge `.ab-rating` shown only when app has ≥ 4 ratings (homepage: ≥10 & ≥4.5).
- Proof metrics (RevenueCat MRR $15,829 / 2,389 subs; AppsFlyer 277% ROAS D7;
  Google Ads 6.79k clicks) are real dashboard numbers from 2026-07 — update, don't invent.
- **Known gotcha:** `cdn.simpleicons.org` removed `appsflyer` and `openai` slugs (404).
  Use `https://www.appsflyer.com/favicon.ico` and the Wikimedia OpenAI PNG instead.
  Base44 has no simpleicon — use styled "44" monogram.
- Sculpted (`id6745438071`) is temporarily delisted (Apple agreement pending) — card kept.
- Coming-soon apps (TrackIQ, Slumber, Breath): dashed cards, monogram icon, no store link.
- **19 live apps, 2,464 total ratings → say "2,400+ ratings".** Do NOT print a single
  "average star" (weighted 4.45 / simple 4.49) — lead with rating VOLUME + top apps:
  Retain Quran 4.4★/2,025 (most-reviewed, Android), SnapTrader 4.7/141, Freed 4.6/127,
  Tradvio 4.8/69. Retain Quran = `com.retainquranapp` (Play), Education · AI.

## Verify locally
`python3 -m http.server 4173 --directory .` then check every page at 375px and 1280px;
all internal links are root-relative so use the server, not file://.
