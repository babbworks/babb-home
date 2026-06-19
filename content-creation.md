# Content creation guide

How to grow the Babb site. Covers all three content systems — dispatches/updates, Worlds, and Places — with full front matter specs and the reasoning behind each pattern.

---

## How the site is built

Jekyll static site. Run `bundle exec jekyll build` to compile; the output goes to `_site/`. One stylesheet (`assets/css/style.css`) covers everything — all SCSS partials compile into it. Navigation, the places picker, and the footer world list are data-driven from `_data/`.

The site has three distinct content systems:

| System | What it is | Where it lives |
|---|---|---|
| **Dispatches** | Timestamped pieces: articles, field reports, editor's notes, product updates | `_posts/` |
| **Worlds** | Thematic beats that organize everything else | `worlds/`, `_data/worlds.yml` |
| **Places** | Standing stories — locations we return to over time | `_places/`, `_data/places_index.yml` |

These cross-reference each other. A dispatch belongs to a World and may be anchored to a Place. A Place accumulates dispatches, angles, audio, video, and field notes. Worlds are the organizing frame for both.

---

## Dispatches

### What a dispatch is

The unit of time-stamped output. Ranges from a short editor's note to a long-form reported piece. Uses Jekyll's built-in `_posts/` system, which means each post has a date, is listed in reverse-chron on `/updates/`, and appears in the RSS feed automatically.

### Creating a dispatch

File naming convention: `_posts/YYYY-MM-DD-slug.md`

```
_posts/2026-05-19-shift-handoff-redesigned.md
```

**Minimal front matter:**

```yaml
---
layout: dispatch
title: "Shift handoff, redesigned"
date: 2026-05-19
---
```

**Full front matter (all optional keys):**

```yaml
---
layout: dispatch
title: "Shift handoff, redesigned"
date: 2026-05-19

# Which World this belongs to — appears as the kicker above the headline
world: Manufacturing

# If it covers or mentions a specific Place
place: hamilton-steel-mill

# If it covers a specific product — surfaces in the Workpads proof-grid
# and in the updates tag filter
product: workpads

# Tags — used for the tag filter on /updates/ and for RSS category feeds
tags: [manufacturing, shift-work, workpads]

# Author — if you want a byline
author: Editor A

# Lead image path (relative to site root) and caption
lead_image: /assets/img/hamilton-shift-handoff.jpg
lead_caption: "Tony R. at the pulpit, 06:14 ET — third shift."

# Pull a table of contents into the sidebar (write it as Markdown)
toc: |
  - [The old handoff](#old)
  - [What changed](#changed)
  - [Three plants, one workflow](#three-plants)

# Related links in sidebar — array of {url, title}
related:
  - url: /places/hamilton-steel-mill/
    title: Hamilton steel mill
  - url: /products/workpads/
    title: Workpads
---

Your prose here. Full Markdown.
```

### Layouts for dispatches

There are two available layouts. Use `dispatch` for almost everything — it has a reading-progress bar, breadcrumb trail, prose column with sidebar, related links, and a bottom band linking out. Use `article` for standalone long-form pieces that aren't part of the regular post stream (e.g. a one-off reported feature that lives at a permanent URL rather than in `/updates/`).

`dispatch` is the workhorse. The sidebar activates when you provide `toc:` or `related:` in front matter; otherwise it collapses and the prose runs full-width.

### The dispatch CSS toolkit

Inside a dispatch body, these classes are available in the prose:

```html
<!-- Pull quote -->
<div class="pull">"The console keeps the number. We keep everything else."<span class="attr">— Tony R.</span></div>

<!-- Figure with caption -->
<figure class="fig">
  <div class="img" style="background-image:url('/assets/img/...')"></div>
  <figcaption>Caption here.</figcaption>
</figure>

<!-- Inline audio clip -->
<div class="clip">
  <button class="ply" aria-label="Play">▶</button>
  <div class="info">
    <div class="t">Tony R. · "You learn the floor when you stop expecting it to behave."</div>
    <div class="dur">0:08</div>
  </div>
</div>

<!-- Inline video/loop embed (dark frame) -->
<div class="clip vid">…</div>

<!-- Glossary term row -->
<div class="gloss">
  <span title="Basic oxygen furnace">BOF</span>
  <span title="Electric arc furnace">EAF</span>
</div>

<!-- End bar / horizontal rule with label -->
<div class="end-bar"><span>End of dispatch</span></div>
```

