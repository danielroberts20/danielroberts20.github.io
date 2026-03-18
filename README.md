# danielroberts20.github.io — portfolio

Personal portfolio and blog — built with Jekyll, hosted on GitHub Pages.

**Live site:** [danielroberts20.github.io](https://danielroberts20.github.io)

---

## Structure

```
├── _config.yml          # Jekyll config and site metadata
├── _layouts/            # base.html, home.html, page.html, post.html
├── _includes/           # nav.html, footer.html
├── _posts/              # Blog posts — YYYY-MM-DD-title.md
├── _data/
│   ├── projects.yml     # Project cards — edit here to add/update projects
│   └── site.yml         # Nav, skills, timeline
├── assets/
│   ├── css/main.css     # Full design system
│   ├── js/main.js       # Nav toggle, scroll effects
│   └── files/           # CV PDF goes here when ready
├── index.md             # Home page
├── about.md             # About page
├── projects.md          # Projects page
├── blog.md              # Blog listing
├── cv.md                # CV / Resume
└── 404.html
```

---

## Adding a blog post

Create a new file in `_posts/` named `YYYY-MM-DD-your-title.md`:

```markdown
---
layout: post
title: "Your Post Title"
subtitle: "Optional subtitle"
date: 2026-06-15
categories: [Technical]   # Technical | Travel
tags: [Python, TravelNet]
read_time: 5
excerpt: >
  One or two sentences shown in the post list.
---

Your post content in Markdown here.
```

Commit and push — that's it. GitHub Pages rebuilds automatically.

**Categories:**
- `Technical` — shown in blue on the blog page
- `Travel` — shown in warm gold on the blog page

---

## Adding a project

Edit `_data/projects.yml` and add a new entry following the existing format.
Set `featured: true` to show it on the home page.

---

## Running locally

```bash
bundle install
bundle exec jekyll serve
# → http://localhost:4000
```

Requires Ruby and Bundler. Install with:
```bash
gem install bundler
```

---

## Deploying

Push to the `main` branch of a repo named `danielroberts20.github.io`.
GitHub Pages detects Jekyll automatically and builds within ~60 seconds.
No CI/CD or build configuration needed.

---

## CV PDF

When ready, drop your CV as `assets/files/dan-roberts-cv.pdf` and uncomment
the download button in `cv.md`.
