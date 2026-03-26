---
title: Runway Re-declaration Tool
tagline: Airport runway parameter recalculation for obstacle scenarios
thumbnail: /assets/images/projects/compass.png
tags: [Java, JavaFX, Agile, Software Engineering, Teamwork]
status: complete
status_label: Completed 2024
github: https://github.com/danielroberts20/Runway-Re-declaration-Tool
featured: false
year: "2024"
weight: 8
---

A second year software engineering group project built following agile methodology with regular customer feedback cycles.

## What it does

When an obstacle (debris, a foreign object) is present on an airport runway, aviation regulations require the runway's declared distances — TORA, TODA, ASDA, LDA — to be recalculated to account for the reduced usable length. This tool automates that recalculation.

Given runway parameters and an obstacle's position, the tool computes re-declared distances for both directions of operation and visualises the result — showing which portions of the runway remain usable and how the obstacle affects each declared distance.

## Process

The project followed a structured agile process: fortnightly sprints, a product backlog, and regular demos to a simulated customer (the module supervisor). The team used Git for version control and tracked work on a shared Kanban board.

## Tech

Built with Java and JavaFX for the desktop GUI. The calculation logic is separated from the UI layer, making it straightforward to extend to new runway configurations or obstacle types.
