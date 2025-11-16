---
layout: page
title: Writing
permalink: /writing/
---

Welcome to the public notebook. Essays from the **loss.backward** series appear alongside broader speaking notes
<<<<<<< HEAD
and research summaries. Prefer a tag-first browsing experience? Visit the [blog index]({{ '/blog/' | relative_url }}) or dive
straight into the [loss.backward archive]({{ '/loss-backward/' | relative_url }}).
=======
and research summaries. Subscribe via RSS or jump straight into the [loss.backward archive]({{ '/loss-backward/' | relative_url }})
if you only want the applied AI/ML dispatches.
>>>>>>> main

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
<<<<<<< HEAD
      {%- if post.tags -%}
      <div class="post-tags-inline">
        {%- for tag in post.tags -%}
        <span class="skill-chip">{{ tag }}</span>
        {%- endfor -%}
      </div>
      {%- endif -%}
=======
>>>>>>> main
    </div>
  </li>
  {%- endfor -%}
</ul>
{%- else -%}
<p>No posts have been published yet. New writing will appear here soon.</p>
{%- endif -%}
