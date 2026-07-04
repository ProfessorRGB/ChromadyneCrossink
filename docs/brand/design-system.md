# Chromadyne Industries — Design System

> Form CD-100 · Color · Signal · Continuity
> The future, in an orderly manner.

Chromadyne Industries is a (fictional) mid-century American corporation, **est. 1949**, headquartered in **Orlando, Fla.** Its business is the orderly preparation of the future: it *"detects faint indications of what is coming, classifies them by color and consequence, and prepares them for general distribution."* The brand is a deadpan, bureaucratic institution — equal parts government agency, cold-war research lab, and pigment standards body. Everything is filed under a form number; enthusiasm is permitted but shall not appear in official correspondence.

The system encodes that voice into a tight, opinionated visual language: warm paper, near-black ink, a four-color "chroma" rule (Signal Red / Carrier Orange / Reference Gold / Continuity Blue), a heavy uppercase grotesk, and IBM Plex Sans/Mono. Hard 2px rules, square corners, no soft shadows.

The public-facing operating unit is **Displaced Futures Co.** (CD-DIV/01), the Corporation's design & brand division — the "author" of this system.

---

## Sources

This system was reverse-engineered from a single self-contained brand artifact provided by the user:

- **Codebase:** `Chromadyne/` (mounted locally), containing:
  - `chromadyne.html` — a complete one-page corporate site (Index / Charter / Organization / Divisions / Bulletins). The canonical source of voice, layout, color, and type. Copied to `reference/chromadyne-site.html`.
  - `chromadyne-wallpaper.svg` / `chromadyne-wallpaperDark.svg` — brand wallpapers (Adobe Illustrator export). Copied to `assets/`.
  - `ChromadyneLightWP.png` / `ChromadyneDarkWP.png` — rendered wallpapers. Copied to `assets/`.

No Figma, no external repo. The brand is fully specified by the above.

> **Font note:** the wallpaper SVG specifies the display face as **Neue Haas Grotesk Display Pro 95 Black** (a licensed typeface, not bundled). The live HTML substitutes **Archivo Black** (Google Fonts), which we adopt as the working web display face. *If you have the licensed Neue Haas files, drop them in and update `tokens/fonts.css` + `--font-display`.*

---

## Content fundamentals

How Chromadyne writes. The voice is the brand.

- **Register:** deadpan institutional / bureaucratic. Reads like a government form or an internal memo from 1955. Dry, formal, quietly absurd. Never winks at the reader.
- **Person:** third-person and impersonal. "The Corporation," "Personnel are reminded…," "Operators are advised…." Almost never "you"; never "we" casually — it's "the Corporation." First person is reserved for signed correspondence.
- **Casing:** Display headings and labels are **UPPERCASE**. Body copy is sentence case. Mono labels are uppercase with wide tracking.
- **Tense & mood:** present tense, declarative, often imperative-by-policy ("shall," "must," "are to be regarded as").
- **Tone moves:**
  - State absurd things with total seriousness: *"Futures stored improperly have been observed to leak into the present."*
  - Bureaucratic understatement: *"answered in the order deserved."*
  - Policy framed as physics: *"Preparation is therefore a manufacturing problem."*
  - Mild menace, politely worded: *"the noise floor is to be regarded as a suggestion."*
- **Naming:** everything has a form/file code — `FORM CD-100 · REV. 6/26`, `CD-DIV/01`, `CD-0061/010`. Divisions read like agency directorates ("Weak Signals Directorate," "Phosphor Works").
- **Taglines:** short, declarative, uppercase. *"The future, in an orderly manner." · "Color · Signal · Continuity." · "Chromadyne neither predicts the future nor prevents it. Chromadyne prepares it."*
- **Emoji:** never. Exclamation points: effectively never. No marketing hype, no "delight," no second-person calls to action beyond a dry "accepting commissions."

When writing new copy, file it under a plausible CD-form number, keep sentences complete and measured, and resist any urge to be friendly.

---

## Visual foundations

Answers to the "how does it look" questions.

**Palette.** Warm **Paper** `#EFEAE0` substrate, warm near-black **Ink** `#17140E`. Four working colors, each carrying meaning: **Signal Red** `#D9341C` (active / public-facing), **Carrier Orange** `#E87B1E` (in transit), **Reference Gold** `#DFA41B` (standards / reference), **Continuity Blue** `#24539B` (standing / archived). Color is *functional* — status is read by hue. Two colors max per surface beyond the chroma band. Gradients are **not** used. See `tokens/colors.css`.

**Type.** Three voices: **Display** = Archivo Black (sub for Neue Haas 95 Black), set UPPERCASE, tracking −0.01em, line-height 0.95 — big, blunt, architectural. **Sans** = IBM Plex Sans for all running text. **Mono** = IBM Plex Mono for form codes, eyebrows, labels, metadata, navigation — wide letter-spacing (0.08em–0.34em). The mono/grotesk pairing is the signature. See `tokens/typography.css`.

**Backgrounds.** Flat paper or flat ink. No photography, no illustration washes, no texture or grain, no gradients. The only decorative graphic is the **concentric quarter-arc "radar"** (red innermost → blue outermost) anchored to a corner — used large in heroes (`assets/arc-motif.svg`). The **chroma band** (four equal color segments) is the recurring ornamental rule, placed under headers and above footers.

**Layout.** Centered column, `max-width: 1080px`, 24px gutters. Strict **8px spacing grid** (`tokens/spacing.css`). Heavy use of full-width 2px rules to divide sections. Content is organized like a form or register: ruled rows, grid tables, code in the left column, status at the right. Sticky header.

