---
layout: default
title: "Releases for BitLedger Protocol"
permalink: /bitledger/releases/
categories: releases bitledger
---
<style>
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Barlow:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Barlow+Condensed:wght@500;600;700&display=swap');

.bh{--bg:#F8F7F4;--ink:#100F0E;--ink-2:#3B3A37;--ink-3:#7A7872;--ink-4:#B8B5AE;--accent:#B07830;--accent-lo:rgba(176,120,48,0.09);--rule:#E0DDD8;--ff-h:'Instrument Serif',Georgia,serif;--ff-b:'Barlow',system-ui,sans-serif;--ff-lbl:'Barlow Condensed',system-ui,sans-serif;font-family:var(--ff-b);color:var(--ink);background:var(--bg);}
.bh{margin:0 -30px;}
@media(max-width:1100px){.bh{margin:0 -15px;}}
.bh-wrap{max-width:1100px;margin:0 auto;padding:0 40px;}
@media(max-width:600px){.bh-wrap{padding:0 20px;}}
.bh-tag{font-family:var(--ff-lbl);font-size:0.6rem;font-weight:700;letter-spacing:0.26em;text-transform:uppercase;color:var(--accent);display:inline-flex;align-items:center;gap:10px;margin-bottom:20px;text-decoration:none;}
.bh-tag::before{content:'';display:block;width:22px;height:1px;background:var(--accent);flex-shrink:0;}
a.bh-tag:hover{color:var(--ink);}
.bh-rule{border:none;border-top:1px solid var(--rule);margin:0;}
.bh-btn{font-family:var(--ff-lbl);font-size:0.65rem;font-weight:700;letter-spacing:0.16em;text-transform:uppercase;text-decoration:none;padding:10px 20px;border:1px solid var(--ink);color:var(--ink);transition:background 0.14s,color 0.14s;display:inline-block;}
.bh-btn:hover{background:var(--ink);color:var(--bg);}
.bh-btn:visited{color:var(--ink);}
.tool-lnk{font-family:var(--ff-lbl);font-size:0.62rem;font-weight:700;letter-spacing:0.14em;text-transform:uppercase;text-decoration:none;color:var(--ink);border-bottom:1px solid var(--accent);padding-bottom:2px;transition:color 0.14s;}
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
@media(max-width:900px){.br-grid{grid-template-columns:1fr;gap:40px;}.br-sidebar{border-left:none;padding-left:0;border-top:1px solid var(--rule);padding-top:32px;}.dispatch-item{grid-template-columns:90px 1fr;}}
@media(max-width:560px){.dispatch-item{grid-template-columns:1fr;gap:3px;}.dispatch-date{font-size:0.54rem;}}
</style>

<div class="bh">
<div class="bh-wrap">

<header class="br-header">
  <span class="bh-tag">Open Binary Standard</span>
  <h1>BitLedger Protocol</h1>
  <p>A compact binary transmission protocol for double-entry financial records — encoding the balance invariant at the wire level, not as an application-layer check after the fact.</p>
</header>

<hr class="bh-rule">

<section class="br-dispatches">
  <div class="br-dispatches-head">
    <a class="bh-tag" href="/categories/releases">Releases</a>
  </div>
  {% assign rel = site.posts | where_exp: "p", "p.categories contains 'releases'" %}
  {% assign proj_posts = rel | where_exp: "p", "p.categories contains 'bitledger'" %}
  {% if proj_posts.size > 0 %}
  <ul class="dispatch-list">
    {% for post in proj_posts limit:5 %}
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

<h2>Balance is structural, not checked</h2>
<p>The foundational commitment of BitLedger: <strong>a record that does not balance cannot be encoded.</strong> This is not validation that runs when you submit. It is a property of the encoding itself. The BitLedger format cannot represent a transaction where debits and credits fail to balance — the same way a correctly designed lock cannot be opened by the wrong key. The balance invariant is structural. Every release must preserve this, and no future extension may introduce a partial-validity state where an unbalanced record might slip through.</p>

<h2>The Pacioli commitment</h2>
<p>Luca Pacioli formalized double-entry bookkeeping in 1494 as a structure in which a record cannot lie without revealing the lie. Debit and credit are not moral categories — they are structural positions. BitLedger encodes this same invariant at the binary wire level, five hundred and thirty years later. <strong>Every release of BitLedger must deepen the fidelity to this lineage, not depart from it.</strong> New features that require weakening the balance invariant, introducing optional fields that compromise structural completeness, or allowing records that require external context to validate are not compatible with this commitment.</p>

<h2>Audit trail by construction</h2>
<p>A BitLedger record preserves the complete transaction by construction. There is no separate audit log, no secondary record, no external ledger required to reconstruct what happened. The encoding is self-describing: account, amount, direction, timestamp, and the structural relationship between entries are all present in the payload. An auditor with the specification document can decode any BitLedger record without access to any external system. Every release must maintain and extend this self-describing property.</p>

<h2>Lean enough to travel anywhere</h2>
<p>Financial records must coordinate across constrained channels — satellite links, SMS, intermittent connections, air-gapped environments. BitLedger is designed so that a complete, auditable double-entry transaction can travel as a compact binary payload over any channel that carries bits. The encoding does not assume a database on either end. It does not require a persistent connection for delivery confirmation. It does not depend on a central authority to validate what was sent. Each release must be evaluated against the minimum-channel assumption: does this change make the payload larger without proportional gain in expressiveness or structural integrity?</p>

<h2>Interoperability with the double-entry ecosystem</h2>
<p>BitLedger is designed for interoperability with hledger and the broader plain-text accounting ecosystem. BitLedger encodes what hledger stores — it is a compact binary transport for records that hledger can natively represent. This relationship is a commitment: each release must maintain or improve the fidelity of the round-trip between BitLedger encoding and hledger-compatible plain-text format. <strong>BitLedger is not a replacement for plain-text accounting. It is a transport that makes those records transmissible everywhere.</strong></p>

<h2>Open standard, no custodian required</h2>
<p>BitLedger is an open standard. The specification is the standard; any developer may implement it; no license is required. The governance model follows BASICS: community review, documented migration impact for changes, explicit replacement for deprecated requirements, and public maintenance. The standard does not belong to Babb — it belongs to the community that implements and relies on it. Each release is a public document, version-controlled, with a complete changelog. No change is made silently.</p>

<div class="br-contribution">
  <h3>Contribute to BitLedger</h3>
  <p>BitLedger is a protocol standard in active development. The specification, reference implementation, and conformance suite are in the repository. The most useful contributions right now are independent implementations and interoperability testing — particularly round-trip testing between BitLedger encoding and hledger-compatible formats. If you work in fintech, accounting software, or plain-text accounting, your domain knowledge directly improves the protocol.</p>
  <p>Clone the repo, read the spec, and try to encode a real transaction. If the spec is ambiguous or incomplete for your use case, open an issue. The governance process is open to proposals for extensions that maintain the balance invariant and structural honesty commitments.</p>
  <div class="br-footnote-links">
    <a class="tool-lnk" href="https://github.com/babbworks/bitledger">GitHub →</a>
    <a class="tool-lnk" href="https://github.com/babbworks/bitledger/issues">Open an Issue →</a>
    <a class="tool-lnk" href="mailto:bitledger@babb.tel">bitledger@babb.tel</a>
  </div>
</div>

</div><!-- /br-prose -->

<div class="br-sidebar">

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Current Release</span>
    <div class="spec">
      <div class="spec-k">Version</div>
      <div class="spec-v">v0.1.0</div>
    </div>
    <div class="spec">
      <div class="spec-k">Status</div>
      <div class="spec-v">Active development · Specification published</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Releases</span>
    {% assign ann = site.posts | where_exp: "p", "p.categories contains 'bitledger' and p.title contains 'v0.1'" | first %}
    <div class="spec">
      <div class="spec-k">v0.1.0</div>
      <div class="spec-v">{% if ann %}<a href="{{ ann.url | relative_url }}">{{ ann.title }}</a>{% else %}Initial specification release{% endif %}</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Technical</span>
    <div class="spec">
      <div class="spec-k">Model</div>
      <div class="spec-v">Double-entry · balance enforced at encoding</div>
    </div>
    <div class="spec">
      <div class="spec-k">Lineage</div>
      <div class="spec-v">Pacioli 1494 → wire-level encoding</div>
    </div>
    <div class="spec">
      <div class="spec-k">Interoperability</div>
      <div class="spec-v">hledger · plain-text accounting formats</div>
    </div>
    <div class="spec">
      <div class="spec-k">Transport</div>
      <div class="spec-v">Any binary channel · constrained-network ready</div>
    </div>
    <div class="spec">
      <div class="spec-k">Conformance</div>
      <div class="spec-v">Test suite included · independently verifiable</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Related</span>
    <div class="spec">
      <div class="spec-v"><a href="/bitpads/releases">BitPads Protocol →</a></div>
    </div>
    <div class="spec">
      <div class="spec-v"><a href="/basics/releases">BASICS Standard →</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Repository</span>
    <div class="spec">
      <div class="spec-v"><a href="https://github.com/babbworks/bitledger">babbworks/bitledger →</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Contact</span>
    <div class="spec">
      <div class="spec-v"><a href="mailto:bitledger@babb.tel">bitledger@babb.tel</a></div>
    </div>
  </div>

  <a class="bh-btn" href="https://github.com/babbworks/bitledger/releases" style="margin-top:8px;">GitHub Releases →</a>

</div><!-- /br-sidebar -->

</div><!-- /br-grid -->

</div><!-- /bh-wrap -->
</div><!-- /bh -->