---

## Worlds

### What a World is

A thematic frame that organizes Places and dispatches. There are seven: Selling, Banking, Farming, Building, Manufacturing, Communications, Management. These are defined in `_data/worlds.yml` and are fixed editorial beats, not tags — they represent the kinds of working life Babb covers. Adding a new World is a significant editorial decision.

### The data file

`_data/worlds.yml` drives the Worlds index page and the footer nav. Each entry:

```yaml
- id: manufacturing        # used for URL, CSS, and matching
  num: "05"                # display number — keep in sequence
  name: Manufacturing      # display label
  url: /worlds/manufacturing/
  line: "Mills, plants, foundries, and the shift supervisors on the floor."
```

### Creating a World index page

```
worlds/manufacturing/index.html
```

```yaml
---
layout: world
title: Manufacturing
world_id: manufacturing
nav_active: worlds
---
```

The `world` layout provides the sysbar, masthead, and footer. The body (`{{ content }}`) is whatever you build: an intro section, a places grid pulling from `site.places`, a dispatches rail filtered by `page.world_id`, an RWL panel. There are no hard requirements — the layout is a blank canvas with the right chrome.

### Tagging content to a World

- **Place files**: `worlds: [Manufacturing, Building]` — a place can belong to multiple Worlds
- **Dispatch front matter**: `world: Manufacturing` — shows as the kicker above the headline
- **Data**: `_data/places_index.yml` carries `worlds:` for each place, which drives the picker panel search

---

## Places

A Place is the core editorial unit of the site. It's a standing story — a location we return to over time and accumulate coverage around. Unlike a dispatch (which has a publish date and is done), a Place is always open. Hamilton steel mill has been open since 2026-04-25 and will keep accumulating.

A fully built Place has six standard sections on its main page, plus up to five types of sub-pages that go deeper on specific aspects.

### Step 1: Register in `_data/places_index.yml`

This file drives two things: the places picker panel (the dropdown that appears in the place layout header) and the footer. Every place must be here before it can be found via the picker.

```yaml
- slug: bronx-tower-pour       # must match the filename and URL exactly
  title: Bronx tower pour
  worlds: [Building]            # array — can be multiple
  route: false                  # true if this is a route/journey rather than a fixed location
  dailies: 0                    # running count — update as you add dailies
```

The `dailies` count is shown in the picker panel and on the place page. Update it manually as you add entries.

### Step 2: Create `_places/slug.html`

This is the Place page itself. Use `_places/hamilton-steel-mill.html` as the template — it has all six section stubs already structured.

**Front matter:**

```yaml
---
layout: place
title: Bronx tower pour
slug: bronx-tower-pour             # must match the data file and URL

# Editorial metadata
worlds: [Building]
coords: "40.83°N · 73.92°W"
location: "The Bronx, NY · USA"
scene_id: "THE BRONX · CONCRETE POUR · TOWER C"
type: "Single location · construction"
years: "Groundbreak 2026-03 · est. completion 2028-Q3"
crew: "~80 workers · 2 shifts"
begun: "2026-05-19"               # when we opened the standing story

# Counts shown in the header nav
dailies_count: 0
broll_count: 0

# Status shown in the header
status: "STANDING STORY"          # or "PAUSED", "CLOSED", "DEVELOPING"
updated: "today"                  # plain text — "2d ago", "2026-05-12", etc.

# Used in SEO and link previews
description: "A standing story from a Bronx high-rise concrete pour."
---
```

**The six sections:**

The place body is structured HTML with six section IDs. The sticky nav in the header tracks scroll position and highlights whichever section is in view. All six IDs must exist for the nav to work, even if some sections are empty placeholders initially.

