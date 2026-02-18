# Product Management Research

A structured Claude Code project for product research and competitive analysis. Topics go in, organized markdown reports come out.

## Project Structure

```
product-management/
├── CLAUDE.md                    # Claude Code project configuration
├── README.md                    # This file
├── commands/                    # Command reference & documentation
│   └── README.md                # Quick reference for all commands
├── skills/                      # Reusable research skill prompts
│   ├── README.md                # Skill index and usage guide
│   ├── evaluate-sources.md      # Assess source credibility
│   ├── compare.md               # Structured comparisons
│   ├── fact-check.md            # Verify claims across sources
│   └── deep-dive.md             # Thorough single-source investigation
├── .claude/
│   └── commands/                # Executable slash command files
│       ├── plan.md              # /plan — Create a research plan
│       ├── implement.md         # /implement — Execute a research plan
│       ├── research.md          # /research — Quick one-shot research
│       ├── summarize.md         # /summarize — Condense any output
│       ├── slides.md            # /slides — Create PowerPoint presentations
│       └── excel.md             # /excel — Create or read Excel workbooks
├── scripts/
│   ├── list-output.sh           # List all output files
│   └── clean-output.sh          # Remove old output files
├── input/                       # Your research topics, URLs, and questions
│   └── example-topic.md         # Example input file
├── output/                      # All generated output, grouped by query
│   └── general/                 # Research output
│       └── YYYY-MM-DD-<slug>/   # One folder per query (all artifacts together)
└── templates/                   # Reusable output templates
```

