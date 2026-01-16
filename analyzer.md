## Description
```
Deeply analyze the codebase while simultaneously gathering latest web context. Read-only for project code.
```

## Content
```
# Context Analyzer Workflow
This workflow is designed to perform a comprehensive analysis of the project source code, supplemented by real-time data and documentation from the web. It is strictly **Read-Only** regarding the project's source code.
## Constraints & Permissions
- **Project Files**: **READ-ONLY**. You are strictly FORBIDDEN from editing, creating, or deleting source code files.
- **Web Access**: **ALLOWED & ENCOURAGED**. Use web tools to verify libraries, patterns, and documentation.
- **Reporting**: You may create markdown report files if necessary to persist findings, but prefer responding in chat.
## Execution Steps
1.  **Scope Definition**
    *   Analyze the user's request to identify the specific area or topic for analysis.
    *   Formulate a set of questions that need to be answered by the code and the web.
2.  **Codebase Exploration**
    *   Start with `list_dir` to understand the project structure.
    *   Read configuration files (`package.json`, `go.mod`, `pom.xml`, etc.) to identify dependencies.
    *   Use `view_file_outline` and `view_file` to understand correct architectural patterns and logic flow.
    *   **Goal**: Establish a baseline understanding of "How it works now".
3.  **Web Context Discovery**
    *   For identified dependencies or patterns, use `search_web` to find:
        *   Latest stable versions and changelogs.
        *   Security advisories or deprecation notices.
        *   Best practice guides relevant to the code's implementation.
        *   Documentation for any obscure or complex logic found in the code.
    *   Use `read_url_content` to extract details from documentation pages.
4.  **Synthesis & Insight Generation**
    *   Compare the "Codebase Reality" (Step 2) with "Web Reality" (Step 3).
    *   Identify gaps:
        *   Is the code using deprecated methods?
        *   Are there newer, more efficient ways to achieve the same result?
        *   Are there security risks mentioned online that apply to this specific implementation?
5.  **Reporting**
    *   Present the findings to the user.
    *   Structure the report with clear sections:
        *   **Current State**: What the code does.
        *   **External Context**: What the web says (Docs, Trends).
        *   **Analysis**: Discrepancies, Risks, and Opportunities.
    *   Do **NOT** propose code changes instructions to be auto-applied; instead, provide advice and references.
```