```html
<section id="shot">   <!-- Establishing frame, treatment, ambient audio, map, facts -->
<section id="angles"> <!-- Canonical angles — usually 3–5 named entry points into the story -->
<section id="people"> <!-- Cast of named people at this place -->
<section id="broll">  <!-- Thumbnail grid linking to /broll/ sub-page -->
<section id="notes">  <!-- Recent 4 field notes linking to /field-notes/ sub-page -->
<section id="dailies"><!-- Recent dispatches anchored here -->
```

### Step 3: Build out sub-pages

Sub-pages go deeper on specific media types. Each lives at a conventional URL under the place slug and uses the matching layout. The layouts provide the sysbar, masthead, context bar (the sticky bar linking back to the place), and footer — you only write the content.

**Context bar (`ctx_links`)**

Every sub-page has a sticky context bar at the top showing where you are and providing quick jumps to sibling sub-pages. You configure this via `ctx_links` in front matter. The "here" key marks the current page.

```yaml
ctx_links:
  - url: /places/bronx-tower-pour/angles/the-pour/
    label: "Angle: The Pour"
  - url: /places/bronx-tower-pour/audio/site-foreman/
    label: "Audio · Site foreman"
  - url: /places/bronx-tower-pour/video/day-one/
    label: "Video · Day one"
  - url: /places/bronx-tower-pour/broll/
    label: B-Roll
    current: true                  # marks this page as active in the bar
  - url: /places/bronx-tower-pour/field-notes/
    label: Field Notes
```

---

#### Angle (`layout: angle`)

An Angle is a long-form written entry point into the story — a named perspective with a hero plate, prose, sidebar, and glossary. Hamilton has four: The Floor, The Owners, The Town, The Future.

```
places/bronx-tower-pour/angles/the-pour.html
```

```yaml
---
layout: angle
title: The Pour
place_slug: bronx-tower-pour
place_title: Bronx tower pour
nav_active: places

# Anchor nav — populates the context bar's tab strip
anchors:
  - { id: overview,  label: Overview }
  - { id: process,   label: Process }
  - { id: people,    label: People }
  - { id: numbers,   label: Numbers }
  - { id: glossary,  label: Glossary }

ctx_links:
  - { url: /places/bronx-tower-pour/angles/the-pour/, label: "The Pour", current: true }
  - { url: /places/bronx-tower-pour/broll/, label: B-Roll }
---
```

The body uses the angle toolkit:

```html
<div class="shell">

  <!-- Hero plate — CSS texture until photos land -->
  <div class="plate">
    <div class="vig">
      <div class="ttl-l">The Pour<span class="punct">.</span></div>
      <div>TOWER C · DAY 14 · FLOOR 22</div>
    </div>
  </div>

  <!-- Title block -->
  <section class="atitle">
    <div class="lede">
      <p class="standfirst">A concrete pour at elevation is different from one at grade. Here is how it works.</p>
      <!-- prose continues -->
    </div>
    <div class="facts">
      <div class="r"><span class="k">Place</span><span><a href="/places/bronx-tower-pour/">Bronx tower pour</a></span></div>
      <div class="r"><span class="k">World</span><span><a href="/worlds/building/">Building</a></span></div>
    </div>
  </section>

  <!-- Body: prose left, sticky sidebar right -->
  <section class="body-row">
    <div class="prose">
      <h2 id="overview">Overview</h2>
      <p>…</p>
      <!-- inline audio -->
      <div class="clip">
        <button class="ply" aria-label="Play"></button>
        <div class="info">
          <div class="t">Foreman · "We pour in the window between shifts."</div>
          <div class="dur">0:12</div>
        </div>
      </div>
      <h2 id="glossary">Glossary</h2>
      <div class="gloss-row">
        <span title="Superplasticiser: admixture that increases workability">SP</span>
        <span title="Slump test: measures concrete consistency">slump</span>
      </div>
    </div>
    <aside class="sidebar">
      <div class="sb-box toc">
        <h4>Contents</h4>
        <ul>
          <li><a href="#overview">Overview</a></li>
          <li><a href="#process">Process</a></li>
        </ul>
      </div>
      <div class="pq">"We pour in the window between shifts."<span class="ts">— Site foreman</span></div>
    </aside>
  </section>
</div>
```

---

#### Audio (`layout: audio`)

An audio episode page. Dark header (`eph`), waveform display, chapters, transcript.

