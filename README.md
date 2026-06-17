# Handoff: Mahboob Imtiyaz — Entrepreneur Profile (one-page site)

## Overview
A single-page, scrollable personal/entrepreneur profile site for **Mahboob Imtiyaz** — a multi-disciplinary entrepreneur & self-taught full-stack developer working in DeSci / Web3 / DevRel. The page's job is to **sell the person**: lead with a bold hero, prove credibility with stats + recognition, showcase active ventures, then walk the full career timeline, supporting skills/education, and close with a mission statement and CTA.

Primary audiences: investors/VCs, potential co-founders & hires, and press/speaking organizers.
Primary CTA: **"Let's Get Building!!"** → `https://cal.com/mahboob/secret`.

## About the Design Files
The files in this bundle are **design references created in HTML** — a working prototype demonstrating the intended look, layout, and behavior. They are **not** production code to lift directly.

The prototype is authored as a "Design Component" (`.dc.html`) that relies on a small runtime (`support.js`) and a web component (`image-slot.js`). **Do not port the runtime.** Your task is to **recreate this design in the target codebase's existing environment** (React, Vue, Svelte, Astro, plain HTML/CSS, etc.) using its established patterns. If no codebase exists yet, a static framework (Astro, Next.js, or even hand-written HTML/CSS) is ideal — this is a content site with light interactivity.

The single source of truth for content + exact styling is `Mahboob Imtiyaz - Profile.dc.html`. In that file, the **markup/layout** lives in the template section and the **content data** (all venture/timeline/skills text) lives in the `renderVals()` method of the logic class as plain JS arrays — copy the data straight from there.

## Fidelity
**High-fidelity (hifi).** Final colors, typography, spacing, and interactions are all specified. Recreate the UI pixel-faithfully. Exact hex values, fonts, and copy are below and in the source file.

---

## Global Design Language

- **Theme:** dark, "crypto-native," neon-accented.
- **Page background:** `#08090b` (near-black, slightly cool).
- **Ambient layer (fixed, behind content, `pointer-events:none`):**
  - Top-center radial glow: `radial-gradient(ellipse, rgba(200,255,46,0.10), transparent 62%)`, blurred 20px, slow drift animation (`glowdrift`, 18s ease-in-out infinite).
  - Bottom-right radial glow: `rgba(46,230,255,0.07)`, blurred 20px, 22s drift (reverse).
  - Faint grid overlay: 64×64px lines at `rgba(255,255,255,0.025)`, radially masked so it fades at the edges (`mask-image: radial-gradient(ellipse 90% 70% at 50% 30%, #000, transparent 90%)`).
- **Content max width:** `1200px`, centered, horizontal padding `32px`.

### Color tokens
| Token | Hex | Use |
|---|---|---|
| `--bg` | `#08090b` | Page background |
| `--bg-elev` | `#0b0c0f` | Stat cells |
| `--surface` | `#0e1013` | Image frame backing |
| `--panel` | `rgba(255,255,255,0.025)` | Cards (skills/edu/corporate) |
| `--panel-border` | `rgba(255,255,255,0.08)` | Card & divider borders |
| `--text` | `#eef0f2` | Primary text |
| `--text-2` | `#b9bdc6` / `#b3b7c0` | Body copy |
| `--text-mut` | `#8c909a` / `#9ca0aa` | Meta / muted |
| `--text-faint` | `#7b7f88` / `#5f636c` | Eyebrows, footers |
| `--accent-lime` | `#c8ff2e` | Primary accent (CTA, highlights, current roles) |
| `--accent-cyan` | `#2ee6ff` | Secondary accent (links, awards, past roles) |
| `--accent-lime-glow` | `rgba(200,255,46,0.x)` | Glows/shadows |

Selection color: background `#c8ff2e`, text `#08090b`.

### Typography
- Display + body: **Space Grotesk** (Google Fonts), weights 400/500/600/700.
- Mono / labels / eyebrows / meta: **JetBrains Mono** (Google Fonts), weights 400/500/700.
- Eyebrow/label pattern: JetBrains Mono, ~11–12px, `letter-spacing:0.14–0.22em`, `text-transform:uppercase`, often lime or faint gray, frequently prefixed with `//`.
- Headline scale uses `clamp()` for fluid sizing (see per-section specs).

