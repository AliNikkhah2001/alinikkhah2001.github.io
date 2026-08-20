---
layout: page
title: loss.backward
permalink: /loss-backward/
---

<div class="loss-backward-header">
  <div class="vhs-rewind" aria-label="loss.backward - rewind to learn">
    <svg viewBox="0 0 24 24" aria-hidden="true">
      <polygon points="11,18 5,12 11,6" />
      <polygon points="22,18 16,12 22,6" />
    </svg>
  </div>
  <h1 class="loss-backward-title">loss.backward</h1>
  <p class="loss-backward-subtitle">
    A lab notebook for the practical side of AI/ML systems work. 
    Every entry dissects a production lesson—so other teams can reuse the scaffolding, not just the headlines.
  </p>
</div>

{%- assign loss_posts = site.posts | where_exp: 'post', 'post.categories contains "loss.backward"' -%}
{%- if loss_posts and loss_posts.size > 0 -%}
<ul class="archive-list">
  {%- for post in loss_posts -%}
  <li class="archive-item">
    <span class="archive-date">{{ post.date | date: site.minima.date_format | default: "%b %Y" }}</span>
    <div class="archive-entry">
      <a class="archive-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      {%- if post.excerpt -%}
      <p class="archive-excerpt">{{ post.excerpt | strip_html | truncate: 200 }}</p>
      {%- endif -%}
      {%- if post.tags -%}
      <div class="post-tags-inline">
        {%- for tag in post.tags -%}
        <span class="skill-chip">{{ tag }}</span>
        {%- endfor -%}
      </div>
      {%- endif -%}
    </div>
  </li>
  {%- endfor -%}
</ul>
{%- else -%}
<div style="text-align: center; padding: 3rem; color: rgba(255,255,255,0.5);">
  <div class="vhs-rewind" style="margin: 0 auto 1.5rem;"></div>
  <p style="font-size: 1.25rem;">No loss.backward entries published yet.</p>
  <p>Subscribe via <a href="/feed.xml">RSS</a> to get updates.</p>
</div>
{%- endif -%}