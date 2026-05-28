# Four Elements Retreats — Static HTML Website

(Folder is named `wordpress-pouyan` for historical reasons — this is plain static HTML, not WordPress.)

## Live site & repo

- **Live**: https://fourelements-retreats.com
- **GitHub Pages fallback URL**: https://pouyankhosravi-jpg.github.io/four-elements-retreats/
- **Repo**: https://github.com/pouyankhosravi-jpg/four-elements-retreats (public, required for free GitHub Pages)
- **Branch served**: `main`, root folder
- **Custom domain config**: `CNAME` file in repo + Gandi DNS A records (185.199.108.153 / .109.153 / .110.153 / .111.153) on `@`, optional `www` CNAME → `pouyankhosravi-jpg.github.io.`
- **SSL**: auto-renewing Let's Encrypt cert by GitHub, HTTPS enforced
- **`.nojekyll` at repo root** — required so Pages serves files as-is (legacy builder choked on a plain-text Google verification file). Do not delete.

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
| `index.html` | Home — long-form sales page, editorial section-by-section system |
| `about.html` | About us — hero + 3 story blocks + alternating team rows + CTA |
| `retreats.html` | **The primary conversion landing page** — every recent design pass has gone here |
| `contact.html` | Contact — static info |
| `style.css` | Shared stylesheet for all four pages |

Nav order on every page: **Home / About us / Retreats / Contact**

## Cache-busting

Every HTML page references the stylesheet with `?v=N` (currently **`style.css?v=201`**).

**Every time you edit `style.css`:**
```
cd ~/Downloads/wordpress-pouyan && sed -i '' 's/style.css?v=OLD/style.css?v=NEW/g' index.html about.html retreats.html contact.html
```

Bump the number by 1. Without this the user sees stale CSS and reports "didn't apply".

Replaced images/videos need their own `?v=` bumped (e.g. `logo.jpg?v=3`, `retreat-clip.mp4?v=2`).

If the user reports a change didn't take effect, check cache version first.

## Current pricing model (live on retreats.html)

| | |
|---|---|
| Standard price | **€899** per person |
| Early bird | **€799** per person — save €100 until **30 June 2026** |
| Deposit | **30%** (~€240) to hold a place |
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

## Editorial design system (used across home + about, retreats has its own premium system)

The home page sections (What to Expect, Four Days, Special Guest, Meet the Team, Page CTAs) and the about page share a consistent editorial system:

- **Eyebrow** — Georgia, uppercase, `0.42em` letter-spacing, ~11–13px, terracotta (`var(--terracotta)` = `#B85A30`). Sits above the section title.
- **Section title** — Georgia 400, ~28–46px (`clamp(28px, 3.2vw, 46px)`), `0.04em` letter-spacing, `var(--text)`.
- **Ornament** — line · dot · line (or line · wave · line on Special Guest). 56px terracotta lines @ 55% opacity + 6px terracotta dot. Sits between the title and the content.
- **Section padding** — `clamp(40–60px, 5–7vw, 60–96px)` vertical, `clamp(20px, 4vw, 56px)` horizontal.
- **Backgrounds** — alternate between `var(--cream)` `#F7EEE3`, `var(--cream-2)` `#EFE4D2`, and warm bone `#F5F0E8` for visual rhythm.
- **Card surfaces** — `var(--cream)` with soft shadow `0 14px 32px -22px rgba(46, 36, 24, 0.45)`, subtle hover lift (`translateY(-3px)` + photo `scale(1.04)`).
- **Hairline accents** — 28–36px terracotta line under names/titles for visual cohesion.
- **Italic numerals 01–04** — Georgia italic, 28–32% opacity terracotta, used as quiet watermarks (about page team rows, what-to-expect blocks).
- **Snell Roundhand** — used for the Sebastián signature, about-CTA "We would love to welcome you.", and home heart-quote script lines.

## index.html section order (top → bottom)

Section spacing: `main > section + section { margin-top: 4px }` (drops to 0 below 800px).