### Radii / shapes
- Cards / panels: `18px`.
- Hero image frame: `22px` (image itself `21px`).
- Big CTA band: `26px`.
- Pills / chips / buttons: `100px` (fully rounded).
- Small stat badge: `6px`.

### Motion
- `@keyframes glowdrift` — translate + scale loop on the ambient glows (18s / 22s).
- Button hover: `transform: translateY(-2px)` + lime glow shadow `0 10px 34px rgba(200,255,46,0.32)`, transition `.25s`.
- Venture card hover: `translateY(-4px)`, border → `rgba(200,255,46,0.5)`, background tints lime, transition `.25s`.
- Outline/link hover: border/color → lime or white, transition `.2s`.
- **Note:** an earlier scroll-reveal animation was intentionally removed — content must be statically visible (no opacity-0 default). Do **not** reintroduce an entrance animation that gates visibility.

---

## Sections (top → bottom)

### 1. Nav (sticky-feel header row, not fixed)
- Left: a 10px lime dot with glow (`box-shadow:0 0 12px #c8ff2e`) + mono text `mahboob.imtiyaz`.
- Right: small 7px lime dot + mono uppercase `Open to building`.
- Padding `26px 32px`, max-width 1200.

### 2. Hero (2-column grid: `1.5fr / 1fr`, gap 56px, padding `48px 32px 60px`)
**Left column:**
- Eyebrow: `— Redefining #DeSci` (28px lime rule + lime mono text, `0.22em`).
- H1: `Mahboob` then `Imtiyaz` on a second line in lime with text-shadow `0 0 36px rgba(200,255,46,0.35)`. Size `clamp(44px,6.4vw,84px)`, weight 700, `line-height:0.96`, `letter-spacing:-0.02em`.
- Sub-paragraph (max 540px, `clamp(16px,1.5vw,19px)`, color `#b9bdc6`): "Multi-disciplinary entrepreneur & self-taught full-stack developer. I take projects from **0 to double-digit growth** — across SaaS, hardware, scientific publishing, Web3 and DeSci." ("0 to double-digit growth" emphasized in `#eef0f2`, weight 600.)
- Tag chips (flex, gap 9px): `DeSci Builder`, `DevRel & Community Engineering`, `Full-Stack · self-taught`, `Web3 · ZK · DiD`, `0 → Growth`. Each: mono 11px, border `1px rgba(255,255,255,0.13)`, pill, padding `7px 13px`, bg `rgba(255,255,255,0.02)`.
- Buttons (flex, gap 14px):
  - Primary: **"Let's Get Building!! ↗"** → `https://cal.com/mahboob/secret`. Bg `#c8ff2e`, text `#08090b`, weight 700, 15px, padding `15px 26px`, pill. Hover lifts + glows.
  - Secondary: **"Email me"** → `mailto:mahboob.imtiyaz@gmail.com`. Ghost: color `#cfd3da`, border `1px rgba(255,255,255,0.14)`, pill. Hover border lime.

**Right column (centered stack, gap 20px):**
- Image frame: `position:relative; width:300px; max-width:100%; height:380px; border-radius:22px; padding:1px;` with a gradient "border" background `linear-gradient(150deg, rgba(200,255,46,0.6), rgba(46,230,255,0.35), transparent 60%)`.
  - Inside: a headshot image filling it — `width:100%;height:100%;object-fit:cover;object-position:50% 30%;border-radius:21px;background:#0e1013;`. Asset: `headshot.png` (see Assets).
  - Overlaid badge bottom-left (`14px`): mono uppercase `India · Malaysia`, text `#08090b` on `#c8ff2e`, padding `5px 9px`, radius 6px.
- Below frame: mono 11px faint route text, centered: `Bengaluru → Dubai → Boise` / `San Francisco → Johor Bahru`.