**Borders & corners.** The **2px solid ink rule** is the structural unit (`--rule`). Corners are **square — always.** The only rounded shape is a status **dot** (and the corner pellet on the arc motif). Dashed 2px rules denote "special / classified" units.

**Shadows.** No blur, ever. The one permitted shadow is a **hard offset block** — `6px 6px 0` in Signal Red — used to flag the active / public-facing unit (e.g. Displaced Futures Co. in the org chart). See `--shadow-block`.

**Motion.** Restrained. The hero arcs **draw on** once via `stroke-dashoffset` over ~1.4s with `cubic-bezier(.6,0,.2,1)`, staggered per ring; respects `prefers-reduced-motion`. No bounces, no parallax, no looping decoration. State changes are fast (~0.12s) color/background swaps.

**Hover & press.** Hover **inverts**: outline elements and ruled rows flip to ink-fill / paper-text (`.divrow:hover`, nav items gain a 2px ink border, the active nav item is ink-filled). Solid buttons deepen slightly; accent buttons go to their `-deep` shade. No scale/shrink on press. Links in the footer underline in gold on hover.

**Focus.** Always visible: `3px solid Continuity Blue`, 2px offset.

**Transparency & blur.** Essentially none — the system is opaque and printed-feeling. Ink text on color uses ink/paper opacity steps (`--ink-70`, etc.) only for secondary text, never frosted glass or backdrop blur.

**Cards.** A card is a **bordered document panel**: 2px ink rule, square, flat paper fill, optional 8px color **stripe** across the top to classify it, optional ink-ruled header (display title left, mono form code right). "Active" cards carry the red offset-block shadow. No rounded corners, no drop shadow, no inner glow.

**Imagery vibe.** There is essentially no photographic imagery in the brand. If imagery is ever introduced, it should read warm and archival (paper-toned), never cool or glossy — but the house default is *type + rule + color*, not pictures.

---

## Iconography

Chromadyne is **near-iconless by design** — it is a typographic, form-driven system.

- **No icon font, no SVG icon set** ships in the source. The brand communicates with type, ruled lines, color, and form codes instead of pictograms.
- **Glyphs in use:** the **middle dot `·`** is the brand's universal separator (`FORM CD-100 · REV. 6/26`, `COLOR · SIGNAL · CONTINUITY`). Used constantly. Em-dashes separate article titles.
- **Status is shown with colored dots/squares**, not icons — see the `StatusDot` component (round for the four working statuses; a hollow ink **square** for "classified/limited," the one non-round form).
- **The arc motif** (`assets/arc-motif.svg`) and **chroma band** are the only recurring graphic devices. The **logomark** (`assets/logomark.svg`) is concentric quarter-arcs in a black square.
- **Emoji:** never used.
- **Custom carets** (form select) are drawn as simple CSS triangles in ink, not icon glyphs.

**If you need icons** (e.g. for a richer product UI the brand never specified): use a **thin, geometric, single-weight line set** that won't fight the square, mechanical feel — **Lucide** (1.5–2px stroke) is the closest CDN-available match. Keep them ink-colored, small, and rare. **Flag any icon use as an extension beyond the documented brand.** Do not hand-draw bespoke SVG icons or use emoji as icons.

---

## Index / manifest

**Root**
- `styles.css` — global entry point (consumers link this). `@import` manifest only.
- `readme.md` — this file.
- `SKILL.md` — Agent-Skill front-matter wrapper.
- `reference/chromadyne-site.html` — the original source brand artifact.

**Tokens** (`tokens/`, all reachable from `styles.css`)
- `fonts.css` — `@import` of Archivo Black + IBM Plex Sans/Mono (Google Fonts). Neue Haas substitution noted here.
- `colors.css` — paper/ink ground, four working colors + `-deep` shades, neutral steps, semantic aliases, status mapping.
- `typography.css` — families, weights, type scale, line-heights, letter-spacing.
- `spacing.css` — 8px grid, layout widths.
- `effects.css` — borders/rules, radii (square!), the offset-block shadow, motion.

**Foundation cards** (`guidelines/`) — specimen cards for the Design System tab: working colors, ground, status encoding; display/body/mono/type-scale; spacing scale, borders & shadow; logo, chroma band, arc motif, voice.

**Components** (`components/`) — React primitives, CSS-variable styled, square & mono:
- `actions/` — **Button** (solid / outline / accent / ghost; sm/md/lg; working-color accents).
- `data-display/` — **StatusDot**, **Badge**, **Tag**, **Card**.
- `layout/` — **ChromaBand**, **FormLine**, **Notice**, **Kicker**.
- `forms/` — **Input**, **Select**.

Each component directory has `<Name>.jsx`, `<Name>.d.ts`, a `*.prompt.md`, and one `@dsCard` `*.card.html` demo. Mount in HTML via `const { Button } = window.ChromadyneDesignSystem_2613a1` after loading `_ds_bundle.js`.

**UI kit** (`ui_kits/corporate/`) — interactive recreation of **chromadyne.com**: Masthead, IndexPage (hero + capabilities + division register + latest bulletin), CharterPage, OrganizationPage (org tree), DivisionsPage, BulletinsPage, SiteFooter. `index.html` runs the full click-through and composes the component primitives. Also registered as a Starting Point.

**Assets** (`assets/`) — `logomark.svg`, `logo-lockup-light.svg`, `logo-lockup-dark.svg`, `arc-motif.svg`, light/dark wallpapers (`.svg` + `.png`).