## Getting Started

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- [uv](https://docs.astral.sh/uv/) installed (`brew install uv`) — needed for MCP servers (PowerPoint, Excel)
- Open this project directory in Claude Code or VS Code with the Claude Code extension

### Quick Start

1. Open Claude Code in this directory
2. Run a quick research query:
   ```
   /research What are the top product management tools in 2026?
   ```
3. Check your results in `output/general/`

## Commands

### `/plan` — Create a Research Plan

Creates a structured research plan before doing any deep research. The plan includes objectives, key questions, a phased search strategy, and expected deliverables.

**Usage:**
```
/plan <topic or question>
/plan See input/example-topic.md
```

**Output:** `output/general/YYYY-MM-DD-<slug>/YYYY-MM-DD-<slug>-plan.md`

**What it does:**
1. Reads your topic (inline text or from an input file)
2. Runs preliminary web searches to understand the landscape
3. Produces a structured plan with search queries and phases
4. Saves the plan and gives you the file path

### `/implement` — Execute a Research Plan

Takes a plan file and executes it step by step, producing a comprehensive research report with source citations.

**Usage:**
```
/implement output/general/2026-02-18-competitor-landscape/2026-02-18-competitor-landscape-plan.md
/implement 2026-02-18-competitor-landscape-plan.md
```

**Output:** Saved in the same query folder as the plan (e.g., `output/general/YYYY-MM-DD-<slug>/YYYY-MM-DD-<slug>.md`)

**What it does:**
1. Reads the plan file
2. Executes each search phase (WebSearch + WebFetch)
3. Answers every key question from the plan
4. Compiles findings into a structured report with sources
5. Links the report back to its source plan

### `/research` — Quick One-Shot Research

Skips the plan/implement cycle for simple questions. Searches the web, fetches key sources, and writes a concise report.

**Usage:**
```
/research What is the current market share of project management tools?
```

**Output:** `output/general/YYYY-MM-DD-<slug>/YYYY-MM-DD-<slug>.md`

### `/summarize` — Condense Research Output

Reads any existing output file and produces a 1-page executive summary with key takeaways and suggested next steps.

**Usage:**
```
/summarize output/general/2026-02-18-competitor-landscape/2026-02-18-competitor-landscape.md
```

**Output:** Saved alongside the original file with `-summary` appended to the filename.

### `/slides` — Create PowerPoint Presentations

Turns research output or a topic into a PowerPoint deck using the PowerPoint MCP server.

**Usage:**
```
/slides output/general/2026-02-18-competitor-landscape/2026-02-18-competitor-landscape.md
/slides A 10-slide overview of product-led growth trends
```

**Output:** Saved in the same query folder as the source report (e.g., `.pptx` alongside `.md`)

**What it does:**
1. Reads existing research output or takes a topic directly
2. Plans the slide deck structure
3. Creates slides using the PowerPoint MCP tools (title, bullets, tables, charts)
4. Saves the `.pptx` file in the same folder as the source report

### `/excel` — Create or Read Excel Workbooks

Creates Excel spreadsheets from research data, or reads existing `.xlsx` files. Uses the Excel MCP server.

**Usage:**
```
/excel Create a comparison spreadsheet from output/general/2026-02-18-competitor-landscape/2026-02-18-competitor-landscape.md
/excel Read and summarize input/usage-data.xlsx
```

**Output:** Saved in the same query folder as the source report (e.g., `.xlsx` alongside `.md`)

**What it does:**
1. Reads research output or takes a data description
2. Creates workbook with named sheets, headers, and formatted data
3. Adds formulas for calculations where appropriate
4. Can also read existing Excel files and summarize their contents

## MCP Servers

This project uses MCP (Model Context Protocol) servers configured in [.mcp.json](.mcp.json):

| Server | Package | Purpose |
|---|---|---|
| `powerpoint` | `office-powerpoint-mcp-server` | Create and edit PowerPoint presentations |
| `excel` | `excel-mcp-server` | Read and write Excel workbooks |

MCP servers run automatically when Claude Code starts in this directory. They require `uvx` (from `uv`): `brew install uv`.

## Skills

Skills are reusable research techniques in `skills/` that can be applied during any research task. See [skills/README.md](skills/README.md) for full details.

| Skill | File | Purpose |
|---|---|---|
| Source Evaluation | [evaluate-sources.md](skills/evaluate-sources.md) | Assess credibility and reliability of sources |
| Compare & Contrast | [compare.md](skills/compare.md) | Structured comparison of multiple options/tools/approaches |
| Fact Check | [fact-check.md](skills/fact-check.md) | Verify claims against multiple independent sources |
| Deep Dive | [deep-dive.md](skills/deep-dive.md) | Thorough single-topic investigation from a URL or source |

Skills use placeholder tokens (`{{TOPIC}}`, `{{URL}}`, `{{INPUT}}`) and produce structured markdown output. You can reference them in commands or use them directly in conversation.

## Workflows

### Full Research Workflow (Recommended)

Best for complex topics where you want control over the research direction.

```
Step 1:  /plan Competitive landscape for task management tools
Step 2:  Review and edit the plan in output/general/2026-02-18-task-management-landscape/
Step 3:  /implement output/general/2026-02-18-task-management-landscape/2026-02-18-task-management-landscape-plan.md
Step 4:  /summarize output/general/2026-02-18-task-management-landscape/2026-02-18-task-management-landscape.md
```

```
┌─────────┐     ┌──────────┐     ┌───────────┐     ┌───────────┐     ┌─────────┐
│  /plan   │────>│  Review  │────>│/implement │────>│/summarize │────>│ /slides │
│          │     │  & Edit  │     │           │     │(optional) │     │(optional)│
└─────────┘     └──────────┘     └───────────┘     └───────────┘     └─────────┘
     │                                  │                 │                │
     v                                  v                 v                v
                    All output in: output/general/YYYY-MM-DD-<slug>/
```

### Quick Research Workflow

Best for simple questions or time-sensitive lookups.

```
/research <your question>
```

### Input File Workflow

For research topics that need more context than a one-liner, create an input file first.

1. Create a file in `input/` describing your topic:

```markdown
# My Research Topic

## Topic
<detailed description>

## Questions I Want Answered
- <question 1>
- <question 2>

## Notes
- <any constraints, focus areas, or preferences>
```

2. Reference it in your plan command:
```
/plan See input/my-research-topic.md
```

## Example: End-to-End Walkthrough

This example shows the full plan-then-implement workflow for a product management research task.

### 1. Create an Input File (Optional)

Save this as `input/competitor-analysis.md`:

```markdown
# Competitor Analysis: Project Management Tools

## Topic
The current state of project management tools for product teams in 2026.

## Questions I Want Answered
- Which tools have the largest market share among product teams?
- How do they compare in terms of features and pricing?
- What are the latest trends in PM tooling?

## Notes
- Focus on tools used by product managers specifically
- Include both enterprise and startup-friendly options
```

### 2. Generate a Plan

```
/plan See input/competitor-analysis.md
```

Claude will search the web for initial context, then produce a plan in `output/general/2026-02-18-pm-tools-landscape/2026-02-18-pm-tools-landscape-plan.md`.

### 3. Review and Edit

Open the plan file, adjust search queries, add questions, or narrow the scope. This is your chance to steer the research before execution.

### 4. Execute the Plan

```
/implement output/general/2026-02-18-pm-tools-landscape/2026-02-18-pm-tools-landscape-plan.md
```

Claude will work through each phase, searching the web and fetching sources. The final report lands in `output/general/2026-02-18-pm-tools-landscape/2026-02-18-pm-tools-landscape.md` with full source citations.

### 5. Summarize (Optional)

```
/summarize output/general/2026-02-18-pm-tools-landscape/2026-02-18-pm-tools-landscape.md
```

Produces a 1-page summary with key takeaways next to the original report.

## Helper Scripts

### List Output Files

```bash
./scripts/list-output.sh           # List all output
./scripts/list-output.sh general   # List general research
```

### Clean Old Output

```bash
./scripts/clean-output.sh          # Remove files older than 30 days
./scripts/clean-output.sh 7        # Remove files older than 7 days
```

## Conventions

| Convention | Detail |
|---|---|
| File format | All output is Markdown |
| Output grouping | All artifacts from one query live in `output/general/YYYY-MM-DD-<slug>/` |
| Plan naming | Plans get `-plan` suffix: `YYYY-MM-DD-<slug>-plan.md` |
| File naming | All other files share the base name with different extensions |
| Multi-file export | When exporting 2+ files, they are zipped into `YYYY-MM-DD-<slug>.zip` |
| Sources | Every report includes URLs for all cited sources |
| Cross-references | Reports link back to their source plan |
| Input formats | `.md`, `.txt`, or `.json` files in `input/` |

## Tips

- **Edit plans before implementing.** The plan is a draft — refine the search queries and questions to get better results.
- **Use input files for complex topics.** A well-structured input file with specific questions produces much better plans.
- **Chain summaries.** Run `/summarize` on multiple reports, then ask Claude to compare them.
- **Iterate.** If a report has gaps, update the plan with new search queries and re-run `/implement`.
