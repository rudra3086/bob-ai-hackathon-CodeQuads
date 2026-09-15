# Solution Overview

## What We Built

Bob is a single-file, browser-based AI operations copilot for container port shift supervisors. You give it four structured datasets — a vessel arrival schedule, berth capacity data, yard storage utilization, and a log of historical incidents — and it immediately produces a complete 72-hour port operations intelligence picture. It tells you which time windows are going to face congestion and exactly why, assigns every incoming vessel to the optimal berth with crane allocation and handling times calculated, ranks the interventions you need to take ordered by impact, and generates a concise operations plan readable in under 2 minutes by a shift supervisor walking onto the floor.

The entire solution is a single HTML file. No server. No database. No installation. No API keys. Open it in a browser and it works.

## How It Works

[Explain the core mechanism step by step. A numbered list or simple flow works well here.]

1. Data is loaded into memory. On page load, the four datasets (vessels, berths, yards, incidents) are parsed into a unified in-memory JavaScript state object. If the user has previously saved a session, their last state is restored instantly from sessionStorage. Otherwise the default datasets ship pre-loaded inside the file.
2. The Congestion Prediction Engine runs. The engine groups incoming vessels into time windows, cross-references each window's total arriving TEU and vessel sizes against the berths that will be free during that window, and scores each window High / Medium / Low. Yard utilization is checked in parallel — if any zone linked to an active berth exceeds 80%, an overflow alert is generated. Every risk rating is accompanied by a plain-English explanation of the specific cause.
3. The Berth & Crane Optimizer runs. Vessels are sorted by ETA. For each vessel, the optimizer finds every physically compatible berth (matching vessel size against berth max-size and checking the vessel's own compatibility list), then selects the berth with the earliest available slot. It calculates handling duration using the formula (TEU ÷ 1000) × berth rate × (3 ÷ cranes) — accounting for the actual number of cranes at that berth. The berth's free time is advanced to the end of that vessel's handling window, so the next vessel in the queue sees the updated availability. This produces a complete, conflict-free assignment schedule for all 12 vessels across all 4 berths.
4. The Routing Recommendation Ranker runs. Any vessel with a computed wait time of 2 or more hours is flagged for intervention. The ranker generates a specific recommended action for each — slow-steam to align with berth clearance, alternate berth routing if size permits, or arrival staggering to break multi-vessel clusters. Yard overflow risks generate their own recommendations (extended gate hours, container clearance prioritization, overflow to adjacent zone). All recommendations are ranked by TEU affected and estimated delay hours saved.
5. The Escalation Flag Generator runs. The generator scans three sources simultaneously: yard utilization thresholds, vessel wait times from the optimizer, and historical incidents matching current patterns. It produces owner-tagged escalation cards — each flag names the responsible party (Yard Manager, VTS Controller, Equipment Superintendent) and states the specific action required.
6. All outputs are rendered across 8 dashboard pages. The UI layer injects computed results into the Overview, Congestion, Vessels, Berths & Cranes, Yard Capacity, Ops Plan, Incidents, and Edit Data pages. Apache ECharts renders all data visualizations — TEU volume bars, berth Gantt timeline, yard utilization, dwell time analysis, incident delay breakdowns.
7. Every edit triggers a full recompute. When a supervisor updates any value — a vessel's ETA, a yard's occupancy, a berth's crane count — the state object is mutated, the entire computation chain re-runs, the current page re-renders, and the new state is auto-saved to sessionStorage.
## Architecture Diagram

> See [`architecture.md`](architecture.md) for the detailed diagram.

## IBM Technologies Used

[Explain specifically HOW you used each IBM technology — not just that you used it.]

IBM Bob (AI Copilot Platform): Bob was used as the primary AI development environment throughout this project. The problem analysis, congestion prediction logic design, routing recommendation framework, berth optimization algorithm, operations plan structure, and all written documentation were developed in active collaboration with Bob. Bob generated the core JavaScript computation engine (congestion scoring, berth assignment algorithm, escalation flag logic), the complete UI (HTML/CSS/JS), the architecture documentation, the problem statement, the solution overview, and the video script. Bob served as the AI pair programmer, technical architect, and domain analyst for the entire submission.
