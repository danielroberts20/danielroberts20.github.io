---
layout: base
title: About
permalink: /about/
---

<div class="about-hero">
  <div class="about-grid">
    <div class="about-content">
      <span class="page-hero__label">About</span>
      <h1>Hi, I'm Dan.</h1>
      <p>
        CS graduate, data scientist in training, lifeguard, and soon — full-time traveller.
        In June 2026 I'm leaving for a 3-year trip through the USA, Fiji, Australia, New Zealand,
        SE Asia and Canada. While I'm out there, I'll be running <a href="/projects/">TravelNet</a> —
        a personal data science project that collects and analyses everything from my GPS traces
        to my spending habits.
      </p>
      <p>
        My academic background is in machine learning on time series data. My dissertation
        implemented and compared AutoPlait to existing time series segmentation algorithms for human activity recognition using the
        <a href="https://www.aeon-toolkit.org/" target="_blank" rel="noopener">aeon Python library</a>
        — work that feeds directly into TravelNet's ML pipeline.
      </p>
      <p>
        I care about building things properly: reliable infrastructure, clean data pipelines,
        honest analysis. TravelNet isn't a weekend project — it's a 3-year longitudinal dataset
        I'm constructing from scratch, one commit at a time.
      </p>
    </div>

    <div class="about-sidebar">
      {% assign today = 'now' | date: "%Y-%m-%d" %}
      {% assign current_status = site.data.site.status_schedule[0] %}
      {% for entry in site.data.site.status_schedule %}
        {% if entry.from <= today %}
          {% assign current_status = entry %}
        {% endif %}
      {% endfor %}
      <div class="sidebar-card">
        <span class="sidebar-card__label">Currently</span>
        <h4 class="sidebar-card__title">{{ current_status.label }}</h4>
        <p>{{ current_status.description }}</p>
        <a href="https://github.com/danielroberts20" class="btn btn--secondary" target="_blank" rel="noopener" style="width:100%;justify-content:center;">↗ GitHub</a>
      </div>

      <div class="sidebar-card">
        <span class="sidebar-card__label">Skills</span>
        <div class="skills-list">
          {% for skill in site.data.site.skills.languages %}
            <span class="tag">{{ skill }}</span>
          {% endfor %}
          {% for skill in site.data.site.skills.ml %}
            <span class="tag">{{ skill }}</span>
          {% endfor %}
          {% for skill in site.data.site.skills.tools %}
            <span class="tag">{{ skill }}</span>
          {% endfor %}
        </div>
      </div>
    </div>
  </div>
</div>

<div class="about-sections">

  <div class="about-section">
    <span class="about-section__label">Professional</span>
    <h2>Data science & ML</h2>
    <p>
      My CS degree gave me the foundations; my dissertation gave me a real project to sink my teeth into.
      I'm interested in the messier, harder end of data science — real-world GPS traces rather than
      clean benchmark datasets, multi-currency financial data with missing values and format inconsistencies,
      health data subject to sensor dropouts. I enjoy looking for meaningful connections between data sources and using ML techniques to gain interesting insights, simply for the fact that they are interesting.
    </p>
    <p>
      TravelNet is where that interest becomes practice. When I get to Australia I'll have three months
      of US data as a baseline and start the ML work: clustering travel behaviours,
      anomaly detection on spending, activity segmentation on GPS traces. I'll be able to automatically identify different workplaces I atteneded, coffee shops I visited, daytrips I took, activities I did and much more.
    </p>
    <p>
      Python is my primary language. I use scikit-learn as my ML workhorse, with PyTorch on the table
      for anything that warrants it. I'm comfortable with Docker, SQLite, REST APIs, and running
      production systems on a Raspberry Pi from 10,000 miles away over Tailscale.
    </p>
  </div>

  <div class="about-section">
    <span class="about-section__label">Personal</span>
    <h2>Lifeguarding & swimming</h2>
    <p>
      Before I was a programmer I was a swimmer. I've been on poolside
      for years;  both swimming and guarding - water is something I (quite literally) cannot live without.
      This summer I'm returning to my favourite job: lifeguarding at a US summer camp for two months for the fourth year in a row. 
    </p>
    <p>
      It keeps me fit, keeps me outside, keeps me social, and is a good reminder that not everything worth doing
      involves a terminal window.
    </p>
  </div>

  <div class="about-section">
    <span class="about-section__label">The trip</span>
    <h2>3 years, 6 countries</h2>
    <p>
      June 2026: I leave. The rough itinerary is Philadelphia/DC → USA summer camp →
      Seattle → Fiji (3-night stopover) → Australia on a Working Holiday Visa →
      New Zealand on a WHV → SE Asia backpacking (the Banana Pancake Trail, 3–4 months) →
      Canada on a WHV. Somewhere in there, a dissertation-worthy dataset gets built (and hopefully,
      some liflong memories and friends).
    </p>
    <p>
      The trip isn't a gap year. It's a deliberate decision to spend a few years being
      somewhere uncomfortable, meeting people I wouldn't otherwise meet, experiencing the 
      world, and generatingdata I couldn't collect any other way. TravelNet is how I make that data useful.
    </p>

    <div class="timeline">
      {% for item in site.data.site.timeline %}
      <div class="timeline-item{% if item.type == 'highlight' %} timeline-item--highlight{% endif %}">
        <p class="timeline-item__year">{{ item.year }}</p>
        <p class="timeline-item__label">{{ item.label }}</p>
      </div>
      {% endfor %}
    </div>
  </div>

</div>