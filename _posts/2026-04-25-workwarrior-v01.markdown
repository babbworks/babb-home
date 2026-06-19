---
layout: post
title:  "Workwarrior v0.1.0 — Initial Release"
date:   2026-04-25 09:10:00 -0500
categories: releases workwarrior
---

Workwarrior v0.1.0 is the first formal release of the unified terminal productivity environment — integrating Taskwarrior, Timewarrior, JRNL, Hledger, and Bugwarrior under a single profile system, with a natural language processing layer and a locally-hosted browser UI.

The v0.1.0 release ships the full profile architecture: each profile is an isolated workspace containing its own tasks, time tracking, journals, double-entry ledgers, and configuration. No symlinks, no config switching, no path hacking — environment variables handle activation cleanly. The natural language processing layer ships with 627 compiled heuristic regex rules across 19 command domains, converting English into tool commands before optionally leveraging a local LLM.

The browser UI launches on port 7777 with 15+ panels and real-time updates via Server-Sent Events. The implementation uses Python 3 stdlib only — no external dependencies for the core. GitHub integration ships in two modes: one-way pull via Bugwarrior integration and bidirectional sync via ww github-sync for individual task-to-issue linking.

Weapons — the specialized task manipulation tools (Gun for bulk series generation, Sword for sequential subtask chains, Next for CFS-inspired scheduling) — are included in this release. The learning layer is built in from day one: every CMD submission is logged, and the --digest flag analyzes past translations to generate new rules. Workwarrior grows with its users.

---

[Workwarrior releases](/workwarrior/releases/) · [All releases](/categories/releases/) · [Workwarrior dispatches](/categories/workwarrior/)
