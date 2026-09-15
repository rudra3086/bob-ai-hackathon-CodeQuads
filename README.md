# 🚀 Bob — Port Operations AI Copilot

> ⚠️ **Replace everything in `[ ]` brackets with your actual content before submission.**

---

## 👥 Team

| Field | Value |
|---|---|
| **Team Name** | CodeQuads |
| **Track** | AI |
| **Team Lead** | Bhavya Durgani— d25cs112@charusat.edu.in |
| **Members** | Rudra Patel, Maitri Sheta, Vainavi Raval |

---

## 🎯 Problem Statement

> In 2–3 sentences: What problem does your project solve? Who experiences this problem?

Container ports like LA/Long Beach suffer severe congestion — 100+ vessels waiting offshore for weeks — costing global supply chains billions of dollars. Berth, crane, and yard allocation is still largely manual and reactive; port operations teams only spot congestion after ships are already queuing at anchor. Shift supervisors lack a forward-looking, data-driven tool to predict bottlenecks and act before delays cascade.

---

## 💡 Solution

> In 2–3 sentences: What did you build? How does it solve the problem above?

Bob is an AI-powered port operations copilot that ingests vessel schedules, berth capacity, yard utilization, and historical incident data to predict congestion up to 72 hours ahead. It automatically computes optimized berth and crane assignments using an earliest-free-compatible-berth algorithm, generates ranked routing recommendations (slow-steam instructions, alternate berth routing, arrival staggering), and produces a concise shift supervisor operations plan. The entire solution runs as a single self-contained interactive dashboard — no backend required — with all data persisted in the browser session.

---

## ✨ Key Features

- **Feature 1:** Congestion Prediction Engine — analyzes incoming vessel schedules against real-time berth and yard capacity to flag high/medium/low risk windows up to 72 hours ahead, with plain-language reasoning for each risk.
- **Feature 2:** Berth & Crane Optimizer — assigns every vessel to the earliest-free compatible berth, computes handling durations by crane count and cargo volume, and surfaces vessels that cannot be accommodated within the window.
- **Feature 3:** Ranked Routing Recommendations — prioritizes interventions by TEU impact and delay hours saved (slow-steam, alternate berth, arrival staggering, yard clearance.
- **Feature 4:** 72-Hour Ops Plan — generates a concise shift supervisor brief with risk summary, berth/crane schedule table, top 3 priority actions, and live escalation flags.
- **Feature 5:** Full CRUD Dashboard — vessels, berths, yard zones, and incidents are all editable inline; all changes persist in browser sessionStorage with no external database

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| **Languages** | HTML5, CSS3, JavaScript (ES2020) |
| **Frameworks** | Vanilla JS (no framework) |
| **IBM Technologies** | IBM Bob (AI Copilot platform) |
| **Databases** | Browser sessionStorage (client-side only) |
| **Other** | Apache ECharts 5.4, Lucide SVG icon system, CSS custom properties |

---

## 📁 Repository Structure

```
├── src/
|   |--frontend/
|       |---index.html                 # All source code
├── docs/                 # Written documentation
│   ├── problem-statement.md
│   ├── solution-overview.md
│   ├── architecture.md
│   └── setup-guide.md
├── demo/                 # Demo artifacts
│   ├── screenshots/      # App screenshots
│   └── demo-video-link.txt  # Link to demo video
├── presentation/         # Slide deck
└── submission.yaml       # Structured submission metadata
```

---

## ⚡ How to Run

> **Copy these exact steps from your [`docs/setup-guide.md`](docs/setup-guide.md)**

```bash
# 1. Clone the repo
git clone https://github.com/bob-ai-hackathon-CodeQuads.git
cd bob-ai-hackathon-CodeQuads

# 2. Install dependencies
# No dependencies — fully self-contained HTML file

# 3. Configure environment
cp .env.example .env
# No environment configuration required

# 4. Run the project
# Open port_ops_dashboard.html directly in any modern browser
```

---

## 🖥️ Demo

| Artifact | Link |
|---|---|
| 📹 Demo Video | [See demo/demo-video-link.txt](demo/demo-video-link.txt) |
| 🌐 Live Demo | [See demo/live-demo-url.txt](demo/live-demo-url.txt) |
| 🖼️ Screenshots | [See demo/screenshots/](demo/screenshots/) |
| 📊 Presentation | [See presentation/slides.pdf](presentation/) |

---

## ⚠️ Known Limitations

> Be honest — judges appreciate transparency over overclaiming.

- Congestion risk windows are rule-based (derived from the four input datasets), not trained ML predictions — a production system would layer in weather feeds, customs data, and vessel AIS streams
- All data lives in browser sessionStorage — refreshing the tab restores state, but closing the browser clears it; a production deployment would require a persistent backend
- The berth optimizer uses earliest-free-compatible-berth (greedy); a full integer-programming solver would yield globally optimal schedules across multi-day horizons.
---

## 🏅 What We're Most Proud Of

The end-to-end analysis engine — from raw CSV inputs to a fully computed 72-hour operations plan with congestion predictions, optimized berth assignments, ranked routing recommendations, and live escalation flags — runs entirely in the browser with zero backend, zero dependencies, and zero setup. A shift supervisor can open one HTML file and immediately see actionable intelligence derived from their own data.

---
