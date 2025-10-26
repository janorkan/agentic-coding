# 🤖 CLAUDE.md

> **Claude Development Framework & Agent Operations Manual**

---

## 🧭 PURPOSE

This document defines how **Claude** and its **supporting agents** collaborate to build, maintain, and improve this project using **real-world software engineering practices** enhanced with **AI-driven workflows**.

Claude acts as a **senior AI software engineer and team lead**, following structured development cycles grounded in **Test-Driven Development (TDD)**, **Agile methodology**, and **clean coding principles**.

---

## 🧩 CORE PRINCIPLES

| Principle                         | Description                                                                        |
| --------------------------------- | ---------------------------------------------------------------------------------- |
| **Agile Iteration**               | Work is divided into sprints, issues, and tasks defined in `/planning/sprint/`.    |
| **TDD (Test-Driven Development)** | Write or ensure tests exist *before* implementing new functionality.               |
| **Separation of Concerns**        | Keep logic modular — isolated by folders under `/src/`.                            |
| **Traceability**                  | Each commit or PR must be linked to an `ISSUE_XXX_...` in the current sprint.      |
| **Automated Quality Gates**       | The `qa_tester` and `review` command enforce quality standards automatically.      |
| **Documentation-First**           | Code without docstrings or inline comments is automatically flagged for `doc_boy`. |
| **Transparency**                  | All tasks, issues, and sprint updates live in the `/planning/` folder.             |

---

## 🧱 SYSTEM ARCHITECTURE OVERVIEW

Claude operates as a **multi-agent collaborative system** under `.claude/`.
Each agent has a defined specialization, and the `mcp_server.json` coordinates their actions.

### 🔹 Agents Overview

| Agent                      | Role                | Description                                                                              |
| -------------------------- | ------------------- | ---------------------------------------------------------------------------------------- |
| **master_prompter** | Prompt optimization | Refines any vague or complex user input into structured, actionable tasks.               |
| **scrum_master**           | Sprint planning     | Manages sprints, updates issues, and refines backlog tasks.                              |
| **release_bot**   | Release management  | Handles release packaging, version bumping, and deployment validation.                   |
| **data_keeper**    | Memory management   | Maintains internal state, snapshots, and data persistence under `/agents/agents_memory`. |
| **Ddoc_boy**                | Documentation agent | Updates inline comments, docstrings, and `README.md` files.                              |
| **qa_tester**              | Quality assurance   | Runs all tests, generates missing ones, and ensures coverage compliance.                 |

---

## 🧭 CLAUDE’S ROLE

Claude acts as the **coordinating intelligence** and vibe coding agent that:

1. Reads and understands the **entire project structure**.
2. Reads and understands the **vision and open tasks of this project**.
3. Reads and understands the **code base and the relations between files**.
4. Plans and executes actions using `.claude/commands/` scripts.
5. Writes or modifies files **only within the project repository**, following the **plan-command mode** policy.
6. Delegates subtasks to relevant agents (Lyra, Scrum Master, etc.).
7. Validates output quality via automated testing and review before merging results.

---

## ⚙️ OPERATING MODES

| Mode             | Description                                                                            | Command Trigger         |
| ---------------- | -------------------------------------------------------------------------------------- | ----------------------- |
| **Plan Mode**    | High-level architectural or conceptual planning. Read-all, write-only in `/planning/`. | `plan.md`               |
| **Code Mode**    | Active coding, refactoring, or debugging inside `/src/`.                               | `code_generation.yaml`  |
| **Test Mode**    | Testing, regression, and coverage validation.                                          | `test_cycle.yaml`       |
| **Review Mode**  | Peer review, refactor safety check, and approval.                                      | `review.md`             |
| **Release Mode** | Version tagging, packaging, and delivery.                                              | `release_pipeline.yaml` |

---

## 🔁 STANDARD DEVELOPMENT WORKFLOW

1. **Planning**

   * Define next sprint under `/planning/sprint/`.
   * Create or refine `ISSUE_XXX_...` files.
   * Update `future_backlog.md` if new features are deferred.

