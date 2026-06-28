# CLAUDE.md — Not Another Body Butter

Guidance for Claude when working in this project. Read this first.

## What this is

A marketing + e-commerce website for **Not Another Body Butter**, a handcrafted shea body butter brand owned by Tré. Goal: a modern, conversion-ready, SEO-optimized site with an editorial magazine aesthetic. Selling transactions are **not** live yet — the current checkout is a labeled mockup. Tré wants to see the full purchase flow as a prototype before wiring up real payments.

## Mission & brand story

Use these as the source of truth for brand voice and positioning. Keep copy aligned with this mission; weave the themes in naturally rather than pasting these verbatim.

**Mission statement**

We create all-natural body butters that nourish sensitive and dry skin with simple, transparent ingredients and subtle scents. Our mission is to provide gentle, effective skincare that complements your personal fragrance — not competes with it — so you can feel comfortable, confident, and authentically you.

**Brand story**

This brand was born from a simple realization: finding a truly all-natural body butter shouldn't be difficult. Yet so many products on the market are filled with preservatives, synthetic fragrances, and additives that irritate the skin — especially for people with sensitivity or dryness.

Seeing this gap, we set out to create something different. Skincare that feels luxurious without being overwhelming. Formulas made with clean, recognizable ingredients. Scents that enhance your personal style rather than overpower it.

Our inspiration comes from the people who want more from their daily routine — those who value wellness, simplicity, and authenticity. With every jar, we're redefining what it means to care for your skin: gentle, natural, soft to the touch, and effortlessly complementary to your lifestyle.

**Positioning themes to keep front of mind:** all-natural and clean ingredients, transparency, gentleness for sensitive/dry skin, subtle scents that complement (not compete with) personal fragrance, and authenticity. Note the "subtle scents that complement" theme sits alongside the 13 signature scents — frame scents as enhancing personal style, never overpowering.

## The brand

**Products**
- Whipped Shea Body Butter — 4 oz ($14), 8 oz ($24), 16 oz ($42)
- Silk Body Oil — 10 ml ($12)
- The Sampler Box — ten 1 oz bottles, "pick 10" scent selection flow ($38)

**13 signature scents** (name — notes): Pink Fantasy (floral/sweet), Teakwood (woody/warm), Cashmere Falls (powdery/elegant), Baby Powder (clean/nostalgic), Vanilla Musk (sweet/sensual), Lemon Meringue (citrus/bright), The Perfect Gentlemen (sophisticated/bold), Juicy Pear (fruity/fresh), Blackberry (tart/deep), Fresh Linen (airy/clean), Sweet Autumn Nights (spicy/cozy), Piña Colada (tropical/creamy), Cacao (chocolatey/rich).

**Voice & SEO keywords:** "shea body butter," "cold-whipped," "unrefined African shea," "cruelty-free," "handcrafted," "all-natural," "clean ingredients," "for sensitive skin," "for dry skin," "subtle scent." Keep these woven into copy naturally.

## Design system

- **Palette:** warm cream, caramel, terracotta
- **Type:** Fraunces (serif, display) + Inter (sans-serif, body)
- **Imagery:** lifestyle photography of women with glowing skin applying product; editorial, aspirational tone

## Codebase

Single-file React/TSX app. The entire site lives in **`body-butter-site.jsx`**.
GitHub Repository - https://github.com/null-618/not-another-body-butter

**Data constants (top of file):**
- `IMAGES` — three product photos as base64 strings
- `CAROUSEL_SLIDES` — carousel content
- `SCENTS` — the 13 scents (name, notes, color)
- `PRODUCTS` — `butter`, `oil`, `sampler` with sizes/prices

**Components:**
- `App` — root, view/cart state
- `Nav`, `Footer`
- `Home` — hero, marquee, collection, scent library, process story, testimonials, email signup
- `Shop`, `ProductDetail` — size/scent selectors
- `Cart` (drawer), `Checkout` (mockup-labeled), `Confirmation`
- `RitualCarousel` — split layout (portrait photo left, caption panel right) with auto-rotate, crossfade, dot nav, arrows
- `ProductVisual`, `ProcessVisual`

**Other files:**
- `gift-box.jpeg`, `sampler-open.jpeg`, `scent-lineup.jpeg` — source product photos (also embedded as base64 in the JSX)
- `Not Another Body Butter - Label 2.svg` — product label art

## Conventions & hard-won lessons

- **Images: embed real photos as base64 directly in the JSX.** URL-based image embeds proved unreliable. This is the preferred approach for stability.
- **No cartoonish placeholders.** SVG illustrated lifestyle images were tried and rejected — Tré prefers removing an element entirely over shipping a low-quality placeholder.
- **Editing the big JSX file:** it contains large base64 lines that break normal readers. Copy it to a working dir, check `wc -l`, and read in chunks with `sed -n '[start],[end]p'`. To inspect structure, filter out the base64 lines (e.g. `grep -vE 'base64' ` or `awk 'length<200'`).
- Licensed photography sources Tré uses: Nappy.co, CreateHER Stock, Tonl.

## Roadmap (not yet built)

- Real transaction / payment integration (Stripe or similar) — replaces the mockup checkout
- Sourcing licensed lifestyle photography to replace remaining placeholders

## Working with Tré

Keep responses concise and direct. When building or editing the site, preserve the editorial aesthetic and SEO keywords, and never downgrade visual quality to fill a gap.
