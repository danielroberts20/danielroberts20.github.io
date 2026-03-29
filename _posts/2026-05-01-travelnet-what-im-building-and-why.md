---
layout: post
title: "TravelNet — here's what I'm building and why"
subtitle: "A 3-year personal data science project, starting June 2026"
date: 2026-05-01
categories: [Technical]
tags: [TravelNet, Python, Raspberry Pi, Data Collection, FastAPI, SQLite]
read_time: 8
excerpt: >
  In June 2026 I'm leaving for a 3-year trip across six countries. I'm also
  bringing a plan to turn the whole
  thing into a longitudinal dataset worth analysing. Here's what I'm building and why.
---

In June 2026, I'm leaving for a 3-year trip. The rough itinerary: Philadelphia → a summer camp in the USA (lifeguarding) → Seattle → Fiji → Australia on a Working Holiday Visa → New Zealand → SE Asia backpacking → Canada. Somewhere in there, I finish a data science project that's been running on a Pi in my bedroom since 2025.

That project is TravelNet.

## What is it?

TravelNet is a live data collection, analysis, and visualisation system built around the trip. It runs on a Raspberry Pi (tucked away at home, not in my bag) and continuously ingests:

- **Location data** — Continuous GPS traces from [Overland](https://github.com/aaronpk/Overland-iOS), with iOS Shortcuts running every 5 minutes as a secondary channel
- **Health data** — Apple Health exports via [Health Auto Export](https://www.healthyapps.dev) (HAE): steps, calories, breathes, heart rate, sleep, workouts
- **Financial data** — Revolut and Wise CSVs uploaded automatically, plus a cash endpoint for physical transactions

Everything goes into SQLite via a FastAPI backend, backed up to Cloudflare R2 with age encryption. Remote access is over Tailscale. The whole thing runs in Docker and has been through a dry run in Ireland in March 2026.

## Why bother?

Two reasons, one practical and one honest.

**The practical reason:** I'm going to spend three years moving through a wildly varied set of environments — urban sprawls, countryside villages, wild campsites, tropical cities, remote islands, mountain hostels, beach towns. That movement will leave traces: in my spending patterns, in my health metrics, in the density and nature of my GPS data. That's a dataset worth having. No one else will ever have quite this dataset, because no one else will have quite this trip.

**The honest reason:** I want to get good at the hard parts of ML engineering and data science. Not benchmark datasets. Not Kaggle. Real data with missing values, sensor dropouts, timezone hell, multi-currency FX complications, iOS background execution bugs, and all the other ways the world resists being measured neatly. TravelNet is a machine for generating hard problems, and I am (with a lot of effort) going to tackle those hard problems and produce some fascinating solutions. 

## What will the ML look like?

I won't start the analysis until I'm in Australia — I want at least three months of US data as a baseline before I begin. But the plan is:

- **GPS segmentation** — clustering and segmentation approaches to identify distinct travel behaviours (slow exploration vs transit, urban vs rural movement patterns). This connects to my CS dissertation, which implemented, compared and evaluated segmentation models, including [AutoPlait](https://dl.acm.org/doi/10.1145/2588555.2588556), for segmentation using the [aeon library](https://www.aeon-toolkit.org/).
- **Spend analysis** — what does daily/weekly/monthly cost of living actually look like across different countries and travel styles? Not averages from the internet — my numbers, from my life.
- **Anomaly detection** — unusual spending events, atypical movement patterns, health metric outliers. The interesting stuff usually lives in the anomalies. Maybe we can find the night I spent so much on drinks that I had to *seriously* budget for the next week.
- **Time series regression** — predicting future spend or movement based on past patterns. Ambitious, but the data will be there.

The dashboard is planned too: an interactive site with the full dataset visualised, plus a public anonymised version on GitHub for anyone who wants to poke around. You can find live stats from my travels, planned future updates, docs and more on the[TravelNet website](https://travelnet.dev)!

## Where it is now

The system is built. The Ireland dry run (March 2026) confirmed:

- Irish coordinates showing up correctly in location data ✅
- Dual-source GPS coverage working as designed (Overland high-density, Shortcuts gap-fill) ✅
- Manual cash transactions logged correctly ✅
- Cloudflare backup running and restorable ✅

The remaining pre-departure work is hardening and enhancing: persistent cron logging, testing mid-upload internet drops, confirming the Pi auto-restarts cleanly after a power cut, ensuring consistency across database tables, and of course, bug fixing. The kind of defensive engineering that matters when you're going to be 15,000 miles away and your only access is a Tailscale tunnel.

## Follow along

I'll write up the ML work as I go — the GPS segmentation piece in particular will be worth a dedicated post once I have real data to work with. If you're interested in ML on messy real-world data, or the infrastructure decisions behind TravelNet, that's what this blog is for.

The [GitHub repo](https://github.com/danielroberts20/travelnet) is public now, and the demo site is up and running with basic live stats and a lot of Coming Soon:tm: pages.

Departure: June 2026. The flights start flying, the money starts draining (hopefully not too much), and the data starts flowing.
