---
title: 'Kicking Off My Senior Design Project: A Power Electronics Build'
date: '2026-06-24T09:00:00-05:00'
categories: [Engineering]
tags: [electrical-engineering, senior-design, power-electronics]
type: post
draft: false
comments: true
mathjax: true
state: top
weight: 1
---

Notes from week one of my capstone project.

<!--more-->

This semester I'm finally starting my senior design project, and I wanted to start documenting it here as I go — partly for anyone else working through something similar, and partly so future-me remembers why I made the decisions I did.

## The project

I'm building a small DC-DC converter board to demonstrate efficient power delivery for a low-voltage embedded system. The rough goals:

- Input: 12V from a standard wall adapter
- Output: regulated 5V and 3.3V rails
- Efficiency target: >90% at typical load
- Compact enough to fit on a single 2-layer PCB

## Why this topology

I'm going with a synchronous buck converter rather than a simple linear regulator. The efficiency math makes the reasoning pretty clear. For a linear regulator, efficiency is roughly:

$$\eta \approx \frac{V_{out}}{V_{in}}$$

Stepping 12V down to 3.3V on a linear regulator would mean throwing away most of the input power as heat. A switching converter doesn't have that problem, since it stores and transfers energy rather than dissipating the difference.

## What's next

Next up is finalizing the inductor and capacitor selection, then moving into simulation before I commit to ordering parts. I'll post an update once I have a working schematic.

If you're also working through a senior design project this year, I'd love to hear what you're building.
