---
title: "BLE Hide 'n' Seek"
tagline: Proximity-based smart lighting control system framed as Hide & Seek
thumbnail: /assets/images/projects/ble.png
pdf: /assets/pdf/comp_networks_report.pdf
tags: [BLE, CoAP, Matter, Thread, IoT, Raspberry Pi, MicroPython, Kalman Filter]
status: complete
status_label: Completed 2025
github: https://github.com/danielroberts20/BLE-Hide-Seek
featured: false
year: "2025"
weight: 3
---

A final year Computer Networks project that uses Bluetooth Low Energy (BLE) proximity sensing to control smart lighting — framed as a game of Hide & Seek.

## Overview

The system uses BLE RSSI readings from a Raspberry Pi to estimate the proximity of a player carrying a BLE beacon. As the player moves closer to or further from the seeker device, smart lights respond in real time — giving the seeker a visual proximity indicator without revealing the hider's exact location.

## Technical stack

- **BLE scanning** — Raspberry Pi continuously scans for BLE advertisement packets and records RSSI values
- **Kalman filter** — Raw RSSI is noisy; a Kalman filter smooths the signal to produce stable proximity estimates
- **CoAP / Matter / Thread** — Lighting control is handled over a CoAP protocol stack, integrating with Thread-based Matter smart home devices
- **MicroPython** — Firmware for the BLE beacon side runs on MicroPython-compatible microcontrollers

## Why it's interesting

Framing a networking protocol exercise as a game made the constraints more concrete: the system had to be responsive enough to feel real-time (sub-second lighting updates) while filtering enough noise to avoid flickering. The Kalman filter tuning was the crux — too aggressive and it lagged, too permissive and it thrashed.
