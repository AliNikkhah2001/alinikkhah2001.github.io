---
layout: home
title: "Ali Nikkhah"
hero:
  eyebrow: "Applied ML architect"
  lede: >-
    I design agentic, multi-modal systems that translate frontier research into resilient,
    production-grade products. My work spans retrieval-augmented generation, high-volume content
    moderation, and ML platform governance for regulated marketplaces.
  actions:
    - label: "Email me"
      href: "mailto:alinkkh9@gmail.com"
      style: primary
    - label: "Download CV"
      href: "/assets/cv.pdf"
      style: ghost
      new_tab: true
  meta:
    - label: "Location"
      detail: "Tehran — Remote-first"
    - label: "Expertise"
      detail: "Agentic ML · Multimodal Systems · MLOps"
    - label: "Availability"
      detail: "Consulting & fractional leadership"
focus: >-
  I partner with founding teams and enterprises to shape the end-to-end lifecycle of intelligent products:
  from discovery and model research through to deployment, alignment, observability, and governance.
  I specialise in orchestrating pipelines that autonomously generate, moderate, and enrich millions of
  listings in real time while staying compliant with multilingual and multi-market regulations.
capabilities:
  - title: "Systems & Platforms"
    items:
      - "Kubernetes, Argo Workflows, and Terraform-first infrastructure"
      - "MLflow, Weights & Biases, and feature stores for lineage"
      - "Realtime retrieval & evaluation harnesses for RAG agents"
  - title: "Applied Research"
    items:
      - "Multimodal representation learning and diffusion pipelines"
      - "Vision-language governance for sensitive content"
      - "Prompt engineering and tool-use agents for ops automation"
  - title: "Leadership"
    items:
      - "Fractional head-of-ML engagements and mentorship"
      - "Cross-functional program design with legal & product"
      - "Scaling experimentation, review boards, and reliability SLAs"
experience:
  - period: "Sep 2025 – Nov 2025"
    role: "Senior Data Scientist"
    org: "Turquoise Digital"
    body: "Directed AI initiatives for retail clients, shipping multilingual recommendation engines and audit-ready monitoring stacks."
  - period: "May 2025 – Nov 2025"
    role: "Machine Learning Researcher"
    org: "Trinity College Dublin"
    body: "Built emotion-aware speech translation models and multimodal perception agents for healthcare communication."
  - period: "Feb 2024 – Nov 2025"
    role: "Research Assistant"
    org: "University of British Columbia"
    body: "Automated ultrasound-report drafting with retrieval-augmented vision-language models integrated into clinician workflows."
  - period: "Jan 2025 – Aug 2025"
    role: "AI Engineering R/D Lead"
    org: "Digikala"
    body: "Architected modular control pipelines, guardrails, and retrieval layers for e-commerce listing intelligence."
education:
  - school: "Sharif University of Technology"
    credential: "B.Sc. Electrical & Electronics Engineering"
    years: "2020 – 2024"
  - school: "Atomic Energy High School"
    credential: "Mathematics Diploma"
    years: "2017 – 2019"
languages:
  - name: "Persian"
    detail: "Native"
  - name: "English"
    detail: "Native/Bilingual"
  - name: "Arabic"
    detail: "Professional"
  - name: "French"
    detail: "Limited working"
  - name: "German"
    detail: "Limited working"
  - name: "Latin"
    detail: "Elementary"
certifications:
  - "Introduction to Machine Learning in Production"
  - "Building Systems with the ChatGPT API"
  - "ChatGPT Prompt Engineering for Developers"
  - "Diffusion Models"
  - "Project-Oriented Course in Web Development with PHP"
contact_links:
  - label: "Email"
    href: "mailto:alinkkh9@gmail.com"
    text: "alinkkh9@gmail.com"
  - label: "LinkedIn"
    href: "https://www.linkedin.com/in/alinikkhah2001/"
    text: "linkedin.com/in/alinikkhah2001"
    new_tab: true
  - label: "GitHub"
    href: "https://github.com/AliNikkhah2001"
    text: "github.com/AliNikkhah2001"
    new_tab: true
---
{%- assign hero = page.hero -%}
<div class="folio-hero">
  <div class="hero-text">
    {%- if hero.eyebrow -%}
    <p class="hero-eyebrow">{{ hero.eyebrow }}</p>
    {%- endif -%}
    <h1 class="hero-title">{{ page.title }}</h1>
    {%- if hero.lede -%}
    <p class="hero-lede">{{ hero.lede }}</p>
    {%- endif -%}
    {%- if hero.actions -%}
    <div class="hero-actions">
      {%- for action in hero.actions -%}
      <a class="btn btn-{{ action.style | default: 'ghost' }}" href="{{ action.href }}"{% if action.new_tab %} target="_blank" rel="noopener"{% endif %}>{{ action.label }}</a>
      {%- endfor -%}
    </div>
    {%- endif -%}
  </div>
  {%- if hero.meta -%}
  <ul class="hero-meta">
    {%- for item in hero.meta -%}
    <li>{{ item.label }}<span>{{ item.detail }}</span></li>
    {%- endfor -%}
  </ul>
  {%- endif -%}