```
places/bronx-tower-pour/audio/site-foreman.html
```

```yaml
---
layout: audio
title: Site foreman · interview
place_slug: bronx-tower-pour
place_title: Bronx tower pour
nav_active: places
duration: "38:12"
ctx_links:
  - { url: /places/bronx-tower-pour/angles/the-pour/, label: The Pour }
  - { url: /places/bronx-tower-pour/audio/site-foreman/, label: "Audio (here)", current: true }
---
```

The body contains the `.eph` header, `.wave` waveform, `.controls`, `.chapters`, `.body-row` with `.transcript` and `.sidebar`. Copy the Hamilton audio structure from `imported-pages/pages/Babb Audio v1.html` as a starting template.

---

#### Video (`layout: video`)

A video page. Dark player with chapters and transcript drawer.

```
places/bronx-tower-pour/video/day-one.html
```

```yaml
---
layout: video
title: Day one
place_slug: bronx-tower-pour
place_title: Bronx tower pour
nav_active: places
duration: "8:42"
ctx_links:
  - { url: /places/bronx-tower-pour/video/day-one/, label: "Video (here)", current: true }
  - { url: /places/bronx-tower-pour/broll/, label: B-Roll }
---
```

Body uses `.player-wrap`, `.vtitle`, `.body-row` with `.chapters`, `.director-notes`, `.drawer` for transcript, `.sidebar`. Copy from `imported-pages/pages/Babb Video v1.html`.

---

#### B-Roll archive (`layout: broll`)

A filterable archive of photos, loops, and ambient audio clips. Has a lightbox built into the layout JS.

```
places/bronx-tower-pour/broll/index.html
```

```yaml
---
layout: broll
title: B-Roll archive
place_slug: bronx-tower-pour
place_title: Bronx tower pour
nav_active: places
item_count: 0              # update as tiles are added
ctx_links:
  - { url: /places/bronx-tower-pour/broll/, label: "B-Roll (here)", current: true }
  - { url: /places/bronx-tower-pour/field-notes/, label: Field Notes }
---
```

Each media item is a `.tile` inside `<section class="grid" id="grid">`. Tile data attributes drive the filter JS — all four must be present:

```html
<div class="tile t1"
     data-i="0"
     data-m="photo"         <!-- photo | video | audio -->
     data-a="pour"          <!-- your angle slugs, matches the filter buttons -->
     data-s="first"         <!-- shift: first | second | third | dawn -->
     data-cap="Concrete pump arm — floor 22">
  <span class="meta-tag">PHOTO</span>
  <span class="id">PH 01</span>
  <span class="when">2026-05-19 · 07:14</span>
</div>
```

**Tile texture classes** (CSS-only placeholders until real photos):
`t1` through `t7` — tan/cream gradient variants  
`dawn` — warm orange-to-amber  
`night` — near-black  
`audio` — dark terminal background with ♪  
`video` — adds a ▶ overlay on top of any other class  

Build the filter buttons to match the `data-a` values you use:

```html
<div class="pill-row" id="angleFilter">
  <button data-a="all" aria-pressed="true">All</button>
  <button data-a="pour">The Pour</button>
  <button data-a="crew">Crew</button>
</div>
```

---

#### Field Notes (`layout: field-notes`)

A chronological log of director's and editor's voice. Each note is a short observation, decision, or flag. The main Place page shows the four most recent; this page is the full archive.

```
places/bronx-tower-pour/field-notes/index.html
```

```yaml
---
layout: field-notes
title: Field Notes
place_slug: bronx-tower-pour
place_title: Bronx tower pour
nav_active: places
note_count: 0
ctx_links:
  - { url: /places/bronx-tower-pour/field-notes/, label: "Field Notes (here)", current: true }
---
```

Notes are grouped by day. The filter JS reads `data-au` (author) and `data-an` (anchor) attributes, and searches `data-text` for the text filter. All three must be present for filtering to work.

**Author codes** — define your own, but the CSS provides `.au-a` (orange-left-border), `.au-b` (dark-left-border), `.au-c` (green/live-left-border):

