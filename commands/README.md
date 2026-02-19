# Commands

Slash commands for Claude Code. The executable command files live in `.claude/commands/` (required by Claude Code), and are documented here for easy reference.

## Available Commands

### Research
| Command | File | Description |
|---|---|---|
| `/plan` | [plan.md](../.claude/commands/plan.md) | Create a structured research plan |
| `/implement` | [implement.md](../.claude/commands/implement.md) | Execute a research plan into a full report |
| `/research` | [research.md](../.claude/commands/research.md) | Quick one-shot web research |
| `/summarize` | [summarize.md](../.claude/commands/summarize.md) | Condense any output into a 1-page summary |

### Product Management Documents
| Command | File | Description |
|---|---|---|
| `/business-case` | [business-case.md](../.claude/commands/business-case.md) | Business Case / Investment Memo |
| `/competitive-analysis` | [competitive-analysis.md](../.claude/commands/competitive-analysis.md) | Competitive Analysis with feature matrix |
| `/prd` | [prd.md](../.claude/commands/prd.md) | Product Requirements Document |
| `/product-vision` | [product-vision.md](../.claude/commands/product-vision.md) | Product Vision & Strategy |

### EdTech Intelligence
| Command | File | Description |
|---|---|---|
| `/edtech-scan` | [edtech-scan.md](../.claude/commands/edtech-scan.md) | Scan EdTech publications for recent coverage of a topic |
| `/state-watch` | [state-watch.md](../.claude/commands/state-watch.md) | Monitor state education agencies for press releases, standards, policy |
| `/competitor-intel` | [competitor-intel.md](../.claude/commands/competitor-intel.md) | EdTech competitor product/business intelligence |
| `/standards-tracker` | [standards-tracker.md](../.claude/commands/standards-tracker.md) | Track academic standards revisions and adoptions |
| `/edtech-landscape` | [edtech-landscape.md](../.claude/commands/edtech-landscape.md) | Comprehensive EdTech landscape briefing |

### Export
| Command | File | Description |
|---|---|---|
| `/slides` | [slides.md](../.claude/commands/slides.md) | Create a PowerPoint deck from research or a topic |
| `/excel` | [excel.md](../.claude/commands/excel.md) | Create or read Excel workbooks |
| `/pdf-report` | [pdf-report.md](../.claude/commands/pdf-report.md) | Convert markdown report to PDF |
| `/pdf-slides` | [pdf-slides.md](../.claude/commands/pdf-slides.md) | Convert PowerPoint to PDF |
| `/export` | [export.md](../.claude/commands/export.md) | Convert report to multiple formats at once |

## How Commands Work

Commands are markdown prompt files stored in `.claude/commands/`. When you type `/plan <topic>` in Claude Code, the contents of `plan.md` are loaded as instructions and `$ARGUMENTS` is replaced with whatever you typed after `/plan`.

## Output Directories

| Command Category | Output Location |
|---|---|
| Research (`/plan`, `/implement`, `/research`) | `output/general/YYYY-MM-DD-<slug>/` |
| PM Documents (`/business-case`, `/prd`, etc.) | `output/product-management/<project-name>/` |
| EdTech Intelligence (`/edtech-scan`, etc.) | `output/edtech/YYYY-MM-DD-<slug>/` |
| Export (`/slides`, `/excel`, `/export`) | Same folder as the source file |

All commands that create markdown files also auto-generate a PDF version.

## Adding a New Command

1. Create a new `.md` file in `.claude/commands/`
2. Include `$ARGUMENTS` where you want the user's input inserted
3. Define the output path (save into the appropriate output directory)
4. Include a "Generate PDF" step using Pandoc + WeasyPrint
5. Document the command in this README

## Command Workflows

### Research Workflow

```
/plan <topic>          -->  output/general/<date>-<slug>/<date>-<slug>-plan.md
       |
       v (review & edit)
/implement <plan-path> -->  output/general/<date>-<slug>/<date>-<slug>.md + .pdf
       |
       v (optional)
/summarize <file-path> -->  <same-folder>/<original>-summary.md + .pdf
       |
       v (optional)
/slides <file-path>   -->  <same-folder>/<date>-<slug>.pptx
/excel <file-or-desc> -->  <same-folder>/<date>-<slug>.xlsx
/export <file> all    -->  <same-folder>/<date>-<slug>.zip (if 2+ files)
```

### PM Document Workflow

```
/product-vision <product>        -->  output/product-management/<project>/
/business-case <product>         -->  output/product-management/<project>/
/prd <product>                   -->  output/product-management/<project>/
/competitive-analysis <product>  -->  output/product-management/<project>/
```

Multiple documents for the same product share a single project folder.

### EdTech Intelligence Workflow

```
/edtech-scan <topic>             -->  output/edtech/<date>-<slug>/
/state-watch <state(s)>          -->  output/edtech/<date>-<slug>/
/competitor-intel <company(ies)> -->  output/edtech/<date>-<slug>/
/standards-tracker [states]      -->  output/edtech/<date>-<slug>/
/edtech-landscape [scope]        -->  output/edtech/<date>-<slug>/
```

EdTech commands use the source catalog at `input/product-management/information-sources/information-sources.md` and RSS feeds from `input/product-management/information-sources/edtech-feeds.opml`.
