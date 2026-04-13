---
layout: post
title: "Why I built a personal data platform before a three-year trip"
subtitle: "A CS grad, a Raspberry Pi, and a lot of data about myself"
date: 2026-04-13
categories: [Technical]
tags: [TravelNet, Python, Raspberry Pi, Data Collection, FastAPI, SQLite]
read_time: 8
excerpt: >
  In June 2026 I'm leaving for a 3-year trip across six countries. I'm also
  bringing a plan to turn the whole thing into a longitudinal dataset worth
  analysing — and I've spent the last few months building the machine to do it.
---

In June 2026 I'm leaving for a 3-year trip. The rough itinerary: Philadelphia → a summer camp in the USA (lifeguarding) → Seattle → Fiji → Australia on a Working Holiday Visa → New Zealand → SE Asia backpacking → Canada. I am, as I write this just under two months out, absolutely *buzzing*. I have already started practising packing my backpack. Yes, really.

But here's the thing nobody tells you when you're planning a trip like this: the tech industry is pretty unforgiving about three-year gaps on your CV, and having amazing campfire stories or a great tan is not going to land you a job as an ML engineer or a data scientist. Eventually those three years will be up. I'll be back in the UK, looking to actually get my teeth into the real working world, and I won't have much to show for it if I spent the whole time learning to surf.

That's the problem TravelNet was built to solve.

<figure>
  <img src="/assets/images/posts/travelnet_overall_route.png" alt="World map showing route from DC, Camp, Seattle, Fiji, Melbourne, Auckland, SE Asia (Bangkok), Vancouver">
  <figcaption>Trip route map. Starting from the UK in June 2026.</figcaption>
</figure>

---

## Why formal experience wasn't an option

