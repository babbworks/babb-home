---
layout: dispatch
title: "ZAKO — What It Is, How It Works, Why It Exists"
date: 2026-06-13
product: zako
tags: [zako, telux, outstack, bitpads, systems, products]
author: Babb
excerpt: "ZAKO is a sovereign mobile operating system. Every interaction it mediates is a conservation event with two sides that must balance and must be provable. Built on AOSP without Google Mobile Services, governed by Outstack, secured by Telux, encoded by BitPads."
---

## What it does

ZAKO is a sovereign mobile operating system. Every interaction it mediates — every resource it governs, every relationship it records — is a conservation event. It has two sides, it must balance, and it must be provable. The protocol that enforces this at the wire level is BitPads and BitLedger. The sovereignty architecture that makes it yours is Telux. The power governance that makes it honest is Outstack. Together they are ZAKO.

A ZAKO device is sovereign in a precise engineering sense:

- **Your records stay on your device.** They are not stored on external servers. They do not leave without an explicit sovereign action that itself produces a record.
- **Your identity is not issued by a third party.** It is an ed25519 key backed by hardware (TrustZone), expressed as a W3C Decentralized Identifier. It is yours.
- **Your power budget is accountable to you.** The device does not drain its battery maintaining background connections to servers you did not choose. Every milliwatt is accounted.
- **You work offline.** Every ZAKO service functions without a network connection. Records are created locally, transmitted when and how you choose — via SMS, QR code, Bluetooth LE, or IP.

The reference hardware is the Babb Cat — a Cat S22 Flip ruggedized flip phone running on a Qualcomm QM215 (MSM8937) with 2GB RAM. A $99 device. The architecture does not depend on the hardware. The same standard runs on any AOSP-compatible platform.

## How it works

ZAKO is not a kernel. It is a coherent assembly — like Ubuntu is to Linux — of a kernel, core daemons, system services, and application infrastructure expressing a unified philosophy: sovereignty.

**Three layers:**

The **Bedrock Layer** is hardware and kernel. TrustZone root of trust, dm-verity integrity checking, hardware power domains, the Telux-SEC kernel security module. These are physical facts. They cannot be overridden by userspace software.

The **Submerged Layer** is where ZAKO's intelligence lives. Outstack governs the device's power state and enforces the relationship between power mode and process execution. Telux manages Islands, newgroups, sovereignty grants, and the exchange ledger. The identity service manages DIDs for every entity — human, machine, AI, or service.

The **Visible Layer** is the surface: group interfaces, exchange queries, telephony, applications, natural language query. Built on AOSP because it is proven, runs on existing hardware, and can be audited without dependency on any single commercial entity.

**The protocol foundation:**

Every ZAKO record is a BitPads frame. BitLedger v3.0 encodes conserved scalar exchanges in 40 bits. BitPads v2.0 wraps every transmission with a meta byte declaring frame type. The Enhancement Sub-Protocol provides priority, acknowledgement, and continuation signalling at 13 declared positions. Three independent error detection mechanisms — CRC-15, cross-layer mirroring, and the conservation invariant — ensure integrity.

**Four architectural lineages:**

Unix gave ZAKO composable small tools and graceful degradation. Plan 9 gave it namespace isolation — every Island is a constructed namespace. seL4 gave it capability-based security — no ambient authority, sovereignty as unforgeable tokens. CICS gave it the transaction as substrate — every exchange recorded before it completes, durable, auditable, sixty years of proven operation.

**No Google Mobile Services:**

GMS removal is the founding design decision. Push notifications via UnifiedPush. Applications via F-Droid. Maps via OpenStreetMap. Authentication via Telux DID. Every replacement is more sovereign, not merely different.

**Five power modes:**

Outstack governs the device through five objective power states: FULL (>80%, unrestricted), NORMAL (60-80%), CONSERVE (20-60%, background limited), CRITICAL (5-20%, essential only), EMERGENCY (<5%, survival). These are not user-selected profiles — they are operational states determined by objective measurement. At `exec()` time, Outstack checks whether the current mode permits the process. A 10% battery is a device exercising sovereignty over which processes continue.

## Why it exists

Every mobile operating system currently available was designed around a premise never stated because it was considered obvious: the phone exists to serve its manufacturer. Android routes push notifications through Google's servers, verifies signatures against Google's keys, sends location history and usage patterns to data centers in jurisdictions the user has no relationship with. Apple's integration is more complete — the phone is a terminal into Apple's services. Neither is dishonest. Both serve hundreds of millions of people adequately.

But there are contexts where the premise must be reversed. Where the phone must serve its user rather than its manufacturer. Where records must belong to the parties to the exchange and to no one else. Where the power budget must be accountable to the mission rather than to a background sync schedule determined on another continent.

ZAKO exists for those contexts. A phone in Lusaka, Zambia. An autonomous excavator in a Mongolian copper mine. A humanoid assistant in a hospital in Lagos. A relay node on a spacecraft crossing between Earth and Mars. The architecture does not change. The deployment profile changes. ZAKO adapts. The sovereignty does not.

ZAKO also exists because writing was invented for ledgers, not literature. Cuneiform tablets recording grain allocations, debt obligations, the transfer of livestock between parties. Writing was invented so that exchange could be trusted across time and distance. The clay token preceded the word. ZAKO is an attempt to build the next such substrate.

## Current status

- **Standard:** ZAKO Standard v1.0 (7 normative documents)
- **Reference hardware:** Babb Cat (Cat S22 Flip, QM215/MSM8937)
- **Protocols:** BitPads v2.0, BitLedger v3.0, Telux, Outstack
- **Services:** PADS, Health, Academy, Agreements (specified)
- **Distributions:** Base profile + distribution template system
- **Packages:** zako-outstack, zako-pads, zako-simba, zako-telux

## Where to find it

- Product page: [ZAKO](/products/zako/)
- Related: [BitPads](/products/bitpads/), [BitLedger](/products/bitledger/), [Telux](/products/telux/), [Outstack](/products/outstack/)
