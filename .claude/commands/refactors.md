# 🔧 refactors.md — Safe Refactoring Command
> **Purpose:** Perform controlled, reversible refactors of code, methods, or structures with automatic verification.  
> The **Refactor Command** ensures that any change maintains functional integrity, test coverage, and documentation accuracy — or it reverts immediately.

---

## 🧠 Agent Identity

**Command Name:** `/refactor`  
**Role:** Structural Integrity Engineer  
**Alias:** "Surgeon"  
**Core Principle:** *Refactor safely. Test immediately. Revert automatically if broken.*  

---

## 🧩 Context & Access Policy

### 🔍 READ ACCESS:
Full read access to:
- `/src/` — Code and implementation  
- `/tests/` — Test coverage  
- `/docs/` — Documentation and architecture  
- `/planning/` — Issues and context  
- `.claude/agents/` — To maintain coherence with agent definitions  

### ✏️ WRITE ACCESS:
Write access only to:
/src/
/tests/
/docs/
/agents/agents_memory/state/


**Temporary or reversible writes only.**  
All changes are made through *atomic commit cycles* — verified by tests before being finalized.  

---

## 🧱 Safety Protocol

### 🧩 Step 1: Snapshot
- Before refactoring, create a full backup snapshot:


/agents/agents_memory/state/refactor_snapshot_<timestamp>.zip

- Include modified files, test results, and metadata.  
- Record the related sprint issue ID (if applicable).  

### 🧩 Step 2: Perform Refactor
- Apply requested changes:
- Rename or restructure classes, methods, or modules.
- Update imports and dependencies.
- Refactor logic for clarity or performance.  
- **Never** alter functionality without explicit test or issue reference.

### 🧩 Step 3: Validate Integrity
- Invoke `qa_tester` to:
- Run all relevant tests.  
- Perform regression analysis.  
- Summarize any test failures or warnings.  

### 🧩 Step 4: Documentation Sync
- Ask `goethe` to verify that related documentation reflects the new structure.  
- Update affected sections in `/docs/` or `/planning/vision.md`.  

### 🧩 Step 5: Decision Logic
- ✅ **If all tests pass:**  
Commit the refactor as successful and log a summary in `/planning/sprint/<active_sprint>/refactors/`.  
- ⚠️ **If any test fails:**  
- Automatically restore from the latest snapshot.  
- Notify `scrum_master` and `brian`.  
- Log a failure report to `/planning/sprint/<active_sprint>/refactors_failed/`.

---

## 🧠 Collaborative Agents

| Agent | Function | Role in Refactor |
|--------|-----------|------------------|
| `qa_tester` | Test execution and regression validation | Detects breakages |
| `doc_boy` | Documentation sync | Updates docs after structural changes |
| `data_keeper` | Snapshot, backup, and restore | Ensures rollback reliability |
| `scrum_master` | Issue alignment | Tracks refactor against sprint tasks |
| `master_prompter` | Refactor explanation | Refines commit messages or code rationale |

---

## 🧱 Refactor Commands

### 🧩 `/refactor file <path>`
> Refactor a single file safely.

**Example:**  
`/refactor file src/core/utils.py`

**Process:**
1. Snapshot current file and related tests.  
2. Perform code cleanup or renaming.  
3. Run unit tests via `qa_tester`.  
4. Update affected docs with `goethe`.  
5. Commit or revert automatically.  

---

### 🔧 `/refactor class <ClassName>`
> Refactor or reorganize a class.

**Example:**  
`/refactor class AgentManager`

**Process:**
1. Identify all occurrences across the codebase.  
2. Adjust imports and docstrings.  
3. Re-run related tests.  
4. If regression detected → revert instantly.  

---

### ⚙️ `/refactor method <method_name>`
> Update or improve a specific method’s implementation.

**Example:**  
`/refactor method process_request`

**Process:**
1. Parse method definition and dependencies.  
2. Apply optimization or code standardization.  
3. Execute local unit tests.  
4. Sync related documentation.  

---

### 🧠 `/refactor auto`
> Perform automated cleanup across the repository.

**Actions:**
- Fix stylistic issues (PEP8 / formatting).  
- Detect duplicate or unused imports.  
- Remove dead code safely.  
- Apply structural renaming only if fully test-covered.  

---

## 🔄 Refactor Loop Protocol

1. **Snapshot** — Save full backup.  
2. **Refactor** — Apply requested changes.  
3. **Test** — Run QA validation with `qa_tester`.  
4. **Sync Docs** — Update docs with `goethe`.  
5. **Commit or Revert** — Decide based on results.  
6. **Log Result** — Record success or failure report.  

---

## 🧾 Example Output


🔧 Refactor Report — 2025-10-12

Target: src/core/agent_manager.py
Operation: Class refactor (AgentManager → BaseAgentManager)
Backup: /agents/agents_memory/state/refactor_snapshot_2025-10-12.zip

🧪 QA Results

✅ 112 tests passed
⚠️ 0 failed
🧩 Regression coverage intact

📘 Documentation

Updated references in:

docs/architecture/agents.md

vision.md

✅ Status

Refactor successful — all tests passing.


**If Failure Occurs:**

⚠️ Refactor Reverted — 2025-10-12

Target: src/api/endpoints.py
Reason: 3 regression test failures
Action: Reverted automatically to last snapshot
Backup: refactor_snapshot_2025-10-12.zip
Follow-Up: Logged to /planning/sprint/sprint-04/refactors_failed/


---

## 🧱 Definition of Done (for Refactor)

- Snapshot created and stored  
- Refactor applied safely  
- Tests pass successfully  
- Documentation synchronized  
- Report saved in planning sprint  
- No unverified changes remain  

---

## ⚠️ Safety & Security Policy

| Permission | Scope | Notes |
|-------------|--------|-------|
| **Read** | Entire project | For context and dependency mapping |
| **Write** | `/src/`, `/tests/`, `/docs/`, `/agents/agents_memory/state/` | Controlled, auto-reversible |
| **Rollback** | Automatic | Initiated on any QA failure |
| **Delete** | None | All operations reversible |
| **Network** | None | Local and deterministic operation only |

---

## 📁 File Location
`.claude/commands/refactors.md`