```html
<div class="day">
  <div class="day-head">
    <div class="d">May 19 <b>Day 01</b> <span class="when">2026-05-19 · Monday</span></div>
    <div class="summary">First pour day. Two notes.</div>
  </div>
  <div class="notes">

    <div class="note au-a" id="n01" data-au="a" data-an="pour" data-text="concrete pump arm angle pour">
      <div class="head">
        <span class="ts"><span class="nu">N 01</span>07:14 ET · on site</span>
        <span class="anchor">anchored to <a href="/places/bronx-tower-pour/angles/the-pour/">The Pour</a></span>
      </div>
      <div class="body">Note text here.</div>
      <div class="foot">
        <span class="by">— <span class="nm">Editor A</span></span>
        <span class="util"><a href="#n01">permalink</a></span>
      </div>
    </div>

  </div>
</div>
```

Build the filter buttons to match the `data-an` values you use:

```html
<div class="pill-row" id="anchorFilter">
  <button data-an="all" aria-pressed="true">All</button>
  <button data-an="pour">The Pour</button>
  <button data-an="general">General</button>
</div>
```

---

### Step 4: Add people (`layout: person`)

People live in the `_people/` collection and output to `/people/:slug/`. Two variants controlled by `type:`.

**Subject** — someone we cover, a person at a Place:

```
_people/tony-r.html
```

```yaml
---
layout: person
title: Tony R.
slug: tony-r
type: subject
role: "Foreman · Hamilton steel mill"
worlds: [Manufacturing]
places: [hamilton-steel-mill]
nav_active: places
---
```

Body uses `.p-hero.subject` (warm portrait placeholder left, bio right), `.body-row` with `.bio` and `.sidebar`, `.timeline`, `.sampler` for audio excerpt, `.pq` for quotes.

**Contributor** — someone on our crew, a staff member or field hand:

```yaml
---
layout: person
title: Editor A
slug: editor-a
type: contributor
role: "Editorial lead"
nav_active: places
---
```

Body uses `.p-hero.contributor` (dark ID-card style), `.stat-strip` for stats, `.bylines` for piece history, `.cov-grid` for coverage thumbnails, `.contact-card` at the bottom.

---

## Data files

These four files in `_data/` are the connective tissue of the site. Touch them when adding content, not just when building layouts.

### `_data/nav.yml`

Drives the primary navigation in `_includes/masthead.html`. Each item:

```yaml
- id: worlds
  label: Worlds
  url: /worlds/
```

The `id` matches against `page.nav_active` in front matter to set the active state.

### `_data/worlds.yml`

Drives the Worlds index page and the footer. Format documented above. The `id` field is what gets matched in `worlds:` arrays throughout the rest of the site.

### `_data/places_index.yml`

Drives the places picker panel (the dropdown in the place layout header) and the footer places list. Every place must be registered here. The `dailies` count is displayed live in the picker; update it manually.

### `_data/products.yml`

Drives the products grid on the homepage and the products index. Each entry should have `id`, `title`, `status`, `url`, and a short `line`. Add new products here before building their product pages.

---

## CSS textures — placeholder policy

Until real photographs are approved and cleared, all image areas use CSS gradient textures. This is intentional, not a placeholder state to apologize for. The available texture classes (`t1`–`t7`, `dawn`, `night`) are defined in `_sass/_broll.scss` and referenced in `.tile`, `.cover`, `.plate`, `.shot`, and `.lb-img`.

When real photos land:

- **Inline**: replace the gradient background with `background-image: url('/assets/img/...')`
- **Tile grid**: add the `<img>` inside the `.tile` with `position: absolute; inset: 0; object-fit: cover; width: 100%; height: 100%` and remove the texture class
- **Plate hero**: same — absolute-fill `<img>` inside `.plate`, remove gradient background

Don't mix textures and real photos on the same page unless it's intentional.

---

## Build and deploy

```bash
# Local preview
bundle exec jekyll serve --livereload

# Production build
bundle exec jekyll build

# Check for errors before committing
bundle exec jekyll build 2>&1 | grep -E "(Error|Liquid)" | grep -v "bigdecimal"
```

The `imported-pages/` directory (the original design deliverables) is excluded from the build. It stays in the repo as reference only.
