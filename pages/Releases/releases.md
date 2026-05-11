---
layout: default
title: Releases
permalink: /releases
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
.spec{display:flex;flex-direction:column;gap:3px;margin-bottom:20px;}
.spec-k{font-family:var(--ff-lbl);font-size:0.56rem;font-weight:700;letter-spacing:0.22em;text-transform:uppercase;color:var(--ink-4);}
.spec-v{font-family:var(--ff-b);font-size:0.82rem;color:var(--ink-2);line-height:1.55;}
.spec-v a{color:var(--accent);text-decoration:none;}
.spec-v a:hover{text-decoration:underline;}

/* Hub page layout */
.rel-header{padding:56px 0 48px;}
.rel-header h1{font-family:var(--ff-h);font-size:clamp(2.2rem,5vw,3.6rem);font-weight:400;color:var(--ink);margin:0 0 16px;line-height:1.08;}
.rel-header p{font-family:var(--ff-b);font-size:1rem;color:var(--ink-3);line-height:1.7;max-width:580px;margin:0;}

.rel-grid{display:grid;grid-template-columns:1fr 300px;gap:72px;padding:52px 0 80px;align-items:start;}

/* Left: dispatches + note */
.rel-dispatches-head{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:20px;}
.rel-note{margin-top:36px;font-family:var(--ff-b);font-size:0.85rem;color:var(--ink-3);line-height:1.75;}
.rel-note strong{font-weight:600;color:var(--ink-2);}

/* Right: project sidebar */
.rel-sidebar{border-left:1px solid var(--rule);padding-left:36px;}
.rel-proj{margin-bottom:32px;padding-bottom:28px;border-bottom:1px solid var(--rule);}
.rel-proj:last-child{border-bottom:none;margin-bottom:0;}
.rel-proj-name{font-family:var(--ff-h);font-size:1rem;font-weight:400;color:var(--ink);margin:0 0 10px;}
.rel-proj-tag{font-family:var(--ff-lbl);font-size:0.54rem;font-weight:700;letter-spacing:0.18em;text-transform:uppercase;color:var(--ink-4);margin-bottom:8px;display:block;}
.rel-proj-links{display:flex;flex-direction:column;gap:6px;}
.rel-proj-link{font-family:var(--ff-b);font-size:0.8rem;color:var(--ink-3);text-decoration:none;transition:color 0.14s;padding:4px 0;border-bottom:1px solid var(--rule);}
.rel-proj-link:last-child{border-bottom:none;}
.rel-proj-link:hover{color:var(--accent);}
.rel-proj-link:visited{color:var(--ink-3);}
.rel-proj-link .rel-arrow{color:var(--accent);font-size:0.7em;margin-left:4px;}

@media(max-width:900px){
  .rel-grid{grid-template-columns:1fr;gap:48px;}
  .rel-sidebar{border-left:none;padding-left:0;border-top:1px solid var(--rule);padding-top:36px;}
  .dispatch-item{grid-template-columns:90px 1fr;}
}
@media(max-width:560px){
  .dispatch-item{grid-template-columns:1fr;gap:3px;}
  .dispatch-date{font-size:0.54rem;}
}
</style>

<div class="bh">
<div class="bh-wrap">

<header class="rel-header">
  <span class="bh-tag">Babb Works</span>
  <h1>Releases</h1>
  <p>Versioned releases for every Babb tool and protocol. Each project maintains a dedicated release page with version history, technical commitments, and contribution information.</p>
</header>

<hr class="bh-rule">

