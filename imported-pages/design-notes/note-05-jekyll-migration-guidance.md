# Design Note 05 — Implementing the new site into Jekyll

_Captured: May 18, 2026_

## Recommendation, plainly

**Migrate in place. Do not start a new project.**

The existing `babbworks/babb-home` repo already has every piece of Jekyll plumbing the new design needs — `_layouts/`, `_includes/`, `_sass/`, `_posts/`, `_data/`, working RSS via `jekyll-feed`, working pagination. The build deploys. The custom domain (`babb.tel` via CNAME) is configured. Starting over throws all of that away.

What we're replacing is the **visual chrome and IA**, not the Jekyll setup.

The one thing in the existing repo that **does** need to die is `newindex.html` — the 1.1MB single-file homepage that `index.html` currently iframes. The new design is ~25KB; iframing is no longer needed.

The standalone sub-apps you flagged (BASICS, workwarrior, compound, basics-app, bitpads, bitpadsdotorg, works-standard) **stay where they are**. They have their own visual languages and that's fine — the new Babb chrome doesn't need to invade them. The new homepage just stops trying to be them and instead points to them as products / experiments.

---

## High-level plan (4 PRs, ~1–2 days of work)

### PR 1 — Tokens + chrome (1–2 hours)
Land the design system as Jekyll plumbing without changing any visible page.

```
_sass/
  _tokens.scss        # the :root CSS variables from the new files
  _base.scss          # body, links, headings — global resets
  _chrome.scss        # .sysbar, .masthead, footer.colophon
  _components.scss    # .term, .smark, .crumbs, .feat cells, etc.
assets/css/
  main.scss           # @imports above, becomes /assets/css/main.css
```

Pull the entire `:root { … }` block from `Babb Homepage v1.html` into `_sass/_tokens.scss` unchanged. Pull the shared chrome CSS (sysbar, masthead, footer, section markers, terminal overlay) into `_sass/_chrome.scss` and `_sass/_components.scss`. The page-specific CSS in each prototype stays with each prototype until that page lands.

No layouts changed yet. No pages changed yet. Just CSS available.

### PR 2 — Layouts + includes (3–4 hours)
Wire up the layout shells so new pages can use them.

```
_layouts/
  default.html        # <html><head> + sysbar + masthead + {{ content }} + footer
  home.html           # extends default; renders homepage sections
  world.html          # extends default; renders Worlds page
  dispatch.html       # extends default; long-form article layout (sticky TOC, progress bar)
  product.html        # extends default; product page layout
  place.html          # extends default; (future)

_includes/
  sysbar.html
  masthead.html
  footer.html
  worlds-rail.html        # auto-scrolling Updates rail
  slideshow.html          # full-bleed slideshow + terminal overlay
  telemetry.html          # live wire
  product-card.html       # one of the homepage grid tiles
  intro-row.html          # product intro row (two-col)
  section-mark.html       # § 02 ───── HEADING marker
  terminal-overlay.html   # the printed-in overlay (data attrs drive content)
```

Each `<!-- @include: name.html -->` comment in the prototype files maps to one of these.

### PR 3 — Data + collections (2–3 hours)
Move the in-page JS dictionaries to `_data/*.yml` so content lives outside of layout code.

```
_data/
  worlds.yml          # the 7 Worlds: title, blurb, subs, density, hero, latest, counts
  products.yml        # workpads, bitpads, .tel, babb-products
  telemetry.yml       # the manually-keyed live-wire lines
  nav.yml             # primary nav items

_places/              # NEW collection (configured in _config.yml)
  hamilton-steel-mill/
    index.md          # front-matter: world, sub_world, coords, hero, etc.
    assets/           # photos for this Place

_posts/               # already exists — dispatches/articles land here
  2026-05-12-two-days-on-a-feed-lot.md
```

`_config.yml` additions:
```yaml
collections:
  places:
    output: true
    permalink: /places/:path/
  dispatches:
    output: true
    permalink: /dispatches/:path/

defaults:
  - scope: { path: "", type: "posts" }
    values: { layout: "dispatch" }
  - scope: { path: "", type: "places" }
    values: { layout: "place" }
```

The Workpads page's "active in 5 of 7 Worlds" widget reads `site.data.worlds` and counts. The article page's "In this piece" sidebar reads the post's front-matter. The telemetry feed iterates `site.data.telemetry`.

### PR 4 — Cutover (1–2 hours)
Replace the iframe, redirect old URLs.

- `index.html` becomes a real page using `layout: home` (no more iframe to `newindex.html`)
- `newindex.html` → either delete or move to `/archive/2025-newindex.html` for posterity
- Add redirects from any old top-level URLs that need to keep resolving (`jekyll-redirect-from` plugin is already in your toolbox if you want it)
- Ship the four new pages: homepage, worlds, dispatches, products/workpads
- Update `_config.yml` `header_pages` to match the new IA — or remove it entirely if `nav.yml` drives nav now

The standalone sub-apps (basics-app, workwarrior, compound, bitpadsdotorg, etc.) keep their existing URLs and their existing aesthetics. They are linked from `/products/` as separate experiments.

---

## What about the standalone sub-apps?

You called these out specifically as "standalone pages with their own aesthetics, disregard those."

Concretely: BASICS, workwarrior, compound, basics-app, works-standard, bitpads, bitpadsdotorg.

