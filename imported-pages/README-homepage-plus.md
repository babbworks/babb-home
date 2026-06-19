# Babb — Site Design Deliverable, v1

_Date: May 18, 2026_

This package contains the visual design system, four production-ready HTML pages, the original wireframes that informed them, design notes (including Jekyll migration guidance), and the source reference imagery you provided.

Open any `.html` file in a browser. Everything works offline — no fonts, no external CDNs, no build step. Page weight is ~25–60KB each.

---

## What's in this package

```
babb-site-deliverable/
├── README.md                          ← you are here
│
├── pages/                             ← the four production-ready pages
│   ├── Babb Homepage v1.html              the canonical homepage
│   ├── Babb Worlds v1.html                /worlds/ index + single-World template
│   ├── Babb Article v1.html               long-form Dispatch template
│   └── Babb Workpads v1.html              product detail template
│
├── wireframes/                        ← the original low-fi wireframes
│   ├── homepage-wireframe-v1.html
│   ├── worlds-wireframe-v1.html
│   ├── places-wireframe-v1.html
│   ├── products-wireframe-v1.html
│   └── subpages-wireframe-v1.html         ← contains 11 sub-templates
│
├── design-notes/                      ← editorial + strategic notes
│   ├── batch-01-notes.md                  read of the first batch of references
│   ├── note-01-homepage-shift.md
│   ├── note-02-worlds-storytelling.md
│   ├── note-03-places-framework.md
│   ├── note-04-homepage-telemetry-and-product-row.md
│   └── note-05-jekyll-migration-guidance.md   ← READ THIS BEFORE PORTING
│
└── uploads/                           ← original source references you provided
    └── (logos, mascot, product shots, brand monuments, mood board, etc.)
```

---

## The four production pages

Each page is a single self-contained HTML file. Open and view.

| File | What it is | Maps to |
|---|---|---|
| `Babb Homepage v1.html` | The canonical homepage. System bar, masthead, two-column hero with auto-scrolling Updates rail, full-bleed slideshow with terminal print-in overlay, product grid, three product intro rows, live telemetry feed, footer. | `/` |
| `Babb Worlds v1.html` | One template doing double-duty as `/worlds/` (index, "All" mode) and `/worlds/<world>/` (deep view). Selector at top, density-aware. URL hash drives the active World (`#farming`, `#banking`, etc.). | `/worlds/`, `/worlds/<world>/` |
| `Babb Article v1.html` | Long-form Dispatch template. Sticky reading-progress bar, drop-cap, pull-quote, inline figure strips, inline dark audio clip, glossary popup, sticky sidebar with scroll-spy TOC, subscribe band, prev/next nav, collapsible comments drawer, related grid. Specimen content: "Two days on a feed-lot in Sioux Falls." | `/dispatches/<slug>/` |
| `Babb Workpads v1.html` | Product detail template. Title block + status panel, lead with a fake-device-frame showing an actual Workpads daily-log entry, 6-cell feature grid, three product moments with stats, proof grid (dispatches that feature Workpads), 5-World deployment strip, spec table, changelog snippet, dark "Get it" band. | `/products/workpads/` |

---

## Design system at a glance

All four pages share one design system. Tokens are defined in `:root { … }` at the top of each file and are identical across files.

**Type**
- Single family: a system monospace stack (`ui-monospace, SF Mono, SFMono-Regular, JetBrains Mono, Menlo, Consolas, monospace`)
- No web fonts loaded — instant render, no FOIT/FOUT
- Hierarchy via size and weight only (16–68px range)

**Color**
- Paper: `#faf8f3` (warm cream)
- Ink: `#1a1a1a`
- Hairline: `#d8d3c4`
- Alt (primary tag / accent): `#a14a00` (burnt sienna — kept from your wireframes)
- Live (status dot, channel indicator): `#2f7a3a`
- Terminal: `#141312` background, `#e8e3d4` foreground, `#ffd58a` links

**Layout vocabulary**
- 1240px shell max-width, 24px gutters
- Hairline-bordered cards on `#ffffff`, striped placeholder areas on `#f3efe5`
- Section markers: `§ 02 ─── HEADING` with leader rules
- Numbered manifests (`01 Selling … 07 Management`)
- ASCII separators: `·` `/` `→`
- Terminal overlay device for hero captions: `babb@tel <world>/<sub> %`