### 3. Stats bar
- 4-column grid, 1px gaps over a `rgba(255,255,255,0.08)` background to fake hairline dividers, border + radius 18px, `overflow:hidden`.
- Each cell: bg `#0b0c0f`, padding `30px 26px`. Big number `clamp(30px,3.4vw,46px)` weight 700 lime; label mono 11px uppercase muted.
- Values: **20+** Ventures founded & built · **16 yrs** Shipping 0 → 1 · **1** Acquisition (Zraya) · **3** Continents operated.
- Below bar: mono 12px line — cyan `◆` + "Selected **Top 30 Under 30 Leaders of Tomorrow** — GapSummit, UK." (recognition kept subtle.)

### 4. Currently Building (active portfolio)
- Section header row: H2 "Currently Building" (`clamp(28px,3.4vw,42px)`, 700) + mono `// active portfolio`.
- 2-column card grid, gap 16px. Each card is an `<a target="_blank">` to the venture URL:
  - Card: `linear-gradient(160deg, rgba(255,255,255,0.045), rgba(255,255,255,0.012))`, border `1px rgba(255,255,255,0.09)`, radius 18px, padding 28px, flex column gap 14px. Hover per Motion.
  - Top row: lime tag pill (mono 10px uppercase, `#08090b` on `#c8ff2e`) + a muted `↗`.
  - Title 23px weight 700; URL line mono 12px cyan.
  - Description paragraph 15px `#b3b7c0`.
- Cards (name · tag · url · description):
  1. **Unblock Research** · DeSci · unblockresearch.com — "Decentralized identity & research platform — fixing the issues that have ailed research for the past 100 years."
  2. **Endangered.dev** · Managing Director · endangered.dev — "Global nonprofit rebuilding careers for developers & knowledge workers displaced by AI — reskilling, free NVIDIA/AWS/Google credits, micro-funding & an AI career coach."
  3. **Folioex** · CTO · folioex.com — "Mutual funds, but for crypto. Expert-designed strategies and integrated AI for investors who prefer structure over speculation."
  4. **Cohortea** · Co-Founder · cohortea.com — "Outsourced DevRel & community engineering that drives the only traction that matters: real applications and contracts deployed."
  5. **Labcritics** · Editor · Analyst · labcritics.com — "The largest dataset of lab-equipment users — deeptech, automation & DeSci discovery, an unbiased resource researchers depend on."

### 5. The Full Build Log (timeline, 2010 → present)
- Header: H2 "The Full Build Log" + mono `// 2010 → present`.
- Vertical line on the left (`padding-left:30px`): a 1px gradient rail `linear-gradient(180deg, #c8ff2e, rgba(46,230,255,0.5), rgba(255,255,255,0.08))` running top→bottom.
- Each entry (`padding-bottom:38px`):
  - Node dot at `left:-30px; top:5px`, 11px circle, color = entry's `dot`, with `box-shadow: 0 0 0 4px #08090b, 0 0 12px <glow>` (the 4px ring punches it out of the rail).
  - Title row: company name (20px, 700) + optional **badge** pill (mono 10px uppercase lime, border `1px rgba(200,255,46,0.4)`, padding `3px 8px`, pill).
  - Meta row: mono 12px — role (in `#cfd3da`), period, location.
  - Description paragraph (max 760px, 14.5px, `#9ca0aa`).
  - Optional **wins** chips row (used by KarmaSnap): cyan pills, mono 11px, `◆ <text>`, border `1px rgba(46,230,255,0.35)`, bg `rgba(46,230,255,0.05)`.
