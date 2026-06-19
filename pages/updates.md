---
layout: updates
title: Updates
permalink: /updates/
nav_active: updates
---

<div class="shell">

  <section class="ttl">
    <div>
      <h1>Updates<span class="punct">.</span></h1>
      <p class="dek">Dispatches, field reports, editor&rsquo;s notes &mdash; everything from the working world and the product company building for it.</p>
    </div>
    <div>
      <div class="subscribe">
        <h4>Subscribe</h4>
        <ul>
          <li><a href="/feed.xml">All updates &middot; RSS</a><span>↪</span></li>
          <li><a href="/feed.xml?cat=places">Places &middot; RSS</a><span>↪</span></li>
          <li><a href="/feed.xml?cat=workpads">Workpads &middot; RSS</a><span>↪</span></li>
          <li><a href="/updates/email/">Email digest</a><span>weekly</span></li>
        </ul>
      </div>
    </div>
  </section>

  <div class="toolstrip">
    <div class="group">
      <input type="search" placeholder="Search updates&hellip;" aria-label="Search" />
    </div>
    <div class="group">
      <span class="lbl">Filter</span>
      <div class="pill-row">
        <button data-tag="all" aria-pressed="true">All</button>
        <button data-tag="dispatch">Dispatch</button>
        <button data-tag="workpads">Workpads</button>
        <button data-tag="places">Places</button>
        <button data-tag="notes">Editor&rsquo;s notes</button>
      </div>
    </div>
  </div>

  {% assign previews = site.posts | slice: 0, 2 %}
  <section class="feat-row" style="margin-bottom:24px">
    {% for post in previews %}
    <a class="fcard" href="{{ post.url | relative_url }}" data-tags="{{ post.tags | join: ',' }}{% if post.product %},{{ post.product }}{% endif %}">
      <div class="cover"></div>
      <div class="body">
        <div class="kicker">{{ post.product | default: post.tags | first | default: "Update" | capitalize }}</div>
        <h4>{{ post.title }}</h4>
        {% if post.excerpt %}<p class="blurb">{{ post.excerpt | strip_html | truncate: 220 }}</p>{% endif %}
        <div class="meta">
          <span>{{ post.date | date: "%Y-%m-%d" }}</span>
          {% if post.product %}<span class="tag" data-product="{{ post.product }}">{{ post.product }}</span>{% endif %}
        </div>
      </div>
    </a>
    {% endfor %}
  </section>

  <section class="rail-list">
    {% for post in site.posts offset:2 %}
    <div class="urow" data-tags="{{ post.tags | join: ',' }}{% if post.product %},{{ post.product }}{% endif %}">
      <div class="ts"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time></div>
      <div class="body">
        <div class="kicker">{{ post.product | default: post.tags | first | default: "Update" | capitalize }}</div>
        <h4><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h4>
        {% if post.excerpt %}<p class="blurb">{{ post.excerpt | strip_html | truncate: 160 }}</p>{% endif %}
      </div>
      <div class="meta">
        {% if post.product %}<span class="tag" data-product="{{ post.product }}">{{ post.product }}</span>{% endif %}
        {% for tag in post.tags limit:2 %}{% unless tag == post.product %}<span class="tag" data-product="{{ tag }}">{{ tag }}</span>{% endunless %}{% endfor %}
      </div>
    </div>
    {% endfor %}
  </section>

  <div class="rail-foot">
    <span>{{ site.posts | size }} updates total</span>
    {% if paginator.total_pages > 1 %}
    <div style="display:flex;gap:18px;">
      {% if paginator.previous_page %}<a href="{{ paginator.previous_page_path | relative_url }}">&larr; Newer</a>{% endif %}
      {% if paginator.next_page %}<a href="{{ paginator.next_page_path | relative_url }}">Older &rarr;</a>{% endif %}
    </div>
    {% endif %}
  </div>

</div>