**Signals doing the "ambitious startup" work without gradients or photography**
- Live pulse dots on system bar + telemetry + rail head
- Real ticking UTC clock in the system bar
- Print-in animation on the terminal overlay
- Auto-scrolling Updates rail with mask-fade top/bottom (pauses on hover)
- Live-printing telemetry feed (prepends new lines every 6–11s)
- Sticky reading progress bar on the article
- Scroll-spy TOC active state

---

## Performance + accessibility

- Every page is < 60KB and renders instantly. No external assets, no fonts, no analytics, no tracking.
- Tap targets meet the 44px minimum on mobile.
- Body type is ~14–16px monospace at 1.55–1.72 line height; the article uses 15.5px / 1.72 at a 62ch measure for reading.
- Color contrast on `--ink` (`#1a1a1a`) over `--paper` (`#faf8f3`) is ~15.6:1, well above WCAG AAA. The lightest secondary text (`--muted: #807d75`) is ~4.8:1, above WCAG AA for body.
- The auto-scrolling Updates rail respects `:hover` pause and is `aria-label`'d. The telemetry feed is `aria-label`'d. All interactive items are real `<a>` or `<button>` elements with keyboard support.
- Responsive breakpoints at 1100px and 640px; tested for layout integrity on each page.

---

## How this maps to Jekyll

Every block in the production pages is wrapped in a `<!-- @include: <name>.html -->` comment. Those markers are the implicit Jekyll partial boundaries.

`design-notes/note-05-jekyll-migration-guidance.md` is the canonical migration plan — read it before porting. Short version:

1. **Migrate in place**, don't start a new project. Existing repo (`babbworks/babb-home`) has all the Jekyll plumbing needed.
2. The 1.1MB `newindex.html` (currently iframed by `index.html`) is the single biggest thing to retire.
3. Standalone sub-apps (BASICS, workwarrior, compound, bitpads, etc.) are **left alone** — they have their own aesthetics and the new chrome doesn't need to invade them.
4. Tokens → `_sass/_tokens.scss`. Shared chrome → `_includes/{sysbar,masthead,footer}.html`. Page-specific bodies → `_layouts/{home,world,dispatch,product,place}.html`. In-page data dictionaries (`WORLDS = {…}`, telemetry array) → `_data/*.yml`.
5. Four-PR plan with file-by-file mappings is in the migration note.

---

## What's not in this package (yet)

The launch-minimum sequence I proposed was: **Homepage → Worlds index → Single World page → Single Place page → Article/Dispatch → Updates index**.

Built so far: Homepage, Worlds (index + single combined), Article/Dispatch, Workpads (product).

Not yet built:
- Single Place page (6-section template: Shot / Angles / People / B-Roll / Field Notes / Dailies)
- Updates index page
- Places index page
- Bitpads, .tel, and Babb Products (stone goods) product pages
- People / Contributor profile + People index
- The 11 subpage templates in `wireframes/subpages-wireframe-v1.html` (Article variants, Video, Audio episode, Person, etc.)
- 404 and Search results
- About page

The wireframes for all of these exist in `wireframes/` — they show the IA and structure. Productionizing them follows the same pattern as the four pages already done.

---

## Visual references used

The `uploads/` folder contains all source imagery you provided in batch 01. `design-notes/batch-01-notes.md` is the read of those references — what's in them, themes spotted, color cues, and open questions. The page designs draw from but do not directly reproduce those visuals (no photography is embedded yet; placeholder textures and the terminal overlay system carry the visual weight until real photography is ready to drop in).

---

## Questions still open

From design notes and the migration note, these are the questions I'd want answered before the next round of work:

- **For dispatches:** `_posts/` (date-based permalinks) or a `_dispatches/` collection (cleaner URLs)?
- **Updates rail data source:** how do manually-keyed updates merge with Jekyll posts in the rail? Pinned vs. interleaved by date?
- **header_pages cleanup:** can the eight pages currently in `_config.yml`'s `header_pages` retire, or do they need to keep resolving at their current URLs?
- **Telemetry feed:** does it continue running while the user sits on the page (real-time/polled) or print a fresh batch on each load and sit still?
- **Photography:** when does real photography land? The current placeholder textures + terminal overlays carry the page beautifully but real images from feed-lots, mills, branches, etc. would elevate everything.

---

_— end of README_
