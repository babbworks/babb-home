---
layout: dispatch
title: "Workwarrior — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: workwarrior
tags: [workwarrior, products, software]
author: Babb
excerpt: "Workwarrior wraps five open-source tools — TaskWarrior, TimeWarrior, JRNL, Hledger, and Bugwarrior — into a single profile-based productivity system. Each profile is an isolated workspace: its own tasks, time tracking, journals, double-entry ledgers, and configuration. Switch contexts instantly. Nothing bleeds between profiles."
---

## What it does

Workwarrior wraps five open-source tools — TaskWarrior, TimeWarrior, JRNL, Hledger, and Bugwarrior — into a single profile-based productivity system. Each profile is an isolated workspace: its own tasks, time tracking, journals, double-entry ledgers, and configuration. Switch contexts instantly. Nothing bleeds between profiles.

The system runs from the terminal, from a locally-served browser UI, or both at once.

What Workwarrior manages per profile:

- **Tasks** (TaskWarrior) — projects, priorities, dependencies, tags, annotations
- **Time** (TimeWarrior) — tracking, reporting, gap detection
- **Journal** (JRNL) — timestamped entries, searchable, encrypted at rest
- **Ledger** (Hledger) — double-entry accounting, budgets, balance reports
- **Bugs** (Bugwarrior) — pull issues from GitHub/GitLab/Jira into TaskWarrior

One command switches everything. `ww @farmwork` and you are in the farmwork context — its tasks, its time logs, its journal, its books. `ww @consulting` and you are somewhere else entirely. The isolation is total.

## How it works

Workwarrior is a bash dispatcher with a natural language command layer. You type what you mean in plain English and Workwarrior translates it into the correct tool command.

The translation engine uses **627 compiled heuristic rules** — pattern-matched against your input — before optionally falling back to a local LLM for anything the rules don't cover. The heuristics are fast, deterministic, and auditable. They handle the commands people actually type: "log 2 hours on the Henderson project," "add a task to fix the gate latch," "how much time did I spend on admin this week."

The browser UI is served locally by a Python HTTP server. It provides a visual interface to the same underlying tools — task boards, time charts, journal entries, ledger views — all reading from and writing to the same profile data the CLI uses. You can have the browser open on one monitor and the terminal on another; they stay in sync.

WebWarrior is the browser-first variant — the same system accessed primarily through the web interface rather than the terminal. Both share the same profile format and can run side by side.

Architecture:
- **Profile isolation** — each profile gets its own directory tree with independent configuration for all five tools
- **Dispatch layer** — bash scripts that route commands to the correct underlying tool
- **NL engine** — 627 heuristic rules compiled into a fast matcher, with optional LLM fallback
- **Browser UI** — locally-served web interface with real-time sync to profile state
- **Dey signal** — session gap detection for continuity tracking

## Why it exists

Productivity tools are either too simple (a single to-do list) or too complex (enterprise project management). The people who do real work — the kind measured in hours, tracked in ledgers, and reported to clients — need something in between: powerful enough to handle tasks, time, money, and notes in one place, simple enough to run from a terminal.

The five tools Workwarrior wraps are individually excellent. TaskWarrior is the best task manager ever built for the command line. TimeWarrior tracks time with zero friction. JRNL keeps encrypted journals. Hledger does proper double-entry accounting. Bugwarrior pulls issues from everywhere.

But running five separate tools with five separate configurations across multiple projects is a coordination tax that defeats the purpose. Workwarrior eliminates that tax. One profile, one switch, one command layer that speaks all five languages. The 627 heuristic rules exist because nobody should have to remember whether "log time" is a TimeWarrior command or an Hledger command — you just say what you mean.

## Current status

- **Version:** v0.1.0 (initial formal release)
- **NL engine:** 627 heuristic rules + optional LLM fallback
- **Tools wrapped:** TaskWarrior, TimeWarrior, JRNL, Hledger, Bugwarrior
- **Interfaces:** Terminal CLI + locally-served browser UI
- **Standard:** Workwarrior Standard (normative)

## Where to find it

- Site: [workwarrior.org](https://workwarrior.org)
- Standard: [ww-standard](https://github.com/babbworks/ww-standard)
- Core: [ww](https://github.com/babbworks/ww)
