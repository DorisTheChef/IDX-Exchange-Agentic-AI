# System Architecture

## Planned flow

```text
User
  |
  v
WhatsApp / Email Channel
  |
  v
OpenClaw Orchestrator
  |-- Property Search Agent ------> rets_property
  |-- Market Statistics Agent ----> california_sold
  |-- Recommendation Agent -------> both MLS tables
  |-- RAG Agent ------------------> indexed reference documents
  `-- Email Draft Agent ----------> approval gate -> email provider
```

## Components

- **Channels:** receive user messages and format outbound responses.
- **Orchestrator:** classifies intent and routes work to one or more agents.
- **Agents:** implement property search, market analytics, recommendations, RAG, and email drafting.
- **Skills and tools:** expose typed operations to agents.
- **Database layer:** provides parameterized, read-only access to the MLS tables.
- **Session memory:** preserves user search preferences during multi-turn conversations.
- **Approval gate:** prevents email from being sent without explicit user confirmation.

This document will be expanded as each weekly module is implemented.
