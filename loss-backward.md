---
layout: page
title: loss.backward
permalink: /loss-backward/
---

Welcome to **loss.backward**, a lab notebook dedicated to the practical side of AI/ML systems work. Every
entry dissects a production lesson—from generative voice translation to medical reporting pipelines—so other
teams can reuse the scaffolding, not just the headlines.

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
<p>No loss.backward entries have been published yet. Subscribe via the RSS feed to get updates.</p>
{%- endif -%}
