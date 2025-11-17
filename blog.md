---
layout: page
title: Blog
permalink: /blog/
---

The **loss.backward** notebook anchors this blog, but every publication—project retrospectives, research notes,
and product essays—lives here with tags so readers can jump straight to the topics they care about.

{%- assign all_tags = site.tags | sort -%}
{%- if all_tags and all_tags.size > 0 -%}
<section class="blog-tags">
  <h2>Tags</h2>
  <ul class="tag-cloud">
    {%- for tag in all_tags -%}
    <li>
      <span class="skill-chip">{{ tag[0] }}</span>
      <span class="tag-count">{{ tag[1].size }} posts</span>
    </li>
    {%- endfor -%}
  </ul>
</section>
{%- endif -%}

{%- if site.posts and site.posts.size > 0 -%}
<section class="blog-roll">
  {%- for post in site.posts -%}
  <article class="post-card post-card--full">
    <p class="post-meta">{{ post.date | date: site.minima.date_format | default: "%b %Y" }}</p>
    <h2 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h2>
    {%- if post.categories and post.categories.size > 0 -%}
    <p class="post-taxonomy">Categories: {{ post.categories | join: ', ' }}</p>
    {%- endif -%}
    {%- if post.excerpt -%}
    <p class="post-summary">{{ post.excerpt | strip_html | truncate: 200 }}</p>
    {%- endif -%}
    {%- if post.tags -%}
    <div class="post-tags-inline">
      {%- for tag in post.tags -%}
      <span class="skill-chip">{{ tag }}</span>
      {%- endfor -%}
    </div>
    {%- endif -%}
  </article>
  {%- endfor -%}
</section>
{%- else -%}
<p>No essays have been published yet. Subscribe via RSS to get notified when new posts land.</p>
{%- endif -%}

<div class="resume-card">
  <p>Want only the AI/ML field notes? Visit the dedicated loss.backward archive.</p>
  <a class="btn btn-primary" href="{{ '/loss-backward/' | relative_url }}">Open loss.backward</a>
</div>
