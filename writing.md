---
layout: page
title: Writing
permalink: /writing/
---

Welcome to a curated log of essays, build notes, and speaking material. Each entry below links to the full article.

{%- if site.posts and site.posts.size > 0 -%}
<ul class="archive-list">
  {%- for post in site.posts -%}
  <li class="archive-item">
    <span class="archive-date">{{ post.date | date: site.minima.date_format | default: "%b %Y" }}</span>
    <div class="archive-entry">
      <a class="archive-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      {%- if post.excerpt -%}
      <p class="archive-excerpt">{{ post.excerpt | strip_html | truncate: 160 }}</p>
      {%- endif -%}
    </div>
  </li>
  {%- endfor -%}
</ul>
{%- else -%}
<p>No posts have been published yet. New writing will appear here soon.</p>
{%- endif -%}
