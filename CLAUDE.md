# Four Elements Retreats — Static HTML Website

(Folder is named `wordpress-pouyan` for historical reasons — this is plain static HTML, not WordPress.)

## Live site & repo

- **Live**: https://fourelements-retreats.com
- **GitHub Pages fallback URL**: https://pouyankhosravi-jpg.github.io/four-elements-retreats/
- **Repo**: https://github.com/pouyankhosravi-jpg/four-elements-retreats (public, required for free GitHub Pages)
- **Branch served**: `main`, root folder
- **Custom domain config**: `CNAME` file in repo + Gandi DNS A records (185.199.108.153 / .109.153 / .110.153 / .111.153) on `@`, optional `www` CNAME → `pouyankhosravi-jpg.github.io.`
- **SSL**: auto-renewing Let's Encrypt cert by GitHub, HTTPS enforced

## Project type

- Pure HTML + CSS, no build step, no backend
- 4 hand-written `.html` pages + one shared `style.css`
- **JavaScript is allowed only where explicitly requested**:
  - vanilla IntersectionObserver on `index.html` for the mobile play-on-scroll video clip in the heart-quote section
  - CSS scroll-driven animations via `@supports (animation-timeline: view())` on retreats.html (no JS)
- Google Fonts (Cinzel, Cormorant Garamond, Inter) loaded **only on `retreats.html`** for the premium type system. Other pages stay on system fonts.

## Pages

| File | Role |
|---|---|
| `index.html` | Home — long-form sales page with all the original sections |
| `about.html` | About us — story + Meet the Team grid |
| `retreats.html` | **The primary conversion landing page** — every recent design pass has gone here |
| `contact.html` | Contact — static info |
| `style.css` | Shared stylesheet for all four pages |

Nav order on every page: **Home / About us / Retreats / Contact**

## Current pricing model (live on retreats.html)

| | |
|---|---|
| Standard price | **€899** per person |
| Early bird | **€799** per person — save €100 until **30 June 2026** |
| Deposit | **15%** (~€120) to hold a place |
| Free cancellation | until **31 July 2026** (full deposit refund) |
| After 31 July | deposits non-refundable but transferable to a future retreat |
| Single tent upgrade | **+€180** (limited availability) |
| Dates | **4–7 September 2026** (Fri 3 PM → Mon 11 AM CEST) |
| Group size | **12 guests max** |
| Airport transfer | included (pickup + drop-off from Málaga) |

## Brand voice rules (apply to every page)

These were set during the conversion/inclusivity rewrite. Do **not** drift back into the old wording.

- ❌ Never call guests "**souls**" as a headcount → ✅ "guests" or "spaces"
- ❌ Never use "**soulful**" more than once on a page
- ❌ No "**around the fire**", "fire ceremony", "fire release" — there is currently **no fire on site**. The elemental theme (Earth · Fire · Water · Air) stays as a thematic frame only.
- ❌ No "**like-minded souls**", "be witnessed", "spiritual traditions from around the world", "Osho", "open heart" (as packing item), "inner glow", "inner vitality", "magic within"
- ✅ Vegetarian menu is described as "**plant-rich Mediterranean cooking — generous, satisfying**" + "most guests don't notice the absence of meat"
- ✅ Location is **"Málaga, Andalucía"** only — never "Guaro" or any specific town
- ✅ Inclusivity line where applicable: "**All bodies, all ages and all levels of experience are welcome**"
- ✅ CTAs avoid pressure phrasing ("the moment is precious, the spaces don't last" → "while spots are still open")

## Typography system

### retreats.html (the premium page — Google Fonts)
- **Cinzel 500** — small-caps eyebrows, 0.38–0.5em letter-spacing, muted terracotta `#B36238`
- **Cormorant Garamond 400/500** — section titles, card titles, italic leads, in deep espresso `#2A211B` or `#2F241D`
- **Inter 400/500** — body text and small labels, soft charcoal `#5E554D` or `#6D6259`
- **Snell Roundhand** — script accents ("if you've been craving a reset…")

