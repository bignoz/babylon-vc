# Babylon — Project Context

This file is read automatically by Claude Code at the start of every session. It carries the full design system, brand voice, and project history forward so iterations stay consistent without re-explaining context.

---

## What this project is

`babylon.vc` — the website for **Babylon**, a pre-seed venture fund based in San Francisco run by Hugo Amsellem. The site is a single static `index.html` deployed to Vercel, with assets (favicons, OG image, logo) sitting alongside.

**Tagline:** "backing founders moving culture."
**Mood reference:** "warm empire, after midnight." (Style direction only — never appears as visible copy on the site.)

The fund invests in narrative-intensive frontier technology — companies that are simultaneously hard to engineer and culturally contested. Bits, atoms, cells.

---

## Repo structure

- `index.html` — the entire site (single file, base64-embedded logo, Google Fonts CDN)
- `og-image.png` / `og-image.jpg` — 1200×630 social preview card
- `favicon-32x32.png` / `favicon-192x192.png` / `apple-touch-icon.png` / `favicon.ico`
- `babylon-logo.png` — full-resolution transparent logo
- `vercel.json` — caching headers and clean URLs
- `robots.txt` / `sitemap.xml`

---

## Brand identity — the design system

### Color tokens (CSS variables in index.html)

```
--lapis: #1D3A6B       — deep anchor, mechanics section background
--gold: #D4A74F        — accents, highlights, deployed sparingly
--vermillion: #C83E2B  — the wildcard hot color (italic display)
--parchment: #EFE4CA   — default page background
--paper: #F4EBD2       — slightly warmer alt background
--ink: #1F1A14         — body text (NEVER use cool black)
--brass: #9F7B3A       — quieter alt to gold (separator dots)
--oxblood: #7A1F1F     — editorial emphasis
--rose: #D47184        — warm accent, currently unused
--olive: #5E6B3B       — quiet labels, eyebrows
```

**Rules:**
- Default background is parchment. Default text is warm ink. Default deep-field is lapis.
- Vermillion and gilt gold are punctuation, not foundation. If you use them in more than 3-4 places per page, you've lost the discipline.
- NEVER use `#000000`, `#FFFFFF`, or any cool grey.

### Typography — three registers

1. **Classical display (default)** — `Fraunces` from Google Fonts, weight 400, letter-spacing -0.02em. Used for ~90% of headlines.
2. **Theatrical wildcard (sparingly)** — `Playfair Display` italic, weight 500, always vermillion. Used for the wildcard moments only — e.g. "moving culture." in the hero, "upstream" in the thesis. If you reach for it, ask whether the moment earns it.
3. **Body workhorse** — `Lora`, 15-19px, line-height 1.55-1.65.
4. **Metadata labels** — `JetBrains Mono`, 10-11px, letter-spacing 0.15-0.22em, uppercase.

NEVER use Inter, Helvetica, Roboto, system sans, or any geometric sans. Site fails the moment it looks SaaS-ish.

### Voice rules

**Always:**
- Lowercase in casual copy. Sentence case in formal copy. Both are alive.
- Short paragraphs, one idea per paragraph.
- Bold key phrases as reading anchors via `<strong>` (gets the gold underline gradient).
- Concrete and visceral over conceptual ("technically hard and culturally scary" > "narrative-first deep tech").
- Forward-moving assertions only.

**Never:**
- All caps headlines or title case.
- Antithesis constructions ("not X, but Y") — Hugo flags these as AI-sounding.
- AI-sounding hedges — "it's worth noting," "navigate," "leverage," "delve into," "robust."
- Startup clichés — moonshots, unicorns, rockets, disruption, game-changing.
- Em-dash overuse. Use selectively.
- Emoji. Exclamation marks outside genuine joy.

---

## Layout & surface principles

### Yes
- Generous vertical rhythm. Cathedral-window aspect ratio over wide shallow.
- Tiered composition — content steps down like a ziggurat.
- Depth and layering — foreground, midground, background, always.
- Hairline rules at 0.5px in `rgba(31, 26, 20, 0.18)` for section dividers.
- The lapis section breaks the parchment rhythm and is the page's high contrast moment. Don't add another one.

### No
- Gradients (except the gold underline highlight on `<strong>`). Mesh. Glow. Drop shadows.
- True black or cool greys.
- Stock photography. Icon grids. Feature-matrix tables.
- Sterility in any form.

---

## Page structure (current)

