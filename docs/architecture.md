# Architecture

## System Architecture

[Describe the overall architecture of your system. Replace the Mermaid diagram below with your actual architecture.]

```mermaid
graph TD
    A[Shift Supervisor / Browser] -->|Opens HTML file locally| B[port_ops_dashboard.html]

    B --> C[sessionStorage API]
    C -->|Persist & restore state| B

    B --> D[Data Layer]
    D --> D1[vessel_schedule.csv]
    D --> D2[berth_capacity.csv]
    D --> D3[yard_capacity.csv]
    D --> D4[historical_incidents.csv]

    D1 & D2 & D3 & D4 -->|Parsed into JS state object| E[In-Memory State Engine]

    E --> F[Congestion Prediction Engine]
    E --> G[Berth & Crane Optimizer]
    E --> H[Routing Recommendation Ranker]
    E --> I[Escalation Flag Generator]

    F -->|Risk windows + reasons| J[UI Render Layer]
    G -->|Vessel-to-berth assignments + wait times| J
    H -->|Ranked actions by TEU impact| J
    I -->|Live escalation alerts + owners| J

    J --> K1[Overview Dashboard]
    J --> K2[Congestion Page]
    J --> K3[Vessels Page]
    J --> K4[Berths & Cranes Page]
    J --> K5[Yard Capacity Page]
    J --> K6[72-Hour Ops Plan Page]
    J --> K7[Incidents Page]
    J --> K8[Edit Data Page]

    K1 & K2 & K3 & K4 & K5 & K6 & K7 --> L[Apache ECharts 5.4]
    L -->|Bar, Pie, Line, Gantt charts| J

    K8 -->|CRUD edits| E
    E -->|Auto-save on every edit| C
```

## Components

| Component | Technology | Responsibility |
|---|---|---|
| Frontend | [e.g., React 18] | [e.g., Dashboard UI, user interaction] |
| Backend API | [e.g., FastAPI] | [e.g., Business logic, orchestration] |
| AI / ML | [e.g., watsonx.ai] | [e.g., Anomaly scoring, classification] |
| Database | [e.g., PostgreSQL] | [e.g., Storing pipeline events and scores] |
| Notifications | [e.g., Slack API] | [e.g., Alerting on threshold breaches] |

## Data Flow

[Describe how data moves through your system from input to output.]

1. [e.g., Pipeline logs are ingested via a webhook from GitHub Actions]
2. [e.g., Logs are preprocessed and chunked into 512-token segments]
3. [e.g., Each chunk is sent to the watsonx.ai inference endpoint]
4. [e.g., Anomaly scores are stored in PostgreSQL]
5. [e.g., The React dashboard polls the API every 30 seconds to refresh]

## Security Considerations

[Note any security decisions relevant to the architecture — even if basic.]

- [e.g., API keys stored in environment variables, never committed to git]
- [e.g., All API routes require a Bearer token]
- [e.g., Database credentials rotated via IBM Secrets Manager]

## Scalability Notes

[Optional: how would this scale beyond the hackathon prototype?]

[e.g., "The FastAPI backend is stateless and could be horizontally scaled behind a load balancer. The watsonx.ai calls are the bottleneck and would benefit from request batching."]
