---
layout: base
title: Projects
permalink: /projects/
---

<div class="page-hero">
  <div class="page-hero-inner">
    <span class="page-hero__label">Projects</span>
    <h1 class="page-hero__title">Things I'm building</h1>
    <p class="page-hero__desc">
      A mix of long-running data science projects and academic work.
      TravelNet is the centrepiece — everything else feeds into it or runs alongside it.
    </p>
  </div>
</div>

<div class="page-body">
  <div class="page-body-inner">
    <div class="projects-grid">
      {% assign sorted_projects = site.projects | sort: "weight" %}
      {% for project in sorted_projects %}
      <div class="project-card{% if project.featured %} project-card--featured{% endif %}">
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

        <p class="project-desc">{{ project.description | default: project.excerpt | strip_html }}</p>

        <div class="project-tags">
          {% for tag in project.tags %}
            <span class="tag">{{ tag }}</span>
          {% endfor %}
        </div>

        <div class="project-links">
          <a href="{{ project.url | relative_url }}" class="project-link">→ View project</a>
          {% if project.github %}
            <a href="{{ project.github }}" class="project-link" target="_blank" rel="noopener">↗ GitHub</a>
          {% endif %}
          {% if project.demo %}
            <a href="{{ project.demo }}" class="project-link" target="_blank" rel="noopener">↗ Live demo</a>
          {% endif %}
          {% if project.pdf %}
            <a href="{{ project.pdf }}" class="project-link" target="_blank" rel="noopener">↗ Report</a>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</div>
