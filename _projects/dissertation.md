---
title: "A Slice of Time: Segmenting Human Activity with aeon"
tagline: Implementing and evaluating AutoPlait for human activity recognition
thumbnail: /assets/images/projects/dissertation.jpg
pdf: /assets/pdf/dissertation.pdf
tags: [Python, aeon, Unsupervised ML, Time Series, Segmentation, HMMs, AutoPlait, HAR, Open Source]
status: complete
status_label: Completed 2025
featured: true
year: "2025"
weight: 2
---

Final year CS dissertation exploring unsupervised segmentation of human activity recognition (HAR) time series data using six existing segmentation algorithms — including AutoPlait — via the aeon Python library.

## The problem

Human activity recognition typically frames the task as classification: given a labelled window of sensor data, predict the activity. But real-world activity traces aren't pre-segmented. People don't announce when they switch from walking to sitting. The harder problem is *segmentation*: given a continuous, unlabelled stream, find where one activity ends and another begins.

This dissertation investigates how well existing time series segmentation algorithms handle that harder problem on HAR data.

## Approach

Six segmentation algorithms were implemented and benchmarked using aeon, the open-source Python library for time series machine learning. The evaluation focused on:

- How accurately each algorithm identifies change points in continuous activity traces
- How algorithms perform across different noise levels and activity transition patterns
- Whether AutoPlait — a multivariate, HMM-based approach — generalises better than simpler methods

## Findings

No single algorithm consistently outperformed the others across all conditions. AutoPlait showed strong performance on complex, multi-modal activity transitions but was sensitive to hyperparameter choice. Simpler methods were more stable but missed subtle transitions.

The main conclusion: HAR segmentation is genuinely hard, and the choice of algorithm should be driven by the specific noise characteristics and transition sharpness of the target domain. There is no one-size-fits-all solution.

## Connection to TravelNet

The GPS segmentation component of TravelNet draws directly on this work — applying similar HMM-based approaches to identify distinct travel behaviours (slow exploration, transit, stationary periods) from continuous location traces.
