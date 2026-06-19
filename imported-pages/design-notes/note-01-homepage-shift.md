# Design Note 01 — Homepage shift toward media & access

_Captured: May 18, 2026_

## Keep
- The current front page is decent.
- **Keep** the section of blocks showing our products.

## Remove
- The topmost line above the header test that reads `--- Babb Works · 2026`.

## Strategic shift
Move the page's identity and layout fully toward **access to media, special pages, blog posts, and company/partner channels** — content that brings people into the world of:
1. The people we're serving
2. The people building our products (software and hardware)

The page should feel like a doorway into that world, not a product brochure.

---

## Section 1 — Two-column: left content + right "Updates" rail

### Right sidebar → vertical continuous-scrolling links module

Replaces the current right sidebar (which shows claims).

**Behavior**
- Vertical, continuous auto-scroll of items.
- **Pauses on hover** so the user can click comfortably.

**Each item shows**
- **Title** (linked)
- **Short description** below the title
- **Below that, in small type:** a product or project tag, plus other topical tags — in an alt color

**Data sources (two inputs, merged)**
1. **Manual entries** I can hand-add/edit
2. **Auto-pulled "Updates"** from blog posts on the Jekyll site
   - URL pattern example: `https://www.babb.tel/projects/workpads/2025/03/13/workpads-project.html`
   - **Jekyll categories** assigned to a post appear in this **nested category mode** (categories drive the tag display / nesting)

---

## Section 2 — Edge-to-edge hero image slideshow (below Section 1)

- **Full-bleed** (edge to edge).
- All images displayed in the **same fixed viewport size**, regardless of the source image's actual dimensions (crop/cover to a uniform frame).
- One image at a time, with a content overlay.

### Overlay treatment per image — terminal-style line

Placement: **soft top-right** of the image, as a **single-line overlay**.

Animation sequence (short):
1. Image appears.
2. A **terminal-esque line** prints in — the opaque bar appears first.
3. Text + linked words then **fade in** over that bar (quickly).

Bar sizing:
- On **desktop**, the bar does **not** extend the full width — it's only as long as needed to fit the text, plus small padding on the right.
- Text is **left-aligned** with small left padding too.

### Text format — command-line style

Pattern: `babb@tel SUBJECT % description text inter-mixed with 1 or 2 links`

Example: `babb@tel workpads % description text inter-mixed with 1 or w links`

So each slide's overlay reads like a shell prompt where `SUBJECT` is the product/project name and the description (which can contain inline links) follows the `%`.

---

## Open follow-ups for me to confirm with you
- Scroll speed of the Updates rail, and approximate item height — do you want them dense or breathing?
- How many manual entries can sit "pinned" above the auto-pulled Jekyll posts, or do they interleave by date?
- For the slideshow: auto-advance interval, and whether the terminal line stays visible the whole time the image is up or fades back out before the next slide.
- Color of the "alt color" tag row — pulled from an existing palette token, or something new?
- Should the terminal bar have a subtle blinking cursor at the end while printing?
