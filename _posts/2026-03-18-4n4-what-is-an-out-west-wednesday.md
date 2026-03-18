---
layout: post
title: "4n4 — What is an `Out West Wednesday`?"
subtitle: "A trip of a lifetime in Arizona, Utah, Wyoming and Colorado in summer 2025"
date: 2026-03-18
categories: [Travel]
image: /assets/images/posts/delicate.jpg
tags: [Camp, Echo Lake, 4n4, Summer]
read_time: 100
excerpt: >
  In June 2026 I'm leaving for a 3-year trip across six countries. I'm also
  bringing a Raspberry Pi, a structured data schema, and a plan to turn the whole
  thing into a longitudinal dataset worth analysing. Here's what I'm building and why.
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

- **GPS segmentation** — clustering and HMM-based approaches to identify distinct travel behaviours (slow exploration vs transit, urban vs rural movement patterns). This is directly connected to my CS dissertation, which compared Hidden Markov Models and AutoPlait for GPS segmentation using the [aeon library](https://www.aeon-toolkit.org/).
- **Spend analysis** — what does daily cost of living actually look like across different countries and travel styles? Not averages from the internet — my numbers, from my life.
- **Anomaly detection** — unusual spending events, atypical movement patterns, health metric outliers. The interesting stuff usually lives in the anomalies.
- **Time series regression** — predicting future spend or movement based on past patterns. Ambitious, but the data will be there.

The dashboard is planned too: an interactive site with the full dataset visualised, plus a public anonymised version on GitHub for anyone who wants to poke around.

## Where it is now

The system is built. The Ireland dry run (March 2026) confirmed:

- Irish coordinates showing up correctly in location data ✅
- Dual-source GPS coverage working as designed (Overland high-density, Shortcuts gap-fill) ✅
- Manual cash transactions logged correctly ✅
- Cloudflare backup running and restorable ✅

The remaining pre-departure work is hardening: persistent cron logging, testing mid-upload internet drops, confirming the Pi auto-restarts cleanly after a power cut. The kind of defensive engineering that matters when you're going to be 15,000 miles away and your only access is a Tailscale tunnel.

## Follow along

I'll write up the ML work as I go — the GPS segmentation piece in particular will be worth a dedicated post once I have real data to work with. If you're interested in the aeon library, time series ML on messy real-world data, or the infrastructure decisions behind TravelNet, that's what this blog is for.

The [GitHub repo](https://github.com/danielroberts20/travelnet) will be public once I'm happy with the code. The demo site will follow once the dashboard has something worth showing.

Departure: June 2026. The data starts flowing then.
