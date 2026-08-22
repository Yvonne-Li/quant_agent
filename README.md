# Stock Agent
I am building a **production-style AI Stock Research Agent** as both a useful personal investment research tool and a side project for developing stronger **AI Engineering, MLE, Data Engineering, and Software Engineering** skills.

When helping me with this project, do not optimize only for getting features working. Help me learn and practice **production engineering habits** including Git workflows, Linux, Docker, testing, deployment, CI/CD, debugging, and system design.

# Roadmap
## MVP 1 — Production Data Pipeline
Build a reliable pipeline for collecting and storing market data.

## MVP 2 — AI Research Agent
Build an evidence-grounded AI agent for stock research.

## MVP 3 — Portfolio Copilot
Build a personalized portfolio monitoring and research system.



## MVP 1 — Production Data Pipeline

### OKR 1: Build a reliable, reproducible stock-data pipeline

- [ ] Support 20+ tickers
- [ ] Daily scheduled run
- [ ] Logging and error handling
- [ ] Retry recoverable failures
- [ ] Unit tests for core logic
- [ ] Run pipeline in Docker
- [ ] Reproducible local setup
- [ ] Deploy to Ubuntu VM

## Github Issue
#1 Set up Python project structure

#2 Implement market data ingestion

#3 Add DuckDB storage

#4 Support configurable ticker list

#5 Add logging and error handling

#6 Add retry mechanism

#7 Add unit tests

#8 Dockerize pipeline

#9 Add daily scheduler

#10 Deploy to Ubuntu VM

## deployment workflow
GitHub Issue #2
      ↓
feature/market-data-ingestion
      ↓
code
      ↓
test
      ↓
commit
      ↓
PR
      ↓
Squash Merge
      ↓
Issue #2 closed
      ↓
delete branch

## relationship between issue and PR
MVP 1
└── OKR 1
    │
    ├── Issue #1
    │    └── feature/project-setup
    │         ├── commit
    │         └── commit
    │
    ├── Issue #2
    │    └── feature/market-data-ingestion
    │
    └── Issue #3
         └── feature/duckdb-storage