# Product Management Research

A structured Claude Code project for product research, competitive analysis, and EdTech intelligence. Topics go in, organized markdown reports (with PDFs) come out.

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
│   ├── deep-dive.md             # Thorough single-source investigation
│   └── edtech-sources.md        # EdTech source selection logic
├── .claude/
│   └── commands/                # Executable slash command files
├── scripts/
│   ├── list-output.sh           # List all output files
│   └── clean-output.sh          # Remove old output files
├── input/                       # Your research topics, URLs, and questions
│   ├── example-topic.md         # Example input file
│   └── product-management/      # PM document templates & source catalogs
│       ├── pm-business-case.md
│       ├── pm-competitive-analysis.md
│       ├── pm-product-requirements-document(PRD).md
│       ├── pm-product-vision-and-strategy.md
│       └── information-sources/  # EdTech source catalog & OPML feeds
├── output/                      # All generated output
│   ├── general/                 # General research output
│   │   └── YYYY-MM-DD-<slug>/   # One folder per query
│   ├── product-management/      # PM document output
│   │   └── <project-name>/      # One folder per project
│   └── edtech/                  # EdTech intelligence output
│       └── YYYY-MM-DD-<slug>/   # One folder per scan
└── templates/                   # Reusable output templates
```

## Getting Started

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- [uv](https://docs.astral.sh/uv/) installed (`brew install uv`) — needed for MCP servers
- Open this project directory in Claude Code or VS Code with the Claude Code extension

### Optional Setup

- **NewsAPI key** — Sign up at [newsapi.org](https://newsapi.org) (free tier) and set `export NEWS_API_KEY=your_key` in your shell profile. Required for the `/edtech-scan`, `/state-watch`, `/competitor-intel`, `/standards-tracker`, and `/edtech-landscape` commands to use news API search.

### Quick Start

1. Open Claude Code in this directory
2. Run a quick research query:
   ```
   /research What are the top product management tools in 2026?
   ```
3. Check your results in `output/general/`

## Commands

### Research

| Command | Description |
|---------|-------------|
| `/plan <topic>` | Create a structured research plan |
| `/implement <plan-path>` | Execute a research plan into a full report |
| `/research <question>` | Quick one-shot web research |
| `/summarize <file>` | Condense any output into a 1-page summary |

### Product Management Documents

| Command | Description |
|---------|-------------|
| `/business-case <topic>` | Business Case / Investment Memo |
| `/competitive-analysis <topic>` | Competitive Analysis with feature matrix |
| `/prd <topic>` | Product Requirements Document |
| `/product-vision <topic>` | Product Vision & Strategy |

### EdTech Intelligence

| Command | Description |
|---------|-------------|
| `/edtech-scan <topic>` | Scan EdTech publications for recent coverage |
| `/state-watch <state(s)>` | Monitor state education agencies |
| `/competitor-intel <company(ies)>` | EdTech competitor intelligence |
| `/standards-tracker [states] [subject]` | Track academic standards changes |
| `/edtech-landscape [scope]` | Comprehensive landscape briefing |

### Export

| Command | Description |
|---------|-------------|
| `/slides <file-or-topic>` | Create a PowerPoint deck |
| `/excel <file-or-desc>` | Create or read Excel workbooks |
| `/pdf-report <file>` | Convert markdown to PDF |
| `/pdf-slides <file>` | Convert PowerPoint to PDF |
| `/export <file> <format(s)>` | Convert to multiple formats at once |

For more information, see [commands/README.md](commands/README.md) for detailed usage, output paths, and workflow diagrams.

## MCP Servers

Configured in [.mcp.json](.mcp.json) and run automatically when Claude Code starts:

| Server | Package | Purpose |
|---|---|---|
| `powerpoint` | `office-powerpoint-mcp-server` | Create and edit PowerPoint presentations |
| `excel` | `excel-mcp-server` | Read and write Excel workbooks |
| `rss` | `rssmcp` | Fetch RSS/Atom feeds from OPML catalog |
| `newsapi` | `news-api-mcp` | Search news articles via NewsAPI |

All servers require `uvx` (from `uv`): `brew install uv`. The `newsapi` server also requires a `NEWS_API_KEY` environment variable.

## Skills

Reusable research techniques in `skills/`. For more information, see [skills/README.md](skills/README.md) for the full index and usage guide.

| Skill | Purpose |
|---|---|
| [evaluate-sources.md](skills/evaluate-sources.md) | Assess credibility and reliability of sources |
| [compare.md](skills/compare.md) | Structured comparison of multiple options |
| [fact-check.md](skills/fact-check.md) | Verify claims against multiple sources |
| [deep-dive.md](skills/deep-dive.md) | Thorough single-source investigation |
| [edtech-sources.md](skills/edtech-sources.md) | EdTech source selection logic for intelligence commands |

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

### PM Document Workflow

Generate product management documents with web-sourced market data. Multiple documents for the same project share a folder.

```
/product-vision AI-powered math tutoring platform
/business-case AI-powered math tutoring platform
/prd AI-powered math tutoring platform
/competitive-analysis AI-powered math tutoring platforms
```

All output lands in `output/product-management/ai-math-tutoring-platform/`.

### EdTech Intelligence Workflow

Monitor the EdTech landscape using publication feeds, state education agencies, and news APIs. For more information on sources, see [information-sources.md](input/product-management/information-sources/information-sources.md).

```
/edtech-scan adaptive learning
/state-watch Texas, California, Florida
/competitor-intel Khan Academy, IXL, DreamBox
/standards-tracker Texas math
/edtech-landscape K-12 math EdTech
```

All output lands in `output/edtech/YYYY-MM-DD-<slug>/`.

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

## Helper Scripts

### List Output Files

```bash
./scripts/list-output.sh           # List all output
./scripts/list-output.sh general   # List general research
./scripts/list-output.sh edtech    # List EdTech intelligence
```

### Clean Old Output

```bash
./scripts/clean-output.sh          # Remove files older than 30 days
./scripts/clean-output.sh 7        # Remove files older than 7 days
```

## Conventions

| Convention | Detail |
|---|---|
| Auto-PDF | Every markdown file also gets a PDF version |
| General research | Output in `output/general/YYYY-MM-DD-<slug>/` |
| PM documents | Output in `output/product-management/<project-name>/` |
| EdTech intelligence | Output in `output/edtech/YYYY-MM-DD-<slug>/` |
| Plan naming | Plans get `-plan` suffix |
| Multi-file export | 2+ exported files are zipped |
| Sources | Every report includes URLs for all cited sources |
| Cross-references | Reports link back to their source plan |

## Tips

- **Edit plans before implementing.** The plan is a draft — refine the search queries and questions to get better results.
- **Use input files for complex topics.** A well-structured input file with specific questions produces much better plans.
- **Chain summaries.** Run `/summarize` on multiple reports, then ask Claude to compare them.
- **Iterate.** If a report has gaps, update the plan with new search queries and re-run `/implement`.
- **Group PM docs by project.** Run multiple PM commands for the same product — they'll share a folder.
- **Set up NewsAPI for EdTech commands.** The free tier (100 req/day) is sufficient for research use.
