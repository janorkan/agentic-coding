# 🧠 Claude Coding Framework

> **An Agentic, Test-Driven AI Software Engineering System**

---

## 🚀 Overview

The **Claude Coding Framework** is a next-generation, agentic development environment that merges
**real-world software-engineering best practices** with **AI-driven automation**.

It’s engineered for:

* **Agentic coding** with collaborative AI agents
* **Agile project management** through sprints and issues
* **Test-Driven Development (TDD)** as a default workflow
* **Continuous documentation, review, and release automation**

Claude acts as the **core engineering intelligence**, orchestrating all operations across agents, workflows, and project folders.

---

# 🚀 How to Start a New Project

> **Kick off your Claude Coding Framework project efficiently**

---

## 1️⃣ Initialize the Project

Create a new folder and copy the framework structure:

```bash
mkdir my_project && cd my_project
git clone <claude-coding-framework-template> .
```

This sets up folders like `.claude/`, `planning/`, `src/`, `tests/`, and `docs/`.

---

## 2️⃣ Define Your Vision

Open `/planning/vision.md` and describe:

* 🎯 **Goal & Purpose**
* 🧱 **Architecture & Principles**
* ⚙️ **Tools & Libraries**
* 🧩 **Initial Requirements**

This gives Claude and your agents a clear foundation.

---

## 3️⃣ Build the Future Backlog

Edit `/planning/future_backlog.md` and add short user stories:

```
As a [user], I want [goal] so that [benefit].
```

Include priority and short notes for each planned feature.

---

## 4️⃣ Plan the First Sprint

Create the first sprint folder:

```bash
/planning/sprint/sprint-01/
```

Use the **Scrum Master** agent to refine tasks:

```bash
claude plan --sprint 01
```

He’ll move items from the backlog into structured issues:

```
ISSUE_101_FEATURE_X.md
ISSUE_102_FEATURE_Y.md
```

---

## 5️⃣ Start Development

Work issue by issue using TDD:

1. Write or verify tests in `/tests/`
2. Implement code in `/src/`
3. Run QA with `claude test`
4. Review with `claude review`

---

## ✅ Sprint Completion

When all issues are done:

```bash
claude document && claude release
```

This updates documentation and prepares the next sprint.