In an ideal world, I'd simply look to pick up some experience under my belt during my time in Australia, New Zealand and Canada. The reality is, a tech company (even a startup) isn't going to hire somebody with non-standard work rights, who's only there for a few months and is probably going to request loads of time off to make sure they don't miss out on any once-in-a-lifetime moments. And even if they *were* willing to hire somebody like that (me, if you haven't figured that out yet), most Working Holiday Visas have restrictions on what kind of employers you can work with and for how long.

I needed something that:

- Shows I'm serious about the AI/ML field
- Is not formal work experience
- Genuinely interests me enough that I actually stay committed to it
- Is a stand-out portfolio piece — not another chatbot or arbitrary financial data dashboard
- Links thoroughly with the trip, making something truly unique
- Gives me something to show for three years that wasn't just photos

And so, from my desk on the 5th February 2026, TravelNet was born.

---

## What it actually is

TravelNet is a live data collection, analysis, and visualisation system built entirely around the trip. It runs on a Raspberry Pi (tucked away at home, not rattling around in my bag) and continuously ingests everything I can throw at it:

| Domain | Source | How it gets in |
| --- | --- | --- |
| Location | [Overland](https://github.com/aaronpk/Overland-iOS), iOS Shortcuts | Automatic push every few minutes |
| Health | [Health Auto Export](https://www.healthyapps.dev) | Scheduled upload every 4 hours |
| Financial | Revolut CSV, Wise ZIP, cash endpoint | Manual export + manual cash logging |
| FX rates | [exchangerate.host](https://exchangerate.host) | Automated Prefect flow, daily |
| Weather | [Open-Meteo](https://open-meteo.com) | Retroactive enrichment by coordinates |

Every possible health metric my Apple Watch Ultra can export, GPS traces, transaction data, weather data, flights, places, timezones — anything and everything to build up the most complete picture of three years of travel as I possibly can.

All that data lands in SQLite via a FastAPI backend, backed up to Cloudflare R2 with age encryption. Remote access is over Tailscale. The whole thing runs in Docker, lives on an external HDD, and has already been through a dry run in Ireland in March 2026.

---

## Why build it before I leave?

> *If you're not leaving for months, why bother building it now?*

This question has two answers, one more impressive than the other.

The less impressive one: my pre-departure life currently consists of waking up at 5am to work in retail. Outside of that, most of my friends live quite far away. If I didn't have *something* to keep me busy I think I would lose my mind before I even managed to book my first flight.

The more important one: **I would lose the first weeks or months of data entirely**.

If I didn't start until I was already in the USA, I'd be trying to develop and debug a Raspberry Pi 3,500 miles away on rural summer camp WiFi, during whatever freetime I had left after a full day of lifeguarding (anyone who has worked at a summer camp will tell you that free time is more precious than gold). That means it would take even longer to get TravelNet to a barely workable state — and it would be full of bugs, security gaps, and god knows what else the whole time.

Starting before departure means I get to the USA with a production-ready system. Every location ping, health metric, and transaction from day one is captured and stored cleanly. The data starts flowing the moment I leave, not three months later when I've finally fixed the SQLite locking bug.

---

## The Ireland dry run

Rather than finding out in Philadelphia that something was catastrophically broken, I used a trip to Ireland in March 2026 as a live test. Six days, a foreign country, and every data source running.

The results:

- Irish coordinates showing up correctly in the location database ✅
- Dual-source GPS coverage working as designed (Overland high-density, Shortcuts gap-fill) ✅
- EUR transactions converting to GBP at the correct FX rate ✅
- Health Auto Export uploading successfully without home WiFi ✅
- Cloudflare backup running and fully restorable ✅

> **~99.4%** location coverage rate across six days, with the small gaps covered by the Shortcuts fallback

The system held up. The remaining pre-departure work is defensive engineering rather than firefighting: testing mid-upload internet drops, confirming the Pi auto-restarts cleanly after a power cut, making sure the whole thing can be recovered remotely from a hotel lobby in a different timezone. The kind of work that matters when your only access is a Tailscale tunnel and you're 15,000 miles away.

---

## So what's the end goal?

It's all well and good saying "Hey, look at me, employer — I collected lots of data about myself!" but you don't have to be particularly tech-savvy to know that handing someone a massive CSV file is a terrible portfolio strategy.

The plan is to demonstrate the full stack: collection, cleaning, feature engineering, ML analysis, and an interactive public dashboard. Once I'm in Australia — with at least three months of US baseline data behind me — the ML work begins properly:

- **GPS segmentation** — identifying distinct travel behaviours (slow exploration vs transit, urban vs rural movement patterns) from the raw traces alone. This connects directly to my CS dissertation, where I implemented and compared segmentation models including [AutoPlait](https://dl.acm.org/doi/10.1145/2588555.2588556) using the [aeon library](https://www.aeon-toolkit.org/)
- **Spend analysis** — what does three years of travel actually cost, broken down by country, activity type, and travel style? Not averages from a blog post — my numbers, from my life
- **Anomaly detection** — unusual spending, atypical movement patterns, health metric outliers. The interesting stuff usually lives in the anomalies. Maybe we can find the night I spent so much on drinks that I had to *seriously* reconsider my budget for the following week
- **Time series regression** — predicting future spend or movement based on established patterns. Ambitious, but the data will be there

The public-facing piece is an interactive demo site with an anonymised version of the dataset for anyone who wants to explore it. Live stats, docs, and a lot of *Coming Soon™* pages are already up at [travelnet.dev](https://travelnet.dev).

---

## A reality check

I am just one 23-year-old. I am not a full-time developer, I'm not some coding prodigy, and I'm not founding the next Palantir from my childhood bedroom. I'm a CompSci graduate going travelling — like many graduates before me — who didn't want a three-year gap on his CV. And while I'll make every effort to make TravelNet as polished and professional as possible, it is a personal project and will always be one, no matter how flashy I make the demo website.

And that's okay. The goal was never to build a product. It was to build something genuinely interesting, genuinely mine, and genuinely hard — and use the next three years to find out what it has to say.

Departure: June 2026. The flights start flying, the money starts draining (hopefully not *too* much), and the data starts flowing.

> *Get ready for Dan's Travel Wrapped™, coming soon.*