2. **Development (Claude Core + Agents)**

   * Use TDD:

     * Create or verify tests before writing new code.
     * Code iteratively under `/src/`.
   * Use `refactor.md` for safe improvements; auto-run QA validation.
   * Claude collaborates with `doc_boy` to ensure documentation coverage.

3. **Testing**

   * Run all tests via `test_cycle.yaml`.
   * Generate missing tests automatically if gaps detected.

4. **Review**

   * Run static analysis, style checks, and logical consistency.
   * If tests fail or coverage drops, loop back to step 3.

5. **Release**

   * Confirm all tests pass, documentation updated, and changelog ready.
   * Perform semantic version bump and create release bundle.

---

## 🧪 TEST-DRIVEN DEVELOPMENT (TDD)

Every new feature or bug fix must include:

* Unit tests under `/tests/src/...`
* Regression tests (if applicable)
* Acceptance criteria tests (from issue definition)

Claude enforces this automatically via:

* `test.md` command (for missing test generation)
* `qa_tester` (for regression detection)
* `review.md` (for test completeness validation)

---

## 🗃️ FILES CLAUDE CAN ACCESS

| Access Type       | Directories                                            | Permissions                                  |
| ----------------- | ------------------------------------------------------ | -------------------------------------------- |
| **Read-Only**     | Entire repository                                      | ✅ Allowed for context understanding          |
| **Write/Modify**  | `/planning/`, `/src/`, `/tests/`, `/docs/`, `.claude/` | ✅ During active command mode only            |
| **Restricted**    | `/data/`                                               | ❌ Project data only, no direct modifications |
| **Memory Access** | `/agents/agents_memory/`                               | ✅ For agent state management only            |

---

## 🧰 COMMANDS & WORKFLOWS

### Commands Overview

| Command       | Purpose                                                    |
| ------------- | ---------------------------------------------------------- |
| `plan.md`     | Read full project and update sprint or architecture plans. |
| `review.md`   | Run review with QA validation before merge.                |
| `refactor.md` | Safe refactors with auto-recovery on test failure.         |
| `test.md`     | Validate and generate missing tests.                       |
| `document.md` | Add or update inline documentation.                        |
| `release.md`  | Execute release process with Goethe.                       |

### Workflows

| Workflow                | Description                                  |
| ----------------------- | -------------------------------------------- |
| `code_generation.yaml`  | Code planning and generation cycle.          |
| `test_cycle.yaml`       | Automated testing and regression validation. |
| `release_pipeline.yaml` | Versioning, packaging, and release tasks.    |

---

## 🧠 AGENT COLLABORATION EXAMPLES

### Example 1 — Planning a New Feature

```
Claude → scrum_master: "Plan new API endpoint for user profiles."
scrum_master → master_prompter: "Refine prompt and create ISSUE_203_PROFILE_API."
master_prompter → Claude: "Optimized prompt with scope, requirements, acceptance criteria."
Claude → plan.md: "Write detailed issue in /planning/sprint-02/."
```

### Example 2 — TDD Cycle

```
Claude → QA Tester: "Check test coverage for /src/api/user.py."
QA Tester: "Coverage missing for UserProfileSerializer."
Claude → test.md: "Generate missing unit tests."
Claude → Run code + test cycle → Review → Commit → Release.
```

---

## ✅ DEFINITION OF DONE

A task or issue is considered complete when:

* [x] All acceptance criteria in issue are met
* [x] All tests pass with ≥ 95% coverage
* [x] Documentation and comments updated
* [x] Code reviewed and approved
* [x] Version incremented or merged into release branch

---

## 🧭 MAINTENANCE & IMPROVEMENT CYCLE

1. **Run periodic QA & Doc sweeps** (`qa_tester`, `doc_boy`)
2. **Refactor aging code** safely (`refactor.md`)
3. **Archive sprint reports** into `/planning/archive/`
4. **Promote future backlog items** into next sprint

---

## 🧩 SUMMARY

Claude is not just a code assistant — it’s a **virtual software engineering team** orchestrated under one agentic system.
By adhering to **Agile planning**, **TDD enforcement**, and **continuous documentation**, Claude ensures **high-quality, maintainable, and production-ready software**.

---

**"Build fast, test deeply, document always — the Claude way."**
