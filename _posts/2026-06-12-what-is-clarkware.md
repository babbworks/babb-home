---
layout: dispatch
title: "Clarkware — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: clarkware
tags: [clarkware, products, software, manufacturing]
world: Manufacturing
author: Babb
excerpt: "Clarkware is the Clark Industrial Process Environment — a manufacturing facility operations platform. It gives technicians, supervisors, and integrated tools a unified interface for tracking jobs, managing notes and communications, flagging issues, and running AI-assisted workflows, all in real time across a connected facility floor."
---

## What it does

Clarkware is the Clark Industrial Process Environment — a manufacturing facility operations platform. It gives technicians, supervisors, and integrated tools a unified interface for tracking jobs, managing notes and communications, flagging issues, and running AI-assisted workflows, all in real time across a connected facility floor.

What a technician sees when they sit down at a Clarkware workstation:

- **Jobs** — the full lifecycle from draft through active, paused, completed, voided, and reopened. Every state transition is recorded.
- **Notes** — append-only with revision chains. You can add to a note but you cannot silently alter what was written. The record is permanent.
- **Real-time events** — a live WebSocket stream shows what is happening on each job as it happens. No refresh, no polling.
- **AI assistance** — summarize a job's history, draft a note from bullet points, route an alert to the right person, review the current state of a process. Powered by Claude, scoped to the facility's data.
- **Artifacts** — photos, documents, readings, attached to jobs via presigned URLs. Upload from the floor, review from the office.

Clarkware targets the underserved middle market between heavyweight ERP systems (SAP, Oracle) and the disconnected tools most small-to-mid manufacturers actually use (spreadsheets, group chats, whiteboards).

## How it works

Clarkware is a Turborepo monorepo with two applications and eight shared packages, all written in TypeScript.

**Applications:**
- `apps/api` — a Fastify REST + WebSocket backend on Node.js. Handles authentication, job management, notes, issues, AI routes, artifact management, and real-time event streaming.
- `apps/ipe` — the workstation shell, built on Eclipse Theia. A browser-based IDE-like environment with React 18 widgets for jobs, notes, conversations, and AI tools.

**Core packages:**
- `@clark/core` — domain types, enums, events, identity. Zero runtime dependencies.
- `@clark/db` — PostgreSQL connection pool and query helpers.
- `@clark/identity` — JWT authentication, Argon2id password hashing, RBAC permission checking.
- `@clark/events` — append-only domain event store with optimistic concurrency.
- `@clark/ai` — Anthropic Claude integration for summarization, note drafting, alert routing, state review.
- `@clark/storage` — MinIO S3-compatible object storage client for artifacts.
- `@clark/messaging` — XMPP client, MUC room manager, sync engine for facility-wide communications.
- `@clark/sync` — offline-first conflict handler and sync queue.

**Infrastructure:**
- PostgreSQL 16 (primary database)
- MinIO (S3-compatible artifact storage)
- Prosody (XMPP messaging server)
- OpenSearch + Dashboards (full-text search and logs)
- RabbitMQ 3.13 (IPC-CFX AMQP message broker for industrial protocol integration)

Authentication uses JWT with RBAC enforcement on all protected routes. Every job state transition, every note revision, every AI invocation is recorded as a domain event in an append-only store.

## Why it exists

Manufacturing runs on institutional knowledge — the kind that lives in a foreman's head, in a technician's notebook, in the shift handoff conversation that happens at 6 AM in a parking lot. When that knowledge is lost — when someone retires, transfers, or just has a bad day — the facility loses capability that took years to build.

Clarkware exists to capture and preserve that knowledge as structured, searchable, permanent operational memory. Not as a replacement for the people who hold it, but as a system that ensures their observations, decisions, and reasoning survive their shift.

The AI integration is not a gimmick. A technician who has spent 30 minutes troubleshooting a furnace does not want to write a report. But they will say "flag this, bearing noise on unit 4, same as last month." Clarkware's AI can take that sentence, attach it to the right job, draft a structured note, and route an alert — while the technician goes back to work.

The Eclipse Theia shell was chosen deliberately. Manufacturing workstations need to be robust, customizable, and capable of running for months without restart. Theia provides a plugin architecture that allows facility-specific tooling without rebuilding the core platform.

## Current status

- **Phase:** P1 V1
- **Fully implemented:** Authentication (JWT + RBAC), job lifecycle, notes (append-only), real-time WebSocket events, AI routes (summarize, draft, route, review), artifact upload/download, developer seed data
- **Scaffolded (DB + routes, no UI yet):** Issues, conversations, shifts, presence, permissions
- **Built but not wired:** XMPP messaging, offline-first sync, reporting queries
- **Related:** Clark Chat (conversation layer, architecture phase), Clark Report (clark.babb.tel, live)

## Where to find it

- Core: [clarkware](https://github.com/babbworks/clarkware)
- Development intelligence: [clarkware-dev](https://github.com/babbworks/clarkware-dev)
- Clark Chat: [clark-chat](https://github.com/babbworks/clark-chat)
- Clark Report: [clark.babb.tel](https://clark.babb.tel)
