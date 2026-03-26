---
layout: home
title: Home
---

<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-glow"></div>
  <div class="hero-inner">
    <div class="hero-left">
      <p class="hero-eyebrow">Dan Roberts</p>
      <h1 class="hero-title">Data scientist,<br><em>traveller</em>,<br>lifeguard.</h1>
      <p class="hero-bio">
        CS graduate building a 3-year personal data science project from the road.
        Currently hardening TravelNet — a live system collecting location, health and
        financial data across 9 countries — before departure in June 2026.
      </p>
      {% assign today = 'now' | date: "%Y-%m-%d" %}
      {% assign current_status = site.data.site.status_schedule[0] %}
      {% for entry in site.data.site.status_schedule %}
        {% if entry.from <= today %}
          {% assign current_status = entry %}
        {% endif %}
      {% endfor %}
      <div class="hero-status">
        <span class="hero-status__dot"></span>
        {{ current_status.pill }}
      </div>
      <div class="hero-ctas">
        <a href="/projects/" class="btn btn--primary">View Projects</a>
        <a href="/about/" class="btn btn--secondary">About Me</a>
      </div>
    </div>
    {% include hero-panel.html %}
  </div>
</section>

<!-- Featured Projects -->
<section class="home-section">
  <div class="home-section-inner">
    <div class="home-section-header">
      <div class="home-section-header__text">
        <span class="section-label">Projects</span>
        <h2 class="section-title">Things I've built</h2>
      </div>
      <a href="/projects/" class="btn btn--secondary">All projects →</a>
    </div>

    <div class="projects-grid">
      {% assign featured_projects = site.projects | where: "featured", true | sort: "weight" %}
      {% for project in featured_projects %}
      <div class="project-card{% if forloop.first %} project-card--featured{% endif %}">
        <div class="project-header{% unless project.thumbnail %} project-header--no-thumb{% endunless %}">
          {% if project.thumbnail %}
            <img src="{{ project.thumbnail }}" alt="{{ project.title }}" class="post-card__thumb">
          {% endif %}
          <div class="project-header__meta">
            <p class="project-tagline">{{ project.tagline }}</p>
            <span class="project-status project-status--{{ project.status }}">{{ project.status_label }}</span>
          </div>
          <h3 class="project-name"><a href="{{ project.url | relative_url }}" style="color: inherit; text-decoration: none;">{{ project.title }}</a></h3>
        </div>
        <p class="project-desc">{{ project.excerpt | strip_html }}</p>
        <div class="project-tags">
          {% for tag in project.tags %}
            <span class="tag">{{ tag }}</span>
          {% endfor %}
        </div>
        <div class="project-links">
          <a href="{{ project.url | relative_url }}" class="project-link">→ View project</a>
          {% if project.github %}<a href="{{ project.github }}" class="project-link" target="_blank" rel="noopener">↗ GitHub</a>{% endif %}
          {% if project.demo %}<a href="{{ project.demo }}" class="project-link" target="_blank" rel="noopener">↗ Live demo</a>{% endif %}
          {% if project.pdf %}<a href="{{ project.pdf }}" class="project-link" target="_blank" rel="noopener">↗ Report</a>{% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<!-- Recent Posts -->
<section class="home-section">
  <div class="home-section-inner">
    <div class="home-section-header">
      <div class="home-section-header__text">
        <span class="section-label">Blog</span>
        <h2 class="section-title">Recent writing</h2>
      </div>
      <a href="/blog/" class="btn btn--secondary">All posts →</a>
    </div>

    <div class="post-list">
      {% for post in site.posts limit:3 %}
      <a href="{{ post.url | relative_url }}" class="post-card{% if post.image %} post-card--has-thumb{% endif %}">
        <span class="post-card__date">{{ post.date | date: "%b %Y" }}</span>
        {% if post.image %}
          <img src="{{ post.image | relative_url }}" alt="{{ post.title }}" class="post-card__thumb">
        {% endif %}
        <div>
          {% if post.categories %}
            <span class="post-card__category post-category--{{ post.categories[0] | downcase }}">
              {{ post.categories[0] }}
            </span>
          {% endif %}
          <h3 class="post-card__title">{{ post.title }}</h3>
          <p class="post-card__excerpt">{{ post.excerpt | strip_html | truncate: 160 }}</p>
        </div>
      </a>
      {% endfor %}
    </div>
  </div>
</section>
