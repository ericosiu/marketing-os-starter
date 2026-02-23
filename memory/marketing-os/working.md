# Working — Current Task Queue

**Purpose**: Real-time task tracking for the Marketing OS agent team. Orchestrator reads and writes this file. Agents check it before starting work.

**Updated by**: MOS-Orchestrator
**Last updated**: [Auto-updated by Orchestrator]

---

## Active Queue

| Task ID | Description | Agent | Status | Waiting For |
|---------|-------------|-------|--------|-------------|
| — | No active tasks | — | — | — |

**Status options**: Pending | In Progress | Waiting for Input | Done | Blocked

---

## Completed Today

| Task ID | Description | Agent | Completed | Output |
|---------|-------------|-------|-----------|--------|
| — | — | — | — | — |

---

## Blocked

| Task ID | Description | Blocker | Flagged |
|---------|-------------|---------|---------|
| — | — | — | — |

---

## How to Use This File

**Orchestrator**: Update this file after every routing decision and after every completed handoff.

**When a task starts**: Move from Pending to In Progress. Note the agent.

**When a task needs input**: Move to "Waiting for Input." Describe exactly what's needed.

**When a task completes**: Move to Completed Today. Record the output file path.

**At the end of each day**: Clear Completed Today into campaign-history.md if relevant.

---

## Task ID Format

`MOS-[YYYYMMDD]-[sequential number]`
Example: `MOS-20260223-001`