<div class="rel-grid">

  <!-- Left: recent releases dispatches -->
  <div>
    <div class="rel-dispatches-head">
      <a class="bh-tag" href="/categories/releases">Release Dispatches</a>
    </div>

    {% assign releases_posts = site.posts | where_exp: "p", "p.categories contains 'releases'" %}
    {% if releases_posts.size > 0 %}
    <ul class="dispatch-list">
      {% for post in releases_posts limit:5 %}
      <li class="dispatch-item">
        <span class="dispatch-date">{{ post.date | date: "%b %d, %Y" }}</span>
        <a class="dispatch-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
      {% endfor %}
    </ul>
    <div style="margin-top:14px;">
      <a class="tool-lnk" href="/categories/releases">All release dispatches →</a>
    </div>
    {% else %}
    <p style="font-family:var(--ff-b);font-size:0.85rem;color:var(--ink-4);font-style:italic;padding:12px 0;border-top:1px solid var(--rule);">No release dispatches yet.</p>
    {% endif %}

    <div class="rel-note">
      <p><strong>On versioning.</strong> All Babb tools and protocols follow semantic versioning. The v0.x series indicates active development with a stable commitment to backward-compatible rule identifiers within each minor series. Breaking changes increment the major version and are announced with migration guides. Releases below v1.0 are production-ready for early adopters and contributors — they are not experimental.</p>
      <p>Critical updates — security, data integrity, or protocol breaking changes — will be noted on this page directly. All other updates are posted to the individual project release pages and announced as dispatches.</p>
    </div>
  </div>

  <!-- Right: project links sidebar -->
  <div class="rel-sidebar">

    <div class="rel-proj">
      <span class="rel-proj-tag">Standard</span>
      <h3 class="rel-proj-name">BASICS Standard</h3>
      <div class="rel-proj-links">
        <a class="rel-proj-link" href="/basics/releases">Release page</a>
        <a class="rel-proj-link" href="https://github.com/babbworks/basics-standard/releases">GitHub Releases <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://github.com/babbworks/basics-standard">Repository <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://basics.babb.tel">Standard site <span class="rel-arrow">↗</span></a>
      </div>
    </div>

    <div class="rel-proj">
      <span class="rel-proj-tag">Application</span>
      <h3 class="rel-proj-name">Workpads</h3>
      <div class="rel-proj-links">
        <a class="rel-proj-link" href="/workpads/releases">Release page</a>
        <a class="rel-proj-link" href="https://github.com/babbworks/workpads/releases">GitHub Releases <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://github.com/babbworks/workpads">Repository <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://workpads.babb.tel">Standard site <span class="rel-arrow">↗</span></a>
      </div>
    </div>

    <div class="rel-proj">
      <span class="rel-proj-tag">Application</span>
      <h3 class="rel-proj-name">Workwarrior</h3>
      <div class="rel-proj-links">
        <a class="rel-proj-link" href="/workwarrior/releases">Release page</a>
        <a class="rel-proj-link" href="https://github.com/babbworks/workwarrior/releases">GitHub Releases <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://github.com/babbworks/workwarrior">Repository <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://workwarrior.babb.tel">Standard site <span class="rel-arrow">↗</span></a>
      </div>
    </div>

    <div class="rel-proj">
      <span class="rel-proj-tag">Binary Protocol</span>
      <h3 class="rel-proj-name">BitPads</h3>
      <div class="rel-proj-links">
        <a class="rel-proj-link" href="/bitpads/releases">Release page</a>
        <a class="rel-proj-link" href="https://github.com/babbworks/bitpads/releases">GitHub Releases <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://github.com/babbworks/bitpads">Repository <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://bitpads.babb.tel">Standard site <span class="rel-arrow">↗</span></a>
      </div>
    </div>

    <div class="rel-proj">
      <span class="rel-proj-tag">Binary Protocol</span>
      <h3 class="rel-proj-name">BitLedger</h3>
      <div class="rel-proj-links">
        <a class="rel-proj-link" href="/bitledger/releases">Release page</a>
        <a class="rel-proj-link" href="https://github.com/babbworks/bitledger/releases">GitHub Releases <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://github.com/babbworks/bitledger">Repository <span class="rel-arrow">↗</span></a>
        <a class="rel-proj-link" href="https://bitledger.babb.tel">Standard site <span class="rel-arrow">↗</span></a>
      </div>
    </div>

  </div><!-- /rel-sidebar -->

</div><!-- /rel-grid -->

</div><!-- /bh-wrap -->
</div><!-- /bh -->
