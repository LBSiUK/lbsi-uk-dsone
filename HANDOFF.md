# Handoff: lbsi.uk — System 1

## Overview
Personal portfolio for Leon Brahams (LBSi UK). Five views: Home, About, Projects, Blogs (index + post), Contact. Angular, monochrome, bordered-grid aesthetic with a solid black top bar and "sweep" fill animations.

## About the design files
`design/Portfolio.dc.html` is a **design reference built in HTML** (it runs via `design/support.js`; open it in a browser). It is not the production code — recreate it as clean static HTML/CSS/JS. All copy, image paths and content data live in that file (template markup + the `Component` class at the bottom: `projects`, `featured`, `posts`, `contacts`, `chips` arrays).

## Fidelity
**High-fidelity.** Reproduce colours, type, spacing, borders and animations exactly.

## Design tokens
- Background: `#000000` (page, header, footer, cards)
- Hatched image placeholder: `repeating-linear-gradient(135deg, #141414 0 8px, #0e0e0e 8px 16px)`
- Borders/dividers: `1px solid #262626`; nav dividers `#333333`; tag borders `#444444`
- Text: primary `#f0f0f0`; body/secondary `#8a8a8a`; tags/chips `#bdbdbd`; blog body `#bdbdbd`
- Fill / active: `#f0f0f0` background with `#000000` text
- Radius: **0 everywhere**. No shadows.
- Fonts: display = `Roman` (`assets/Roman.otf`, weight normal); UI/body = `"Segoe UI", Tahoma, Geneva, Verdana, sans-serif`; labels = `ui-monospace, Menlo, monospace`
- Content column: `max-width: 1368px; margin: 0 auto; padding: 0 2rem`
- Easing: `cubic-bezier(0.76, 0, 0.24, 1)`

## Global layout
### Header (sticky, top: 0, z-index 100)
- Height 64px, black, `border-bottom: 1px solid #262626`, `display:flex; justify-content:space-between; align-items:stretch`.
- Left: logo "lbsi.uk" — Roman 2rem, line-height 1, padding `9px 2rem 0` (the font sits high; this optically centres it), `border-right: 1px solid #262626`.
- Right: nav items, **right-aligned**, each full bar height, `padding: 0 1.9rem`, `border-left: 1px solid #333333`, 0.72rem, weight 600, letter-spacing 0.16em, uppercase. Labels: HOME, ABOUT, PROJECTS, BLOGS, CONTACT.
- Active item: `#f0f0f0` fill, black text.

### Footer
Black, `border-top: 1px solid #262626`, flex space-between. Left (one line): "© Leon Brahams / LBSi UK 2023–2026. Images © Leon Brahams / LBSi UK unless stated otherwise." Right: "NW London" with `border-left: 1px solid #262626`. Both 0.78rem `#8a8a8a`, padding `1.4rem 2rem`, letter-spacing 0.05em.

### Section header pattern (About / Projects / Blogs / Contact)
- H2 in Roman, `clamp(2.2rem, 5vw, 3.8rem)`, line-height 1.08, padding-bottom 2rem, bottom border.
- Section padding `4rem 0 5rem`.

## Screens
### Home
1. Hero: 2-col grid `minmax(0,1fr) minmax(0,360px)`, border on left/right/bottom.
   - Left (padding `4rem 2.5rem`, vertically centred, right border): H1 "Welcome to LBSi UK" (Roman, `clamp(2rem,4.4vw,3.6rem)`, lh 1.05), two paragraphs (1.05rem, `#8a8a8a`, lh 1.75, max-width 600px).
   - Right: `images/hero.png` at **3:4 aspect**, `object-fit: cover`, `grayscale(1)`; below it a full-width "SEE ALL PROJECTS →" button (`#f0f0f0` bg, black text, 0.78rem 600, letter-spacing 0.14em, padding `1.3rem 1.5rem`) → Projects.
2. "Public facing work": H2 Roman 1.5rem with bottom border; grid `repeat(auto-fill, minmax(max(280px, calc((100% - 1px) / 3)), 1fr))`, gap 0, cells share borders (grid has left+top border, each card right+bottom).
   Card: image area 150px (bg image cover, left-center for Onward; hatched placeholder when none) → body padding 1.5rem (Roman 1.2rem title, 0.875rem `#8a8a8a` desc, tags) → sweep link row "VIEW PROJECT →".
   Cards: Onward's website (images/onward.png, → https://onward-site-v3.vercel.app), lbsi.uk, Pixelbook Go — Linux.

