---
layout: dispatch
title: "Outstack — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: outstack
tags: [outstack, telux, systems, products]
author: Babb
excerpt: "Outstack is an Alpine Linux derivative focused on two unified concerns: security and power management. It treats both as expressions of resource control — a component that cannot be power-gated is a component that cannot be isolated during a security incident."
---

## What it does

Outstack is an Alpine Linux derivative focused on two unified concerns: security and power management. It treats both as expressions of resource control — a component that cannot be power-gated is a component that cannot be isolated during a security incident.

The name comes from the northernmost exposed rock of the United Kingdom: permanently uninhabited, geologically stable, essential to the maritime definition of where Britain ends. It is the bedrock beneath everything. It has no residents. It is not optional.

Outstack is exactly that for the systems it runs on: the uninhabited, always-running bedrock that enforces the rules.

Four core tenets:

1. **Default deny** — nothing runs, nothing has power, nothing has access unless explicitly granted.
2. **Hierarchical isolation** — CPU, memory, network, and power form independent containment boundaries.
3. **Verifiable state** — at any moment, the system can attest exactly what is running and what is consuming power.
4. **Graceful degradation** — security incidents and power exhaustion trigger controlled shutdowns, not crashes.

## How it works

**Kernel:** Outstack tracks Alpine's kernel source and layers a hardened configuration on top. No patching, no forking. KSPP essentials: stack protector, FORTIFY_SOURCE, hardened usercopy, SLAB freelist hardening, init-on-alloc/free, devmem/devkmem/kexec disabled. Per-board defconfigs (RPi4, iMX8, generic x86).

**Security layers** (boot to runtime):

| Layer | Mechanism |
|---|---|
| 1. Secure boot | TPM/eFuse root of trust, verified bootloader, dm-verity kernel |
| 2. Runtime integrity | dm-verity read-only root, IMA/EVM, immutable /usr, encrypted mutable /var |
| 3. MAC | AppArmor for process confinement + Landlock for self-sandboxing |
| 4. Network | nftables default-deny egress, WireGuard for all external comms, no listeners |

**Power management** (`outstack-powerd`):

A userspace daemon that reads power budgets from `/etc/outstack/power.conf`, monitors via powercap/RAPL, INA sensors, and SoC PMICs, and enforces budgets with configurable violation actions (throttle, power-gate, deny). Power domains receive individual budgets, governors, and idle timeout policies.

The critical innovation: **power anomalies trigger security alerts**. Unexpected power draw from a subsystem may indicate compromise. A compromised peripheral can be physically power-killed — not just software-disabled. Power state is included in attestation reports. This creates a security guarantee based on physics, not policy.

**Five system operating modes:**

| Mode | Trigger | Behavior |
|---|---|---|
| FULL | External power / >80% battery | Unrestricted |
| NORMAL | 60-80% | Normal operation |
| CONSERVE | 20-60% | Background limited |
| CRITICAL | 5-20% | Critical tasks only |
| EMERGENCY | <5% | Survival mode |

**Execution gating:** At `exec()` time, Outstack checks whether the current power mode permits the new process to start. In EMERGENCY mode, only CRITICAL-class processes execute. This is a scheduling primitive, not a firewall rule.

**Image system:** A/B rootfs partitions (dm-verity protected), recovery partition, encrypted data partition. Signed OTA updates with automatic rollback on failure. Profile-based builds: minimal, iot-sensor, gateway.

**Package tiers:**

| Tier | Source | Policy |
|---|---|---|
| Passthrough | Alpine direct | Trust Alpine, auto-update |
| Rebuilt | Alpine APKBUILD, hardened flags | `-fstack-clash-protection -fcf-protection -fPIE`, audit |
| Custom | Our APKBUILDs | Full control (`outstack-init`, `outstack-powerd`) |

## Why it exists

Every existing approach to OS-level security focuses on software boundaries: access control lists, mandatory access controls, capability tokens, encrypted memory. These are essential. But they share a common vulnerability: a sufficiently privileged software actor can, in principle, bypass them.

Outstack adds a layer beneath software: physical power control. A hardware peripheral that is power-gated is not merely denied access — it does not exist as a computing entity. No software privilege escalation, no kernel exploit, no hypervisor escape changes this fact.

This creates a new class of security guarantee: **resources isolated by Outstack are secure by physics, not by policy**.

Outstack also exists because power management and security are, at the hardware level, the same problem. Both are about controlling which resources are available to which processes. Treating them as separate concerns — the way every other OS does — creates gaps. A device that can be software-disabled but not power-gated can still be exploited. A device that is power-gated cannot.

The aerospace heritage is deliberate. Outstack's power model was inspired by RTG-powered spacecraft, where every milliwatt must be accounted across the mission lifetime. The same discipline applies to battery-powered industrial tools, remote field devices, and eventually to actual spacecraft running Telux nodes.

## Current status

- **Phase:** Initial design, documented architecture
- **Base:** Alpine Linux derivative (hardened config, no fork)
- **Target hardware:** x86_64, aarch64, armv7, RISC-V (as ecosystem matures)
- **Design documents:** Core design doc, five-mode power model, kernel hardening spec, security layer architecture, image build pipeline, package tier system
- **Companion:** Telux (Outstack is the bedrock layer for the Telux OS)
- **Open design work:** `outstack-powerd` internals, `outstack-init` specification, board-specific device tree overlays, CI/CD pipeline, attestation protocol

## Where to find it

- Research corpus: ZAKO research folder (Outstack)
- Related: [Telux](/updates/what-is-telux/) (the OS that Outstack serves)
