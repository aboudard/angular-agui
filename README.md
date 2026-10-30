# Agentic UI Journey — AG-UI & A2UI with Angular

A step-by-step learning repository to understand and implement **agentic user interfaces**
with the [AG-UI protocol](https://docs.ag-ui.com) and the [A2UI specification](https://github.com/google/A2UI),
ending with an **Angular** application talking to a **NestJS** backend that hosts a **Mastra** agent (OpenAI).

## Running example

**IT Incident Assistant** — an operator chats with an agent that displays incident cards,
proposes remediation actions for approval, and keeps a shared incident board in sync.

## Repository layout

| Folder    | Content                                                                                   | Introduced in |
|-----------|-------------------------------------------------------------------------------------------|---------------|
| `docs/`   | Concepts, roadmap and per-step notes                                                      | Step 0        |
| `server/` | NestJS AG-UI endpoint (SSE) with a pluggable `AgentRunner`: mock (Steps 1–5), Mastra (6+) | Step 1        |
| `web/`    | Angular application (standalone components, signals)                                      | Step 1        |

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md). Each step is delivered on its own Git tag (`step-0`, `step-1`, ...)
with a short README: goal, what is mocked, how to run it.

## Start here

1. Read [docs/00-concepts.md](docs/00-concepts.md).
2. Follow the steps in order.

## Prerequisites

- Node.js 22+ and npm
- An OpenAI API key (from Step 6 only)
