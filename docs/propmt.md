You are a Principal Staff Engineer and AI Systems Architect.

Design and implement a production-grade Agent Operating System (Agent OS) that is modular, scalable, and extensible.

The system must support multiple domains (Investment OS, Crypto OS, Founder OS, Developer OS) while sharing a common platform architecture.

## Goals

Build a long-term AI platform, not a chatbot.

The system must support:

* AI agents
* workflows
* memory
* tools
* multi-model routing
* background jobs
* future autonomous automation

The architecture should remain stable even when new domains are added.

---

# Tech Stack

Frontend:

* Next.js
* TypeScript
* Tailwind
* shadcn/ui

Backend:

* Node.js
* TypeScript
* Fastify

Database:

* PostgreSQL
* pgvector

Cache / Queue:

* Redis

Agent Runtime:

* LangGraph

Containerization:

* Docker
* Docker Compose

Future:

* Docker Swarm
* Kubernetes

---

# Core Principles

1. Modular Monolith First

Build as a modular monolith.

Do NOT create microservices.

Each domain should be isolated into modules.

Example:

modules/
├── investment
├── crypto
├── founder
└── coding

Modules can later become services.

---

2. Provider Agnostic AI Layer

Create a provider abstraction.

interface AIProvider {
generate(request): Promise<Response>
}

Implement:

* OpenAI
* Anthropic
* Gemini
* xAI

The rest of the system must never know which provider is used.

---

3. Smart Model Router

Build a Model Router.

Responsibilities:

* provider selection
* fallback handling
* latency optimization
* cost optimization

Examples:

coding -> OpenAI
research -> Anthropic
cheap tasks -> Gemini
real-time tasks -> xAI

---

4. Agent Orchestrator

Create a central orchestrator.

Responsibilities:

* execute workflows
* manage state
* route tasks
* coordinate agents

Components:

* Planner
* Workflow Engine
* State Manager
* Task Router

---

5. Memory System

Create a long-term memory layer.

Storage:

* PostgreSQL
* pgvector

Memory Types:

* conversations
* research
* investment theses
* decisions
* notes
* knowledge

Support:

* semantic search
* retrieval
* memory updates

---

6. Workflow Engine

Use LangGraph.

Support:

* branching
* retries
* checkpoints
* human approval
* parallel execution

Example workflows:

Research Workflow
Portfolio Workflow
Crypto Workflow
Coding Workflow

---

7. Tool System

Create a plugin architecture.

interface Tool {
execute(input): Promise<Output>
}

Tools:

* Browser
* GitHub
* PostgreSQL
* Market Data
* News
* SEC Filings
* Filesystem

Support MCP.

---

8. Background Jobs

Worker service.

Responsibilities:

* research scans
* portfolio updates
* alerts
* summarization

Queue:

Redis

---

9. Investment OS (First Domain)

Build first-class support for investing.

Entities:

* portfolio
* watchlist
* positions
* transactions
* research
* earnings
* alerts

Features:

* stock analysis
* investment thesis tracking
* watchlist monitoring
* earnings summaries
* catalyst tracking

---

10. API Layer

Fastify API.

Features:

* auth
* streaming
* rate limiting
* RBAC

Expose:

/chat
/workflows
/memory
/tools
/portfolio
/watchlist

---

11. Frontend

Next.js dashboard.

Pages:

* Chat
* Portfolio
* Research
* Watchlist
* Workflows
* Memory
* Settings

Use clean modern SaaS design.

---

12. CLI

Create a CLI client.

Commands:

agent chat
agent research TSLA
agent portfolio
agent memory search
agent workflow run

CLI and Web must use the same backend.

---

13. Infrastructure

Docker Compose.

Containers:

* web
* api
* worker
* postgres
* redis

Use bind mounts.

Create:

docker-compose.yml
Dockerfiles
.env.example

---

14. Observability

Implement:

* structured logging
* tracing
* metrics
* audit logs

Track:

* token usage
* model costs
* workflow execution
* tool execution

---

15. Deliverables

Generate:

1. Complete architecture
2. Folder structure
3. Database schema
4. TypeScript interfaces
5. Docker setup
6. LangGraph workflows
7. API design
8. Frontend architecture
9. CLI architecture
10. Step-by-step implementation plan

Focus on maintainability, extensibility, and production readiness.

The platform should be capable of evolving into a personal AI operating system over multiple years without requiring a major architectural rewrite.
