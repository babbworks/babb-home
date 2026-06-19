# Design Note 03 — "Places" as a standalone page framework

_Captured: May 18, 2026_

## Relationship to Worlds
**Places** is a high-level organizing concept that sits alongside (or one level beneath) **Worlds**. Where a World is a beat (Farming, Manufacturing, etc.), a **Place** is a specific real location where work happens — and a Place page is a **standing story** about that location.

Examples of what a Place can be:
- A neighborhood
- A factory
- A village
- A moon base
- A job site
- …essentially any setting where work and life intersect

## Page concept
- **A reusable framework / template** — every time we begin a standing story about a Place, we instantiate this template.
- **Single scrolling page**, presented in a **cinematic** register — but **not confusing or inundating**. Restraint is mandatory.
- Goal: convey the **character, personality, and uniqueness** of the Place from a few **standard angles**.
- Creative use of **inline drawers, popups, and overlays** to surface content without forcing the user off the scroll.
- **Its own sticky header**, including a link back to the Babb homepage. (Implies a Places-specific top chrome distinct from the main site nav.)

## Core sub-concept — "Angles"
Drawn directly from the **camera recording / Director's notion of angles** for shots. Each Angle is a standard lens through which we present the Place. Likely a few canonical Angles per page, presented in sequence, with consistent vocabulary across all Place pages so users learn the framework.

---

## Other Director's-vocabulary concepts to consider _(suggestions)_

Mining film-production language for sister concepts to **Angles**. These would all read naturally on a Place page and reinforce the cinematic posture without being gimmicky.

| Concept | What it could organize on a Place page |
|---|---|
| **Establishing Shot** | The opening hero — wide view that locates the Place. Always first. |
| **Coverage** | The full set of Angles needed to "cover" the Place — implies completeness. |
| **B-roll** | Ambient texture: detail photos, sounds, small moments. Could live inside drawers/overlays so it's available but not loud. |
| **Cast** | The people of the Place — workers, residents, owners, regulars. Profile cards / portraits. |
| **Dailies** (or **Rushes**) | Unedited, time-stamped dispatches from the field. Maps cleanly to the "VICE on the ground" posture from Note 02. |
| **Scenes** | Grouped beats — e.g. "Morning shift," "Closing time." Useful if a Place has a strong daily rhythm. |
| **Takes** | Alternate versions / revisits of the same subject over time. Good for showing a Place change. |
| **Field Notes** | The Director's voice — short prose, observations, captions. Could be a recurring drawer style. |
| **Call Sheet** | What's happening / scheduled at this Place. Practical, planning-oriented. |
| **Soundtrack** | Embedded audio: ambient recordings, interviews, music local to the Place. |
| **Cuts** | Curated short-form video reels assembled from the raw material. |
| **Treatment** | The "about this Place" / editorial intent — a short directorial statement. |

**Locked initial standard set** (see Answered follow-ups below):

1. **Shot** — opening / locate the Place
2. **Angles** — the canonical multi-angle body of the page
3. **People** — the cast of the Place
4. **B-Roll** — ambient texture, accessed via drawers/overlays rather than dumped inline
5. **Field Notes** — director/editor voice, as inline pull-outs or margin notes
6. **Dailies** — recent on-the-ground updates (ties to Updates rail / Jekyll posts)

Six is a comfortable cap. We can add **Soundtrack** / **Cuts** / **Takes** when a specific Place warrants them, but they shouldn't be required.

---

## Interaction patterns to lean on
- **Sticky header** specific to Places, with `← babb` home link, the Place name, and probably the parent World.
- **Inline drawers** — slide-in or accordion-style — to keep secondary content (B-roll, transcripts, supplementary photos) one tap away without leaving the scroll.
- **Overlays / lightboxes** — for full-bleed image viewing, video playback, audio players.
- **Popups** — small, anchored to a phrase or photo, for footnotes / Field Notes / quick context.
- **Anchored scroll-jumping** within the page — so the sticky header can offer a tiny menu of the Angles/sections.

## Tone guardrails
- Cinematic, not theatrical.
- One strong image at a time. Don't stack heroes.
- Whitespace and pacing matter as much as content.
- Drawers and overlays should feel earned — used to **reveal**, not to **hide complexity**.

