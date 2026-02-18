# Skill: EdTech Source Selection

Select and prioritize sources from the EdTech source catalog based on the research objective.

## When to Use

Apply this skill at the start of any EdTech-specific command to determine which sources (RSS feeds, news API queries, web searches, direct URLs) to use for the research task.

## Instructions

1. Read the source catalog at `input/product-management/information-sources/information-sources.md`
2. Based on `{{RESEARCH_TYPE}}`, select the appropriate source tier:

### Source Tiers by Research Type

| Research Type | Primary Sources | Secondary Sources | Verification |
|---|---|---|---|
| publication-scan | RSS feeds (Section B publications) | NewsAPI keyword search | WebFetch on article URLs |
| state-monitoring | SEA feeds/pages (Sections D, E, G) | NewsAPI state+education queries | WebFetch on SEA sites |
| competitor-intel | Vendor RSS feeds (Section C) | NewsAPI vendor name queries | WebFetch on press releases |
| standards-tracking | Standards pages (Sections E, F, H) | NewsAPI standards queries | WebFetch on board agendas |
| landscape-scan | All of the above | All of the above | Cross-reference across tiers |

3. For each selected source, determine the fetch method (in priority order):
   - **RSS available:** Use `rss` MCP server (`get_rss` tool) with `since` parameter for date filtering
   - **Broad query needed:** Use `newsapi` MCP server (`search-news` tool) with keyword queries
   - **Specific URL needed:** Use `WebFetch` to read a known page
   - **Discovery needed:** Use `WebSearch` to find relevant pages
   - **MCP unavailable:** Fall back to `WebSearch` + `WebFetch` for any source

4. Apply the verification workflow from Section I of the source catalog:
   - Treat aggregation hits (NewsAPI, RSS) as **signals**
   - Verify on primary-source pages (SEA sites, vendor newsrooms, board documents) before including in final output
   - Cross-reference across multiple sources when possible

## Common NewsAPI Query Patterns

| Research Type | Query Template |
|---|---|
| Publication scan | `"{{TOPIC}}" AND ("edtech" OR "education technology" OR "K-12")` |
| State monitoring | `"{{STATE}} Department of Education" OR "{{STATE}} standards"` |
| Competitor intel | `"{{COMPANY}}" AND ("launch" OR "release" OR "partnership" OR "funding")` |
| Standards tracking | `"{{STATE}}" AND ("adopts" OR "revises") AND ("standards" OR "framework")` |

## State Standards Terminology Reference

Some states use specific names for their standards (from Section G):
- Texas: **TEKS** (Texas Essential Knowledge and Skills), SBOE
- Virginia: **SOL** (Standards of Learning)
- Florida: **B.E.S.T.** (Benchmarks for Excellent Student Thinking)
- Iowa: **Iowa Core**
- Louisiana: **Student Standards**, BESE
- Massachusetts: **Curriculum Frameworks**
- New Jersey: **Student Learning Standards**
- Ohio: **Learning Standards / Model Curricula**

Use these terms in state-specific searches for better results.

## Output

Return a source plan listing:
- Sources selected and why
- Fetch method for each source
- Query strings for news API searches
- Specific state/vendor targets

## Placeholders

- `{{RESEARCH_TYPE}}` — One of: publication-scan, state-monitoring, competitor-intel, standards-tracking, landscape-scan
- `{{TOPIC}}` — The specific topic, vendor, state, or standard to research
- `{{STATE}}` — US state name (for state-specific commands)
- `{{COMPANY}}` — Vendor/competitor name (for competitor commands)
