# Product Management Research

This is a Claude Code project for structured product research and competitive analysis.

## Project Structure

```
product-management/
├── CLAUDE.md              # Project configuration (this file)
├── commands/              # Command reference & documentation
├── skills/                # Reusable research skill prompts
├── .claude/
│   ├── commands/          # Slash commands (/plan, /implement, etc.)
│   └── settings/          # Project settings
├── scripts/               # Helper scripts for processing
├── input/                 # Research topics, URLs, questions (user-provided)
├── output/                # All generated output, organized by query
│   └── general/           # Research output
│       └── YYYY-MM-DD-<slug>/  # One folder per research query
└── templates/             # Reusable templates for output formatting
```

## Skills

Reusable research techniques in `skills/`. Apply during any research task:
- **evaluate-sources** — Assess source credibility (authority, currency, accuracy, purpose)
- **compare** — Structured comparison matrices with strengths/weaknesses
- **fact-check** — Verify claims against multiple independent sources
- **deep-dive** — Thorough investigation of a single source or subtopic

## Workflow

1. **Plan** — Run `/plan` with a research topic. Creates a query folder in `output/general/YYYY-MM-DD-<slug>/` and saves the plan there.
2. **Implement** — Run `/implement` with a plan file path. Executes the plan and saves the report in the same query folder.
3. **Research** — Run `/research` for quick one-shot queries. Output goes to `output/general/YYYY-MM-DD-<slug>/`.

## Product Management Documents

Generate common PM documents with web research. Each command takes a topic/product description as input, researches the market, and produces a complete document. Templates are in `input/product-management/`.

- `/business-case <topic>` — Business Case / Investment Memo (opportunity, financials, ROI, risks)
- `/competitive-analysis <topic>` — Competitive Analysis (market map, competitor profiles, feature matrix)
- `/prd <topic>` — Product Requirements Document (goals, user stories, functional/non-functional requirements)
- `/product-vision <topic>` — Product Vision & Strategy (vision, market landscape, strategic pillars, roadmap)

## Conventions

- All output is grouped by research query in a single folder: `output/general/YYYY-MM-DD-<slug>/`
- Plan files get a `-plan` suffix: `YYYY-MM-DD-<slug>-plan.md`
- All other files share the same base name with different extensions (`.md`, `.pdf`, `.pptx`, `.xlsx`)
- When exporting produces multiple output files, zip them: `YYYY-MM-DD-<slug>.zip` in the query folder.
- Plans reference their implementation output and vice versa.
- Input files in `input/` can be `.md`, `.txt`, or `.json`.
- When searching the web, always include source URLs in output.

## Tools Available

- `WebSearch` — Search the web for current information.
- `WebFetch` — Fetch and extract content from specific URLs.
- `Read`/`Write`/`Glob`/`Grep` — Local file operations.
- `Bash` — Run scripts from `scripts/` directory.

## MCP Servers

Configured in `.mcp.json` (project-scoped):
- **powerpoint** — Create and edit PowerPoint presentations via `office-powerpoint-mcp-server`. Requires `uvx` (install: `brew install uv`).
- **excel** — Read and write Excel workbooks via `excel-mcp-server`. Requires `uvx`.
