# Mode Prompts Analysis

This document provides a comparative analysis of three specific mode prompts: **Architect**, **Debug**, and **Ask**. These modes define distinct roles, permissions, and workflows for the AI agent, ensuring specialized behavior for different stages of the development lifecycle.

## Comparative Overview

| Feature | Architect Mode | Debug Mode | Ask Mode |
| :--- | :--- | :--- | :--- |
| **Filename** | `architect.md.resolved` | `debug.md.resolved` | `ask.md.resolved` |
| **Role** | Technical Leader / Planner | Expert Software Debugger | Technical Assistant |
| **Primary Goal** | Plan, gather context, create todo lists | Diagnose and resolve issues systematically | Answer questions, explain concepts |
| **Edit Permission** | **Restricted**: Markdown (`.md`) files only | **Allowed**: All files (Strictly **NO LOGGING**) | **Forbidden**: Cannot edit any files |
| **Mandatory Tools** | `update_todo_list` (or markdown write), `switch_mode` | `dap-proxy`, `macos-control` | None specified |
| **Key Constraint** | Never provide time estimates | **Logging is NOT debugging** | Do not switch to implementation automatically |

## Detailed Analysis

### 1. Architect Mode (`architect.md.resolved`)
**Focus:** Planning and Design.
*   **Persona:** "Roo", an inquisitive and excellent planner.
*   **Workflow:**
    1.  Gather information and context.
    2.  Ask clarifying questions.
    3.  Create a detailed, actionable **Todo List** (or `plan.md`).
    4.  **Crucial Step:** Get user approval *before* implementation.
    5.  Use `switch_mode` to hand off to an implementer.
*   **Unique Constraints:** It explicitly forbids providing level-of-effort time estimates, keeping the focus purely on technical breakdown. It is the only mode restricted to editing only Markdown files, enforcing a clear separation between "planning" and "coding".

### 2. Debug Mode (`debug.md.resolved`)
**Focus:** Systematic Diagnosis and Repair.
*   **Persona:** "Roo", an expert debugger using professional tools.
*   **Workflow:**
    1.  **Environment Check:** Immediately verify `dap-proxy` and `macos-control`. If missing, **STOP** and instruct the user to install.
    2.  **Strategy:** Formulate a plan using breakpoints and variable inspection.
    3.  **Execution:** Fix the issue based on runtime data.
*   **Unique Constraints:** This mode has the most aggressive tooling requirements. It strictly prohibits "console.log" debugging, forcing the use of the specified MCP tools (`dap-proxy` for DAP, `macos-control` for input/window manipulation). This enforces a high standard of professional debugging.

### 3. Ask Mode (`ask.md.resolved`)
**Focus:** Education and Explanation.
*   **Persona:** "Roo", a knowledgeable technical assistant.
*   **Workflow:**
    1.  Analyze code and external resources.
    2.  Explain concepts and answer questions.
    3.  Use Mermaid diagrams for clarity.
*   **Unique Constraints:** This is a read-only mode. Editing is **FORBIDDEN**. This ensures that the user can ask questions without fear of accidental code changes. It acts as a safe "consultation" layer.

## Conclusion

The three modes create a structured development pipeline:
1.  **Ask**: Understand the system.
2.  **Architect**: Plan the changes.
3.  **Debug**: Fix complex issues that arise (distinct from standard implementation).

Each mode has "guardrails" (permissions, mandatory tools) that fundamentally shape the agent's behavior to match the specific task.
