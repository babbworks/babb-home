---
layout: dispatch
title: "BASICS — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: basics
tags: [basics, standards, products]
author: Babb
excerpt: "BASICS — Business Assistance System — is a practical standard for building business tools that can operate across unstable conditions, constrained devices, mixed operator skill levels, and long product lifecycles."
---

## What it does

BASICS — Business Assistance System — is a practical standard for building business tools that can operate across unstable conditions, constrained devices, mixed operator skill levels, and long product lifecycles.

It is a commitments system with testable obligations. If you build a tool that claims BASICS conformance, you are making specific, verifiable promises about how that tool behaves when conditions are bad: when the network is down, when the device is old, when the operator is new, when the power is low, when the data must last decades.

BASICS does not tell you what to build. It tells you what your tool must survive.

## How it works

BASICS defines a set of **rules** — each with a stable identifier — organized into **profiles** that represent tiers of conformance. Each rule is a testable obligation: a concrete, verifiable statement about tool behavior under specified conditions.

The standard covers:

- **Offline operation** — tools must function without network connectivity, not merely degrade gracefully
- **Constrained devices** — tools must work on low-memory, low-power, small-screen hardware, including feature phones
- **Mixed skill levels** — tools must be operable by people who did not build them and may not read English
- **Data durability** — records must be exportable in open formats, never locked to a vendor
- **Long lifecycles** — tools must be designed to operate for decades, not just until the next funding round

The **BASICS CLI** (`basics`) is a command-line assessor that evaluates a local repository against the standard. It examines code, configuration, documentation, and test coverage to produce an evidence-backed conformance report. The assessor does not guess — it checks specific files, specific patterns, specific behaviors, and reports what it finds.

Conformance is tiered. The Core tier establishes baseline requirements that all BASICS tools must meet. Higher tiers add obligations for specific deployment contexts (intermittent connectivity, KaiOS devices, multi-language operation, audit-grade record keeping).

## Why it exists

Most software standards describe what a system should do when everything is working. BASICS describes what a system must do when things are not working — because in the working world, things are frequently not working. The network is down. The device is five years old. The operator learned the tool yesterday. The power went out an hour ago.

Tools built for the frontier — feed-lots, factory floors, rural branches, remote field offices — cannot afford the assumptions that tools built for Silicon Valley make. BASICS exists to codify what frontier-grade software requires, so that builders can commit to it and users can verify it.

The standard also exists because Babb builds tools (Workpads, BitPads, BitLedger, Workwarrior) and needed a way to hold itself accountable. BASICS is the internal discipline made public: the same rules Babb applies to its own products, available for anyone building tools for the same conditions.

## Current status

- **Version:** BASICS Standard v0.1.1
- **CLI assessor:** `basics` — evidence-backed conformance checking
- **Conforming tools:** Workpads Standard v0.1 (Core tier)
- **Profiles:** Core (baseline), with additional tiers in development

## Where to find it

- Standard: [BASICS Standard](https://github.com/babbworks/BASICS-standard)
- CLI: [BASICS CLI](https://github.com/babbworks/BASICS-cli)
- Site: [basics.babb.tel](https://basics.babb.tel)
