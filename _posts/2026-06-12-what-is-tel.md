---
layout: dispatch
title: ".tel — What It Is, How It Works, Why It Exists"
date: 2026-06-12
product: tel
tags: [tel, protocols, products]
author: Babb
excerpt: ".tel is the connective layer for Babb. It provides identity, routing, and channels for people who do work in the world."
---

## What it does

.tel is the connective layer for Babb. It provides identity, routing, and channels for people who do work in the world.

The simplest way to understand .tel: it routes the noise away from the people who need to reach you, and toward the ones who actually do. A small protocol with a long view. Built to outlast a platform cycle.

.tel handles three things:

1. **Identity** — a stable, portable identifier for a person or entity. Not tied to an email provider, a phone carrier, or a social platform. Yours to keep.
2. **Routing** — rules for how messages, notifications, and requests reach you. Who gets through, who waits, who gets redirected. Configurable per context, per time, per relationship.
3. **Channels** — the actual communication paths. Email, SMS, and structured channels that connect .tel identities to each other and to Babb products.

.tel is self-hostable. You can run your own node. The protocol is open and the specification is public.

## How it works

.tel operates as a protocol layer between identity (who you are) and delivery (how messages reach you). A .tel address resolves to a set of routing rules maintained by the address holder. Those rules determine what happens when someone or something tries to reach you.

The routing is context-aware. A .tel address can behave differently depending on:
- Who is contacting you (known contact, new contact, automated system)
- When they are contacting you (working hours, off hours, emergency)
- What they are contacting you about (structured request types vs. open messages)
- Which channel they are using (email, SMS, structured .tel channel)

Nodes are the infrastructure units. A node serves .tel addresses, maintains routing tables, and handles message delivery. Nodes can be self-hosted (run your own) or operated by Babb. The protocol is the same either way.

.tel integrates with every other Babb product. A Workpads notification routes through .tel. A BitPads transaction confirmation routes through .tel. A Clarkware alert routes through .tel. The connective layer is the connective layer for the entire ecosystem.

## Why it exists

Every communication platform wants to own your identity. Your email address belongs to your provider. Your phone number belongs to your carrier. Your social handle belongs to the platform. When the platform changes its rules, your identity changes with it.

.tel exists because identity should be infrastructure, not a product. A working person's reachability should not depend on which platform is popular this year. A protocol that routes messages based on rules you control — not rules a platform imposes — is more durable than any app.

.tel also exists because Babb's products need a connective layer that is not email. Email is universal but noisy, unstructured, and impossible to route intelligently. SMS is reliable but expensive and character-limited. .tel provides a structured alternative that integrates with both while adding the routing intelligence that neither has.

The long view matters. .tel is designed to be simple enough that a reimplementation from the specification alone — without access to the original codebase — is straightforward. Infrastructure that cannot be rebuilt from its documentation is infrastructure that will not survive.

## Current status

- **Stage:** Alpha, invite only
- **Spec:** Open, public
- **Nodes:** Self-hostable
- **Channels:** Email, SMS, structured .tel channels

## Where to find it

- Product page: [babb.tel/products/tel](/products/tel/)
- Spec: [.tel specification](/products/tel/spec/)
