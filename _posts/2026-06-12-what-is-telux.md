---
layout: dispatch
title: "Telux — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: telux
tags: [telux, outstack, systems, products]
author: Babb
excerpt: "Telux is a proposed operating system — or OS layer — whose byline is \"System for Group Exchange.\" It unifies three capabilities that no existing operating system combines: group identity, power management, and transactional security, all as a single coherent primitive rather than three separate subsystems bolted together."
---

## What it does

Telux is a proposed operating system — or OS layer — whose byline is "System for Group Exchange." It unifies three capabilities that no existing operating system combines: group identity, power management, and transactional security, all as a single coherent primitive rather than three separate subsystems bolted together.

Its logo is modeled on ancient Sumerian clay tokens — the first known formal value-representation system, predating writing. The symbolism is a design constraint: Telux is built to operate across millennia-scale timeframes, from handheld industrial tools today to interplanetary nodes eventually.

The core concepts:

- **newgroup** — an evolution of the Linux `group` primitive. A newgroup can contain any combination of human users, system services, commercial APIs, AI models, and IoT-connected physical systems. Groups are dynamic, can be permanent or temporary, and represent coalesced organizations with processing priorities.
- **Islands** — sovereign containers. Every group belongs to a place called an Island. Islands are the primary security boundary. Each Island must declare who or what is Sovereign over it. Sovereignty is hierarchical and grantable. The sovereign controls group lifecycle.
- **Outstack** — the bedrock service layer. A three-tier vertical stack (Visible, Submerged, Bedrock) that runs from the group chat interface down to hardware-isolated key storage and power gates.

## How it works

Telux inherits from three architectural traditions:

**Plan 9** (Bell Labs, 1987) — per-process namespace isolation. Every Island is a constructed namespace; every group inhabits it on sovereign terms.

**seL4** (2009) — capability-based security. The Sovereign mechanism is a capability system for group membership, power budget delegation, and exchange authorization. No ambient authorities.

**CICS** (IBM, 1960s) — transaction orchestration. Every exchange between entities in a group is recorded before it completes. The record is hashed, signed, and distributed to the appropriate visibility tier. The write-ahead log is the bedrock of trust.

The three-layer architecture:

| Layer | Name | Contents |
|---|---|---|
| 1 | **Visible** | Group chat interface, NL query API, member-visible exchange records |
| 2 | **Submerged** | Outstack daemon, sovereignty enforcer, permissioned logs, power governor |
| 3 | **Bedrock** | LSM module (Telux-SEC), immutable audit trail, TPM/HSM key storage, power gates |

The natural language query interface is not an AI wrapper. It is the designed query interface for the transactional ledger. A member asks "what did the inventory service send to the billing service last Tuesday?" and receives scoped, signed records — scoped by the Sovereignty model, not by AI judgment.

Power management is the operating premise, not a feature. Islands receive electricity budgets. Exceeding that budget is a security event. At `exec()` time, Outstack checks whether the power budget of the calling Island permits the new process to start at all. In EMERGENCY mode, only CRITICAL-class processes execute.

The identity model uses W3C Decentralized Identifiers (DIDs) for all non-human members — self-administered, cryptographically verifiable, decentralized, persistent. This gives Telux interoperability with the emerging global identity ecosystem and independence from any central authority.

## Why it exists

No operating system in existence today unifies group identity, power management, and transactional security into a single coherent model. Linux groups are static, local, human-only. Kubernetes namespaces are not groups. Cloud IAM systems have no concept of power management. Microkernels have no transactional ledger.

Telux exists because the gap is real and unexploited. Recent security research confirms that clock and power gating mechanisms are attack surfaces — adversaries who can manipulate which subsystems receive power can selectively disable security controls. The security community responds defensively. No OS project has turned this around: using power control offensively as a security primitive.

The insight is profound: software isolation can be bypassed by software. Hardware power isolation cannot be bypassed by software. A peripheral with no power has no attack surface — not because of a policy, not because of a privilege level, but because of physics.

Telux also exists because the working world is increasingly populated by non-human entities — AI models, IoT sensors, automated services — that participate in exchanges with humans but have no OS-level identity. They are either invisible (background processes) or shoehorned into human identity models (service accounts). Telux gives them first-class membership in groups, with capabilities, power budgets, and auditable exchange records.

## Current status

- **Phase:** Research and architecture
- **Documentation:** Comprehensive design documents covering newgroup primitive, Island sovereignty, three-layer architecture, power management integration, identity model, exchange layer, deployment vision
- **Implementation probes:** TeluxOS-AOSP prototype, TeluxOS-OpenHardware prototype, Bedrock Purity Assessment
- **Companion project:** Outstack (see separate article)
- **Open questions:** Accounting notation format, AI entity identity model, sovereignty succession rules, cross-Island protocol, bedrock access model, bootstrap key ceremony

## Where to find it

- Research corpus: ZAKO research folder (Telux, Outstack, TeluxOS-Probes)
- Related: [Outstack](/updates/what-is-outstack/) (the power/security bedrock)
- Related: [BitPads](/updates/what-is-bitpads/) (the record encoding layer)