1. **Nav** (fixed, parchment with backdrop blur) — `[coin logo] babylon` left, nav links right, contained at 1180px max-width matching body.
2. **Hero** — `[coin logo] backing founders / moving culture.` in one inline row, then a vermillion rule, then prose underneath spanning wider.
3. **Thesis** — sticky aside with Roman numeral I., body column with header "Culture is moving *upstream* of technology.", a vermillion-bordered pullquote, three paragraphs.
4. **Portfolio** — three category blocks: Bits / Atoms / Cells. Companies listed inline with brass `·` separators (CSS pseudo-element, flex-wrap responsive).
5. **Dinners** — centered. Stamp + huge italic vermillion title + gold divider + prose.
6. **Contact** — two-column, asymmetric, `hugo@babylon.vc` and `babylon.co · letters`.
7. **Footer** — full-width black-rule top, three columns.

---

## Decisions already made (do not relitigate)

- **Order is atoms → bits → cells.** Always. Do not reorder to bits-first or cells-first.
- **No "warm empire, after midnight" anywhere visible on site.** It's the style brief, not a tagline.
- **No "VC" in the wordmark or nav.** Just "babylon."
- **Apex serves the site, www redirects to apex.** Set in Vercel domains.
- **No mechanics/numbers section.** The 23 portfolio companies are the proof.
- **Logo is base64-embedded inline.** Single-file HTML deploys cleanly.
- **WebP for embedded logos, PNG for the standalone logo file.**
- **Whole-body `zoom: 1.25` is applied to the body** for overall scale. Hugo asked for this explicitly to match how he reads the site at +25% browser zoom.
- **Logo sits LEFT of the tagline in the hero**, sized to match the two-line tagline height (`width: clamp(104px, 16.25vw, 234px)` after the 30% bump).
- **Wordmark + logo in nav**: text first, logo second was wrong. Logo first, then text — same as hero.

---

## Portfolio companies

Order matters — these are the actual portcos as of last edit. Update if Hugo adds/removes.

**Atoms (9):** dynamo air, eridale, apollo atomics, orion, starlife, vight, minerva, kickback, enough.

**Bits (10):** airbuds, argil, delphi, customuse, palabra, aicoustics, deduction, miso, klipy, eigen.

**Cells (4):** acorn genetics, phase labs, metabologic, kangaroo bio.

URLs are in the HTML — verify before changing.

---

## Deployment

- Hosted on Vercel, connected to this GitHub repo. Auto-deploys on every push to main.
- Custom domain: `babylon.vc` (apex serves) + `www.babylon.vc` (redirects to apex).
- Domain registrar: Atom (atom.com). DNS is slow — changes can take hours to propagate.
- HTTPS auto-issued by Let's Encrypt via Vercel.
- OG image cache: when changing `og-image.png`, validate via Twitter Card Validator, LinkedIn Post Inspector, and Facebook Debugger to bust their caches.

---

## How to iterate

When making changes to this site:

1. **Read the index.html before editing.** It's one file, ~360KB (most is the embedded logo). The CSS is at the top in a single `<style>` block, organized by section with `/* ============ */` comment dividers.
2. **Preserve the design tokens** — never hardcode colors, always use the CSS variables.
3. **Test the responsive breakpoint at 720px** — that's where the layout stacks for mobile. The breakpoint is intentionally low so the inline desktop layout holds at common laptop widths.
4. **Check that hero logo + tagline still sit inline at common widths** before committing. The logo is sized to match tagline height; if you change the tagline font size, also check the logo width clamp.
5. **When in doubt, default to restraint.** Babylon's brand is built on holding two things in tension (scholar + hedonist). The page reads correctly only when ~80% of it feels civilized. The hedonist energy is the punctuation, not the foundation.

---

## Open / future work

- Swap Google Fonts (Fraunces, Playfair Display, Lora) for licensed Canela + Tiempos Text (~$400-600 one-time) before serious LP outreach.
- Generate the painterly oil image deck (10 hero / interior / feast images) and weave them into hero, between sections, and in the dinner section.
- Babylon Letters (publication, formerly internetculture.co) — separate site at `babylon.co/letters`, not part of this repo.
- Email setup at `hugo@babylon.vc` — Google Workspace recommended, separate from website hosting.

---

## Test checklist before pushing

- [ ] Site renders at 1440px, 1280px, 1024px, 768px, 375px (Chrome DevTools device toolbar)
- [ ] All portfolio links work (open in new tab via `target="_blank" rel="noopener"`)
- [ ] OG card validates at https://www.opengraph.xyz/url/https%3A%2F%2Fbabylon.vc
- [ ] No console errors
- [ ] HTML still single file, deploys cleanly to Vercel

---

*Read this file before making changes. If you're about to violate one of the "Decisions already made" entries, stop and ask first.*