### index.html / about.html / contact.html (system fonts)
- **Georgia, "Times New Roman", serif** for headings
- **System sans** (`-apple-system, BlinkMacSystemFont, ...`) for body
- **Snell Roundhand** for handwritten accents

## Header (shared across every page)

```
[ logo (52 px) ]                              HOME · ABOUT US · RETREATS · CONTACT
```

- Background `#F6EFE4` (sampled exactly from the logo JPG so the logo dissolves into it)
- Border-bottom `1px solid var(--divider)`
- **Sticky**, 76 px desktop / 64 px mobile
- Logo left, nav hard-right via `justify-content: space-between`
- Nav: system sans, 0.72 rem, 0.18em letter-spacing, color `#2f3540`
- Hover → muted silver `#8b8b8b`; active link → solid black `#111`

## retreats.html section order (top → bottom)

Adjacent sections separated by a 4 px gap (`main > section + section { margin-top: 4px }`). Mobile (≤800px) drops this to 0.

1. **Banner** (`.banner.retreat-banner`)
   - Background image: `retreat-hero.jpg` (cream backdrop + arched meditation-circle photo on right, mountains lower-left, olive sprigs)
   - **Height driven by text content** (overlay is `position: relative`, image is `position: absolute; inset: 0`). `min-height: 320 px` keeps the photo readable
   - Left-aligned content stack in the cream half: Cinzel eyebrow ("THE RETREAT · 4–7 SEPTEMBER 2026") + Cormorant Garamond title ("Ground. Flow. / Breath. Glow.") + italic lead + filled-terracotta `Reserve your place →` CTA scrolling to `#book`

