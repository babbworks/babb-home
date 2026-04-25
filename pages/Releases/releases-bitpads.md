---
layout: default
title: "Releases for BitPads Protocol"
permalink: /bitpads/releases/
categories: releases bitpads
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
  <h1>BitPads Protocol</h1>
  <p>A compact binary encoding standard for job records — optimized for constrained transmission channels including SMS, satellite links, KaiOS feature phones, and low-bandwidth field operations.</p>
</header>

<hr class="bh-rule">

<section class="br-dispatches">
  <div class="br-dispatches-head">
    <a class="bh-tag" href="/categories/releases">Releases</a>
  </div>
  {% assign rel = site.posts | where_exp: "p", "p.categories contains 'releases'" %}
  {% assign proj_posts = rel | where_exp: "p", "p.categories contains 'bitpads'" %}
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

<h2>Every bit must earn its place</h2>
<p>The minimum wire footprint is a hard commitment, not a preference. BitPads encoding is designed to carry the full PADS job record — Processes, Actions, Details, Story — in a payload that travels as a standard SMS message. <strong>No field is included by default that is not required for reconstruction.</strong> Every release of BitPads must be evaluated against this constraint: does any change increase the minimum payload size? If so, the change requires explicit justification and must be weighed against the cost to the lowest-bandwidth use case.</p>

<h2>Structural honesty at the wire level</h2>
<p>A malformed BitPads record cannot be encoded. This is a property of the format, not a validator that runs at application layer. The encoding enforces the structural constraints of the PADS model by construction: a record missing required fields does not produce a partial encoding — it does not produce an encoding at all. Every release must preserve this property. Adding fields or extending the schema must never introduce partial-validity states where a record can be encoded but not safely decoded.</p>

<h2>The Baudot inheritance</h2>
<p>BitPads reclaims three upper bits of the C0 control character space that Baudot established in 1870 and every subsequent standard has left unclaimed. This is not a historical curiosity — it is a structural pocket mathematically guaranteed by the five-bit constraint that has governed every binary communication standard from telegraph code through ASCII to Unicode control characters. <strong>The BitPads Enhancement Grammar defines the occupancy of this space and owns it forward.</strong> Each release must document any extension to the Enhancement Grammar with full justification for why it belongs in this reserved pocket.</p>

<h2>Transport agnosticism</h2>
<p>BitPads payloads are designed to travel over any binary channel: SMS, IP, satellite, serial, or any future transport. The protocol makes no assumptions about the channel it traverses. It does not assume packet ordering, reliable delivery, or low latency. It does not assume the sender and receiver share a data connection. It assumes only that bits can be transmitted and that the receiver can decode them. Every release must test against this minimum transport assumption, not against the most convenient modern network.</p>

<h2>Open standard, freely implementable</h2>
<p>BitPads is an open standard under the same governance model as BASICS — no license fees, no platform dependency, no proprietary encoding. The specification is the standard; the reference implementation demonstrates it. Any developer may implement BitPads encoding and decoding independently, and those implementations are equally valid BitPads implementations if they conform to the specification. <strong>Conformance is verifiable, not claimed.</strong> Each release ships a conformance test suite that any implementation can run.</p>

<div class="br-contribution">
  <h3>Contribute to BitPads</h3>
  <p>BitPads is an open protocol standard. The specification document, reference implementation, and conformance suite are all in the repository. The most valuable contributions are independent implementations: if you build a BitPads encoder or decoder in any language and run it against the conformance suite, you are doing the work that validates the standard. Gaps in the spec that only manifest when implementing from scratch are the most important gaps to find.</p>
  <p>Clone the repo, read the spec, write an encoder, run the tests. If something does not make sense, open an issue. If something is missing, open a PR. The Enhancement Grammar extension process is documented — proposals for new usage of the C0 space go through that process.</p>
  <div class="br-footnote-links">
    <a class="tool-lnk" href="https://github.com/babbworks/bitpads">GitHub →</a>
    <a class="tool-lnk" href="https://github.com/babbworks/bitpads/issues">Open an Issue →</a>
    <a class="tool-lnk" href="mailto:bitpads@babb.tel">bitpads@babb.tel</a>
    <a class="tool-lnk" href="https://twitter.com/bitpads">@bitpads</a>
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
    <div class="spec">
      <div class="spec-k">Application layer</div>
      <div class="spec-v"><a href="/workpads/releases">Workpads →</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Releases</span>
    {% assign ann = site.posts | where_exp: "p", "p.categories contains 'bitpads' and p.title contains 'v0.1'" | first %}
    <div class="spec">
      <div class="spec-k">v0.1.0</div>
      <div class="spec-v">{% if ann %}<a href="{{ ann.url | relative_url }}">{{ ann.title }}</a>{% else %}Initial specification release{% endif %}</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Technical</span>
    <div class="spec">
      <div class="spec-k">Encoding</div>
      <div class="spec-v">Compact binary · SMS-transportable</div>
    </div>
    <div class="spec">
      <div class="spec-k">Heritage</div>
      <div class="spec-v">Baudot C0 Enhancement Grammar · five-bit constraint lineage</div>
    </div>
    <div class="spec">
      <div class="spec-k">Transport</div>
      <div class="spec-v">SMS · IP · satellite · any binary channel</div>
    </div>
    <div class="spec">
      <div class="spec-k">Conformance</div>
      <div class="spec-v">Test suite included · independently verifiable</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Repository</span>
    <div class="spec">
      <div class="spec-v"><a href="https://github.com/babbworks/bitpads">babbworks/bitpads →</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Contact</span>
    <div class="spec">
      <div class="spec-v"><a href="mailto:bitpads@babb.tel">bitpads@babb.tel</a></div>
    </div>
    <div class="spec">
      <div class="spec-v"><a href="https://twitter.com/bitpads">@bitpads</a></div>
    </div>
  </div>

  <a class="bh-btn" href="https://github.com/babbworks/bitpads/releases" style="margin-top:8px;">GitHub Releases →</a>

</div><!-- /br-sidebar -->

</div><!-- /br-grid -->

</div><!-- /bh-wrap -->
</div><!-- /bh -->
