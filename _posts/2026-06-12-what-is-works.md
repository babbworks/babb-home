---
layout: dispatch
title: "Works — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: works
tags: [works, compound, products, software]
author: Babb
excerpt: "Works is an industrial compound for business information. The metaphor is intentional and load-bearing: a works — in the Victorian sense, a textile works, an ironworks, a gasworks — is a complete operational site where raw materials arrive, move through specialized processes, and leave as finished goods."
---

## What it does

Works is an industrial compound for business information. The metaphor is intentional and load-bearing: a works — in the Victorian sense, a textile works, an ironworks, a gasworks — is a complete operational site where raw materials arrive, move through specialized processes, and leave as finished goods.

Works applies this model to business information: tasks, time records, journal entries, financial transactions, documents, agent outputs, API responses, and any other operational content a business produces or consumes. Information arrives at a defined intake point, is verified and classified, held in named stores, transformed in mills, authorized for departure through a gate, and dispatched to its destination. A ledger records everything that entered, moved, and left — permanently.

Works is not just software. It is a protocol — a specification of buildings, conveyance rules, actor types, and constitutional guarantees that any conforming implementation must honor. The Compound Browser is the reference implementation.

## How it works

Works maps directly to the von Neumann stored-program computer, extended with three additional structures (Gate, Office, Actors) that von Neumann had no need for:

| Von Neumann | Works |
|---|---|
| Memory Unit | **Stores** — named, addressed chunk repositories |
| Stored Program | **Barrels** — instruction sequences stored in Stores |
| Control Unit | **Barrel** — fetch, sequence, cycle, policy-check |
| ALU | **Mill** — transform, combine, run lens pipeline |
| Registers | **Bench** — session workspace, staging area |
| Input Unit | **Intake** — receive, verify, classify, route |
| Output Unit | **Dispatch** — publish, write, broadcast |
| System Bus | **Stream** — append-only log + real-time bus + replay |

Three additions beyond von Neumann:

- **Gate** — nothing leaves the compound without explicit authorization. Every chunk must pass through Gate before Dispatch. This is the Right to Assembly: the compound does not emit information accidentally.
- **Office** — the policy authority. Issues capability tokens, maintains the actor registry, enforces rules, records audit logs, and can veto any Gate decision.
- **Actors** — first-class operators in four types: Human, Agent (AI), Automated (Barrel-driven), and External (cross-compound or WebWarrior bridge). Every action in the compound is attributed to a named Actor with session scope.

Storage uses a **Row x Level x Bin** addressing system. Row is a unique object identifier. Level is the lifecycle stage (Raw, Staged, Integrated). Bin is the field classifier. This gives every chunk a precise, human-memorable address.

The Stream is the constitutional bottleneck. Every building action crosses Stream. This costs performance and buys auditability, replay, and policy enforcement as structural properties.

The Compound Browser — the reference implementation — is a browser-based application built with Preact, using OPFS for append-only storage and IndexedDB for structured queries. It includes full UI panels for every building, chunk visualization (card/row/kanban views), drag-and-drop, a WebWarrior bridge, and a dashboard with live stats.

## Why it exists

Business information is the most valuable thing most businesses produce, yet it is handled with less care than raw materials in a Victorian factory. Documents live in email threads. Tasks live in four different apps. Financial records live in spreadsheets that nobody audits. When something goes wrong, nobody can reconstruct what happened, when, or who authorized it.

Works exists because business information deserves the same structural guarantees that made industrial compounds reliable: physical containment, specialized roles, gated departure, permanent ledger. These are not aspirational principles — they are enforceable protocol rules. A conforming Works implementation cannot emit information without Gate authorization. Cannot process without Mill. Cannot store without addressed inventory. Cannot operate without Stream recording.

The von Neumann mapping is not decoration. It is an argument: the architecture that made general-purpose computing possible — stored program, addressable memory, arithmetic unit, control unit, I/O — is also the architecture that makes general-purpose business information processing reliable. Works takes that architecture seriously and adds what business requires: authorization gates, policy offices, and accountable actors.

## Current status

- **Standard:** Works Standard (normative)
- **Reference implementation:** Works Compound Browser — 42 files, fully functional end-to-end
- **Buildings implemented:** Intake, Store, Mill, Bench, Barrel, Gate, Dispatch, Office, Vault (all complete)
- **UI:** Full browser-based panels for every building, chunk cards/rows/kanban, dashboard
- **Bridges:** WebWarrior BroadcastChannel bridge, File System Access API adapter
- **Stream:** Hollerith-encoded append-only log with replay and real-time pub/sub

## Where to find it

- Overview: [Works documentation](https://github.com/babbworks/works)
- Compound Browser: [works-compound-browser](https://github.com/babbworks/works-compound-browser)
- Standard: [works-standard](https://github.com/babbworks/works-standard)
