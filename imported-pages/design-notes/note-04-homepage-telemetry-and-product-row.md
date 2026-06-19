# Design Note 04 — Homepage: telemetry feed + product intro row

_Captured: May 18, 2026_

## What's working today
- The **footer Updates section** on the current live homepage — concept is good.
- Caveat: entries there are **mocked** and don't link to real Updates. The **RSS feed itself is working** and should be the real source.

We want to:
1. **Fix the existing footer Updates** so entries actually surface from `/updates` (via the working RSS feed) and link through correctly.
2. **Add a second, parallel Updates surface on the homepage** with a different feel — see below.

---

## New section — "Telemetry" feed

A second updates surface that lives **on the homepage** (not the footer) and feels more like a **live printout / telemetry stream** than a list of cards.

### Content source
- **Manually written updates** (separate stream from the Jekyll/RSS Updates).
- Same editorial pattern as the Updates rail (Note 01): **one main subject in an alternate color** per line.

### Behavior — live printing
- Prints out **a line at a time** as a continuous, ongoing process.
- When a new line begins, **the previously printed line is pushed down** rather than the section staying fixed-height.
- Result: the section **grows / lengthens** instead of cycling within a fixed block.
- Implication: this section's height is **not fixed** — page layout below it has to accept that this region expands over time during a session.

### Aesthetic kinship
- Reads as a **terminal printout** — same family as the slideshow's terminal overlay (Note 01).
- "Telemetry feel" — instrumented, low-key, ambient. Not shouty.
- Probably monospaced, modest type size, subject highlighted in the alt color.

### Placement
- **At the bottom of the page**, as an ambient running tail before the footer.
- Distinct from the footer Updates (which is the canonical RSS-driven list). The two can coexist: one is **the record**, the other is **the live wire**.

---

## New section — Product intro row (two-column)

Sits **below the existing product cards section** (the block-of-products grid we're keeping per Note 01).

### Layout
- **Two columns.**
- **Left column:** explanations / introductions — copy that situates the product, who it's for, why it exists.
- **Right column:** product **screenshots**.
- Likely repeats per product (one row per product), giving each a chance to introduce itself with prose + visual after the user has seen the dense card grid above.

### Function in the page narrative
- The card grid is the **index** (at-a-glance overview).
- This row is the **read** (slow-down moments, one product at a time).
- Together: scan → linger → continue.

---

## Updated homepage section order (working assembly so far)

Combining Notes 01, 02, and this one:

1. **Header** (existing, minus the `--- Babb Works · 2026` line)
2. **Two-column section** — left content + right Updates rail (auto-scroll, hover-pause, manual + Jekyll posts with nested categories)
3. **Edge-to-edge slideshow** with terminal-style top-right overlays (`babb@tel SUBJECT % …`)
4. **Product cards grid** (existing — keep)
5. **Product intro row** — two-column, screenshots right + introductions left, one per product *(new in this note)*
6. **Telemetry printout** — live-growing manual feed at the bottom *(new in this note)*
7. **Footer** — with the existing Updates section, but pointed at the real `/updates` RSS feed

---

## Open follow-ups for me to confirm with you
- Telemetry feed:
  - Does the printout continue running while the user sits on the page (real-time/polled), or does it print a fresh batch on each load and then sit still?
  - Maximum height before the oldest lines fade out / clip, or is it truly unbounded for the session?
  - Same alt color as the Updates rail tags, or its own?
  - Should each telemetry line be linkable (clickable subject), or is this surface intentionally read-only?
- Product intro row:
  - How many products at launch — and do all of them get a row, or only a curated subset?
  - Screenshots: device-framed (in a phone / browser chrome) or bare?
  - Order — manual, or driven by some signal (recency, priority)?
- Footer Updates fix:
  - Should the footer pull the same RSS the new Updates rail does, or a different filtered slice (e.g. only "Company" / "Announcements" categories)?
