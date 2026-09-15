# Problem Statement

## Background

The global container shipping industry moves over 80% of all traded goods. Container ports are the critical nodes in this supply chain — every vessel that docks, unloads, and departs on time keeps factories running, shelves stocked, and economies moving. At major hub ports like Los Angeles/Long Beach, Rotterdam, and Singapore, hundreds of vessels arrive every week, each carrying thousands of containers that must be unloaded, stored in a yard zone, and dispatched by truck or rail within a tight dwell window. The orchestration of berths (docking slots), cranes (unloading equipment), and yard zones (container storage) is what determines whether a port runs efficiently or grinds to a halt.

## The Problem

Port operations teams have no forward-looking, data-driven tool to predict congestion before it materialises. Berth, crane, and yard allocation is performed manually by shift supervisors using static spreadsheets, radio communication, and tribal knowledge. A supervisor arriving for their shift has no automated system that tells them: "Three large vessels are arriving within a 6-hour window tomorrow morning, only two compatible berths are available, Yard Zone Y1 is at 87% capacity and will overflow before noon, and Vessel V106 will sit at anchor for 4.8 hours unless you issue a slow-steam instruction in the next 2 hours." Instead, congestion is identified only after ships are already queuing at anchor — at which point cascading delays are inevitable, expensive, and often multi-day in duration.

## Who is Affected

Primary users: Port shift supervisors and VTS (Vessel Traffic Service) controllers at container terminals — the operations professionals responsible for assigning berths, coordinating crane allocation, managing yard capacity, and communicating with vessel agents. These are experienced practitioners managing billions of dollars of cargo flow per day, but they are doing so with reactive, fragmented tooling: a berth planner in one spreadsheet, yard utilisation in another system, vessel ETAs from a separate AIS feed, and historical incident records in a paper logbook or a shared drive. They have no single unified view and no predictive capability.

Secondary users: Vessel agents and shipping line operations teams who need timely slow-steam or holding pattern instructions to avoid costly anchor-wait time, and terminal managers responsible for gate throughput and truck scheduling who are downstream of berth and yard decisions.

## Why It Matters

During the 2021 LA/Long Beach congestion crisis, over 100 vessels waited offshore for an average of 17 days, costing the global supply chain an estimated $1 billion per month in delays, detention charges, and spoiled cargo
A single large vessel (4,000–5,000 TEU) sitting at anchor for 24 hours costs the shipping line approximately 30,000–80,000 in fuel, crew, and demurrage fees alone
Yard overflow events — where a storage zone reaches 100% capacity — force a complete halt to unloading at the linked berths, cascading into multi-vessel queues that can take 12–24 hours to clear (evidenced directly by Incident I003 in this project's dataset: 9-hour shutdown, 2 vessels affected)
Congestion at one major hub port propagates globally: delayed vessels miss their onward connections, causing ripple delays at 3–5 downstream ports per incident
For the port operator, chronic congestion damages terminal reputation, triggers penalty clauses in service contracts, and accelerates shipping line decisions to divert traffic to competing ports — a loss that is structural, not just episodic


## Why Existing Solutions Fall Short

1. Terminal Operating Systems (TOS) are retrospective, not predictive.
Enterprise TOS platforms (Navis N4, OPUS Terminal, etc.) are excellent at recording what has happened — vessel arrivals, crane movements, container positions. They are not designed to run forward simulations, score upcoming time windows for congestion risk, or recommend interventions. They show the current state; they do not show what the state will be in 18 hours if no action is taken.

2. Manual berth planning tools have no constraint awareness.
Most ports use spreadsheet-based berth planners where a supervisor manually drags vessel blocks into time slots. These tools have no knowledge of yard capacity, crane availability, or vessel compatibility constraints. A planner can schedule three large vessels to Berth 1 back-to-back without the tool flagging that Yard Zone Y1, which serves Berth 1, will overflow by the second vessel's arrival.

3. AIS vessel tracking feeds raw data, not decisions.
Automatic Identification System (AIS) feeds give real-time vessel positions and ETAs, but they are data streams — not decision-support tools. A supervisor watching an AIS screen sees that 12 ships are inbound; they do not see that 3 of those ships will create a berth conflict at 06:30 tomorrow or that the combined cargo volume of the day's arrivals exceeds yard capacity.

4. Historical incident systems are disconnected from planning.
Incident logs exist in isolation. There is no system that looks at a current vessel schedule, recognises that it matches the pattern of a past incident (e.g., "multiple large vessels in the same 6-hour window" — the exact pattern that caused an 18-hour delay in Incident I005), and surfaces that historical context as a live warning before the supervisor has made any allocation decisions.

5. Existing AI/ML tools require significant infrastructure and expertise.
Cloud-based port optimisation products exist (e.g., IBM Sterling, Kaleris) but require months of integration work, dedicated data engineering teams, and ongoing cloud infrastructure costs. They are inaccessible to mid-size port operators and impractical to deploy or demonstrate in a rapid-innovation context. There is no lightweight, zero-setup tool that a shift supervisor can use immediately with the data they already have.