2. **Trust bar** (`.trust-bar`)
   - **Deep espresso background `#2F241D`** with cream text (no longer terracotta — that's reserved for CTAs)
   - 4 cells: Dates · Location · Group · Includes (no price here — too aggressive right after the hero)
   - Type: Cinzel labels at 0.62 rem / 0.28em, Cormorant values at 1.02 rem

3. **Retreat-intro** ("An invitation") — soft warm cream `#FBF8F2`, 5 typographic moments only: eyebrow → title ("You'll know when / it's time to slow down") → italic Cormorant lead → Inter sensory paragraph → 5 px terracotta dot → Snell Roundhand signature

4. **Who-its-for** ("Is this for you?")
   - Pure-CSS backdrop: warm cream gradient with a 22% terracotta radial-glow under the YES card and an 18% taupe radial-glow under the NO card (matches the sun/moon symbols on the cards)
   - Header: tiny sun SVG + hairline → Cinzel eyebrow → Cormorant title "This retreat is a *yes* if…" → small line/circle/line SVG ornament
   - 2 cards: **YES** (terracotta accent line + sun icon disk + 7 ✓ bullets including the inclusivity line) / **NO** (taupe moon icon disk + 3 em-dash bullets — title softened to "It might be worth waiting if…")

5. **Included** ("Everything you need to soften and arrive")
   - 2-col grid (1.35fr / 1fr): `included-collage.jpg` (6-panel landscape grid) on left + 7-bullet list on right
   - Bullets are logistics only (3 nights tent, 3 meals + tea, programme summary, welcome pack, airport transfer, pool/jacuzzi, group of 12)

6. **Accommodation** ("Bell tents under the Andalusian stars")
   - 3 equal cards (`repeat(3, 1fr)`), 4:3 aspect
   - Captions: `Under the stars · Nights at the camp` / `Twin tent — shared · Included in the retreat price` / `Single tent — private · Optional upgrade · +€180`

7. **Practices** ("The practices that shape your journey")
   - Warm bone `#F5F0E8` background with paper grain
   - 4 cards in one row (`repeat(4, 1fr)`), 2×2 at ≤1000px, stacked at ≤560px
   - Each card: **4:3 image area at the top** + 3 px element-coloured stripe + body. Element classes:
     - `.elem-earth` (Body / Yoga & Movement) → `#484830` olive — image `yoga.jpg` at `object-position: center 30%`
     - `.elem-water` (Inner / Meditation & Inner Work) → `#486078` blue — image `meditate.jpg` at `object-position: center 30%`
     - `.elem-fire` (Voice / Sound, Voice & Expression) → `#A86030` terracotta — image `day-spirit.jpg`
     - `.elem-air` (Nature / Nature Immersion) → `#8A6A38` warm gold — image `nature.jpg`
   - **Element labels were removed** — each card shows only the Cormorant title now (no Cinzel "EARTH · BODY" eyebrow)

8. **Facilitators** ("Meet your guides")
   - 2 equal photo cards (Rosa left, Pouyan right). 4:5 portrait, 880 px max-width container
   - Each card: photo + name + role (Inter terracotta small caps) + one-sentence Inter bio

9. **Nourishment** ("Nourishment & the kitchen")
   - Warm bone bg with paper grain
   - 4-up image strip at top (`repeat(4, 1fr)`): chef plating + sunset dinner + chef serving dessert + long table
   - 2-col body: chef Chris bio + "A day at the table" rhythm list (Morning / Midday / Afternoon / Evening)
   - Vegetarian wording: "**Plant-rich Mediterranean cooking — generous, satisfying and made with fresh Andalusian ingredients**"

10. **Timetable** ("A day-by-day rhythm")
    - 4 day-detail cards: Friday/Earth, Saturday/Fire, Sunday/Water & Air, Monday/Spirit
    - **Specific clock times** (e.g. "7:30–8:30 AM Dynamic Morning Yoga")
    - Saturday 9:15 PM is **"Letting Go Ceremony — a candlelit ritual to write down and release what no longer serves you"** (was Fire Release — adjusted for the no-fire constraint)
    - Sunday 6–7 PM is a featured highlighted row for **Sebastián Serpell**'s sound healing session (`.schedule-feature` class adds a terracotta left border)

11. **Outcomes** ("Four days that stay with you")
    - Editorial 2×2 grid with the right column shifted down 72 px for magazine-style stagger
    - 4 cards with oversized italic Cormorant numerals (01–04) at 14% opacity as watermarks
    - Card titles: "A nervous system reset" / "Practices you can return to" / "Meaningful human connection" / "Clarity & creative renewal"

12. **Welcome pack** ("Your Four Elements welcome pack")
    - White card with 3 px terracotta top border, 2-column bullet list (8 items: journal, element envelopes, perfumes, illustrated map, etc.)

13. **Investment** ("Reserve your place") — `id="book"`
    - White card on cream-2 background
    - Top: scarcity pill "Limited spaces · only 12 guests"
    - **Price block**: terracotta pill "Early bird · save €100 until 30 June" + headline `~~€899~~ €799 per person` (struck-through anchor + new price on one line)
    - Meta list: Dates, Arrival, Departure, Group size, **Deposit · Just 15% (≈ €120)**, **Cancellation · Free until 31 July 2026**, Airport transfer, Private tent
    - "How to reserve" 3-step process (terracotta numeric pills)
    - Primary CTA → `contact.html` + secondary WhatsApp link → `wa.me/34640124026`
    - Fine print: "Free cancellation until 31 July 2026 — full deposit refund."

14. **Gallery** ("Moments from the past") — 11 unique images, 4-col grid with `grid-auto-flow: dense`, 170 px rows, mix of `.gallery-tall` and `.gallery-wide` for editorial rhythm. Fire-related photos removed.

15. **Founders note** ("Why we created Four Elements Retreats") — personal letter from Rosa & Pouyan, 720 px narrow container, Snell Roundhand signature

16. **Location** ("Hidden in the hills of Málaga")
    - Heading + 2-col text/map grid (Google Maps embed, no API key)
    - **Facilities & amenities** list with 10 inline-SVG icons (Wisdome, Shadome, amphitheatre, pool/jacuzzi, sauna, bell tents, kitchen, trails, donkeys, etc.)
    - "A glimpse of the space" mini gallery — 12 `facility-*.jpg` images

17. **FAQ** ("Your questions, answered") — 8 native `<details>` items, `+` / `−` terracotta circular markers

18. **Final CTA** (`.page-cta.page-cta-urgent`) — "Reserve your place" with anchor link to `#book`

19. **Sticky mobile CTA bar** — fixed bottom bar on mobile only: `€799` + `4–7 Sept · 12 spots` + Reserve button (linked to `#book`). Body padding adjusted via `body:has(.sticky-cta-mobile)`.

## index.html section order

Largely unchanged structure since the original build — only the **copy** was rewritten in the brand-voice pass:

1. Banner (`banner-plain.jpg` with overlay)
2. Elements strip (`elements.png`)
3. Retreat-feature (2-col text + `costa-del-soul.jpg`)
4. Location-banner
5. Heart-quote (3-col with mobile video clip + IntersectionObserver script)
6. What-to-expect (decorative bg + 2 text blocks)
7. Four-days (Earth/Water/Fire/Spirit with `day-*.jpg` photos)
8. Special-guest (Sebastián Serpell)
9. Meet-the-team (Pouyan / Rosa / Chris / Kasia)
10. Location-extras (extra image)
11. Footer

## about.html

- Page header (h1 "A small team devoted to the elements")
- About-story (Where it began / Inspired by the elements / What guides us)
- Meet the Team (4 cards: Pouyan, Rosa, Chris, Kasia)
- Page CTA

## Color palette

CSS variables at the top of `style.css` (use these where possible):

| Token | Hex | Use |
|---|---|---|
| `--cream` | `#F7EEE3` | Main page background |
| `--cream-2` | `#EFE4D2` | Alt section background |
| `--terracotta` | `#B85A30` | Primary CTAs only |
| `--terracotta-hover` | `#9F4824` | Button hover |
| `--text` | `#2E2418` | Body text |
| `--text-muted` | `#6B5E4D` | Secondary text |
| `--divider` | `#D9CDB4` | Borders, dividers |

**Hardcoded colors used in the premium retreats.html system:**
| Hex | Use |
|---|---|
| `#F6EFE4` | Header background (exact match to logo JPG) |
| `#FBF8F2` | Soft warm cream (retreat-intro) |
| `#F5F0E8` | Warm bone (practices, nourishment) |
| `#F3E0CB` | Peach cream (banner fallback) |
| `#2F241D` / `#2A211B` | Title espresso |
| `#5A4A40` | Italic lead text |
| `#5E554D` / `#6D6259` | Body charcoal |
| `#4C4138` | Stronger body charcoal |
| `#9A4F26` | Deeper terracotta (text, signatures) |
| `#B36238` | Standard terracotta accent (labels, stripes) |
| `#214 169 134` (rgba glows) | Soft sun-side glow |
| **Logo element colours (sampled from `logo.jpg`)** | |
| `#484830` | Earth — olive |
| `#486078` | Water — dusty blue |
| `#A86030` | Fire — terracotta |
| `#C0A878` / `#8A6A38` | Air — warm gold |

## Image assets (current state)

### Banner & section backgrounds
| File | Use |
|---|---|
| `retreat-hero.jpg` | Retreats banner — 21:9 cream + arched meditation photo |
| `invitation-bg.jpg` | (kept on disk, not currently used in HTML) |
| `banner-plain.jpg` | Home page banner |
| `banner.png` | Old home banner (kept) |
| `location-banner.png` | "The Location" banner on home + about |
| `elements.png` | Home Four Elements strip |

### Retreats page imagery
| File | Section |
|---|---|
| `included-collage.jpg` | "What's included" — 6-panel landscape grid |
| `accommodation-night.jpg` | Accommodation "Under the stars" |
| `accommodation-single.jpg` | Single private tent |
| `accommodation-double.jpg` | Twin shared tent |
| `yoga.jpg` | Practices/Earth (Body) card |
| `meditate.jpg` | Practices/Water (Inner) card |
| `nature.jpg` | Practices/Air (Nature) card |
| `day-spirit.jpg` | Practices/Fire (Voice) card |
| `team-rosa.jpg` | Facilitators — Rosa portrait |
| `team-pouyan.jpg` | Facilitators — Pouyan portrait |
| `team-chris.jpg` | Used on home/about Meet-the-team |
| `team-kasia.webp` | Used on home/about Meet-the-team |

### Gallery (retreats page) — 11 unique
gallery-2 (meditation circle, tall), gallery-13 (pool), gallery-15 (poolside), gallery-14 (outdoor meditation, wide), gallery-9 (dome at sunset, tall), gallery-3 (live guitar), gallery-5 (group sharing, **kept but had no fire-explicit alt**), gallery-12 (Andalusian house, wide), gallery-10 (glamping tent), gallery-11 (kept), gallery-16 (bell tent interior)

Removed from gallery to dedupe with Nourishment: gallery-1, gallery-4, gallery-6, gallery-7 (those are in the Nourishment strip)
gallery-8 is in the gallery section (was previously also in Nourishment bottom row, which is removed)

### Facility images (Location section, retreats page)
12 facility images — `facility-wisdome-ext.jpg`, `facility-wisdome-int.jpg`, `facility-shadome.jpg`, `facility-pool.jpg`, `facility-jacuzzi.jpg`, `facility-sauna.jpg`, `facility-belltent.jpg`, `facility-amphitheatre.jpg`, `facility-kitchen.jpg`, `facility-donkey.jpg`, `facility-trails.jpg`, `facility-aerial.jpg`

### Home page (index.html) day-element imagery
`day-earth.jpg`, `day-water.jpg`, `day-fire.webp`, `day-spirit.jpg` — Still used on the home's four-days section. **Note**: `day-fire.webp` visually shows warm sunset/fire glow. Alt text was changed to "Sunset and warm light at the retreat" so the wording doesn't promise fire, but the image itself may want swapping if user wants to remove fire visuals entirely.

### Misc
`logo.jpg`, `retreat-icons.png` (CSS sprite), `divider-leaf.png`, `heart-photo-left.webp`, `heart-photo-right.webp`, `costa-del-soul.jpg`, `four-days-bg.png`, `what-to-expect-bg.png`, `special-guest-bg.png`, `sebastian.png`

### Retreat-clip video
`retreat-clip.mov` — mobile-only play-on-scroll in heart-quote section (vanilla IntersectionObserver, the only JS on the site)

## Reusable patterns

### Section gap
```css
main > section + section { margin-top: 4px; }      /* desktop — was 8px before compaction */
@media (max-width: 800px) { main > section + section { margin-top: 0; } }
```

### Decorative bg image + live HTML overlay (home page sections)
```css
.section {
  position: relative;
  background-image: url("bg.png");
  background-size: 100% 100%;
  aspect-ratio: W / H;
  container-type: inline-size;
}
.section .child {
  position: absolute;
  top: NN%;
  font-size: clamp(min, Xcqw, max);
}
```
Used in `.what-to-expect-section`, `.four-days`, `.special-guest`. Mobile: drop `aspect-ratio` and `background-image`, position children statically.

### Element-coloured practice cards (retreats page)
```css
.practice-card.elem-earth  { --elem: #484830; }
.practice-card.elem-water  { --elem: #486078; }
.practice-card.elem-fire   { --elem: #A86030; }
.practice-card.elem-air    { --elem: #8A6A38; }
```
The `--elem` custom property drives the 3 px stripe, label text, bullet dashes, hover border, and any inline italic emphasis.

### Per-card image focus
```css
.elem-water .practice-img img { object-position: center 30%; }  /* meditation — keeps head in frame at 4:3 */
.elem-earth .practice-img img { object-position: center 30%; }  /* yoga */
```

## Cache-busting

Every HTML page references the stylesheet with `?v=N` (currently **`style.css?v=144`**).

**Every time you edit `style.css`:**
```
cd ~/Downloads/wordpress-pouyan && sed -i '' 's/style.css?v=OLD/style.css?v=NEW/g' index.html about.html retreats.html contact.html
```

Bump the number by 1. Without this the user sees stale CSS and reports "didn't apply".

Replaced images need their own `?v=` bumped (e.g. `logo.jpg?v=3`, `location-banner.png?v=2`).

If the user reports a change didn't take effect, check cache version first.

## Mobile responsive breakpoints

- `<1024px` — meet-the-team goes 2-col (home/about)
- `<1000px` — practices 4-col → 2×2
- `<900px` — heart-quote stacks, retreat-feature stacks, four-days goes 2-col
- `<820px` — who-its-for stacks
- `<800px` — universal section gap removed
- `<720px` — most retreats-page sections collapse to single column, sticky mobile CTA bar appears
- `<700px` — header nav wraps, what-to-expect drops bg
- `<600px` — meet-the-team 1-col, four-days 1-col
- `<560px` — practices stacks to 1-col
- `<380px` — extra-narrow tweaks (logo 36px, nav font 0.6rem)

## Local preview
```
cd ~/Downloads/wordpress-pouyan
python3 -m http.server 8082
# open http://localhost:8082
```

## Deployment workflow

Site auto-rebuilds on push to `main`:
```
cd ~/Downloads/wordpress-pouyan
git add <files>
git commit -m "..."
git push
```
Live in ~30–60 seconds on the GitHub Pages URL and custom domain.

## DNS & domain (Gandi)

- Registrar: Gandi
- Apex `fourelements-retreats.com` → 4 A records to `185.199.108.153 / .109.153 / .110.153 / .111.153`
- `www` CNAME → `pouyankhosravi-jpg.github.io.` (trailing dot required)
- TTL: 1800
- HTTPS enforced via `gh api -X PUT '/repos/pouyankhosravi-jpg/four-elements-retreats/pages' -F 'https_enforced=true'`

## Editing rules

- Edit HTML/CSS directly in this folder
- Keep header/footer/nav identical across all 4 pages (no templating — copy-paste)
- Update **all 4 pages** when changing nav or cache-bust version
- No JS unless explicitly requested (existing JS: heart-quote mobile video, retreat-intro CSS scroll animations)
- No external dependencies (no CDN fonts/JS) except the Google Fonts on retreats.html (Cinzel, Cormorant Garamond, Inter)
- When user says "didn't apply" → check cache-bust version first, not the file contents
- Apply the brand voice rules above when writing or editing copy
- For complex layouts on the home page (`heart-quote`, `what-to-expect`, `four-days`, `special-guest`), keep the decorative-bg + HTML overlay pattern

## Recent design passes (most recent first)

- **Practice card images** moved from 16:9 → 4:3 aspect so portrait photos fit head + pose + feet
- **Pricing model** introduced: €899 standard / €799 early bird / 15% deposit / free cancellation until 31 July
- **Trust bar** switched from saturated terracotta to deep espresso `#2F241D`, price removed
- **Brand voice rewrite** across all pages: souls → guests, no fire wording, no spiritual jargon, vegetarian softened to "plant-rich Mediterranean", inclusivity line added, no "Guaro"
- **Page-wide compaction**: every section's padding tightened, duplicate gallery images deduped
- **Facilitators**: photos swapped for new Rosa + Pouyan portraits, layout collapsed to 2-card grid
- **Practices**: element labels removed, single-title cards
- **Banner**: cream backdrop + 21:9 content-driven height
- **An invitation, Is this for you?, Outcomes** sections all redesigned to a quiet-luxury editorial system (Cinzel + Cormorant Garamond + Inter)
- **Header**: 76 px gallery-label style with bg matched to logo JPG (`#F6EFE4`)

## Out of scope

- WordPress (folder name is historical)
- Forms with actual submission
- Database, auth, server-side logic
- Bug bounty / security work (personal project)
