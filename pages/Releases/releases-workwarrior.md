---
layout: default
title: "Releases for Workwarrior"
permalink: /workwarrior/releases/
categories: releases workwarrior
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
  <span class="bh-tag">Flagship · Terminal-first · Open Source</span>
  <h1>Workwarrior</h1>
  <p>A unified terminal productivity environment integrating tasks, time, journals, and ledgers under a single profile system — with a natural language layer and locally-hosted browser UI.</p>
</header>

<hr class="bh-rule">

<section class="br-dispatches">
  <div class="br-dispatches-head">
    <a class="bh-tag" href="/categories/releases">Releases</a>
  </div>
  {% assign rel = site.posts | where_exp: "p", "p.categories contains 'releases'" %}
  {% assign proj_posts = rel | where_exp: "p", "p.categories contains 'workwarrior'" %}
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

<h2>The terminal is the foundation, not the ceiling</h2>
<p>Workwarrior is built on the terminal because the terminal is correct. It is the interface that survived every generation of "simpler" successors because it models the computer as it actually is: a machine that receives explicit instructions and returns deterministic output. Every release of Workwarrior must deepen this foundation — extending composability, improving scriptability, and reducing the gap between a user's intent and the command that executes it. The terminal is where we establish the data models, the discipline, and the composability that will extend outward onto every other surface.</p>

<h2>Profile isolation is inviolable</h2>
<p>Each Workwarrior profile is a completely isolated workspace: its own tasks, time tracking, journals, double-entry ledgers, and configuration. Profiles never bleed into each other. Activating a profile must never touch data from another profile — no shared state, no implicit inheritance, no exceptions. <strong>No release may weaken this guarantee.</strong> The profile system is what makes Workwarrior safe to use for multiple clients, projects, or contexts on the same machine. Isolation is the feature that makes everything else trustworthy.</p>

<h2>Composability over monolith</h2>
<p>Workwarrior orchestrates best-in-class CLI tools — Taskwarrior, Timewarrior, JRNL, Hledger, Bugwarrior — it does not replace them. Each underlying tool remains independently operable. Workwarrior's value is the coherent profile layer, the unified command surface, and the natural language translation — not a reimplementation of what these tools already do well. Every release must preserve the composability of the underlying tools and resist the temptation to abstract away what users might need to reach directly.</p>

<h2>No external dependencies for the core</h2>
<p>The Workwarrior browser UI is implemented in Python 3 standard library only — no external dependencies. The bash core uses no tools beyond what ships with a standard macOS or Linux environment. This is not a constraint imposed from outside; it is a design commitment. A tool that requires a dependency manager to install its core runtime is a fragile tool. Each release of Workwarrior must maintain a dependency-minimal core and document clearly what is required versus optional.</p>

<h2>The learning layer ships with every release</h2>
<p>Workwarrior goes beyond help documentation. The natural language processing layer — 627 compiled heuristic regex rules across 19 command domains, with a self-improving mechanism via <code>--digest</code> — is the first expression of the learning layer. Every CMD submission is logged. Every translation becomes potential training data for improved rules. <strong>Each release must advance guided understanding, not just feature count.</strong> The goal is a tool that makes its users genuinely more capable over time, not one that merely executes more commands.</p>

<h2>The terminal travels outward</h2>
<p>The rigor of the terminal — composable, scriptable, transparent, deterministic — must travel outward as Workwarrior extends to mobile devices, dedicated work screens, and consumer hardware. The intimidation factor does not travel. Each release must expand the addressable audience without compromising the depth available to power users. The browser UI at port 7777 is the first outward step. Future surfaces will follow the same contract: same data, same profile isolation, same composability. Different entry point.</p>

<div class="br-contribution">
  <h3>Contribute to Workwarrior</h3>
  <p>Workwarrior is open source, maintained in bash and Python, and actively developed. The best way to get started is to clone the repo, run the installer, create a profile, and use it for a week of real work. The gaps you encounter are the contributions that matter most. The service architecture is documented — each of the 18 major service domains is a discrete target for improvement or extension.</p>
  <p>If you have experience with Taskwarrior, JRNL, hledger, or any of the underlying tools, your domain knowledge is directly applicable. If you want to work on the browser UI, the Python stdlib implementation is straightforward. If you want to improve the NLP layer, the rule compiler and digest system are designed for contributor extension.</p>
  <div class="br-footnote-links">
    <a class="tool-lnk" href="https://github.com/babbworks/workwarrior">GitHub →</a>
    <a class="tool-lnk" href="https://github.com/babbworks/workwarrior/issues">Open an Issue →</a>
    <a class="tool-lnk" href="mailto:workwarrior@babb.tel">workwarrior@babb.tel</a>
    <a class="tool-lnk" href="https://twitter.com/workwarriortool">@workwarriortool</a>
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
      <div class="spec-v">Active development</div>
    </div>
    <div class="spec">
      <div class="spec-k">Platforms</div>
      <div class="spec-v">macOS · Linux</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Releases</span>
    {% assign ann = site.posts | where_exp: "p", "p.categories contains 'workwarrior' and p.title contains 'v0.1'" | first %}
    <div class="spec">
      <div class="spec-k">v0.1.0</div>
      <div class="spec-v">{% if ann %}<a href="{{ ann.url | relative_url }}">{{ ann.title }}</a>{% else %}Initial release{% endif %}</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Components</span>
    <div class="spec">
      <div class="spec-k">Core tools</div>
      <div class="spec-v">Taskwarrior · Timewarrior · JRNL · Hledger · Bugwarrior</div>
    </div>
    <div class="spec">
      <div class="spec-k">NLP layer</div>
      <div class="spec-v">627 heuristic rules · 19 domains · self-improving via --digest</div>
    </div>
    <div class="spec">
      <div class="spec-k">Browser UI</div>
      <div class="spec-v">Port 7777 · Python stdlib only · 15+ panels</div>
    </div>
    <div class="spec">
      <div class="spec-k">Weapons</div>
      <div class="spec-v">Gun · Sword · Next · Schedule</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Trajectory</span>
    <div class="spec">
      <div class="spec-v">Terminal → mobile → dedicated screens → consumer devices</div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Repository</span>
    <div class="spec">
      <div class="spec-v"><a href="https://github.com/babbworks/workwarrior">babbworks/workwarrior →</a></div>
    </div>
  </div>

  <div class="br-sidebar-section">
    <span class="br-sidebar-head">Contact</span>
    <div class="spec">
      <div class="spec-v"><a href="mailto:workwarrior@babb.tel">workwarrior@babb.tel</a></div>
    </div>
    <div class="spec">
      <div class="spec-v"><a href="https://twitter.com/workwarriortool">@workwarriortool</a></div>
    </div>
  </div>

  <a class="bh-btn" href="https://github.com/babbworks/workwarrior/releases" style="margin-top:8px;">GitHub Releases →</a>

</div><!-- /br-sidebar -->

</div><!-- /br-grid -->

</div><!-- /bh-wrap -->
</div><!-- /bh -->
