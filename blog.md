---
layout: page
title: Blog
permalink: /blog/
---

I'm a **machine learning researcher / engineer** documenting applied AI experiments, reproducible evaluation harnesses, and ongoing collaborations. The **loss.backward** notebook anchors this feed, but every publication—project retrospectives, research notes, and product essays—lives here with live tag filtering so you can focus on the topics you care about most.

Exploring similar territory or running a lab that aligns with this work? I'm actively seeking master's/PhD roles and co-authorship opportunities, so feel free to [reach out](/contact/) after browsing.

{%- assign all_tags = site.tags | sort -%}
{%- if all_tags and all_tags.size > 0 -%}
<section class="blog-tags">
  <h2>Tags</h2>
  <div class="tag-filters" role="group" aria-label="Filter posts by tag">
    <button class="tag-filter is-active" data-tag="all" type="button">All topics</button>
    {%- for tag in all_tags -%}
    <button class="tag-filter" data-tag="{{ tag[0] }}" type="button">{{ tag[0] }}</button>
    {%- endfor -%}
  </div>
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
  <article class="post-card post-card--full" data-tags="{%- if post.tags -%}{{ post.tags | join: '|' }}{%- endif -%}">
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
<p class="blog-empty" hidden>No posts match that tag yet. Try another filter.</p>
{%- else -%}
<p>No essays have been published yet. Subscribe via RSS to get notified when new posts land.</p>
{%- endif -%}

<div class="resume-card">
  <p>Want only the AI/ML field notes? Visit the dedicated loss.backward archive.</p>
  <a class="btn btn-primary" href="{{ '/loss-backward/' | relative_url }}">Open loss.backward</a>
</div>

<script>
  (function() {
    const filters = document.querySelectorAll('.tag-filter');
    const posts = document.querySelectorAll('.blog-roll .post-card');
    const emptyState = document.querySelector('.blog-empty');

    if (!filters.length || !posts.length) {
      return;
    }

    function applyFilter(tag) {
      let visibleCount = 0;
      posts.forEach((card) => {
        const tags = (card.dataset.tags || '').split('|').filter(Boolean);
        const matches = tag === 'all' || tags.includes(tag);
        card.classList.toggle('is-hidden', !matches);
        if (matches) {
          visibleCount += 1;
        }
      });

      if (emptyState) {
        emptyState.hidden = visibleCount > 0;
      }
    }

    filters.forEach((button) => {
      button.addEventListener('click', () => {
        filters.forEach((btn) => btn.classList.remove('is-active'));
        button.classList.add('is-active');
        applyFilter(button.dataset.tag);
      });
    });

    applyFilter('all');
  })();
</script>
