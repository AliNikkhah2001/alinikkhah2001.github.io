---
layout: page
title: loss.backward
permalink: /loss-backward/
---

<div class="loss-backward-header">
  <h1 class="loss-backward-title"><span class="prompt">$</span> loss.backward()</h1>
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
<div class="loss-backward-header">
  <p class="loss-backward-subtitle">No loss.backward entries published yet.</p>
  <p class="loss-backward-subtitle">Subscribe via <a href="/feed.xml">RSS</a> to get updates.</p>
</div>
{%- endif -%}
