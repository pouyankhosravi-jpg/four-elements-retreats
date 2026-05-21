# Four Elements Retreats — Static HTML Website

(Folder is named `wordpress-pouyan` for historical reasons — this is plain static HTML, not WordPress.)

## Live site & repo

- **Live**: http://fourelements-retreats.com (HTTPS pending Let's Encrypt cert provisioning by GitHub)
- **GitHub Pages fallback URL**: https://pouyankhosravi-jpg.github.io/four-elements-retreats/
- **Repo**: https://github.com/pouyankhosravi-jpg/four-elements-retreats (public, required for free GitHub Pages)
- **Branch served**: `main`, root folder
- **Custom domain config**: `CNAME` file in repo + Gandi DNS A records (185.199.108.153 / .109 / .110 / .111) on `@`, optional `www` CNAME → `pouyankhosravi-jpg.github.io.`
- **SSL**: Free auto-renewing Let's Encrypt cert provisioned by GitHub. Enable "Enforce HTTPS" once cert is ready via `gh api -X PUT '/repos/pouyankhosravi-jpg/four-elements-retreats/pages' -F 'https_enforced=true'`.

## Goal
Build a simple **static HTML website** (no backend, no JavaScript functionality) and deploy via **GitHub Pages**.

## Project Type
- Pure HTML + CSS only
- No JS frameworks, no build step, no backend
- All pages are hand-written `.html` files
- No external CDN fonts unless explicitly requested (current site uses system fonts only)

## Pages (4 total)
- `index.html` — Home (the long-form page; all major sections live here)
- `about.html` — About us (basic page, untouched recently)
- `retreats.html` — Retreats (basic page, untouched recently)
- `contact.html` — Contact (static info only, no form submission)
- `style.css` — Shared stylesheet

Nav order across every page: **Home / About us / Retreats / Contact**

## index.html section order (top → bottom)

Adjacent sections are separated by an 8px cream gap on desktop (rule: `main > section + section { margin-top: 8px; }`). On mobile (≤800px) this gap is removed and each section's own padding provides the rhythm.

