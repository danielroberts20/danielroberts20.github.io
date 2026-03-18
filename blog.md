---
layout: base
title: Blog
permalink: /blog/
---

<div class="page-hero">
  <div class="page-hero-inner">
    <span class="page-hero__label">Blog</span>
    <h1 class="page-hero__title">Writing</h1>
    <p class="page-hero__desc">
      Technical deep-dives, travel writing, and everything in between.
      New posts arrive via Markdown commits — which conveniently keeps the GitHub
      contribution graph alive while I'm on the road.
    </p>
  </div>
</div>

<div class="page-body">
  <div class="page-body-inner">

    {% assign technical_posts = site.posts | where_exp: "post", "post.categories contains 'Technical'" %}
    {% assign travel_posts = site.posts | where_exp: "post", "post.categories contains 'Travel'" %}

    {% if technical_posts.size > 0 %}
    <div style="margin-bottom: var(--space-2xl);">
      <h2 style="font-size:1rem; font-family: var(--font-mono); color: var(--accent); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: var(--space-xl); font-weight:400;">Technical</h2>
      <div class="post-list">
        {% for post in technical_posts %}
        <a href="{{ post.url | relative_url }}" class="post-card{% if post.image %} post-card--has-thumb{% endif %}">
          <span class="post-card__date">{{ post.date | date: "%b %Y" }}</span>
          {% if post.image %}
            <img src="{{ post.image | relative_url }}" alt="{{ post.title }}" class="post-card__thumb">
          {% endif %}
          <div>
            <span class="post-card__category post-category--technical">Technical</span>
            <h3 class="post-card__title">{{ post.title }}</h3>
            <p class="post-card__excerpt">{{ post.excerpt | strip_html | truncate: 180 }}</p>
          </div>
        </a>
        {% endfor %}
      </div>
    </div>
    {% endif %}

    {% if travel_posts.size > 0 %}
    <div style="margin-bottom: var(--space-2xl);">
      <h2 style="font-size:1rem; font-family: var(--font-mono); color: var(--warm); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: var(--space-xl); font-weight:400;">Travel</h2>
      <div class="post-list">
        {% for post in travel_posts %}
        <a href="{{ post.url | relative_url }}" class="post-card{% if post.image %} post-card--has-thumb{% endif %}">
          <span class="post-card__date">{{ post.date | date: "%b %Y" }}</span>
          {% if post.image %}
            <img src="{{ post.image | relative_url }}" alt="{{ post.title }}" class="post-card__thumb">
          {% endif %}
          <div>
            <span class="post-card__category post-category--travel">Travel</span>
            <h3 class="post-card__title">{{ post.title }}</h3>
            <p class="post-card__excerpt">{{ post.excerpt | strip_html | truncate: 180 }}</p>
          </div>
        </a>
        {% endfor %}
      </div>
    </div>
    {% endif %}

    {% if site.posts.size == 0 %}
    <p style="color: var(--text-muted); font-family: var(--font-mono); font-size: 0.85rem;">
      First post coming before June 2026.
    </p>
    {% endif %}

  </div>
</div>
