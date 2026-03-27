---
title: TravelNet
tagline: 3 years of personal data science, live from the road
tags: [Python, FastAPI, SQLite, Docker, Scikit-learn, HMMs, Time Series, Raspberry Pi]
status: live
status_label: Live & collecting data
github: https://github.com/danielroberts20/travelnet
demo: https://travelnet.dev
featured: true
year: "2026–2029"
weight: 1
---

In June 2026, I'm leaving for a 3-year trip. The rough itinerary: Philadelphia → a summer camp in the USA (lifeguarding) → Seattle → Fiji → Australia on a Working Holiday Visa → New Zealand → SE Asia backpacking → Canada. Somewhere in there, I finish a data science project that's been running on a Pi in my bedroom since 2025.

That project is TravelNet.

## What is it?

TravelNet is a live data collection, analysis, and visualisation system built around the trip. It runs on a Raspberry Pi (tucked away at home, not in my bag) and continuously ingests:

- **Location data** — GPS traces from iOS Shortcuts every 5 minutes, with Overland running as a continuous secondary tracker
- **Health data** — Apple Health exports: steps, heart rate, sleep, workouts
- **Financial data** — Revolut and Wise CSVs uploaded automatically, plus a cash endpoint for physical transactions

Everything goes into SQLite via a FastAPI backend, backed up to Cloudflare R2 with age encryption. Remote access is over Tailscale. The whole thing runs in Docker and has been through a dry run in Ireland in March 2026.

## Why bother?

Two reasons, one practical and one honest.

**The practical reason:** I'm going to spend three years moving through a wildly varied set of environments — tropical cities, remote islands, mountain hostels, beach towns. That movement will leave traces: in my spending patterns, in my health metrics, in the density and nature of my GPS data. That's a dataset worth having. No one else will ever have quite this dataset, because no one else will have quite this trip.

**The honest reason:** I want to get good at the hard parts of data science. Not benchmark datasets. Not Kaggle. Real data with missing values, sensor dropouts, timezone hell, multi-currency FX complications, iOS background execution bugs, and all the other ways the world resists being measured neatly. TravelNet is a machine for generating hard problems.

## What will the ML look like?

I won't start the analysis until I'm in Australia — I want at least three months of US data as a baseline before I begin. But the plan is:

- **GPS segmentation** — clustering and HMM-based approaches to identify distinct travel behaviours (slow exploration vs transit, urban vs rural movement patterns)
- **Spend analysis** — what does daily cost of living actually look like across different countries and travel styles?
- **Anomaly detection** — unusual spending events, atypical movement patterns, health metric outliers
- **Time series regression** — predicting future spend or movement based on past patterns

The dashboard is planned too: an interactive site with the full dataset visualised, plus a public anonymised version on GitHub.

## Where it is now

The system is built. The Ireland dry run (March 2026) confirmed:

- Irish coordinates showing up correctly in location data ✅
- Dual-source GPS coverage working as designed ✅
- Manual cash transactions logged correctly ✅
- Cloudflare backup running and restorable ✅

The remaining pre-departure work is hardening: persistent cron logging, testing mid-upload internet drops, confirming the Pi auto-restarts cleanly after a power cut.
