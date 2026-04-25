---
layout: default
title: "Releases for BASICS Standard"
permalink: /basics/releases/
categories: releases basics
---
<style>
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Barlow:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Barlow+Condensed:wght@500;600;700&display=swap');

.bh { --bg:#F8F7F4;--ink:#100F0E;--ink-2:#3B3A37;--ink-3:#7A7872;--ink-4:#B8B5AE;--accent:#B07830;--accent-lo:rgba(176,120,48,0.09);--rule:#E0DDD8;--ff-h:'Instrument Serif',Georgia,serif;--ff-b:'Barlow',system-ui,sans-serif;--ff-lbl:'Barlow Condensed',system-ui,sans-serif;font-family:var(--ff-b);color:var(--ink);background:var(--bg); }
.bh { margin:0 -30px; }
@media(max-width:1100px){.bh{margin:0 -15px;}}
.bh-wrap { max-width:1100px;margin:0 auto;padding:0 40px; }
@media(max-width:600px){.bh-wrap{padding:0 20px;}}

.bh-tag { font-family:var(--ff-lbl);font-size:0.6rem;font-weight:700;letter-spacing:0.26em;text-transform:uppercase;color:var(--accent);display:inline-flex;align-items:center;gap:10px;margin-bottom:20px;text-decoration:none; }
.bh-tag::before { content:'';display:block;width:22px;height:1px;background:var(--accent);flex-shrink:0; }
a.bh-tag:hover { color:var(--ink); }
.bh-rule { border:none;border-top:1px solid var(--rule);margin:0; }

.bh-btn { font-family:var(--ff-lbl);font-size:0.65rem;font-weight:700;letter-spacing:0.16em;text-transform:uppercase;text-decoration:none;padding:10px 20px;border:1px solid var(--ink);color:var(--ink);transition:background 0.14s,color 0.14s;display:inline-block; }
.bh-btn:hover{background:var(--ink);color:var(--bg);}
.bh-btn:visited{color:var(--ink);}

.tool-lnk { font-family:var(--ff-lbl);font-size:0.62rem;font-weight:700;letter-spacing:0.14em;text-transform:uppercase;text-decoration:none;color:var(--ink);border-bottom:1px solid var(--accent);padding-bottom:2px;transition:color 0.14s; }
.tool-lnk:hover{color:var(--accent);}
.tool-lnk:visited{color:var(--ink);}

.dispatch-list{list-style:none;margin:0;padding:0;}
.dispatch-item{display:grid;grid-template-columns:110px 1fr;gap:16px;padding:11px 0;border-bottom:1px solid var(--rule);align-items:baseline;}
.dispatch-item:first-child{border-top:1px solid var(--rule);}
.dispatch-date{font-family:var(--ff-lbl);font-size:0.58rem;font-weight:600;letter-spacing:0.14em;text-transform:uppercase;color:var(--ink-4);}
.dispatch-title{font-family:var(--ff-b);font-size:0.85rem;color:var(--ink);text-decoration:none;line-height:1.4;transition:color 0.14s;}
.dispatch-title:hover{color:var(--accent);}
.dispatch-title:visited{color:var(--ink-2);}
.br-empty{font-family:var(--ff-b);font-size:0.82rem;color:var(--ink-4);font-style:italic;padding:12px 0;border-top:1px solid var(--rule);}

.spec{display:flex;flex-direction:column;gap:3px;margin-bottom:20px;}
.spec-k{font-family:var(--ff-lbl);font-size:0.56rem;font-weight:700;letter-spacing:0.22em;text-transform:uppercase;color:var(--ink-4);}
.spec-v{font-family:var(--ff-b);font-size:0.82rem;color:var(--ink-2);line-height:1.55;}
.spec-v a{color:var(--accent);text-decoration:none;}
.spec-v a:hover{text-decoration:underline;}

.br-header{padding:56px 0 40px;}
.br-header h1{font-family:var(--ff-h);font-size:clamp(2rem,4vw,3rem);font-weight:400;color:var(--ink);margin:0 0 14px;line-height:1.1;}
.br-header p{font-family:var(--ff-b);font-size:0.95rem;color:var(--ink-3);line-height:1.7;max-width:560px;margin:0;}

.br-dispatches{padding:44px 0 36px;}
.br-dispatches-head{display:flex;align-items:baseline;gap:20px;margin-bottom:20px;}

.br-grid{display:grid;grid-template-columns:1fr 280px;gap:64px;padding:48px 0 72px;align-items:start;}
.br-sidebar{border-left:1px solid var(--rule);padding-left:36px;}
.br-sidebar-section{margin-bottom:36px;}
.br-sidebar-head{font-family:var(--ff-lbl);font-size:0.58rem;font-weight:700;letter-spacing:0.22em;text-transform:uppercase;color:var(--ink-4);margin:0 0 14px;display:block;}

.br-prose h2{font-family:var(--ff-h);font-size:1.35rem;font-weight:400;color:var(--ink);margin:40px 0 10px;line-height:1.2;}
.br-prose h2:first-child{margin-top:0;}
.br-prose p{font-family:var(--ff-b);font-size:0.88rem;color:var(--ink-2);line-height:1.8;margin:0 0 14px;}
.br-prose strong{font-weight:600;color:var(--ink);}

.br-contribution{margin-top:48px;padding-top:32px;border-top:1px solid var(--rule);}
.br-contribution h3{font-family:var(--ff-h);font-size:1.1rem;font-weight:400;color:var(--ink);margin:0 0 10px;}
.br-contribution p{font-family:var(--ff-b);font-size:0.83rem;color:var(--ink-3);line-height:1.75;margin:0 0 16px;}
.br-footnote-links{display:flex;flex-wrap:wrap;gap:10px 24px;margin-top:14px;}

@media(max-width:900px){
  .br-grid{grid-template-columns:1fr;gap:40px;}
  .br-sidebar{border-left:none;padding-left:0;border-top:1px solid var(--rule);padding-top:32px;}
  .dispatch-item{grid-template-columns:90px 1fr;}
}
@media(max-width:560px){
  .dispatch-item{grid-template-columns:1fr;gap:3px;}
  .dispatch-date{font-size:0.54rem;}
}
</style>

<div class="bh">
<div class="bh-wrap">

<header class="br-header">
  <span class="bh-tag">Open Standard</span>
  <h1>BASICS Standard</h1>
  <p>A commitments framework with testable obligations — the engineering foundation shared across every Babb tool and open to any developer building for constrained, real-world operating conditions.</p>
</header>

<hr class="bh-rule">

<section class="br-dispatches">
  <div class="br-dispatches-head">
    <a class="bh-tag" href="/categories/releases">Releases</a>
  </div>
  {% assign basics_releases = site.posts | where_exp: "p", "p.categories contains 'releases'" %}
  {% assign basics_posts = basics_releases | where_exp: "p", "p.categories contains 'basics'" %}
  {% if basics_posts.size > 0 %}
  <ul class="dispatch-list">
    {% for post in basics_posts limit:5 %}
    <li class="dispatch-item">
      <span class="dispatch-date">{{ post.date | date: "%b %d, %Y" }}</span>
      <a class="dispatch-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
  </ul>
  {% else %}
  <p class="br-empty">No release dispatches yet — check back soon.</p>
  {% endif %}
</section>

<hr class="bh-rule">

<div class="br-grid">

<div class="br-prose">

<h2>The record is not optional</h2>
<p>BASICS begins from a single premise: the record is the unit of coordination. Every tool built under the standard must produce records that are self-describing, minimal, and structurally honest. A record that requires special software to read is not a durable record — it is a liability. BASICS enforces this at the framework level, not the application level.</p>

<h2>Command and control belongs to the operator</h2>
<p>The BASICS framework is anchored to this principle without exception. No BASICS-conformant tool may require network connectivity to perform local operations. No BASICS-conformant tool may default to remote storage without explicit operator election. Data belongs to the person or organization that created it, and the tool is a means of access — not a custodian. Every release of the BASICS Standard strengthens and clarifies this commitment, never retreats from it.</p>

<h2>Conformance is machine-checkable evidence</h2>
<p>BASICS replaces narrative certification with testable obligations. The three conformance tiers — Core, Field, and Industrial — each specify binary pass/fail mandatory requirements. Optional controls use maturity scoring. The purpose is accountability: a tool that claims BASICS conformance can be audited, challenged, and verified. No tier is achieved by assertion. Each release of the standard must preserve this verifiability and expand its coverage.</p>

<h2>Governance runs on 100-day cycles</h2>
<p><strong>Every change to BASICS requires community review.</strong> Proposals enter a structured cycle: draft, review, trial implementation, then decision. Target: 100 days from draft to outcome. No requirement changes without a published migration impact assessment. Requirements sunset only with explicit replacement — never silently removed. This discipline is what separates a standard from a preference. Each release of BASICS must follow this process, including releases to the governance rules themselves.</p>

<h2>Interoperability is an engineering discipline, not a promise</h2>
<p>BASICS treats interoperability as a first-class engineering requirement. The Shared Core defines universal rules for command contracts, record formats, versioning, and inter-tool communication. The Software, Hardware, and Firmware Profiles specify how conformance extends from code to silicon. Operational Extensions provide formal pathways for tool-specific behavior without breaking the common base. Each release expands the scope of testable interoperability while maintaining backward-compatible stable identifiers.</p>

<h2>Local-first, always</h2>
<p>BASICS-conformant tools default to local operation. Sync, collaboration, and cloud capabilities may be added, but they are extensions of local-first behavior — not replacements for it. The reference implementation for v0.1.0 is Workpads, which stress-tests these commitments in production: KaiOS feature phones, intermittent SMS-only connectivity, mixed digital and paper workflows. BASICS evolves as its reference implementations reveal gaps, with each revision maintaining what prior versions guaranteed.</p>

<div class="br-contribution">
  <h3>Contribute to BASICS</h3>
  <p>BASICS is an open standard maintained under open governance. The specification, conformance tests, and tooling live on GitHub. The best way to engage is to implement a tool against the standard and report what breaks, what is unclear, and what is missing. Proposals are welcome from anyone. The community review cycle is the mechanism — not editorial discretion.</p>
  <p>Clone the repo, run the conformance suite against something real, and open an issue or PR. If you are building tools for constrained environments — field devices, low-bandwidth networks, offline-first mobile — BASICS was written for your constraints.</p>
  <div class="br-footnote-links">
    <a class="tool-lnk" href="https://github.com/babbworks/basics-standard">GitHub →</a>
    <a class="tool-lnk" href="https://github.com/babbworks/basics-standard/issues">Open an Issue →</a>
    <a class="tool-lnk" href="mailto:basics@babb.tel">basics@babb.tel</a>
    <a class="tool-lnk" href="https://twitter.com/basicprotocol">@basicprotocol</a>
  </div>
</div>

</div><!-- /br-prose -->

<div class="br-sidebar">

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Current Release</span>
    <div class="spec">
      <div class="spec-k">Version</div>
      <div class="spec-v">v0.1.1</div>
    </div>
    <div class="spec">
      <div class="spec-k">Status</div>
      <div class="spec-v">Active development · Stable rule identifiers</div>
    </div>
    <div class="spec">
      <div class="spec-k">Reference implementation</div>
      <div class="spec-v"><a href="/workpads/releases">Workpads</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Releases</span>
    <div class="spec">
      <div class="spec-k">v0.1.1</div>
      <div class="spec-v"><a href="https://github.com/babbworks/basics-standard/releases">Stable identifiers &amp; profile boundaries</a></div>
    </div>
    {% assign ann = site.posts | where_exp: "p", "p.categories contains 'basics' and p.title contains 'v0.1'" | first %}
    <div class="spec">
      <div class="spec-k">v0.1.0</div>
      <div class="spec-v">{% if ann %}<a href="{{ ann.url | relative_url }}">{{ ann.title }}</a>{% else %}Initial framework release{% endif %}</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Repository</span>
    <div class="spec">
      <div class="spec-v"><a href="https://github.com/babbworks/basics-standard">babbworks/basics-standard →</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Contact</span>
    <div class="spec">
      <div class="spec-v"><a href="mailto:basics@babb.tel">basics@babb.tel</a></div>
    </div>
    <div class="spec">
      <div class="spec-v"><a href="https://twitter.com/basicprotocol">@basicprotocol</a></div>
    </div>
  </div>

  <a class="bh-btn" href="https://github.com/babbworks/basics-standard/releases" style="margin-top:8px;">GitHub Releases →</a>

</div><!-- /br-sidebar -->

</div><!-- /br-grid -->

</div><!-- /bh-wrap -->
</div><!-- /bh -->
