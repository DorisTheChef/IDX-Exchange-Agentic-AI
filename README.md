# IDX Exchange Agentic AI

An individual internship project for building a production-oriented, multi-agent real estate assistant with OpenClaw and MLS data.

## Project goals

- Search active property listings using natural-language requests.
- Support multi-turn conversations and remember search preferences.
- Analyze historical sales and market trends.
- Add semantic search, recommendations, and RAG-based answers.
- Integrate WhatsApp and human-approved email workflows.

## Data sources

The application uses two local MySQL tables:

- `rets_property`: active MLS listings.
- `california_sold`: historical sales and comparable transactions.

Raw MLS data, SQL dumps, CSV files, credentials, and generated embeddings are not stored in this repository. See [data/README.md](data/README.md) for the local import policy.

## Repository structure

```text
docs/           Architecture and project documentation
src/agents/     Specialized AI agents
src/skills/     OpenClaw skills
src/tools/      Agent-callable tools
src/database/   Database connection and query modules
src/channels/   WhatsApp and email channel integrations
tests/          Automated tests
data/           Import documentation only; no raw data
```

## Initial setup

1. Copy `.env.example` to `.env` and fill in local credentials.
2. Install Node.js dependencies with `npm install`.
3. Create a Python virtual environment and install `requirements.txt`.
4. Import the two MLS datasets into a local MySQL database by following `data/README.md`.

Detailed runtime and OpenClaw setup instructions will be added during Week 0.

## Security

- Never commit `.env`, API keys, passwords, authentication sessions, or QR codes.
- Never commit CSV files, SQL dumps, raw MLS records, or embedding files.
- Use parameterized SQL queries for all user-controlled filters.
- Require explicit human approval before sending email or performing outbound actions.

## Status

Week 0: repository structure and local environment setup.