1. **Header** (`.site-header` + `.nav`) — sticky, cream bg, logo + 4 nav links left-aligned with `gap: 140px` between logo and nav. Logo 100px tall → 56px at <700px → 48px at <380px. Nav wraps with `flex-wrap` on mobile.
2. **Banner** (`.banner`) — full-width `banner.png` hero. "View retreats" button absolutely positioned via `.banner-btn` at `top: 66% left: 8.5%`. Title text is BAKED INTO the image.
3. **Elements** (`.elements`) — full-width `elements.png` (Ground / Flow / Breathe / Glow). Text BAKED INTO the image.
4. **Retreat-feature** (`.retreat-feature` + `.retreat-feature-grid`) — 2-column. Left: text panel ("THE RETREAT" eyebrow, serif h2, lead paragraph, 5-item list with CSS sprite icons from `retreat-icons.png`, terracotta `.retreat-cta` → retreats.html). Right: full-bleed `costa-del-soul.jpg` (absolute-positioned img inside relative parent so it stretches to text height). Grid `minmax(380px, 500px) 1fr`. Icon sprite uses `mix-blend-mode: multiply` because the source PNG has a white bg.
5. **Location-banner** (`.location-banner`) — full-width `location-banner.png` ("THE LOCATION / Andalucía, Spain / Sun, stillness and space to reconnect" text baked in). HTML "EXPLORE THE LOCATION →" link absolutely positioned over the image at `left: 5.5% top: 68%`. Link goes to `retreats.html`.
6. **Heart-quote** (`.heart-quote` + `.heart-quote-grid`) — 3-column: photo | center text | photo (photos act as pillars). Center contains: large serif h2 ("Escape to the heart of Andalucía…" one line, `white-space: nowrap`), handwritten `.script` ("inspired by the elements") in terracotta, `.heart-quote-body` (4 short paragraphs), then `.cta-experience` terracotta pill button → contact.html. Photos use `object-fit: cover` to fill the pillar columns. Grid `minmax(240px, 1.2fr) minmax(0, 4.6fr) minmax(240px, 1.2fr)`. Container max 1400px.
7. **What-to-expect-section** (`.what-to-expect-section`) — decorative `what-to-expect-bg.png` as `background-size: 100% 100%` with `aspect-ratio: 1774 / 887`. HTML text positioned absolutely over the bg's structural elements (two bullet markers + middle divider). Uses `container-type: inline-size` + `cqw` units so text scales with section width. Two `.wte-block` text blocks at `top: 27%` and `top: 67%`. Mobile (<700px) drops the bg and stacks text normally.
8. **Four-days** (`.four-days` + `.fd-grid`) — Earth/Water/Fire/Spirit day cards. Decorative `four-days-bg.png` (1536×1024) as background — has top leaf ornament, 4 element icons at top of each column, vertical column dividers, and side botanicals. `aspect-ratio: 1536 / 1024`. Inside: 4-column grid with `padding: 22% 5% 4%`, each `.fd-col` has title (color-coded: `.fd-earth #8C5A32`, `.fd-water #6B7B5D`, `.fd-fire #B36238`, `.fd-spirit #B36238`), thin `#D8C8B8` rule with terracotta diamond accent, centered Georgia serif body in `#3F3A36`, and bottom photo (3:4.2 aspect, rounded corners, soft shadow). Mobile <900px drops the bg, reflows to 2-col; <600px stacks to 1 col.
9. **Special-guest** (`.special-guest`) — Sebastián Serpell sound journey. Uses `special-guest-bg.png` as bg (botanicals on sides + 5 icons baked in at bottom) with `aspect-ratio: 1536 / 880`. Absolute-positioned children: header (SPECIAL GUEST + SOUND JOURNEY), photo (`sebastian.png`) on left, text on right (signature + rule with diamond + body + small leaf SVG + 2nd body), and 5-column `.sg-labels` grid at `bottom: 3%` aligned under the bg icons (alternating terracotta `#B36238` and olive `#6F775D` titles + italic taupe `#7B6C63` subtitles). Mobile (<800px) drops bg and stacks.
10. **Meet-the-team** (`.meet-the-team`) — 4-column grid of team cards (Pouyan, Rosa, Chris, Kasia). Each card: 3:4 portrait photo + terracotta uppercase name with bottom divider + bio paragraphs. Small leaf SVG above the "MEET THE TEAM" title. Stacks 2-col under 1024px, 1-col under 600px. `padding: 50px 0 100px` (desktop) → `32px 0 56px` (mobile).
11. **Footer** (`.site-footer`) — dark green-dark bg, uppercase copyright line.

## Image Assets

| File | Use | Notes |
|---|---|---|
| `logo.jpg` | Top-left logo on every page | Sized to `height: 100px` (desktop) / `56px` (mobile). Cache-busted `?v=N`. |
| `banner.png` | Home page hero banner | Full-width. **Text baked in.** |
| `elements.png` | Home Four Elements section | Full-width. **Text baked in.** |
| `costa-del-soul.jpg` | retreat-feature right column | Cropped via `object-fit: cover` to stretch to text panel height. |
| `retreat-icons.png` | CSS sprite for retreat-feature bullets | 5 icons stacked vertically in 253×530. White bg neutralized with `mix-blend-mode: multiply`. Sprite scale: `background-size: 117px 245px`, positions `.retreat-icon-1` … `-5`. |
| `location-banner.png` | "The Location" full-width banner | 2172×724. Title baked in. Live HTML "EXPLORE THE LOCATION →" overlay. |
| `heart-photo-left.webp` | heart-quote left pillar | 1827×2560 portrait |
| `heart-photo-right.webp` | heart-quote right pillar | 1707×2560 portrait |
| `divider-leaf.png` | (unused after redesign) | 683×58 thin horizontal leaf divider |
| `what-to-expect.png` | (unused after redesign — replaced by bg+HTML) | Original baked-text version |
| `what-to-expect-bg.png` | what-to-expect section bg | 1774×887. Decorative botanicals + 2 bullet markers + middle diamond divider. NO text baked in. |
| `four-days-bg.png` | four-days section bg | 1536×1024. Top leaf ornament + 4 element icons + vertical column dividers + side botanicals. No text baked in. |
| `day-earth.jpg` | Day 1 (Earth) photo | Rainbow over Andalusian mountains |
| `day-water.jpg` | Day 2 (Water) photo | Pool + Andalusian courtyard |
| `day-fire.webp` | Day 3 (Fire) photo | Fire ceremony |
| `day-spirit.jpg` | Day 4 (Spirit) photo | Sound healing inside the geodesic dome |
| `sebastian.png` | special-guest left photo | 1448×1086, Sebastián playing instrument at sunset |
| `special-guest-bg.png` | special-guest section bg | 1536×1024. Top leaf ornament + side botanicals + 5 icons at bottom. No text baked in. |
| `team-pouyan.jpg` | Meet the team — Pouyan | (handpan in wooden room) |
| `team-rosa.jpg` | Meet the team — Rosa | (white dress in forest at sunset) |
| `team-chris.jpg` | Meet the team — Chris | (chef cooking) |
| `team-kasia.webp` | Meet the team — Kasia | (with white donkey in flower field) |

