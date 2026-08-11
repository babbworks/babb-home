# babb.tel single landing page — design

Date: 2026-08-11
Status: approved (Direction C)

## Goal

Replace the current multi-section homepage with a single informational landing page
that has no depth. Outbound links to product pages will be wired manually later; for
now the page must carry Babb's focus, vision, ambition and product development in a
narrative that scans quickly.

The rest of the site stays as it is. Only the index page changes.

## Narrative

Ordered vision-first. Reporting is present and strongly stated but not a major section.

1. Masthead — wordmark, one-line positioning
2. Thesis — "The bottleneck was never the factory", paired with a four-layer schematic
3. The argument — three blocks: computerization as electrification, open systems,
   century-capable by design
4. Reporting — one pull quote, one short paragraph
5. Community Assistance — Paton Hall
6. The stack — all twelve products grouped into four layers
7. Contact — hello@babb.tel, GitHub, X, RSS

## Flatness

The page is flat by instruction. Paton Hall is the only link in the body; product
rows, the Dispatch mention and everything else are plain text. The only other
anchors are the contact details in the footer.

This is enforced by data, not markup: `stack.yml` items carry no `url`, and the
template renders an unlinked row when `url` is absent. Adding a `url` to an item
turns that row into a link with no template change.

## The stack

Ordered top-down so the concrete comes first. A visitor grasps Workpads immediately;
Outstack only makes sense once they know what it sits under.

| Layer | Gloss | Products |
|---|---|---|
| Tools | what people touch | Workpads, Workwarrior, Clarkware, heybabb |
| Protocols | how it moves | BitPads, BitLedger, .tel |
| Standards | what must hold | BASICS, SIMBA, Works |
| Systems | what it runs on | Outstack, Telux |

The layering is the argument, not decoration: standards constrain protocols, protocols
carry tools, tools run on systems. The hero states it as a diagram; the products
section is that same diagram expanded. If a thirteenth product doesn't fit one of the
four layers, the hero needs rethinking — this is a deliberate constraint.

## Visual direction — "Stack"

Cool and schematic, distinct from the warm paper aesthetic used elsewhere on the site.

Color:
- ground `#e6e9ec`, panel `#f4f6f7`, surface `#ffffff`
- ink `#0f1519`, secondary `#3e4a52`, muted `#7e8b94`, rule `#c3ccd1`
- signal blue `#1b6fa8`, stepped through the layers (`#c2582e` `#2f86bd` `#1b6fa8` `#16506f`)
- the warm `#c2582e` marks the Tools layer — the only layer people physically touch

Type:
- display: Iowan Old Style / Palatino / Georgia serif, set tight and large
- body: system sans
- utility: the existing `--mono` token, for labels, versions and glosses

Layout: single column, max 1000px. Split hero — thesis left, schematic right. Products
as bordered layer blocks with ruled rows inside.

## Implementation

New files:
- `_data/stack.yml` — four layers, each with name, gloss and items (no urls, see Flatness)
- `_data/community.yml` — community assistance entries
- `_layouts/landing.html` — standalone shell; deliberately excludes `sysbar`,
  `masthead` and `colophon` so the page has no navigation depth
- `_sass/_landing.scss` — all rules namespaced `lp-`, imported by `assets/css/style.scss`

Modified:
- `index.html` — switches to `layout: landing`, holds the page markup

Explicitly not modified:
- `_data/products.yml` stays at its current four entries. It is consumed by
  `dispatch/index.html`, which renders one block per entry; extending it to twelve
  would silently change that page. Consequence: product copy now lives in three
  places (`products.yml`, the hardcoded `_includes/products-grid.html`, and
  `stack.yml`). Consolidating them is follow-up work, out of scope here.

## Dropped from the current homepage

- Telemetry ticker and its `feed/telemetry.json` fetch — competes with the thesis
- Auto-scrolling updates rail, and the slideshow — depth devices on a page with no depth
- Headline auto-fit script — replaced by ordinary responsive type
- Email signup — held back for now; the one candidate for adding back, since a page
  with no depth has nowhere else to send an interested reader

None of these files are deleted; they are simply no longer referenced by the index page.

## Open items

- Version strings are taken from `_includes/products-grid.html` and should be confirmed
  current before this ships
- `Works` is filed under Standards although the existing grid describes it as
  "standard + software"