### About
Grid `minmax(0,1fr) minmax(0,360px)`. Left: paragraphs (0.97rem, `#8a8a8a`, lh 1.85, key phrases `<strong>` in `#f0f0f0`), skill chips (0.74rem, padding `0.4rem 0.8rem`, border `#333`, bg `#0f0f0f`). Right: `images/leon.jpeg` 3:4, grayscale.

### Projects
Same card grid, `minmax(max(280px, calc((100% - 1px) / 3)), 1fr)`, image area 170px (grayscale). Five projects (see `projects` array).

### Blogs
- Index: list rows, each a sweep link: grid `minmax(0,220px) minmax(0,1fr) auto`, gap 2rem, padding 1.5rem — 4:3 grayscale thumbnail, mono date, Roman 1.6rem title, lede, "READ →".
- Post: top bar with "← ALL POSTS" sweep button (left, right border) and mono date (right). Body column max-width 720px, padding `3.5rem 2rem 4rem`, gap 1.4rem. H1 Roman `clamp(2rem,4vw,3rem)`. Lead line Roman 1.5rem `#f0f0f0`. Paragraphs 1rem `#bdbdbd` lh 1.85. List: no bullets, "—" in `#555`, rows separated by `#262626` borders. Images 4:3, full colour, 1px `#262626` border. Inline link: `#f0f0f0`, underline, offset 3px.
- First post: "We've got a new site! (again)", 24 September 2026, 00:45. Full text verbatim in `posts` array. Images: `blog-2.png` (after list; also the thumbnail), `blog-1.png` (after the first-year paragraph).

### Contact
Grid `minmax(0,1fr) minmax(0,1.4fr)`. Left: intro + "Discord: @lbsiuk". Right: stacked sweep links (EMAIL, LINKEDIN, YOUTUBE, INSTAGRAM, TELEGRAM → URLs in `contacts`), grid `minmax(0,1fr) auto`, padding `1.25rem 1.5rem`, 0.8rem 600, letter-spacing 0.14em, "→" right.

## Interactions & behaviour
### Button sweep (nav items, VIEW PROJECT rows, contact links, blog rows, ← All posts)
- Implemented as a background-image layer: `background-image: linear-gradient(#f0f0f0,#f0f0f0); background-repeat:no-repeat; background-size: 0% 100%` → `100% 100%`, with `transition: background-size .38s cubic-bezier(.76,0,.24,1), color .25s ease`. Text goes `#f0f0f0` → `#000000`.
- **Always left → right**: filling uses `background-position: left center` (grows from left); emptying uses `right center` (shrinks toward the right edge).
- **Always completes**: if the pointer leaves mid-fill, the fill finishes, then empties. If it re-enters mid-empty, the empty finishes, then fills again. Track per-element state (`empty | filling | full | emptying`, plus `hovered`), advance with 380ms timers. See `componentDidMount` in the reference.
- The current page's nav item is excluded (stays filled).

### Page change wipe
- A fixed full-viewport `#f0f0f0` panel (z-index 200, above the header) animates `translateX(-100%) → 0 → 100%` over 760ms with the same easing (left → right, always).
- At the midpoint (380ms) swap the view, scroll to top, and move the nav active state **instantly** (no transition) while covered — so the old item appears cleared when the panel exits. Re-enable transitions after the wipe ends.
- Clicking the current page does nothing; ignore clicks during a wipe.
- Opening a blog post / "All posts" switches without the wipe.

## State
`page` (home | about | projects | blog | contact), `post` (index or null), `busy` (wipe in progress), per-button sweep state.

## Responsive
Grids use `minmax(0, …)` / auto-fill so cards wrap. Two-column sections (hero, About, Contact, blog rows) should stack to one column below ~760px; nav may need to scroll horizontally or collapse on narrow phones (not designed — keep angular/bordered).

## Assets (design/images)
hero.png (hero, 3:4), leon.jpeg (About), onward.png, oldsite.png, code_ss.png, pslide-roger.jpeg (project cards), blog-1.png, blog-2.png (blog, 4:3). Font: Roman.otf. All © Leon Brahams unless stated.

## Files
- `design/Portfolio.dc.html` — full reference (markup + data + behaviour)
- `design/support.js` — runtime needed only to view the reference
