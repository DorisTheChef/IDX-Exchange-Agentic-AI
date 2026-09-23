# IDX Exchange Agentic AI

An individual IDX Exchange internship project that builds a production-oriented, multi-agent real estate assistant using OpenClaw and real MLS data.

## Project goals

The final assistant will help users explore California real estate through a conversational interface. It is designed to:

- Search active listings from natural-language requests.
- Remember a user's budget, location, and property preferences across a conversation.
- Analyze historical sales, comparable properties, and market trends.
- Find semantically similar listings using vector embeddings.
- Recommend properties and validate prices against recent sold comparables.
- Answer real estate and MLS questions with retrieval-augmented generation (RAG).
- Coordinate specialized agents through a single OpenClaw entry point.
- Communicate through WhatsApp and prepare emails with a human approval gate.

## Problem being solved

MLS data is large, highly structured, and difficult for non-technical users to query directly. Traditional filters also miss descriptive requests such as "a charming craftsman with mountain views."

This project combines structured SQL filtering, semantic search, market analytics, and conversational memory so a user can search and understand real estate data in ordinary language. A multi-agent architecture separates property search, analytics, recommendations, knowledge retrieval, and communication into focused components.

## Technology stack

- **Agent runtime and orchestration:** OpenClaw
- **Application runtime:** Node.js 20+ and TypeScript/JavaScript
- **Data and ML services:** Python 3, pandas, NumPy, scikit-learn, and SQLAlchemy
- **LLM and embeddings:** OpenAI API
- **Database:** MySQL
- **Communication:** WhatsApp through an OpenClaw channel; email through an approval-controlled workflow
- **Testing and version control:** Node test runner, automated tests, Git, and GitHub

The stack will be refined as the weekly modules are implemented.

## Data sources

The application uses two tables in a local MySQL database:

- **`rets_property`** contains active MLS listings. It supports property search, listing details, structured filters, listing remarks, photos, and semantic matching.
- **`california_sold`** contains historical sold and closed transactions. It supports comparable-property analysis, pricing validation, days-on-market metrics, and market trends.

Raw MLS data is stored outside this repository. See [data/README.md](data/README.md) for the local import policy.

## Repository structure

```text
IDX-Exchange-Agentic-AI/
├── data/              Data import documentation only
├── docs/              Architecture and project documentation
├── src/
│   ├── agents/        Specialized AI agents
│   ├── channels/      WhatsApp and email integrations
│   ├── database/      Database connection and query modules
│   ├── skills/        OpenClaw skills
│   └── tools/         Agent-callable tools
├── tests/             Automated tests
├── .env.example       Environment-variable template
├── .gitignore         Secret, data, and build exclusions
├── package.json       Node.js project configuration
└── requirements.txt   Python dependencies
```

## Current progress

The project is currently in **Week 0: environment setup and configuration**.

- [x] Create the individual project repository.
- [x] Add the initial directory structure.
- [x] Configure rules that exclude secrets and raw data from Git.
- [x] Add the environment-variable template and initial documentation.
- [ ] Install and verify Node.js, Python, MySQL, and OpenClaw.
- [ ] Create the local MySQL database.
- [ ] Import and verify `rets_property` and `california_sold`.
- [ ] Configure required API credentials locally.
- [ ] Connect the OpenClaw WhatsApp channel.
- [ ] Complete an end-to-end test message.

## Installation

### 1. Prerequisites

Install the following locally:

- Git
- Node.js 20 or later and npm
- Python 3 and `venv`
- MySQL
- OpenClaw

### 2. Clone the repository

```bash
git clone https://github.com/DorisTheChef/IDX-Exchange-Agentic-AI.git
cd IDX-Exchange-Agentic-AI
```

### 3. Configure local environment variables

```bash
cp .env.example .env
```

Fill in `.env` with local credentials. Never commit that file.

### 4. Install Node.js dependencies

```bash
npm install
```

### 5. Create the Python environment

```bash
python3 -m venv venv
source venv/bin/activate
python3 -m pip install -r requirements.txt
```

### 6. Prepare the database

Create the local database and import the authorized datasets from a location outside this repository. Follow [data/README.md](data/README.md) for the import outline.

## Running the project

The application entry point will be added as the OpenClaw agents are implemented. During Week 0, verify the local tools and project configuration with:

```bash
node --version
npm --version
python3 --version
mysql --version
openclaw --version
npm test
```

Later milestones will add the exact commands for starting the orchestrator and connecting the WhatsApp channel. This README will be updated as those commands become available.

## Security and data policy

- Never commit `.env`, API keys, passwords, private keys, authentication sessions, or WhatsApp QR codes.
- Never commit CSV files, SQL dumps, database files, raw MLS records, or generated embeddings.
- Keep authorized datasets outside the repository and import them directly into local MySQL.
- Use parameterized SQL queries for every user-controlled database filter.
- Limit query results instead of exporting or bulk-downloading MLS datasets.
- Do not log credentials, personal information, or sensitive record contents.
- Require explicit human approval before sending email or performing another outbound action.

## Architecture

The planned multi-agent flow is documented in [docs/architecture.md](docs/architecture.md).
