# Four Elements Retreats — Static HTML Website

(Folder is named `wordpress-pouyan` for historical reasons — this is plain static HTML, not WordPress.)

## Goal
Build a simple **static HTML website** (no backend, no JavaScript functionality) and deploy via **GitHub Pages**.

## Project Type
- Pure HTML + CSS only
- No JS frameworks, no build step, no backend
- All pages are hand-written `.html` files
- No external CDN fonts unless explicitly requested (current site uses system fonts only)

## Pages (4 total)
- `index.html` — Home (the long-form page; all major sections live here)
- `about.html` — About us
- `retreats.html` — Retreats (was originally `services.html`)
- `contact.html` — Contact (static info only, no form submission)
- `style.css` — Shared stylesheet

Nav order across every page: **Home / About us / Retreats / Contact**

## index.html section order (top → bottom)

1. **Header** (`.site-header` + `.nav`) — sticky, cream bg, logo + 4 nav links left-aligned with `gap: 140px` between logo and nav
2. **Banner** (`.banner`) — full-width `banner.png` hero. "View retreats" button absolutely positioned via `.banner-btn` at `top: 66% left: 8.5%`. Title text is BAKED INTO the image.
3. **Elements** (`.elements`) — full-width `elements.png` (Ground / Flow / Breathe / Glow). Text BAKED INTO the image.
4. **Retreat-feature** (`.retreat-feature` + `.retreat-feature-grid`) — 2-column. Left: text panel ("THE RETREAT" eyebrow, serif h2, lead paragraph, 5-item list with CSS sprite icons from `retreat-icons.png`, terracotta CTA → retreats.html). Right: full-bleed `costa-del-soul.jpg` (absolute-positioned img inside relative parent so it stretches to text height). Grid `minmax(380px, 500px) 1fr`. Icon sprite uses `mix-blend-mode: multiply` because the source PNG has a white bg.
5. **Location-banner** (`.location-banner`) — full-width `location-banner.png` ("THE LOCATION / Andalucía, Spain / Sun, stillness and space to reconnect" text baked in). HTML "EXPLORE THE LOCATION →" link absolutely positioned over the image at `left: 5.5% top: 68%`. Link goes to `retreats.html`. Has small `margin-top: 8px` to create a thin cream gap between this and the retreat-feature above.
6. **Heart-quote** (`.heart-quote` + `.heart-quote-grid`) — 3-column: photo | center text | photo. Center contains: large serif h2 ("Escape to the heart of Andalucía…" one line, `white-space: nowrap`), handwritten `.script` ("inspired by the elements") in terracotta, `.heart-quote-body` (4 short paragraphs), then `.cta-experience` terracotta pill button → contact.html. Photos use `object-fit: cover` to fill the pillar columns. Grid `minmax(240px, 1.2fr) minmax(0, 4.6fr) minmax(240px, 1.2fr)`. Container max 1400px.
7. **What-to-expect-section** (`.what-to-expect-section`) — decorative `what-to-expect-bg.png` as `background-size: 100% 100%` with `aspect-ratio: 1774 / 887`. HTML text positioned absolutely over the bg's structural elements (two bullet markers + middle divider). Uses `container-type: inline-size` + `cqw` units so text scales with section width. Two `.wte-block` text blocks at `top: 27%` and `top: 67%`. Mobile (<700px) drops the bg and stacks text normally.
8. **Special-guest** (`.special-guest`) — Sebastián Serpell sound journey. Uses `special-guest-bg.png` as bg (botanicals on sides + 5 icons baked in at bottom) with `aspect-ratio: 1536 / 880`. Absolute-positioned children: header (SPECIAL GUEST + SOUND JOURNEY), photo (`sebastian.png`) on left, text on right (signature + rule with diamond + body + small leaf SVG + 2nd body), and 5-column `.sg-labels` grid at `bottom: 3%` aligned under the bg icons (alternating terracotta `#B36238` and olive `#6F775D` titles + italic taupe `#7B6C63` subtitles). Mobile (<800px) drops bg and stacks.
9. **Meet-the-team** (`.meet-the-team`) — 4-column grid of team cards (Pouyan, Rosa, Chris, Kasia). Each card: 3:4 portrait photo + terracotta uppercase name with bottom divider + bio paragraphs. Small leaf SVG above the "MEET THE TEAM" title. Stacks 2-col under 1024px, 1-col under 600px. `padding: 50px 0 100px`.
10. **Footer** (`.site-footer`) — dark green-dark bg, uppercase copyright line.

## Image Assets