---

## Answered follow-ups _(May 18, 2026)_

### Locked section set for v1 (six)
Final vocabulary — note **Cast → People** and **Establishing Shot → Shot**:

1. **Shot** — the opening / locate the Place
2. **Angles** — the canonical multi-angle body
3. **People** — the cast of the Place
4. **B-Roll** — ambient texture (drawers / overlays)
5. **Field Notes** — director/editor voice
6. **Dailies** — on-the-ground updates

### IA
- **Places is top level.** URL: `/places/<place>` (not nested under a World).
- Places are **often cross-linked** to one or more Worlds — the relationship is many-to-many, surfaced on the page rather than encoded in the URL.

### Sticky header
- **Rich**, not minimal.
- Includes a **Places nav** (probably a dropdown / drawer listing other Places, possibly grouped by World).
- Back-to-Babb home link.
- In-page section anchors for the six standard sections.

### Media at launch
- **Yes** to ambient audio and interview clips on Place pages from v1.
- Plan for inline audio players (lightweight, scrubbable, with transcript drawer where available).

### Maps
- Maps **will be included** with their own CSS / theming so they fit the cinematic register.
- Treatment method — see proposal below.

### Routes
- A Place is **mostly a single physical location**.
- **Routes are special** — a separate sub-type / variant of Place (e.g. "the dairy route" across multiple sites). Worth designing for, but distinct from the standard single-location Place. Likely needs a multi-stop map and a sequential / itinerary treatment.

---

## Templating & reuse — proposed method

Goal: I can manually edit a Place page freely, but new Places can be created without copy-pasting boilerplate, and shared chrome (sticky header, section scaffolding, map theming, audio player styling) updates everywhere when changed.

**Recommended structure** (works with Jekyll):

```
_layouts/
  place.html               # the Place template — sticky header, six-section scaffold, map/audio includes
_includes/
  place/
    sticky-header.html
    map.html               # themed map embed, takes lat/lng or geojson from front-matter
    audio-player.html
    section-shot.html
    section-angles.html
    section-people.html
    section-broll.html
    section-field-notes.html
    section-dailies.html
places/
  <place-slug>/
    index.md               # front-matter (title, world tags, coords, hero, route?: true/false)
                           # + per-section content blocks (markdown / liquid)
    assets/                # photos, audio, video, captions specific to this Place
```

**Why this shape**
- Each Place is its own folder with its own `assets/` subfolder — clean, portable, easy to hand-edit.
- `_layouts/place.html` keeps the sticky header, navigation, map theming, and player styling consistent across every Place. Change once, propagates.
- Section partials in `_includes/place/` let me override or omit any of the six sections per Place without breaking the template.
- Front-matter flags (e.g. `route: true`) flip on the Route variant of the template — same scaffolding, different map + sequential People/Shot treatment.

**Creating a new Place** — two viable paths:
1. **`bin/new-place <slug>` script** — copies a `places/_template/` skeleton (index.md + empty assets/) into `places/<slug>/`. Lightweight, no Jekyll plumbing needed.
2. **Jekyll generator / collection** — register `places` as a Jekyll collection so the layout auto-applies to anything in `places/**/index.md`. Combine with the script for the file scaffold.

I'd recommend **both** — collection for layout consistency, script for fast scaffolding.

**Map inclusion method**
- A single `_includes/place/map.html` partial that accepts `lat`, `lng`, `zoom`, and optional `route` (geojson path) from the page's front-matter.
- All map styling (basemap palette, marker style, route stroke) lives in one CSS file imported by the partial — so theming is centralized and the page only declares geography, not appearance.
- For Routes, the same partial renders a multi-stop polyline; the variant is driven by data, not a different include.

## Remaining small questions
- Map provider preference (Mapbox / MapLibre + OSM tiles / Leaflet)? This affects how deep the CSS theming can go.
- For Routes, do stops have their own mini-pages (`/places/<route>/<stop>`) or are they purely sections on the Route page?
- Audio: do interview clips need built-in transcripts at launch, or is that v2?
