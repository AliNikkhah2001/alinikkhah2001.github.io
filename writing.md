---
layout: page
title: Writing
permalink: /writing/
---

Welcome to the public notebook. Essays from the **loss.backward** series appear alongside broader speaking notes
and research summaries. Subscribe via RSS or jump straight into the [loss.backward archive]({{ '/loss-backward/' | relative_url }})
if you only want the applied AI/ML dispatches.

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
