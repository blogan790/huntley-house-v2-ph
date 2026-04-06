# Shopify Developer Draft — Design Reference

**URL:** https://huntleyhouse.com | **Password:** diya  
**Theme:** Impact by Exhibea v6.12.0 — customized as "V2 – Exhibea for Huntley House"

---

## Scrolling & Page Behavior

- **Standard vertical scroll** — no full-page snap, no sections locked to viewport height
- Sections flow continuously and blend into each other (`section-blends` class)
- **Featured collection on homepage is a horizontal carousel**, not a grid — `scroll-area is-scrollable` with prev/next circle-chevron buttons and a scrollbar progress indicator
- **Impact text (value props) is a horizontal scroll** with `snap-center` on each item — users swipe through the 3 value props
- Blog posts section also uses a horizontal carousel on mobile (`auto-flow 52vw` per card)

---

## Hero / Slideshow

- Full-width, full-height slideshow
- **Zero overlay** on hero images (`--content-over-media-overlay: 0 0 0 / 0.0`) — image is shown clean, no dark tint
- Text enters with staggered **fade-up animation** (`spence-fade-up`):
  - Heading: 0.2s delay
  - Subheading: 0.4s delay
  - Content: 0.6s delay
  - Button: 0.8s delay
- Animation: `translateY(30px) → 0`, `opacity 0 → 1`, duration `1.2s cubic-bezier(0.215, 0.61, 0.355, 1)`

---

## Section Structure & Layout

| Section | Layout | Notes |
|---------|--------|-------|
| Slideshow | Full-bleed, full-height | Staggered text reveal |
| Featured Collection | Horizontal scroll carousel | 4-col desktop, ~36vw/card mobile |
| Media With Text ("Ritual") | 50/50 split | Olive bg (`#848247`), chocolate text; has divider icon |
| Rich Text | Centered text block | Brand story paragraph |
| Media Grid | 2-item grid, each 2×2 spanning | Row height 400px desktop / 260px mobile |
| Blog Posts | 3-col desktop, horizontal scroll mobile | Same 3 articles |
| Image With Text Overlay | Full-bleed, text bottom-left | Zero overlay, large format |
| Impact Text | Horizontal scroll, snap-center | Diamond shape decorative element; dark choc bg |
| Newsletter | Centered block | |
| Footer | Standard 4-col | Cocoa bg |

- Max container width: **1720px** (very wide — generous whitespace at large screens)
- Container gutter: **2rem**
- `section-full` = edge-to-edge, no horizontal padding
- `section-blends` = no visible breaks between adjacent sections (background bleeds)

---

## Typography

| Role | Font | Transform | Letter-spacing |
|------|------|-----------|----------------|
| Headings | Stylebender | Uppercase | **−0.015em** (tight) |
| Body | NeueHaasGroteskDisp Pro | Normal | 0.2px |

Type scale (responsive — 3 breakpoints):
- h0: 3rem → 4rem → 5rem
- h1: 2.5rem → 3rem → 3.75rem
- h2: 2rem → 2.5rem → 3rem
- h3: 1.5rem → 2rem → 2.25rem

---

## Color Application by Section

| Section | Background | Text |
|---------|------------|------|
| Header | Deep Cocoa `47 27 27` | Cream `239 230 216` |
| Hero | Image (no overlay) | Cream |
| Collection | Cream `239 230 216` | Cocoa |
| Media With Text (Ritual) | Warm Olive `132 130 71` | Chocolate `74 47 42` |
| Impact Text | Dark Choc `124 44 30` | Cream |
| Newsletter | (footer group) | Cream |
| Footer | Deep Cocoa `47 27 27` | Cream |

Primary button: Vintage Blue `143 190 196` with white text  
Secondary button: Warm Olive `132 130 71`

---

## Product Cards

- Primary image: box top (portrait)
- Secondary image: puzzle artwork — revealed on hover (`product-card--show-secondary-media`)
- Ratings displayed (judge.me)
- Product list stagger-reveals on scroll (`stagger-products-reveal-opacity: 0` → animated in)

---

## Header

- Always opaque cocoa (transparent header CSS present but not activated)
- Logo height: 46px desktop / different breakpoint config
- Non-sticky (`sticky-header-enabled: 0`)

---

## Animation System

- `spence-fade-up`: hero text entrance
- `IntersectionObserver`: scroll-triggered reveals throughout
- Product grid: staggered fade-in on scroll
- Transitions: `opacity 1.2s cubic-bezier(0.25, 1, 0.5, 1)` — slow, luxurious
