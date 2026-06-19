# Design Note 02 — "Worlds" as the storytelling franchise

_Captured: May 18, 2026_

## Core idea
Babb creates powerful products, **but our role as a source for captivating storytelling should even eclipse the tools we create.** The homepage tone should reflect that — Babb is a media outfit first, a product company alongside.

## Framing device
A constant hallmark / differentiator for how we deliver stories and educational media:

- **"Working Worlds"** — or simply **"Worlds"**

Use this as the recurring vocabulary across page sections, tags, navigation, and editorial framing.

## Initial slate of Worlds
1. Selling
2. Banking
3. Farming
4. Building
5. Manufacturing
6. Communications
7. Management

(Each is a "world" we report from / build for — both an editorial beat and an audience.)

## Editorial posture
**Babb is becoming a different kind of "VICE Media"** —
- Often **travels on the ground**
- Goes **into the places of work and living** of its customers and creators
- Relays to viewers and readers an **unfiltered view of how things really operate**

The implied register: documentary, first-person, location-aware, gritty when warranted, respectful of craft and labor. Not corporate B-roll.

---

## Design implications I'm noting (to confirm later)
- **Worlds** likely needs to be a top-level navigation primitive — a menu, a section, or a persistent filter on the Updates rail.
- The terminal-overlay slideshow (Note 01) could surface the active World as the `SUBJECT`: e.g. `babb@tel farming % …`, `babb@tel manufacturing % …`. This makes the prompt do double duty as a beat tag.
- Tag system on the Updates rail can mirror the seven Worlds as the top-level category, with project/product tags nested under (ties cleanly to Jekyll categories from Note 01).
- The "different kind of VICE" posture argues for **strong photography and place-based imagery** over illustration — real shops, real fields, real factory floors. Worth flagging when we're choosing hero treatments.
- Likely wants a "From the field" or "Dispatch" style label on certain posts to mark on-the-ground reporting vs. studio/editorial work.

## Answered follow-ups _(May 18, 2026)_
- **Label:** **"Worlds"** is the canonical short form used generally. **"Working Worlds"** is used limitedly — treat it as a tagline / fuller phrasing rather than the nav label.
- **Growth:** The list will grow over time. Additionally, **some Worlds will gain sub-specificity** (sub-Worlds / nested beats under a parent). The design must accommodate this from the start.
- **Landing pages:** **Each World gets its own landing page** — imminent. **Plan for it now** in IA and link structure (the Worlds nav should resolve to real pages, not just filtered views).
- **Launch priority:** No early emphasis among the seven. Visual prominence will follow whatever actual posts / videos / combined content can be mustered early on — so the layout needs to gracefully handle uneven content density across Worlds.

## Resulting design constraints
- Treat **Worlds** as a first-class IA primitive, with **dedicated `/worlds/<world>` pages** (and `/worlds/<world>/<sub>` for sub-Worlds).
- Updates rail tagging (Note 01) should support **nested categories** under a World — fits the Jekyll category model already noted.
- Homepage Worlds module should be **content-density aware**: a World with five rich posts and one with zero should both look intentional. Likely means a flexible grid or list with empty-state grace, not fixed-size feature tiles.
- The terminal-overlay slideshow's `SUBJECT` slot can carry the World name, and optionally a sub-World after a slash — e.g. `babb@tel farming/dairy % …`.
