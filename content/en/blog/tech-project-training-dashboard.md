---
title: "Building a Training Dashboard with Go & HTMX"
date: 2026-05-09
draft: false
tags: ["tech", "projects", "go"]
description: "A lightweight dashboard to track my training data."
---

I wanted a simple way to visualize my training data without subscribing to another platform. So I built one.

### Stack

- **Backend:** Go (Chi router)
- **Frontend:** HTMX + Tailwind CSS
- **Database:** SQLite
- **Deployment:** Fly.io

### What it does

It ingests FIT files exported from my bike computer, parses them, and displays:

- Weekly volume (km and hours)
- Elevation gain over time
- Power distribution charts
- A simple training log

### Why HTMX?

I wanted to see if the hype is real. Honestly? It's refreshing. No build step for the frontend, no JavaScript framework fatigue. A Go template with HTMX attributes does 90% of what I'd normally use React for.

### Key takeaway

Perfect is the enemy of done. This took me one weekend to get a working MVP, and I've been iterating since.

[Source code is on GitHub](https://github.com/manupanu) — feel free to adapt it for your own use.