</div>

<section class="folio-section" id="focus">
  <h2 class="section-title">Focus</h2>
  <p>{{ page.focus }}</p>
</section>

{%- if page.capabilities -%}
<section class="folio-section" id="capabilities">
  <h2 class="section-title">Capabilities</h2>
  <div class="folio-columns">
    {%- for block in page.capabilities -%}
    <article class="folio-panel">
      <h3>{{ block.title }}</h3>
      <ul class="folio-list">
        {%- for item in block.items -%}
        <li>{{ item }}</li>
        {%- endfor -%}
      </ul>
    </article>
    {%- endfor -%}
  </div>
</section>
{%- endif -%}

{%- if page.experience -%}
<section class="folio-section" id="experience">
  <h2 class="section-title">Recent Experience</h2>
  <ol class="timeline">
    {%- for entry in page.experience -%}
    <li class="timeline-item">
      <p class="timeline-period">{{ entry.period }}</p>
      <h3 class="timeline-role">{{ entry.role }}</h3>
      <p class="timeline-org">{{ entry.org }}</p>
      <p class="timeline-body">{{ entry.body }}</p>
    </li>
    {%- endfor -%}
  </ol>
  <div class="resume-card">
    <p>Need the full record? Download the full CV for publications, talks, and advisory work.</p>
    <a class="btn btn-primary" href="{{ '/assets/cv.pdf' | relative_url }}" target="_blank" rel="noopener">Download the CV</a>
  </div>
</section>
{%- endif -%}

{%- if page.education -%}
<section class="folio-section" id="education">
  <h2 class="section-title">Education</h2>
  <div class="folio-columns">
    {%- for edu in page.education -%}
    <article class="folio-panel">
      <h3>{{ edu.school }}</h3>
      <p><strong>{{ edu.credential }}</strong><br />{{ edu.years }}</p>
    </article>
    {%- endfor -%}
  </div>
</section>
{%- endif -%}

{%- if page.languages or page.certifications -%}
<section class="folio-section" id="languages">
  <h2 class="section-title">Languages & Certifications</h2>
  <div class="folio-columns">
    {%- if page.languages -%}
    <article class="folio-panel">
      <h3>Languages</h3>
      <ul class="folio-list">
        {%- for lang in page.languages -%}
        <li>{{ lang.name }} &mdash; {{ lang.detail }}</li>
        {%- endfor -%}
      </ul>
    </article>
    {%- endif -%}
    {%- if page.certifications -%}
    <article class="folio-panel">
      <h3>Certifications</h3>
      <ul class="folio-list">
        {%- for cert in page.certifications -%}
        <li>{{ cert }}</li>
        {%- endfor -%}
      </ul>
    </article>
    {%- endif -%}
  </div>
</section>
{%- endif -%}

<section class="folio-section" id="writing">
  <h2 class="section-title">Latest Writing</h2>
  {%- if site.posts and site.posts.size > 0 -%}
  <ol class="folio-posts">
    {%- for post in site.posts limit: 4 -%}
    <li class="folio-post">
      <article class="post-card">
        <p class="post-meta">{{ post.date | date: site.minima.date_format | default: "%b %Y" }}</p>
        <h3 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
        {%- if post.excerpt -%}
        <p class="post-summary">{{ post.excerpt | strip_html | truncate: 140 }}</p>
        {%- endif -%}
      </article>
    </li>
    {%- endfor -%}
  </ol>
  <p class="folio-cta"><a class="btn btn-ghost" href="{{ '/writing/' | relative_url }}">View the full archive</a></p>
  {%- else -%}
  <p class="folio-cta">Essays and notes will appear here soon. Stay tuned!</p>
  {%- endif -%}
</section>

{%- if page.contact_links -%}
<section class="folio-section" id="contact">
  <h2 class="section-title">Contact</h2>
  <ul class="contact-grid">
    {%- for link in page.contact_links -%}
    <li><span>{{ link.label }}</span><a href="{{ link.href }}"{% if link.new_tab %} target="_blank" rel="noopener"{% endif %}>{{ link.text }}</a></li>
    {%- endfor -%}
  </ul>
</section>
{%- endif -%}
