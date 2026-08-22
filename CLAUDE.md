# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# Stock Agent — Project Context Prompt

I am building a **production-style AI Stock Research Agent** as both a useful personal investment research tool and a side project for developing stronger **AI Engineering, MLE, Data Engineering, and Software Engineering** skills.

When helping me with this project, do not optimize only for getting features working. Help me learn and practice **production engineering habits** including Git workflows, Linux, Docker, testing, deployment, CI/CD, debugging, and system design.

## 1. Development Environment

### Local Development

* macOS
* VS Code
* Terminal / zsh
* Python 3.12
* Git / GitHub
* Docker Desktop
* Docker Compose
* SSH / SCP
* Homebrew
* Conda is installed, but project dependencies should NOT be installed directly into the global `base` environment.

### Deployment Environment

Eventually deploy the application to a **Linux Ubuntu VM** on a cloud provider such as GCP or AWS.

Target workflow:

```text
Mac
 ↓
Feature Branch
 ↓
GitHub PR
 ↓
Squash Merge
 ↓
main
 ↓
CI/CD
 ↓
Docker Image
 ↓
Linux VM
 ↓
Running Stock Agent
```

I specifically want hands-on practice with:

* Git branches
* PRs
* squash merge
* rebase
* merge conflicts
* deleting merged branches
* GitHub workflows
* SSH / SCP
* Linux commands and permissions
* processes/services
* Docker images and containers
* Docker Compose
* logs and production debugging
* environment variables / secrets
* CI/CD
* deployment
* monitoring

Do not abstract these things away unnecessarily. When appropriate, explain what each command does and let me perform the workflow myself.

---

# 2. MVP 1 — Production Data Pipeline

## Objective

Build a reliable foundation that automatically collects and stores market/research data.

Potential data:

* Stock prices
* Company fundamentals
* Financial statements
* News
* Insider transactions
* Economic indicators

Initial scope should remain small. Start with a few tickers and expand later.

Architecture should initially favor simplicity, e.g.:

```text
Data Sources
     ↓
Python Ingestion
     ↓
Validation / Transformation
     ↓
DuckDB / PostgreSQL
     ↓
Stock Agent
```

### Engineering Goals

Practice:

* Python project structure
* dependency/environment management
* Git workflow
* Docker
* logging
* configuration
* testing
* scheduling
* error handling
* Linux deployment

### OKR 1 — Reliable Data Foundation

**Objective:** Build a reliable, reproducible stock-data pipeline.

Key Results:

* Support at least 20 tickers by the end of MVP 1
* Automatically run daily
* Implement logging and meaningful error handling
* Retry recoverable failures
* Add unit tests for core business/data logic
* Run the entire pipeline inside Docker
* Make local setup reproducible from the README
* Successfully deploy and run it on an Ubuntu VM

---

# 3. MVP 2 — AI Stock Research Agent

## Objective

Build an AI research assistant on top of the data platform.

Example questions:

> Why did NVDA fall today?

> What changed in this company's fundamentals?

> What are the major risks to this investment thesis?

> Summarize the important developments for this company over the last month.

Agent workflow:

```text
User Question
     ↓
Planner / Agent
     ↓
Retrieve Internal Data
     +
External Research
     ↓
Reasoning / Analysis
     ↓
Source-grounded Answer
```

Potential technologies:

* LLM APIs
* Tool calling
* RAG
* embeddings/vector search when justified
* agent orchestration such as LangGraph if complexity warrants it

Avoid adding technologies simply because they are fashionable. Prefer the simplest architecture that solves the problem.

### OKR 2 — AI Research Analyst

**Objective:** Build a useful, evidence-grounded AI stock analyst.

Key Results:

* Answer company-specific research questions
* Perform multi-step research workflows
* Cite/source important factual claims
* Retrieve historical company information
* Combine structured financial data with unstructured news/research
* Evaluate agent outputs with repeatable test cases
* Maintain previous research/history where useful
* Produce useful research reports rather than generic LLM summaries

---

# 4. MVP 3 — Personal Portfolio Copilot

