---
layout: dispatch
title: "Workpads — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: workpads
tags: [workpads, products, software]
author: Babb
excerpt: "Workpads is a field notebook for the working world. It pairs structured forms with photos, audio recordings, and signoffs so that a single pass through a site — a feed-lot pen, a furnace floor, a bank branch lobby — produces a complete record. It runs on iOS, Android, and the web."
---

## What it does

Workpads is a field notebook for the working world. It pairs structured forms with photos, audio recordings, and signoffs so that a single pass through a site — a feed-lot pen, a furnace floor, a bank branch lobby — produces a complete record. It runs on iOS, Android, and the web.

The core unit is the **pad**: a structured document with required and optional fields, attached media, and a signoff chain. A pad can be a daily log, a shift handoff, a branch open/close checklist, or any repeating operational record. Pads are designed per Place — a feed-lot is not a bank branch, and the forms reflect that.

Six things, in order of how often they matter:

1. **Structured forms** — required where it must be, optional where it should be. Tap targets are 44px minimum, tested with gloves on.
2. **Photos attached to fields** — a photo lives on the entry it documents, not in a separate bucket.
3. **Audio on every entry** — tap-and-hold to record, transcribed when there's a signal.
4. **Offline-first sync** — works when it can, syncs when it can't. Conflict resolution favors the person who was there.
5. **Open export** — CSV, JSON, PDF. Your records are yours, on disk, readable in any tool.
6. **Multi-place, multi-crew** — one operator can run two lots, one reporter can cover three Worlds. Permissions per Place, per role, per shift.

## How it works

Workpads is built on a PADS model — a portable, addressable document structure that encodes job records into a compact binary format called **pads-v1**. This codec, implemented in the `@workpads/codec` package, uses fflate DEFLATE compression and base64url encoding to produce records compact enough to transmit via SMS, satellite link, or QR code.

Storage is local SQLite, synced to your tenant. The sync engine uses CRDTs for conflict-free merging — when two people edit the same record offline, the person who was physically on-site wins. The queue length is unlimited; Workpads will hold weeks of unsynced data without complaint.

The system runs on three platforms from a shared codebase:
- **KaiOS** — the original target. A 240x320px feature phone app controlled with a D-pad. This is the canonical lab where constraints are tightest.
- **Mobile** (iOS/Android) — the production deployment target for most field crews.
- **Web** — a full-width desktop browser app for office review, reporting, and administration.

Each platform implements the same record format and sync protocol. A pad created on a KaiOS phone in a feed-lot can be opened on the web app in an office 400 miles away.

Integrations include per-form webhooks with signed payloads, OIDC/SAML SSO, and a REST + read-only GraphQL API.

## Why it exists

Most field software is built by people who have never worked a shift. The forms are too long, the buttons are too small, the app dies without signal, and the data is locked in a vendor's cloud. The people who actually use these tools — the ops lead walking pens before dawn, the technician handing off a shift, the branch officer closing for the night — deserve better.

Workpads exists because the working world needs a record system that respects the conditions of the work: cold hands, wet screens, dead zones, twelve-hour shifts. It was built with the people Babb covers — in feed-lots, on factory floors, in branch lobbies — not in a design studio.

The open export guarantee is non-negotiable. Your records are yours. We do not hold your data hostage.

## Current status

- **Version:** v2.3.1
- **Platforms:** iOS 16+, Android 11+, Web (evergreen browsers)
- **Standard:** Workpads Standard v0.1 (BASICS-conformant)
- **Codec:** pads-v1 v2.0
- **Deployed:** 14 Places across 5 Worlds (Farming, Manufacturing, Banking, Management, Building)
- **Pricing:** Free for individuals / $12/mo per user for teams / $50/mo per Place for production

## Where to find it

- Product page: [babb.tel/products/workpads](/products/workpads/)
- Standard: [Workpads Standard v0.1](https://github.com/babbworks/workpads-standard)
- Site: [workpads.org](https://workpads.org)