| File | Use | Notes |
|---|---|---|
| `logo.jpg` | Top-left logo on every page | Sized to `height: 100px` in CSS. Cache-busted `?v=N`. |
| `banner.png` | Home page hero banner | Full-width. **Text baked in.** |
| `elements.png` | Home Four Elements section | Full-width. **Text baked in.** |
| `costa-del-soul.jpg` | retreat-feature right column | Cropped via object-fit: cover to stretch to text panel height. |
| `retreat-icons.png` | CSS sprite for retreat-feature bullets | 5 icons stacked vertically in a 253×530 image. Source has cream/white bg — site uses `mix-blend-mode: multiply` to make it invisible against the cream page. Sprite scale: `background-size: 117px 245px`, positions `.retreat-icon-1` through `.retreat-icon-5`. |
| `location-banner.png` | "The Location" full-width banner | 2172×724. Title text baked in. Live HTML "EXPLORE THE LOCATION →" link overlaid via `.location-banner-cta` with absolute positioning. |
| `heart-photo-left.webp` | heart-quote left pillar | 1827×2560 portrait |
| `heart-photo-right.webp` | heart-quote right pillar | 1707×2560 portrait |
| `divider-leaf.png` | (unused now — was previously below "inspired by the elements") | 683×58 thin horizontal leaf divider |
| `what-to-expect-bg.png` | what-to-expect section bg | 1774×887. Decorative botanicals + 2 bullet markers + middle diamond divider. NO text baked in (text added via HTML). |
| `sebastian.png` | special-guest left photo | 1448×1086, Sebastián playing instrument at sunset |
| `special-guest-bg.png` | special-guest section bg | 1536×1024. Top leaf ornament + side botanicals + 5 icons at bottom. No text baked in. |
| `team-pouyan.jpg` | Meet the team — Pouyan | (handpan in wooden room) |
| `team-rosa.jpg` | Meet the team — Rosa | (white dress in forest at sunset) |
| `team-chris.jpg` | Meet the team — Chris | (chef cooking) |
| `team-kasia.webp` | Meet the team — Kasia | (with white donkey in flower field) |

**Important:** images with text baked in (banner, elements, location-banner) won't reflow or stay crisp on retina. To change their text, you need a new image OR an HTML-overlay approach.

## Color Palette
Defined as CSS variables at the top of `style.css` — use these, don't hardcode.

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

**Section-specific hard-coded colors** (used in the Sebastián section per design spec):
- `#F5EEE6` — special-guest bg (warmer ivory than --cream)
- `#B36238` — burnt terracotta (title, signature, labels)
- `#3F352F` — warm charcoal brown (subtitle)
- `#4A4039` — warm dark taupe (body text)
- `#7B6C63` — warm muted taupe (label subtitles)
- `#6F775D` — olive green (alt label color)
- `#D8B39A` — faded terracotta beige (decorative rule)

## Typography (system fonts only)
- **Headings**: `Georgia, "Times New Roman", serif`
- **Body + nav**: system sans (`-apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif`)
- **Handwritten/script** (used for "inspired by the elements" and "Sebastián Serpell" signature): `"Snell Roundhand", "Brush Script MT", "Apple Chancery", "Lucida Handwriting", cursive`
- Nav links + button labels: uppercase with wide letter-spacing
- Many section titles use `clamp(min, Xcqw, max)` so they scale with their container width

## Local Preview
```
cd ~/Downloads/wordpress-pouyan
python3 -m http.server 8082
# open http://localhost:8082
```

Server is typically left running in the background while editing.

## Cache-Busting (IMPORTANT)
Browser aggressively caches CSS + images. Every HTML page references the stylesheet with a `?v=N` query string (currently at `style.css?v=46`).

**Every time you edit `style.css`:**
```
cd ~/Downloads/wordpress-pouyan && sed -i '' 's/style.css?v=OLD/style.css?v=NEW/g' index.html about.html retreats.html contact.html
```
Bump the number by 1. Without this the user sees stale CSS and reports "didn't apply".

Replaced images also need their `?v=` bumped in CSS/HTML (see `retreat-icons.png?v=4`, `location-banner.png?v=2`, etc.).

If you forget, suggest a hard refresh (Cmd+Shift+R).

## Editing Rules
- Edit HTML/CSS files directly in this folder
- Keep the same header/footer/nav across every page (copy-paste, no templating)
- Update all 4 pages when changing the nav
- No JS — if a feature needs JS, ask first or skip it
- No external dependencies (no CDN fonts/JS) unless explicitly requested
- When user says "didn't apply" → check cache-bust version first, not the file contents
- For complex layouts (heart-quote, what-to-expect, special-guest) the patterns to know:
  - `aspect-ratio` + `background-size: 100% 100%` to lock a bg image to a known shape
  - `container-type: inline-size` + `cqw` units for text that scales with the section
  - Absolute positioning with `%` coords so overlays scale together with the bg

## Sprite icon positioning notes (retreat-icons.png)
The source image is 253×530 with 5 stacked icons. Source y-centers were measured by Python downsample to ~57, 148, 244, 351, 463. CSS uses `background-size: 117px 245px` (0.462x scale). bg-pos-y values land at the center of each icon's view:
- `.retreat-icon-1` → `-37px -4px` (yoga, spiral)
- `.retreat-icon-2` → `-37px -46px` (bowl with leaves)
- `.retreat-icon-3` → `-37px -91px` (plant)
- `.retreat-icon-4` → `-37px -140px` (3 people)
- `.retreat-icon-5` → `-37px -192px` (tent)

If a fresh source image of the same icons is dropped in, re-measure with the same Python BMP-pixel-scan approach (downsample → analyze brightness per row → cluster icon ranges).

## GitHub Pages Deployment
When ready to publish:
1. `git init` in this folder
2. Create repo on GitHub (e.g. `four-elements-retreats`)
3. `git remote add origin <repo-url>`
4. `git add . && git commit -m "initial site"`
5. `git push -u origin main`
6. On GitHub → Settings → Pages → Source: `main` branch, `/ (root)` folder
7. Site goes live at `https://<username>.github.io/<repo-name>/`

For a custom domain or user/org site (`<username>.github.io`), ask first.

## Out of Scope
- WordPress (folder name is historical — this is plain HTML)
- Forms with actual submission
- Database, auth, server-side logic
- Any bug bounty / security work (this is a personal project)
