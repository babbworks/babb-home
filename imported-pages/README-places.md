# Babb — Place page, v1

_Date: May 18, 2026_

This small package contains the Place page (Hamilton steel mill specimen) and the design notes that informed it.

```
babb-place-deliverable/
├── README.md
├── Babb Place v1.html              ← the page (open in any browser)
└── notes/
    ├── note-03-places-framework.md     ← the spec this page implements
    └── note-05-jekyll-migration-guidance.md   ← how it lands in Jekyll
```

## The page

`Babb Place v1.html` is a single self-contained HTML file. No external assets, no fonts, no build step. Open it in any browser. Uses URL hash (`#sioux-falls-feedlot`) to deep-link to other Place specimens via the picker — the picker covers 11 specimen places including 2 Route variants.

### Six standard sections (per note 03)
1. **Shot** — establishing image + treatment + ambient audio + themed map + facts panel
2. **Angles** — four canonical lenses, each with an inline `<details>` drawer for secondary content
3. **People** — cast cards with audio samplers
4. **B-Roll** — 12-tile grid with mixed media types + a real lightbox overlay (←/→/Esc keyboard nav)
5. **Field Notes** — editor's-voice pull-outs anchored back to other sections
6. **Dailies** — feed-list of recent updates with calendar/map view links

### Place-specific chrome
The Place page has its own two-row sticky header that **replaces the normal masthead** — when you're inside a Place, you're inside the story.

- Row 1: `← babb.` back · crumbs · Place name · World pills · standing-story status · **Places ▾ picker**
- Row 2: numbered anchor nav (01 Shot · 02 Angles · …) + dailies/b-roll counts + subscribe link
- Header **condenses on scroll** and the anchor nav **highlights the current section** as you scroll
- The Places picker has search with `--alt` term highlighting, Recent list, Route-variant tagging, and full keyboard nav

### Cinematic moves
- The Shot section is the only place on the entire site system that uses **reversed-out white type on a dark image** — used once, used well
- Generous section spacing (62px markers)
- Real lightbox modal with keyboard navigation
- Inline drawers (`<details>`) for secondary content — keeps the scroll uninterrupted
- CSS-only themed map placeholder (paper background, hairline grid, ink marker, scale ruler, coords) — drop-in replacement for a Leaflet/MapLibre embed later

## How it lands in Jekyll

See `notes/note-05-jekyll-migration-guidance.md` for the full plan. Short version:

- Page → `_layouts/place.html`
- Place data → `_places/<slug>/index.md` front-matter (title, worlds, route flag, coords, treatment, audio)
- Sticky header → `_includes/place/sticky-header.html`. The Places picker reads `site.places` server-side; the swap-on-click JS becomes hard nav per slug.
- Field Notes → sub-collection (`_places/<slug>/field-notes/*.md`), filtered by place slug
- Dailies → same pattern
- Map → replace the CSS placeholder with `_includes/place/map.html` (Leaflet/MapLibre + OSM tiles, themed via one shared CSS file per the design note)
- **Route variant** — `route: true` in front-matter flips the map to multi-stop polyline and adds the "Stops" act-structure section

## Specimen content

The page is populated with realistic-feeling content for Hamilton steel mill so the system can be evaluated end-to-end:

- **4 Angles** with distinct lens labels, drawer content (photo strips, CSS timeline chart, annotated aerial map, glossary terms)
- **4 People** with role descriptions and audio samplers (one honestly marked "audio TBD")
- **12 B-roll items** with mixed media types and 12 unique captions in the lightbox
- **4 Field Notes** with anchored references to other sections
- **4 Dailies** with mixed media kinds (photo essays, audio interview, field note)
- **3 Related** cards pointing at another single-location Place, a Route variant, and the parent World

Edit freely — the structure is what matters.

_— end of README_
