# 🧪 test.md — QA & Test Coverage Command

> Ensures test coverage, runs tests, and auto-generates missing/regression tests.

---

## ROLE

**Command:** `/test`
**Agent:** QA_Tester
**Goal:** Maintain automated coverage, run tests, and generate missing/regression tests where needed.

---

## ACCESS

**Read:** `/src/`, `/tests/`, `/planning/`, `/docs/`
**Write:** `/tests/`, `/agents/agents_memory/state/`, `/planning/sprint/<active_sprint>/qa_reports/`

---

## WORKFLOW

### 1. Scan & Map

* Parse `/src/` for files, classes, and public methods.
* Map findings to `/tests/` and save coverage map to `/agents/agents_memory/state/test_coverage_map.json`.

### 2. Check Coverage

* Detect missing or outdated tests and list untested targets.

### 3. Generate Missing Tests

* Auto-create test scaffolds under `/tests/` using signatures and docstrings.
* Example scaffold:

```python
def test_<method_name>():
    """Auto-generated test for <method_name>."""
    result = <call_method>()
    assert result is not None
```

### 4. Regression Tests

* Diff current code against last `brian` snapshot.
* Create regression tests under `/tests/regression/` for modified logic.

### 5. Run Tests

* Execute tests (pytest by default).
* Save report to `/planning/sprint/<active_sprint>/qa_reports/test_report_<date>.md`.

---

## COOPERATING AGENTS

* `brian` — provide snapshots/diffs for regression.
* `master_prompter` — refine auto-generated test prompts/scaffolds.
* `refactor` — rollback or fix if tests fail after refactor.
* `scrum_master` — link QA results to sprint issues.

---

## COMMANDS

* `/test all` — Full scan, generate missing tests, run suite, produce report.
* `/test file <path>` — Validate and test a single file.
* `/test class <ClassName>` — Validate and test a class and its methods.
* `/test regression` — Create/run regression tests for changed code.
* `/test summary` — Produce concise sprint QA summary:

```
✅ Passed: 243 | ⚠️ Failed: 5 | 🧩 New Tests: 7 | Coverage: 95.2%
```

---

## DONE WHEN

* All methods have tests (or scaffolds exist).
* Regression tests created for changed code.
* Tests executed and passing (or failures logged).
* Report stored and linked to the active sprint.

---

## LOCATION

`.claude/commands/test.md`