## Objective

Turn the research agent into a tool I actually use regularly.

Capabilities may include:

* Portfolio tracking
* Position analysis
* Sector/concentration exposure
* Risk analysis
* Watchlists
* Trade journal
* Daily market/company briefing
* Weekly portfolio review

Example questions:

> What happened to my portfolio today?

> Which positions had material developments?

> What should I pay attention to tomorrow?

> Where am I overly concentrated?

> Has anything happened that challenges one of my investment theses?

### OKR 3 — Useful Personal Investment Copilot

**Objective:** Create a system useful enough that I personally use it every week.

Key Results:

* Track my portfolio/watchlist
* Generate automated daily briefings
* Generate a weekly portfolio/research report
* Maintain an investment/trade journal
* Analyze portfolio concentration and exposure
* Connect important news/events to affected holdings
* Reduce irrelevant information instead of simply summarizing everything

---

# 5. Production Engineering Objective

Production engineering should evolve throughout all three MVPs rather than being postponed until the end.

### OKR 4 — Production-Ready Engineering

**Objective:** Learn to operate the project like a real software system.

Key Results:

* Feature branch → PR → squash merge workflow
* Delete merged branches and keep `main` clean
* Automated unit/integration tests
* GitHub Actions CI
* Dockerized application
* Linux VM deployment
* Health checks
* Structured logs
* Error notifications
* Secrets/configuration separated from source code
* Reproducible deployment
* Basic monitoring
* Practice diagnosing intentionally introduced failures

Examples of failures I should eventually learn to diagnose:

```text
Container crashed
API unavailable
API key missing
Scheduler stopped
VM restarted
Disk full
Network timeout
Bad deployment
Dependency failure
Data pipeline partially failed
```

---

# 6. Possible Future MVPs

Only pursue these after MVPs 1–3 provide real value.

### Multi-Agent Research System

Potential specialized agents:

```text
Research Agent
News Agent
Fundamental Agent
Macro Agent
Risk Agent
Portfolio Agent
        ↓
Coordinator / Planner
        ↓
Research Report
```

Do NOT introduce multiple agents unless specialization clearly improves reliability, maintainability, or quality.

### Web Application

Possible future architecture:

```text
Frontend
   ↓
FastAPI
   ↓
Agent / Data Services
   ↓
PostgreSQL
   ↓
Docker
   ↓
Linux VM / Cloud
```

Potential UI:

* Chat
* Portfolio
* Watchlist
* Research reports
* Charts
* Alerts

---

# 7. How I Want You to Help Me

Treat this as a **learning project, not merely a code-generation project**.

When I ask you to implement something:

1. Tell me where it belongs in the architecture.
2. Explain the relevant engineering concept briefly.
3. Recommend an appropriate Git branch name.
4. Break large changes into small commits when appropriate.
5. Give me commands I can execute myself.
6. Explain potentially destructive commands before I run them.
7. Prefer production-style practices without unnecessary enterprise complexity.
8. Help me debug errors rather than immediately replacing everything with new code.
9. Point out when I am overengineering.
10. Keep track of which MVP/OKR the work contributes toward.

For Git specifically, reinforce the workflow:

```text
git checkout main
git pull
        ↓
create feature branch
        ↓
develop
        ↓
test
        ↓
commit
        ↓
push
        ↓
PR
        ↓
squash merge
        ↓
delete remote branch
        ↓
checkout main
        ↓
pull
        ↓
delete local branch
```

For infrastructure, progressively teach me:

```text
Local Mac
    ↓
Docker
    ↓
Linux VM
    ↓
SSH / SCP
    ↓
Manual Deployment
    ↓
CI
    ↓
Automated Deployment
    ↓
Monitoring
```

Do not skip directly to fully automated infrastructure because part of the purpose of this project is for me to understand what the automation is actually doing.

## North Star

> Build a production-quality AI stock research system that I genuinely use, while developing the engineering judgment and hands-on skills expected from a strong Senior Data Engineer / MLE / Applied AI Engineer.