**Leave them alone.** The new Babb chrome (sysbar, masthead, footer) is not a wrapper they should inherit. The new system makes the *parent* site (`babb.tel`, `/worlds/`, `/places/`, `/products/`, individual product detail pages, dispatches) feel like one publication. The sub-apps are deliberately not part of that publication — they're separate works the publication points at.

If any of those sub-apps later wants to come into the system, that's a separate decision and a separate PR.

**One small recommendation:** add a tiny "← back to babb" link in the top-left of each standalone sub-app, styled to match the sysbar. Optional. It just gives visitors a thread back to the main site.

---

## Specific gotchas in the current repo

- **`newindex.html` is 1.1MB.** It's probably a Webflow / GoDaddy / Wix export with inlined fonts + CSS + JS. Killing the iframe in `index.html` and replacing with the new homepage is the single biggest perf win available.
- **`_config.yml` `header_pages`** lists eight pages that drive the existing nav. The new nav is `Worlds · Places · Products · Updates · About`. Either rewrite `header_pages` or stop using it and let `_data/nav.yml` drive nav from `_includes/masthead.html`. The latter is cleaner.
- **`theme: minima`** is in `_config.yml`. The new design replaces all of minima's CSS and most of its layouts. We can either keep minima as a base (and override almost everything) or remove the theme line and ship layouts directly. Removing it is cleaner — there's nothing of minima we want.
- **`jekyll-paginate`** is already installed and works. The Updates index page will use it (`/updates/page2/`, etc.) — no new gems needed.
- **`MANAGEMENT/` folder** at the repo root looks like internal docs. Not a content collection — leave alone.

---

## Migration order, mapped to the files we already have

The five HTML prototypes are the source of truth. Each maps to a Jekyll layout + Liquid templating pass.

| Prototype file                  | Jekyll layout       | Lives at URL                     |
|---------------------------------|---------------------|----------------------------------|
| `Babb Homepage v1.html`         | `_layouts/home.html`     | `/`                         |
| `Babb Worlds v1.html`           | `_layouts/world.html`    | `/worlds/`, `/worlds/<world>/` |
| `Babb Article v1.html`          | `_layouts/dispatch.html` | `/dispatches/<slug>/`       |
| `Babb Workpads v1.html`         | `_layouts/product.html`  | `/products/workpads/`       |
| (future) Single Place page      | `_layouts/place.html`    | `/places/<place>/`          |

For the JS-driven pieces specifically:

| In prototype          | In Jekyll                                              |
|-----------------------|--------------------------------------------------------|
| `WORLDS = { ... }` JS dict in Worlds page | `_data/worlds.yml`, iterated via `{% for w in site.data.worlds %}` |
| Telemetry feed JS array | `_data/telemetry.yml` + same client-side append script for live additions |
| Updates rail dummy items | `{% for post in site.posts | slice: 0, 8 %}` |
| Article sidebar "In this piece" | Post front-matter (`place:`, `world:`, `products:`, `people:`) |
| Workpads "active in 5 Worlds" tile counts | `{% assign deployments = site.data.workpads.deployments %}` |

---

## What stays the same after migration

- The HTML files in `Babb * v1.html` continue to be the canonical **design source of truth.** When you want to change the look of something, you edit the prototype first, eyeball it, then mirror the change into the Jekyll partial. The prototypes are the wireframe-aesthetic equivalent of a Figma file — and unlike Figma, they're already real HTML and CSS.
- Tokens stay in `:root`. When a token changes in one prototype, it changes in `_sass/_tokens.scss` too. The two stay in sync by convention, not by tooling, but it's a one-file edit.
- Every block has a `<!-- @include: name.html -->` marker. Those markers are the implicit Jekyll partial boundaries.

---

## What I'd do if I were doing this

1. Land PR 1 (tokens + chrome SCSS). 20 minutes. Nothing changes visibly.
2. Land PR 2 (layouts + includes for the homepage only). Build a new `/preview/` page that uses the new `home.html` layout, see it deploy alongside the old iframe.
3. When `/preview/` looks right, swap `index.html` to use `layout: home` and delete the iframe. PR 3.
4. Now the homepage is live and the system is proven. Roll out Worlds, Dispatches, Workpads as separate PRs, one per session.
5. Place pages last, since they're the most ambitious template.

Total: ~one weekend if it's a focused weekend, or ~2 weeks at a relaxed pace.

---

## When NOT to migrate in place

The only case where I'd start over is if you wanted to switch off Jekyll entirely — to Astro, Eleventy, or a different SSG. The new design is portable; it's plain HTML and CSS with a small amount of JS, none of which depends on Jekyll specifically. But you have working Jekyll, a working RSS feed, working pagination, working build, and a custom domain. There's no Jekyll-specific reason to switch frameworks.

If you ever do switch: the prototypes port directly. The tokens stay. The includes become whatever the new framework calls partials. The data files become whatever the new framework calls collections. The work I'd worry about losing is the IA + content, not the visuals — and Jekyll holds the IA + content perfectly well.

---

## Open questions

- Do the old top-level pages currently in `header_pages` (tools, releases, basics, bitpadsdotorg, workwarrior, works, compound) need to keep resolving at their current URLs, or can they retire?
- For dispatches — do you want them in `_posts/` (uses Jekyll's date-based permalinks) or in a `_dispatches/` collection (cleaner URLs, but loses `jekyll-paginate` defaults)?
- The Updates rail on the homepage is supposed to merge **manual entries + Jekyll posts.** Manual entries probably live in `_data/updates.yml` and get merged with `site.posts` at render time. Confirm before I implement?