- **Color convention:** current/landmark roles use lime dot `#c8ff2e` + glow `rgba(200,255,46,0.7)`; past roles use cyan dot `#2ee6ff` + glow `rgba(46,230,255,0.6)`.
- Entries in order (company · role · period · location · badge · notes):
  1. Endangered Devs · Managing Director · May 2026 — Present · India · **Now** (lime)
  2. Folioex · Chief Technology Officer · Feb 2026 — Present · Mumbai · **Now** (lime)
  3. Cohortea · Co-Founder · Oct 2025 — Present · Bengaluru · **Now** (lime)
  4. Labcritics · Editor & Deeptech Analyst · Feb 2023 — Present · Bengaluru · **Now** (lime)
  5. Fidociary · Head of Development · Jun 2024 — Nov 2025 · Dubai, UAE (cyan)
  6. BitGenix · Head of Development · Jan 2024 — Feb 2025 · Dubai, UAE · **Stealth** (cyan)
  7. Accuzar · Technology Officer · Oct 2023 — Apr 2024 · Ontario, Canada (cyan)
  8. Cohortea — Crypto Experience · DAO1 · Apr 2021 — Mar 2022 · Remote (cyan)
  9. Zraya · Founder & Director · Feb 2016 — Oct 2021 · Bengaluru · **Acquired** (lime)
  10. Apiria Technologies · PM & Frontend Lead · May 2020 — Aug 2021 · Bangalore · **Acquired** (lime)
  11. Volubilis Tech · CEO · 2014 — Feb 2021 · Bengaluru (cyan)
  12. LabCritics · Founder, BD & Editor · Sep 2013 — Sep 2020 · Bangalore (cyan)
  13. Ventive · Founding Developer · Sep 2014 — Feb 2017 · Boise, ID (cyan)
  14. KarmaSnap · COO & UI/UX · Feb 2014 — Jun 2015 · Dubai (lime) · **wins:** "Citrix Hackathon — 1st Prize · 2014", "DP World Accelerator"
  15. NeighborCity · Web Developer · Sep 2012 — Oct 2013 · San Francisco (cyan)
  16. Innovators4Hire · Founder, Developer & CIO · Nov 2011 — Nov 2012 · Bangalore (cyan)
  17. BioFlukes · Founder · May 2011 — Sep 2012 · India (cyan)
  18. Content Cruise · Software & Web Developer · Jun 2011 — Dec 2011 · India (cyan)

  Full description copy for each is in `renderVals()` → `timeline`.

### 6. Corporate Experience (enterprise track)
- Header: H2 "Corporate Experience" (`clamp(24px,2.8vw,34px)`) + mono `// enterprise track`.
- 2-column card grid, gap 16px. Card: panel bg `rgba(255,255,255,0.025)`, border `1px rgba(255,255,255,0.08)`, radius 18px, padding 26px.
  - Company (19px, 700), meta row mono 12px (role / period / location), description 14.5px.
- Entries:
  1. **Halliburton** · Development Lead · Sep 2020 — Oct 2021 · Bangalore — "Lead developer upgrading well-drilling visualization from 2D to 3D with a WebGL application for real-time drilling decisions and projections."
  2. **Genpact — Empower Research** · Analyst · 2010 — 2011 · India — "Research and analytics at enterprise scale — where the journey started."

### 7. Skills / Languages / Education (3-column grid, gap 16px)
Each is a panel card (bg `rgba(255,255,255,0.025)`, border, radius 18px, padding 28px) with a lime mono uppercase heading.
- **Top Skills** (rows divided by `1px rgba(255,255,255,0.06)`, 16px weight 600): Director-level Leadership · Community Building · Developer Relations. Then a cyan "Certifications" sub-heading: Effective Presentation Skills · Strategic Thinking.
- **Languages** (name 15px weight 600 + mono level, right-aligned, divided rows): English — Full Professional · Hindi — Full Professional · Urdu — Full Professional · Kannada — Limited Working · Arabic — Limited Working.
- **Education** (school 15px weight 600 + degree + mono years): Visvesvaraya Technological University — BEng, Biotechnology — 2006 — 2009 · Dayananda Sagar College of Engineering — PUC, PCMB — 2003 — 2005.

### 8. Mission / CTA band
- Bordered band: border `1px rgba(200,255,46,0.25)`, radius 26px, padding `clamp(36px,6vw,72px)`, bg `linear-gradient(150deg, rgba(200,255,46,0.06), rgba(46,230,255,0.04), transparent 70%)`.
- Mono eyebrow `// Mission` (lime).
- Big statement (max 860px, `clamp(22px,2.8vw,36px)`, weight 600): "Obsessed with removing the bottlenecks that slow scientific progress — building tools that let researchers, founders and creators move faster. **Decentralized is the way.**" (last sentence lime.)
- Buttons: primary "Let's Get Building!! ↗" → cal.com link; ghost "LinkedIn" → `https://www.linkedin.com/in/mahboobimt`.
- Contact row (mono 12.5px, muted): `mahboob.imtiyaz@gmail.com` · `+91 8123 642 511` · `India · Malaysia`.
- Footer line below, centered mono uppercase faint: `Scientist · Reformer · Traveler · Environmentalist · Hands-on Builder`.

