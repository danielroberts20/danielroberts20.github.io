---
layout: base
title: CV
permalink: /cv/
---

<div class="cv-wrapper">
  <div style="display:flex; align-items:flex-start; justify-content:space-between; margin-bottom: var(--space-2xl); gap: var(--space-lg); flex-wrap: wrap;">
    <div>
      <span style="font-family: var(--font-mono); font-size: 0.75rem; color: var(--accent); text-transform: uppercase; letter-spacing: 0.1em; display:block; margin-bottom: var(--space-sm);">CV</span>
      <h1 style="margin-bottom: var(--space-sm);">Dan Roberts</h1>
      <p style="font-size: 0.95rem;">Data scientist · <a href="https://github.com/danielroberts20" style="color: var(--accent-bright);">github.com/danielroberts20</a> · <a href="https://www.linkedin.com/in/daniel-roberts-69b55b240/" style="color: var(--accent-bright);">LinkedIn</a></p>
    </div>
    <!-- Uncomment when you have a PDF CV ready:
    <a href="/assets/files/dan-roberts-cv.pdf" class="btn btn--primary" download>↓ Download PDF</a>
    -->
  </div>

  <div class="cv-section">
    <p class="cv-section__title">Education</p>
    <div class="cv-entry">
      <div>
        <h4 class="cv-entry__title">First Class BSc Computer Science</h4>
        <p class="cv-entry__sub">A Slice of Time; Segmenting Human Activity with <i>aeon</i></p>
        <p class="cv-entry__desc">Focus on machine learning, time series analysis, software engineering and algorithm comparison. Contribution to open-source Python library. Dissertation work links to the TravelNet ML pipeline.</p>
      </div>
      <span class="cv-entry__period">2022 – 2025</span>
    </div>
  </div>

  <div class="cv-section">
    <p class="cv-section__title">Projects</p>
    <div class="cv-entry">
      <div>
        <h4 class="cv-entry__title">TravelNet</h4>
        <p class="cv-entry__sub">Personal data science project — 3-year longitudinal travel dataset</p>
        <p class="cv-entry__desc">
          Designed and built a live data collection system on Raspberry Pi (FastAPI, SQLite, Docker, Tailscale)
          collecting GPS traces, Apple Health metrics and multi-currency financial data across a 3-year international trip.
          ML pipeline — clustering, segmentation, anomaly detection, time series regression — to be built during Australia leg (late 2026).
        </p>
      </div>
      <span class="cv-entry__period">2026 – 2029</span>
    </div>

    <div class="cv-entry">
      <div>
        <h4 class="cv-entry__title">Time Series ML Dissertation</h4>
        <p class="cv-entry__sub">Final year CS project</p>
        <p class="cv-entry__desc">
          Benchmarked variety of segmentation algorithms against <span style="font-variant: small-caps;">AutoPlait</span> for unsupervised segmentation of human activity recognition data.
          Used the aeon Python library.
        </p>
        <details class="cv-abstract">
          <summary>Abstract</summary>
          <p>Time series segmentation is a crucial step in the wider problem of human activity recognition. There are many algorithms that perform semantic segmentation of time series data, several of which are included in the open-source Python library <i>aeon</i>. How do these algorithms perform for the task of human activity recognition? Is there a better algorithm not yet included in <i>aeon</i>? This report implements a segmentation algorithm for time series data not currently present in the library; <span style="font-variant: small-caps;">AutoPlait</span>. We evaluate it and existing <i>aeon</i> algorithms on five human activity datasets and show that it performs in line with other algorithms currently present in <i>aeon</i>, achieving similar precision, recall and, F-score, in addition to providing information on any repeating or unique patterns in the data. We conclude with a critical evaluation of <span style="font-variant: small-caps;">AutoPlait</span> and its implementation, suggestion for further work, and a retrospective review of the project.</p>
          <a href="{{ '/assets/pdf/report.pdf' | relative_url }}"
            class="cv-abstract__download"
            download>
            ↓ Download dissertation (PDF)
          </a>
        </details>
      </div>
      <span class="cv-entry__period">2024 – 2025</span>
    </div>

  <div class="cv-section">
    <p class="cv-section__title">Experience</p>
    <div class="cv-entry">
      <div>
        <h4 class="cv-entry__title">Lifeguard & Swim Teacher</h4>
        <p class="cv-entry__sub">Various · UK & USA</p>
        <p class="cv-entry__desc">
          Multi-year experience poolside — lifeguarding, teaching swimming across all ages and abilities,
          and running structured swim sessions. Summer 2023-2026: lifeguarding and swim teaching at Camp Echo Lake, NY.
        </p>
      </div>
      <span class="cv-entry__period">2023 – present</span>
    </div>

    <div class="cv-entry">
      <div>
        <h4 class="cv-entry__title">Service Team Support</h4>
        <p class="cv-entry__sub">UK</p>
        <p class="cv-entry__desc">
          Multi-year experience poolside — lifeguarding, teaching swimming across all ages and abilities,
          and running structured swim sessions. Summer 2023-2026: lifeguarding and swim teaching at Camp Echo Lake, NY.
        </p>
      </div>
      <span class="cv-entry__period">2019 – present</span>
    </div>
  </div>

  <div class="cv-section">
    <p class="cv-section__title">Technical skills</p>
    <div style="margin-bottom: var(--space-lg);">
      <p style="font-size: 0.85rem; color: var(--text-muted); margin-bottom: var(--space-sm); font-family: var(--font-mono);">Languages</p>
      <div class="skills-list" style="display:flex; flex-wrap:wrap; gap: var(--space-sm);">
        {% for skill in site.data.site.skills.languages %}<span class="tag">{{ skill }}</span>{% endfor %}
      </div>
    </div>
    <div style="margin-bottom: var(--space-lg);">
      <p style="font-size: 0.85rem; color: var(--text-muted); margin-bottom: var(--space-sm); font-family: var(--font-mono);">ML & Data Science</p>
      <div class="skills-list" style="display:flex; flex-wrap:wrap; gap: var(--space-sm);">
        {% for skill in site.data.site.skills.ml %}<span class="tag">{{ skill }}</span>{% endfor %}
      </div>
    </div>
    <div>
      <p style="font-size: 0.85rem; color: var(--text-muted); margin-bottom: var(--space-sm); font-family: var(--font-mono);">Infrastructure & Tools</p>
      <div class="skills-list" style="display:flex; flex-wrap:wrap; gap: var(--space-sm);">
        {% for skill in site.data.site.skills.tools %}<span class="tag">{{ skill }}</span>{% endfor %}
      </div>
    </div>
  </div>

</div>
