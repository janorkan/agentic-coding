# 🧾 document.md — Documentation & Code Comment Command

> Maintains and generates consistent documentation across project files.
> Ensures inline comments, docstrings, and high-level documentation stay up to date with current code.

---

## ROLE

**Command:** `/document`
**Agent:** Doc_Boy
**Goal:** Keep project documentation accurate, structured, and synchronized with the source code.

---

## ACCESS

**Read:** `/src/`, `/tests/`, `/docs/`, `/planning/`
**Write:** `/docs/`, `/src/`, `/agents/agents_memory/state/`

---

## WORKFLOW

### 1. Analyze Source Code

* Scan `/src/` and `/tools/` for files missing docstrings or inline comments.
* Identify outdated or incomplete function/class documentation.
* Build a **Documentation Coverage Map**:

  ```
  /agents/agents_memory/state/doc_coverage_map.json
  ```

### 2. Generate & Update Documentation

* Add or refresh:

  * **Inline comments** for key logic blocks
  * **Docstrings** for all functions and classes
  * **File headers** with summaries and author metadata
* Use consistent Markdown-friendly style (Google or NumPy format).
* Example:

```python
def process_data(input_df):
    """
    Cleans and processes the input DataFrame.

    Args:
        input_df (pd.DataFrame): Raw input data.

    Returns:
        pd.DataFrame: Cleaned and normalized output.
    """
    # Filter invalid entries
    ...
```

### 3. Sync High-Level Docs

* Cross-reference `/planning/vision.md` and `/docs/architecture/` for feature alignment.
* Update relevant documentation files:

  * `/docs/architecture/overview.md`
  * `/README.md`
  * `/docs/tutorials/` (if user-facing behavior changes)
* Use consistent terminology and include code examples where helpful.

### 4. Verify & Format

* Run docstring lint checks (e.g., `pydocstyle`, `flake8-docstrings`).
* Format Markdown output for readability.
* Validate cross-references to ensure no broken links or missing sections.

### 5. Summarize Changes

* Generate summary report:

  ```
  /planning/sprint/<active_sprint>/documentation_updates_<date>.md
  ```

  Report includes:

  * Files updated
  * Missing docstrings added
  * Inline comments inserted
  * Outdated sections revised

---

## COOPERATING AGENTS

| Agent             | Function                                                 |
| ----------------- | -------------------------------------------------------- |
| `master_prompter` | Refines documentation text and tone                      |
| `brian`           | Ensures documentation matches code state                 |
| `scrum_master`    | Links documentation tasks to sprint issues               |
| `qa_tester`       | Validates that documented tests exist and are up to date |

---

## COMMANDS

* `/document all` — Scan all code for missing documentation and update files.
* `/document file <path>` — Document a single file or module.
* `/document class <ClassName>` — Generate docstrings and inline docs for one class.
* `/document summary` — Create sprint-level summary report.

---

## DONE WHEN

* All public functions and classes are documented.
* Inline comments explain complex logic.
* README and architecture docs reflect current state.
* Sprint documentation report is generated and linked.

---

## LOCATION

`.claude/commands/document.md`
