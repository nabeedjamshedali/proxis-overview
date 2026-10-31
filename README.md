# Proxis: AI Operations Assistant for Teams

> **Status: in active development (Final Year Project).** The source code is private for security reasons. This repository is a public overview only. Access to a demo or the code can be given on request.

Proxis connects to the tools a team already uses (Jira, Slack, Microsoft Teams, calendars) and answers questions about the work in plain language: *what is delayed and why, who is free today, what changed since yesterday*. Answers come from real records, not guesses. Any action it proposes (create a task, assign it, post a message) happens only after a person approves it.

## What it does today

- **Ask about your work in plain language.** Project updates, delays and their causes, daily briefings, and who is free or best suited for a task.
- **Grounded answers.** Responses are built from synced Jira data and live Slack/Teams channel reads, not from model memory.
- **Per-person project access.** Admins decide which projects each person can ask about. Someone without access to a project gets "couldn't find a project" instead of a leak.
- **Approval before changes.** Proposed actions wait in an approval queue and expire if unattended.
- **Sign in to connect.** Jira (Atlassian) and Slack connect through OAuth, with API tokens as a fallback.
- **Typo-tolerant project matching.** "atlus checkout" still finds the right project; unclear matches ask "Did you mean X or Y?".

## Planned

- **Meeting stand-in:** an agent that attends a recurring meeting on a user's behalf, shares status updates, and can be tagged live to propose solutions using Slack/Jira context.
- Continuous voice conversations.

## Architecture

```
Browser -> Next.js web app -> FastAPI backend -> PostgreSQL + Redis
                                   |
                                   +-> LangGraph agent -> LLM provider (configurable)
                                   |
                                   +-> Jira / Slack / Teams / Calendar connectors
```

## Tech stack

| Layer | Technology |
|---|---|
| Backend | Python 3.12, FastAPI, SQLAlchemy (async), Alembic, arq background jobs |
| Agent | LangGraph, LangChain, configurable LLM providers |
| Data | PostgreSQL, Redis |
| Frontend | Next.js 15, React 19, TypeScript, Tailwind CSS |
| Quality | pytest (unit tests), Vitest, Playwright end-to-end tests |
| Infra | Docker Compose |

## My role

Conceived the project, lead the team, and lead the AI and backend architecture. A small team implements the system with my direction.

## Contact

Nabeed Ali, [LinkedIn](https://linkedin.com/in/nabeed-jamshed), [GitHub](https://github.com/nabeedjamshedali)