1. **Banner** (`.banner`) — `banner-plain.jpg` hero with overlay (title + subtitle + "View retreats" CTA → `retreats.html`)
2. **Elements** (`.elements`) — Ground · Flow · Breathe · Glow strip. SVG element icons.
   - Desktop bg: `elements-bg.jpg`
   - Mobile (≤800px) bg: `elements-bg-mobile.png` (portrait paper texture with leaf corners — added because the wide banner-style image looked squashed on phones)
3. **Retreat-feature** (`.retreat-feature`) — 2-col text + `costa-del-soul.jpg`
4. **Location-banner** (`.location-banner`) — `location-banner.jpg` with "Explore the location" CTA → `retreats.html#location` (anchored to the Location section on the retreats page)
5. **Heart-quote** (`.heart-quote`) — 3-col with mobile-only play-on-scroll video clip (`retreat-clip.mp4?v=2`). Heading + script "inspired by the elements" + body paragraphs + **"Yes, I want this experience!" CTA → `retreats.html`**.
   - Mobile: video sits flush between the section above and the heart-quote text (`.heart-quote` padding-top: 0 + `.heart-clip-wrap` margin: 0 + `.heart-quote-grid` margin-top: 24px). Reads like a banner image stitched between sections.
6. **What to Expect** (`.what-to-expect-section`) — `var(--cream-2)` bg. Eyebrow "The Experience" + title + ornament + **two alternating image/text rows**:
   - Row 1: `wte-woman.jpg` (image left) + Block 01 text right — "Pause, breathe and return to your natural rhythm…"
   - Row 2: text left + `wte-group.jpg` (image right, portrait cropped to landscape 4:3 via `object-position: center 38%`) — "At our retreat, you aren't just a guest…"
   - Frames: 4:3 aspect, soft shadow + inner cream outline ring
7. **Four Days** (`.four-days`) — Warm bone `#F5F0E8` bg. Eyebrow "Four Days · Four Elements" + title "A journey through the elements" + ornament + 4 cream cards.
   - Day labels are **weekday names** in Georgia (titles), with element name as the small terracotta label above:
     - Friday · Earth (`day-earth.jpg`)
     - Saturday · Fire (`day-fire.webp`)
     - Sunday · Water (`day-water.jpg` — **waterfall photo**, cropped at `center 42%` via `.fd-img-waterfall`)
     - Monday · Spirit (`day-spirit.jpg`)
   - Each card: 4:3 photo, 3px element-coloured top stripe (`--elem` per card), hover lift + photo zoom
8. **Mid-page CTA** (`.page-cta`) — Snell Roundhand script "ready to journey through the elements?" + button **"Reserve your place →"** → `retreats.html#book` (jumps directly to the booking section)
9. **Special Guest** (`.special-guest`) — Sebastián Serpell sound journey. Cream bg with two soft radial sound-wave ring decorations (top-left + bottom-right). Compact **single-row** layout (photo left, text right with header inline) at ≤760px stacks photo-above-text.
   - Photo: 4:5 portrait, max 340px wide, with **offset terracotta hairline frame** behind (`::before` inset 14px -14px -14px 14px, 55% opacity)
   - Content: Snell Roundhand signature → role line → italic blockquote with oversized terracotta open-quote watermark → short bio
10. **Meet the Team** (`.meet-the-team`) — Cream bg. Standard eyebrow ("The People") + title + ornament. 4 cards in a row (4-col desktop, 2×2 ≤900px, 1-col ≤520px).
    - Each card: 3:4 portrait with soft shadow + inner cream outline ring, **poetic role label** (terracotta small caps), mixed-case Georgia name with 28px terracotta hairline accent, short bio.
    - Roles: **Pouyan — Sounds & Silence** / **Rosa — Yoga & Scent** / **Chris — Food & Nourishment** / **Kasia — Care & Welcome**
11. **Location-extras** (`.location-extras`) — mobile-only extra location image strip

## about.html section order