```

Claude will:

1. Read `/planning/sprint/.../ISSUE_101_NEW_FEATURE.md`
2. Generate or verify matching tests in `/tests/src/...`
3. Implement feature code under `/src/...`
4. Run automated test cycle
5. Document results

### 7️⃣ Run Full Test Cycle

```bash
> claude test --all
```

The **QA Tester agent**:

* Checks for missing unit or regression tests
* Runs all tests in `/tests/`
* Auto-generates missing coverage if needed

### 8️⃣ Review, Document, and Release

```bash
> claude review && claude document && claude release
```

This sequentially:

* Runs the **Review Command** (`review.md`)
* Updates documentation and code comments via **Doc Boy**
* Executes the **Release Bot (Goethe)** for packaging and version tagging

---

## 🧩 Core Capabilities

| Capability                   | Description                                     |
| ---------------------------- | ----------------------------------------------- |
| **Agile Sprint Management**  | Manage sprints and issues via `/planning/`.     |
| **TDD Enforcement**          | Requires unit tests before implementation.      |
| **Autonomous Agents**        | Specialized agents collaborate for each domain. |
| **Safe Refactoring**         | Auto rollback on failed tests.                  |
| **Documentation Automation** | Docstrings and READMEs updated automatically.   |
| **Continuous Integration**   | YAML workflows for build, test, and release.    |

---

## 🧠 Agent System Overview

| Agent            |  Purpose                                                    |
| ---------------- | ---------------------------------------------------------- |
| `master_prompter`  | Optimizes prompts for clarity and actionability.           |
| `scrum_maser` | Manages sprints, issues, and backlog.                      |
| `data_keeper`     | Handles embeddings and memory in `/agents/agents_memory/`. |
| `doc_boy`    | Writes inline comments and updates docs.                   |
| `qa_tester`   | Runs tests, detects missing coverage, creates regressions. |
| `release_bot`     | Builds, tests, and bumps release versions.                 |

---

## ⚙️ Command System

| Command       | Purpose                                   |
| ------------- | ----------------------------------------- |
| `plan.md`     | Strategic planning and sprint management. |
| `review.md`   | Code review and logic validation.         |
| `refactor.md` | Safe automated refactors.                 |
| `test.md`     | Test validation and generation.           |
| `document.md` | Code documentation and docstring updates. |
| `release.md`  | Executes release pipelines.               |

---

## 🔁 Development Workflow

1. **📋 Planning** – Define new sprints and issues under `/planning/sprint/`.
2. **🧠 Optimization** – Lyra structures high-level tasks into detailed specs.
3. **💻 Development** – Claude writes code with test-first principles.
4. **🧪 Testing** – QA Tester ensures full coverage.
5. **🔍 Review** – Review command ensures structure, quality, and style.
6. **🚀 Release** – Goethe builds, tags, and deploys the final version.

---

## 🧱 Folder Structure

```
project-root/
├── planning/               # Vision, backlog, and sprint issues
│   ├── vision.md
│   ├── future_backlog.md
│   └── sprint/
│       └── sprint-01/
│           ├── ISSUE_101_FEATURE.md
│           └── ISSUE_102_FIX.md
│
├── .claude/                # Agent configuration and operations
│   ├── agents/             # Agent definitions (Lyra, Brian, Goethe, etc.)
│   ├── commands/           # Operational command files
│   ├── workflows/          # YAML build/test/release automation
│   ├── skills/             # Skill modules for agent extensions
│   └── mcp_server.json     # Multi-agent communication server
│
├── src/                    # Source code
│   ├── agents/
│   ├── core/
│   ├── api/
│   ├── infra/
│   ├── frontend/
│   └── tools/
│
├── tests/                  # Tests mirror /src/ structure
│   ├── src/
│   ├── specs/
│   ├── regression/
│   └── benchmarks/
│
├── data/                   # Project data (not agent memory)
│   ├── raw/
│   ├── database/
│   └── output/
│
├── agents/agents_memory/   # Agent state, embeddings, logs
├── docs/                   # Documentation (ADR, architecture, tutorials)
├── ops/                    # Deployment, CI/CD configs
├── configs/                # Config presets and environment settings
├── research/               # Experiments and transcripts
│
├── CLAUDE.md               # Operations manual
├── README.md               # This file
├── .env                    # Secrets
├── .env.example
└── requirements.txt
```

---

## 🧭 Engineering Philosophy

| Principle                 | Description                                          |
| ------------------------- | ---------------------------------------------------- |
| **TDD First**             | Write tests before code for stability.               |
| **Iterative Development** | Progress in small, reviewable sprints.               |
| **Documentation as Code** | Keep documentation up to date automatically.         |
| **Agent Collaboration**   | Each AI agent performs one specialized function.     |
| **Safety by Design**      | Auto rollback on test failure, version-safe changes. |

---

## 🧩 Example Commands

```bash
# Plan next sprint
claude plan --next-sprint

# Work on a specific issue
claude code --from ISSUE_203_API_FEATURE

# Run tests and regressions
claude test --all

# Generate docs and comments
claude document

# Execute safe refactor
claude refactor --safe

# Release build
claude release
```

---

## 🧩 Integrations

* **GitHub Actions / CI** → Integrate `.claude/workflows/` pipelines
* **Claude API** → Orchestrates agent collaboration
* **Python CLI** → Local TDD testing and code execution

---

## ✅ Definition of Success

> A project built with the **Claude Coding Framework** operates like a real, autonomous dev team:
>
> * Tasks planned and tracked in sprints
> * Tests and docs always current
> * Refactors safe and reversible
> * Releases stable, documented, and traceable

**Build fast. Test deep. Ship clean. — The Software Enginnering Quality Way.**