---

## Interactions & Behavior
- **Links:** all venture cards, both CTAs, email, and LinkedIn open in new tabs (`target="_blank"`). CTA → `https://cal.com/mahboob/secret`; email → `mailto:mahboob.imtiyaz@gmail.com`; LinkedIn → `https://www.linkedin.com/in/mahboobimt`.
- **Hover states:** buttons lift + lime glow; venture cards lift + lime border/tint; ghost buttons + links shift border/color toward lime/white. (See Motion.)
- **Ambient animation:** two drifting radial glows loop continuously (decorative only).
- **No JS state** is required for a faithful rebuild — this is a static content page. (The prototype's headshot was a drag-to-replace slot during authoring; in production just render a static `<img>`.)

## Responsive behavior
- The prototype is built for desktop width. For production, collapse the hero `1.5fr/1fr` grid to a single column on narrow viewports (stack image above or below text), and drop the 2-column venture/corporate grids and 3-column skills grid to a single column on mobile. Keep the 1200px max-width container and 32px gutters. The 4-up stats bar can wrap to 2×2 on small screens.

## Design Tokens (quick reference)
- **Colors:** `#08090b`, `#0b0c0f`, `#0e1013`, `#eef0f2`, `#b9bdc6`, `#b3b7c0`, `#cfd3da`, `#9ca0aa`, `#8c909a`, `#7b7f88`, `#5f636c`, accent lime `#c8ff2e`, accent cyan `#2ee6ff`. Borders `rgba(255,255,255,0.06–0.14)`. Panels `rgba(255,255,255,0.025)`.
- **Spacing rhythm:** container padding 32px; section vertical padding ~84–100px top; card padding 26–28px; grid gaps 16px; chip gaps 8–9px.
- **Radii:** 6 / 18 / 21 / 22 / 26 / 100px.
- **Type scale (clamp):** H1 `clamp(44px,6.4vw,84px)`; section H2 `clamp(28px,3.4vw,42px)` (corporate `clamp(24px,2.8vw,34px)`); mission `clamp(22px,2.8vw,36px)`; body 14.5–19px; meta/eyebrows 10–12px mono.
- **Shadows/glows:** CTA hover `0 10px 34px rgba(200,255,46,0.32)`; card hover `translateY(-4px)`; node ring `0 0 0 4px #08090b, 0 0 12px <glow>`; H1 text-shadow `0 0 36px rgba(200,255,46,0.35)`.

## Assets
- **`headshot.png`** (800×800) — a stylized illustrated portrait, recolored to match the theme (dark background with a faint lime top-glow, shirt graded to the cyan accent). Provided in this bundle. Swap for the client's preferred headshot if updated; keep `object-fit:cover; object-position:50% 30%`.
- **Fonts:** Space Grotesk + JetBrains Mono via Google Fonts (`https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap`). Use the codebase's font-loading convention.
- **Icons:** none — arrows (`↗`), diamonds (`◆`), and the `//` prefix are plain text glyphs. No icon library required.

## Files in this bundle
- `Mahboob Imtiyaz - Profile.dc.html` — the full design prototype. **Layout** = template markup; **all content/copy** = the `renderVals()` arrays (`tags`, `stats`, `building`, `timeline`, `corporate`, `skills`, `certs`, `languages`, `education`) in the logic class. This is the authoritative reference.
- `headshot.png` — hero image asset.
- `image-slot.js`, `support.js` — prototype runtime dependencies. **Reference only; do not port.** They exist so the `.dc.html` opens standalone in a browser.

## Implementation notes
- Rebuild as ordinary semantic HTML/CSS (or your framework's components). The prototype's data arrays map cleanly to a CMS collection or a local data file (`ventures[]`, `timeline[]`, `corporate[]`, etc.).
- Use fl/grid with `gap` for all the chip/card rows (as the prototype does) rather than margins.
- Preserve the lime-vs-cyan semantic: lime = current/landmark, cyan = past/secondary.
- Keep content statically visible (no visibility-gating entrance animations).