**Important:** images with text baked in (banner, elements, location-banner) won't reflow or stay crisp on retina. To change their text, you need a new image OR an HTML-overlay approach.

## Color Palette

CSS variables at the top of `style.css` (use these, don't hardcode):

| Token | Hex | Use |
|---|---|---|
| `--cream` | `#F7EEE3` | Main page background |
| `--cream-2` | `#EFE4D2` | Alt section background |
| `--terracotta` | `#B85A30` | Buttons, accents, link hover, h3 labels |
| `--terracotta-hover` | `#9F4824` | Button hover |
| `--teal` | `#3D6B7C` | Secondary accent (About h2s) |
| `--green-dark` | `#5B6647` | Footer |
| `--tan` | `#B89F76` | Subtle accent (unused, available) |
| `--text` | `#2E2418` | Body text |
| `--text-muted` | `#6B5E4D` | Secondary text, lead paragraphs |
| `--divider` | `#D9CDB4` | Borders, dividers |

**Section-specific hardcoded colors** (used in the Sebastián & Four Days sections per design spec):
- `#F5EEE6` — special-guest bg (warmer ivory than --cream)
- `#F6F0E8` — four-days bg
- `#B36238` — burnt terracotta (titles, signature, labels)
- `#3F352F` — warm charcoal brown (subtitle)
- `#4A4039` — warm dark taupe (body text in special-guest)
- `#3F3A36` — body text in four-days
- `#7B6C63` — warm muted taupe (label subtitles)
- `#6F775D` — olive green (alt label color, water title)
- `#8C5A32` — warm earthy brown (earth title)
- `#D8B39A` — faded terracotta beige (decorative rule, special-guest)
- `#D8C8B8` — column divider color (four-days rules)

## Typography (system fonts only)
- **Headings**: `Georgia, "Times New Roman", serif`
- **Body + nav**: system sans (`-apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif`)
- **Handwritten/script** (used for "inspired by the elements" and "Sebastián Serpell" signature): `"Snell Roundhand", "Brush Script MT", "Apple Chancery", "Lucida Handwriting", cursive`
- Nav links + button labels: uppercase with wide letter-spacing
- Many section titles use `clamp(min, Xcqw, max)` so they scale with their container width

## Reusable patterns

### Decorative bg image + live HTML overlay
Used in what-to-expect, four-days, and special-guest. Pattern:
```css
.section {
  position: relative;
  background-image: url("bg.png");
  background-size: 100% 100%;
  aspect-ratio: W / H;          /* lock to bg image aspect */
  container-type: inline-size;  /* enable cqw units for children */
}
.section .child {
  position: absolute;
  top: NN%;                     /* % positions scale with section */
  font-size: clamp(min, Xcqw, max);  /* font scales with section width */
}
```
On mobile, override: drop `aspect-ratio` (`auto`), drop `background-image`, set normal padding, position children statically.

### Consistent section gap
```css
main > section + section { margin-top: 8px; }    /* desktop */
@media (max-width: 800px) {
  main > section + section { margin-top: 0; }    /* rely on internal padding on mobile */
}
```

### Sprite icon positioning (retreat-icons.png)
Source 253×530 with 5 stacked icons. Y-centers measured by Python BMP-pixel-scan at ~57, 148, 244, 351, 463 (src px). CSS uses `background-size: 117px 245px` (0.462× scale). bg-pos-y centered:
- `.retreat-icon-1` → `-37px -4px` (yoga)
- `.retreat-icon-2` → `-37px -46px` (bowl)
- `.retreat-icon-3` → `-37px -91px` (plant)
- `.retreat-icon-4` → `-37px -140px` (3 people)
- `.retreat-icon-5` → `-37px -192px` (tent)

If a fresh source image is dropped in, re-measure with the same approach: `sips -z H W -s format bmp ... --out /tmp/p.bmp`, then Python BMP-pixel-scan to find dark row clusters → cluster centers.

## Mobile responsive breakpoints

- `<1024px` — meet-the-team goes 2-col
- `<900px` — heart-quote stacks, retreat-feature stacks, four-days goes 2-col (bg dropped)
- `<800px` — section gap removed (universal margin-top: 0), special-guest stacks (bg dropped)
- `<700px` — header nav wraps + smaller, what-to-expect stacks (bg dropped), most things shrink
- `<600px` — meet-the-team 1-col, four-days 1-col
- `<380px` — extra-narrow tweaks (logo 48px, nav font 0.66rem)

Mobile section padding is normalized to ~32px top/bottom for visual rhythm (instead of varying 50–80px which produced inconsistent gaps).

## Local Preview
```
cd ~/Downloads/wordpress-pouyan
python3 -m http.server 8082
# open http://localhost:8082
```

## Cache-Busting (IMPORTANT)
Browsers aggressively cache CSS + images. Every HTML page references the stylesheet with `?v=N` (currently `style.css?v=50`).

**Every time you edit `style.css`:**
```
cd ~/Downloads/wordpress-pouyan && sed -i '' 's/style.css?v=OLD/style.css?v=NEW/g' index.html about.html retreats.html contact.html
```
Bump the number by 1. Without this the user sees stale CSS and reports "didn't apply".

Replaced images also need their `?v=` bumped where they're referenced (see `retreat-icons.png?v=4`, `location-banner.png?v=2`, etc.).

If you forget, suggest a hard refresh (Cmd+Shift+R).

## Editing Rules
- Edit HTML/CSS files directly in this folder
- Keep the same header/footer/nav across every page (copy-paste, no templating)
- Update all 4 pages when changing the nav
- No JS — if a feature needs JS, ask first or skip it
- No external dependencies (no CDN fonts/JS) unless explicitly requested
- When user says "didn't apply" → check cache-bust version first, not the file contents
- For complex layouts (heart-quote, what-to-expect, four-days, special-guest), use the decorative-bg-image + live HTML overlay pattern (`aspect-ratio` + `background-size: 100% 100%` + `container-type: inline-size` + `cqw` units + absolute `%` positioning).

## Deployment workflow

Site auto-rebuilds on push to `main`:
```
cd ~/Downloads/wordpress-pouyan
git add <files>
git commit -m "..."
git push
```

After ~30–60s, changes are live on the GitHub Pages URL (and on the custom domain once DNS+cert are settled).

## DNS & domain notes (Gandi)
- Registrar: Gandi
- Apex domain `fourelements-retreats.com` → 4 A records pointing at `185.199.108.153` / `.109.153` / `.110.153` / `.111.153`
- Recommended `www` CNAME → `pouyankhosravi-jpg.github.io.` (trailing dot is required by Gandi)
- TTL: 1800
- HTTPS cert: auto-provisioned by GitHub Pages once DNS resolves. After cert exists: `gh api -X PUT '/repos/pouyankhosravi-jpg/four-elements-retreats/pages' -F 'https_enforced=true'` to force HTTPS redirect.

## Out of Scope
- WordPress (folder name is historical — this is plain HTML)
- Forms with actual submission
- Database, auth, server-side logic
- Any bug bounty / security work (this is a personal project)
