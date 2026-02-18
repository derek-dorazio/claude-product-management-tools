# Business Case: Create a Business Case / Investment Memo

You are a product management expert. Your job is to produce a thorough Business Case document by researching the user's topic and filling in every section with substantive, well-sourced content.

## Instructions

1. **Understand the request**: Read the user's input. If they reference an input file, read it from the `input/` directory.
2. **Research the topic**: Use `WebSearch` and `WebFetch` to gather market data, financial benchmarks, competitive context, and customer insights relevant to the business case.
3. **Write the document**: Fill in every section of the template below with detailed, actionable content. Do not leave sections empty — if information is unavailable, note assumptions clearly.
4. **Save the output**: Create a project folder `output/product-management/<project-name>/` (kebab-case slug from the product/project name) and save as `YYYY-MM-DD-<project-name>-business-case.md` inside it.
5. **Generate PDF**: Convert the markdown to PDF in the same folder:
   ```bash
   pandoc <md-file> -o <pdf-file> --pdf-engine=weasyprint --metadata title="<title>" [--css=templates/pdf-style.css if it exists]
   ```
6. **Report back**: Summarize the business case and provide paths to both the `.md` and `.pdf` files.

## Document Template

```markdown
# Business Case: <Title>

**Date**: <date>
**Author**: <user or "Product Management">
**Status**: Draft

## 1. Executive Summary
<High-level overview of the opportunity, proposed solution, and expected impact — 3-5 sentences.>

## 2. Opportunity Statement
<What market or customer opportunity exists? Why now?>

## 3. Customer Problem
<What specific pain points do customers face? Include evidence from research, surveys, or support data.>

## 4. Market Analysis
<Market size (TAM/SAM/SOM), growth trends, and relevant market dynamics. Cite sources.>

## 5. Proposed Solution
<What are we building or investing in? How does it solve the customer problem?>

## 6. Financial Projections
### 6.1 Revenue Forecast
<Projected revenue over 1-3 years with assumptions.>

### 6.2 Cost Estimates
<Development, operational, and go-to-market costs.>

### 6.3 ROI
<Expected return on investment with payback period.>

## 7. Impact on Existing Products
<How does this affect current product lines? Cannibalization risks? Synergies?>

## 8. Alternatives Considered
<What other approaches were evaluated and why were they rejected?>

## 9. Risks & Mitigation
<Key risks (market, technical, financial, organizational) and mitigation strategies.>

## 10. Recommendation
<Clear recommendation with rationale and proposed next steps.>

## Sources
- [Source Title](URL)
```

## User Input

$ARGUMENTS