1. **Hero** (`.about-hero`, cream bg) — Eyebrow "About us" + h1 "A small team devoted to the elements" + line·dot·line ornament + 3 intro paragraphs. The third paragraph ("This retreat is our way of sharing what has shaped us.") is in italic terracotta as a quiet thesis statement.
2. **Story** (`.about-story`, cream-2 bg) — 3 blocks separated by hairline dividers, each with its own small terracotta eyebrow + Georgia heading:
   - Origins — "Where it began" (origin story, italic "It is not about escaping life. It is about returning to what feels real.")
   - Philosophy — "Inspired by the elements" (with italic terracotta intro "Earth grounds us. Water softens us. Fire awakens us. Air clears us.")
   - Our values — "What guides us" (presence over perfection / italic inclusivity line)
3. **Team** (`.about-team`, cream bg) — Header (eyebrow + h2 "Four friends, one shared vision" + ornament + lead). Then **alternating image/text rows** (one of the trust-building patterns):
   - Each `.about-person`: 4:5 portrait (max 380px) with offset terracotta hairline frame behind, italic 01–04 numeral watermark, terracotta role pairing (same as home: Sounds & Silence / Yoga & Scent / Food & Nourishment / Care & Welcome), mixed-case Georgia name with terracotta hairline accent, full 2-paragraph bio (Chris and Kasia's bios reference their former ownership of Lime & Lemon as credibility cues).
   - Reverse class flips photo to the right column on rows 02 and 04.
4. **CTA** (`.about-cta`, cream-2 bg) — Eyebrow "Come and meet us" + lead + Snell Roundhand "We would love to welcome you." + terracotta button → `contact.html`

## retreats.html section order (top → bottom)

Adjacent sections separated by a 4 px gap (`main > section + section { margin-top: 4px }`). Mobile (≤800px) drops this to 0.

1. **Banner** (`.banner.retreat-banner`)
   - **Desktop**: `retreat-hero.jpg` (cream backdrop + arched meditation-circle photo on right). Content overlay is `align-items: center` with **asymmetric vertical padding** (top `clamp(20px, 3vw, 36px)`, bottom `clamp(56px, 8vw, 104px)`) — pulls the Reserve CTA up so it breathes before the espresso trust bar below.
   - **Mobile (≤820px)**: split into a **2-column grid** — text on cream left (no image behind), arched photo cropped right via `object-position: right center`. Three breakpoints (820 / 560 / 400) tighten column ratio and typography.
2. **Trust bar** — espresso `#2F241D` bg, 4 cells (Dates · Location · Group · Includes)
3. **Retreat-intro** ("An invitation")
4. **Who-its-for** ("Is this for you?")
5. **Included** ("Everything you need to soften and arrive")
6. **Accommodation** ("Bell tents under the Andalusian stars")
7. **Practices** ("The practices that shape your journey")
8. **Facilitators** ("Meet your guides")
9. **Nourishment** ("Nourishment & the kitchen")
10. **Timetable** ("A day-by-day rhythm")
11. **Outcomes** ("Four days that stay with you")
12. **Welcome pack**
13. **Investment** (`id="book"`) — "Reserve your place" booking card
14. **Gallery** ("Moments from the past")
15. **Founders note**
16. **Location** (`id="location"`) — "Hidden in the hills of Málaga" (anchor target for the home "Explore the location" CTA)
17. **FAQ**
18. **Final CTA**
19. **Sticky mobile CTA bar**

## CTA wiring summary

| CTA | Destination |
|---|---|
| Home banner "View retreats" | `retreats.html` |
| Home heart-quote "Yes, I want this experience!" | `retreats.html` |
| Home location-banner "Explore the location" | `retreats.html#location` |
| Home mid-page "Reserve your place" | `retreats.html#book` |
| Home retreats-feature "Read more" | `retreats.html` |
| About page bottom "Get in touch" | `contact.html` |
| Retreats banner "Reserve your place" | `#book` |
| Retreats final CTA | `#book` |

## Mobile-specific behaviour worth remembering

- **Heart-quote video on mobile** — sits flush, no cream borders above/below. As you scroll into view, IntersectionObserver auto-plays it. Reads like a connecting banner image between sections.
- **Elements bg on mobile** — uses `elements-bg-mobile.png` (portrait paper texture with leaf corners) instead of the desktop `elements-bg.jpg`. Cover sizing keeps the leaf corners visible.
- **Retreats banner on mobile** — full split layout (text left on cream, photo cropped right). Title's hardcoded `<br>` is hidden so it wraps naturally.
- **About person rows on mobile (≤820px)** — stack image above text on every row (including reversed rows).
- **Mobile polish block at the end of style.css** — `@media (max-width: 720px)` and `(max-width: 480px)` consolidated overrides that tighten every section's vertical padding, ornament gaps, eyebrow margins and CTA button sizing for thumb-friendly scrolling.

## Image / video assets — recently added or replaced

| File | Use |
|---|---|
| `wte-woman.jpg` | What to Expect row 01 (woman walking through the arched entrance) |
| `wte-group.jpg` | What to Expect row 02 (group at the dome, portrait cropped to 4:3 via `.wte-img-portrait`) |
| `day-water.jpg` | Four Days Sunday/Water — **waterfall** (replaces old pool photo). Cropped at `center 42%` via `.fd-img-waterfall` |
| `elements-bg-mobile.png` | Mobile-only background for the Elements section |
| `retreat-clip.mp4?v=2`, `retreat-clip.mov` | New heart-quote mobile autoplay video (transcoded via `/usr/bin/avconvert` because the project machine has no ffmpeg) |

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
| `#F5F0E8` | Warm bone (practices, nourishment, **home four-days bg**) |
| `#F3E0CB` | Peach cream (retreats banner mobile bg) |
| `#2F241D` / `#2A211B` | Title espresso |
| `#5A4A40` | Italic lead text |
| `#5E554D` / `#6D6259` | Body charcoal |
| `#4C4138` | Stronger body charcoal |
| `#9A4F26` | Deeper terracotta (text, signatures) |
| `#B36238` | Standard terracotta accent (labels, stripes) |
| **Element colours** | |
| `#484830` / `#8C5A32` | Earth — olive / brown |
| `#486078` / `#2F538E` / `#6B7B5D` | Water — dusty blue / olive (varies by section) |
| `#A86030` / `#B36238` | Fire — terracotta |
| `#C0A878` / `#8A6A38` / `#6F775D` | Air / Spirit — warm gold / olive |

## Reusable patterns

### Section gap
```css
main > section + section { margin-top: 4px; }      /* desktop */
@media (max-width: 800px) { main > section + section { margin-top: 0; } }
```

### Editorial section header (eyebrow + title + ornament)
```css
.section-eyebrow { font-family: Georgia, serif; text-transform: uppercase; letter-spacing: 0.42em; font-size: clamp(11px, 0.78vw, 13px); color: var(--terracotta); }
.section-title { font-family: Georgia, serif; font-weight: 400; font-size: clamp(28px, 3.2vw, 46px); letter-spacing: 0.04em; color: var(--text); line-height: 1.1; }
.section-ornament { display: flex; gap: 12px; align-items: center; justify-content: center; margin: 22px auto clamp(36px, 4.5vw, 56px); }
.section-ornament .line { width: 56px; height: 1px; background: var(--terracotta); opacity: 0.55; }
.section-ornament .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--terracotta); }
```

### Offset terracotta hairline frame (used on Special Guest + About team photos)
```css
.photo { position: relative; aspect-ratio: 4 / 5; }
.photo img { position: relative; z-index: 2; ... box-shadow: 0 20px 44px -22px rgba(46, 36, 24, 0.5); }
.photo::before {
  content: ""; position: absolute; z-index: 1;
  inset: 14px -14px -14px 14px;          /* offset down-right */
  border: 1px solid var(--terracotta); opacity: 0.55;
}
.photo-reverse::before { inset: 14px 14px -14px -14px; } /* offset down-left */
```

### Element-coloured cards (home four-days, retreats practices)
```css
.card.elem-earth  { --elem: #8C5A32; }
.card.elem-water  { --elem: #6B7B5D; }
.card.elem-fire   { --elem: #B36238; }
.card.elem-spirit { --elem: #8A6A38; }
.card .card-body { border-top: 3px solid var(--elem); }
.card .label { color: var(--elem); }
```

### Per-image crop overrides
```css
.fd-img-waterfall  { object-position: center 42%; } /* Sunday/Water — keep falls in frame */
.wte-img-portrait  { object-position: center 38%; } /* Group photo — keep faces */
```

## SEO setup (added during 2026-05-26 indexing pass)

All four pages have:
- Unique `<title>` (≤60 chars), `<meta description>` (≤160 chars), `<link rel="canonical">`, Open Graph + Twitter cards.

Structured data (JSON-LD):
- **index.html** — `Organization` + `WebSite` + `<meta name="google-site-verification" content="3fqiCA7Zl3Xa-BYWrBqPE8rDV26ZKTjeqiwrCTG3McM" />`
- **about.html** — `AboutPage` linking to `Organization`
- **retreats.html** — `Event` (startDate, endDate, location, performer Rosa/Pouyan/Sebastián Serpell, offer €799 Early bird until 2026-06-30)
- **contact.html** — `ContactPage` with `ContactPoint` (`+34-640-12-40-26`, languages en/es/fa/pl) and `sameAs` Instagram link. Visible Languages section reads "English, Spanish, Persian, Polish".

Other SEO files:
- `sitemap.xml` — lists all 4 URLs with `lastmod` 2026-05-26
- `robots.txt` — `Allow: /` + `Sitemap:` reference
- `.nojekyll` — empty file at root, disables Jekyll on GitHub Pages

**Manual Search Console steps (done by the user, not Claude):**
1. Verify the property in Google Search Console using the HTML tag method (the meta tag in `index.html`)
2. Submit `sitemap.xml` in the Sitemaps section
3. Use URL Inspection → "Request indexing" for each of the 4 URLs to speed up first indexing

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

**If Pages builds start failing silently** — `gh api repos/pouyankhosravi-jpg/four-elements-retreats/pages/builds --jq '.[0:5]'` shows recent build statuses with their error messages. Past gotchas:
- A plain-text file with a `.html` extension (e.g. an old-style Google verification file) breaks the legacy Jekyll builder even if `.nojekyll` is present — wrap it in proper HTML or use the meta-tag verification method instead.
- The legacy Pages builder occasionally gets stuck in "building". A no-op empty commit (`git commit --allow-empty -m "Nudge"`) or `gh api -X POST .../pages/builds` typically un-sticks it.

## DNS & domain (Gandi)

- Registrar: Gandi
- Apex `fourelements-retreats.com` → 4 A records to `185.199.108.153 / .109.153 / .110.153 / .111.153`
- `www` CNAME → `pouyankhosravi-jpg.github.io.` (trailing dot required)
- TTL: 1800
- HTTPS enforced via `gh api -X PUT '/repos/pouyankhosravi-jpg/four-elements-retreats/pages' -F 'https_enforced=true'`
- Existing TXT records: SPF (Zoho mail), Facebook domain verification, Zoho verification, an older `google-site-verification=hA1wmvcyESzGKwjpVeXticxF...` (from a previous account/property)

## Editing rules

- Edit HTML/CSS directly in this folder
- Keep header/footer/nav identical across all 4 pages (no templating — copy-paste)
- Update **all 4 pages** when changing nav or cache-bust version
- No JS unless explicitly requested (existing JS: heart-quote mobile video, retreat-intro CSS scroll animations on retreats.html)
- No external dependencies (no CDN fonts/JS) except the Google Fonts on retreats.html (Cinzel, Cormorant Garamond, Inter)
- When user says "didn't apply" → check cache-bust version first, not the file contents
- Apply the brand voice rules above when writing or editing copy
- For complex layouts on the home page, use the editorial system pattern (eyebrow + title + ornament + grid/row content)

## Out of scope

- WordPress (folder name is historical)
- Forms with actual submission
- Database, auth, server-side logic
- Bug bounty / security work (personal project)
