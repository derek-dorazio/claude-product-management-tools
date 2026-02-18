# EdTech PM Intelligence Sources (US States + Federal/Common Core) — with MCP/API Fetch Options

This consolidates:
- **Publications**
- **Company product announcements**
- **State Department of Education (SEA) press releases**
- **State standards / standards-change signals**
- **Federal/Common Core standards**

It also flags practical ways to fetch each stream:
- **MCP servers** (where commonly available)
- **Direct APIs**
- **Other reliable methods** (RSS/Atom, RSSHub, page-diff, email capture)

---

## A. Cross-cutting “how to fetch” options (works across most sources)

### 1) RSS / Atom feeds (best default)
**Use when:** a site publishes RSS/Atom, or you can generate one via RSSHub.  
**MCP availability:** RSS MCP servers exist (can ingest standard RSS/Atom and often RSSHub feeds). :contentReference[oaicite:0]{index=0}

**Fallback when there’s no RSS:**  
- Use **RSSHub** (when it can generate feeds for a given site) + RSS MCP ingestion. :contentReference[oaicite:1]{index=1}  
- Use **page-change monitoring** (HTML diff) for “press releases” and “standards PDF” pages.

### 2) News aggregation APIs (fast “catch-all” monitoring)
**Use when:** you need broad coverage, deduping, and alerts for specific entities (vendor names, “State Board adopts…”, “standards revision”, etc.).  
- **NewsAPI**: MCP servers exist. :contentReference[oaicite:2]{index=2}  
- **Google News via SerpAPI**: MCP server exists. :contentReference[oaicite:3]{index=3}  
- **GNews API**: MCP server exists. :contentReference[oaicite:4]{index=4}  
- **GDELT** (news/event data): MCP provider listings exist (and GDELT is a well-known API source for large-scale monitoring). :contentReference[oaicite:5]{index=5}

> Practical pattern: use RSS (primary sources) + a news API (secondary coverage) to catch early signals, then verify on the primary source.

### 3) Government feeds (when available)
Some government sites provide RSS feed directories (varies by agency). Example: U.S. Department of State RSS feed directory. :contentReference[oaicite:6]{index=6}  
For federal publications, **govinfo** provides RSS feeds for multiple official collections. :contentReference[oaicite:7]{index=7}

---

## B. Publications (industry + policy + market)

### Best sources (high-signal examples)
- Education Week, EdSurge, Chalkbeat, eSchool News, THE Journal
- Inside Higher Ed, Chronicle of Higher Education
- Brookings (education), RAND (education), AEI (education)
- HolonIQ, ASU+GSV, EdTech Digest

### Fetch options
- **Preferred:** RSS/Atom → RSS MCP :contentReference[oaicite:8]{index=8}
- **Broad monitoring:** NewsAPI / Google News / GDELT MCPs :contentReference[oaicite:9]{index=9}
- **Fallback:** newsletter ingestion (email) and/or page-diff for paywalled or RSS-less sites

---

## C. Company product announcements (competitors, platforms, partners)

### Best sources
- Vendor newsroom/blog + release notes + changelogs
- Press wire pickups (Business Wire / PR Newswire) via aggregation
- App/LMS marketplaces and “What’s New” sections
- (If public companies) investor relations releases / SEC filings

### Fetch options
- **Vendor blog / release notes:** RSS/Atom → RSS MCP; RSSHub if needed :contentReference[oaicite:10]{index=10}
- **Press mentions:** NewsAPI / Google News / GDELT MCPs for queries like:
  - `"VendorName" AND ("launch" OR "release" OR "district" OR "approved vendor")`
  :contentReference[oaicite:11]{index=11}
- **Fallback:** page-diff on release notes pages

---

## D. State Department of Education (SEA) press releases (all US states + DC)

### What to track (per state)
**Primary-source pages on the SEA site (common labels):**
- “News”, “Press Releases”, “Media”, “Communications”, “Announcements”, “Newsroom”

### Fetch options
- **If RSS/Atom exists:** RSS MCP :contentReference[oaicite:12]{index=12}
- **If not:** RSSHub (if supported) + RSS MCP :contentReference[oaicite:13]{index=13}
- **Otherwise:** page-diff + email subscription (if the SEA offers “Subscribe” / listserv)

### Authoritative directory to start from
Use the **CCSSO SEA Directory** to get each state’s official SEA and its “More Info” entry (which typically points you to the SEA website). :contentReference[oaicite:14]{index=14}

---

## E. State standards changes (all US states + DC)

Standards changes are often a *process* across multiple pages, not a single announcement.

### What to track (per state)
On the SEA (and sometimes State Board) sites, look for:
- “Standards”, “Academic Standards”, “Curriculum”, “Frameworks”
- “State Board” agendas/minutes (adoptions often happen here)
- “Rulemaking / Administrative Register” (public comment + final adoption notices)
- Versioned PDFs (ELA/Math/Science/SS) and “revision timeline” pages

### Fetch options
- **RSS (if available):** RSS MCP :contentReference[oaicite:15]{index=15}
- **Primary-source backstop:** page-diff on standards landing pages + board agenda pages
- **Early signal:** NewsAPI / Google News / GDELT MCP queries like:
  - `"StateName" AND ("adopts" OR "revises") AND ("standards" OR "framework")`
  :contentReference[oaicite:16]{index=16}

---

## F. Federal / Common Core (CCSS)

### What to track
- **Common Core “Read the Standards”** pages (ELA & Math) :contentReference[oaicite:17]{index=17}
- **CCSSO-hosted PDF standards** (Math PDF is a common reference artifact) :contentReference[oaicite:18]{index=18}
- **Development/background pages** (useful for context in PM comms) :contentReference[oaicite:19]{index=19}

### Fetch options
- RSS/Atom if published by the site (or RSSHub/page-diff if not)
- News aggregation MCPs for mentions of CCSS updates, controversies, adoption changes :contentReference[oaicite:20]{index=20}

---

# G. Per-state list (US states + DC) — where to fetch Press Releases + Standards Changes

**How to use this list**
1. Start at the SEA website (linked/identified via the CCSSO SEA Directory). :contentReference[oaicite:21]{index=21}  
2. Find the **Press Releases/News** page and the **Standards/Curriculum** page.
3. Apply fetch method:
   - RSS present → RSS MCP :contentReference[oaicite:22]{index=22}
   - No RSS → RSSHub→RSS MCP (if possible) :contentReference[oaicite:23]{index=23}
   - Otherwise → page-diff + (optional) news API MCP alerts :contentReference[oaicite:24]{index=24}

> Notes: SEA naming varies; Ohio is listed as “Department of Education and Workforce” in the CCSSO directory. :contentReference[oaicite:25]{index=25}

---

## Alabama — Alabama Department of Education
- **Press releases:** look for News / Press / Media / Communications
- **Standards changes:** look for Academic Standards / Curriculum / State Board agenda packets
- **Fetch:** RSS→RSS MCP; else RSSHub/page-diff; add news API alerts :contentReference[oaicite:26]{index=26}

## Alaska — Department of Education and Early Development
- Press releases; Standards/Curriculum/Frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:27]{index=27}

## Arizona — Department of Education
- Press releases; Standards (often “Academic Standards”)
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:28]{index=28}

## Arkansas — Department of Education
- Press releases; Standards/Frameworks + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:29]{index=29}

## California — Department of Education
- Press releases; Standards/Frameworks + State Board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:30]{index=30}

## Colorado — Department of Education
- Press releases; Academic Standards + board/commission updates
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:31]{index=31}

## Connecticut — State Department of Education
- Press releases; Standards/Curriculum frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:32]{index=32}

## Delaware — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:33]{index=33}

## District of Columbia — Office of the State Superintendent of Education
- Press releases; Standards/Curriculum guidance
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:34]{index=34}

## Florida — Department of Education
- Press releases; Standards (“B.E.S.T.”, etc. as applicable) + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:35]{index=35}

## Georgia — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:36]{index=36}

## Hawaii — State Department of Education
- Press releases; Standards/Curriculum (HIDOE-specific structure)
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:37]{index=37}

## Idaho — Department of Education
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:38]{index=38}

## Illinois — State Board of Education
- Press releases; Learning Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:39]{index=39}

## Indiana — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:40]{index=40}

## Iowa — Department of Education
- Press releases; Standards/Curriculum (Iowa Core, etc.)
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:41]{index=41}

## Kansas — State Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:42]{index=42}

## Kentucky — Department of Education
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:43]{index=43}

## Louisiana — Department of Education
- Press releases; Standards/Curriculum (“Student Standards”) + BESE actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:44]{index=44}

## Maine — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:45]{index=45}

## Maryland — Department of Education
- Press releases; Standards/Curriculum frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:46]{index=46}

## Massachusetts — Department of Elementary and Secondary Education
- Press releases; Curriculum Frameworks (MA frameworks)
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:47]{index=47}

## Michigan — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:48]{index=48}

## Minnesota — Department of Education
- Press releases; Standards/Academic Standards
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:49]{index=49}

## Mississippi — Department of Education
- Press releases; College- & Career-Readiness Standards / Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:50]{index=50}

## Missouri — Department of Elementary and Secondary Education
- Press releases; Learning Standards
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:51]{index=51}

## Montana — Office of Public Instruction
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:52]{index=52}

## Nebraska — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:53]{index=53}

## Nevada — Department of Education
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:54]{index=54}

## New Hampshire — Department of Education
- Press releases; Curriculum Frameworks / Standards
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:55]{index=55}

## New Jersey — Department of Education
- Press releases; Student Learning Standards (NJ standards)
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:56]{index=56}

## New Mexico — Public Education Department
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:57]{index=57}

## New York — State Education Department
- Press releases; Learning Standards / Curriculum guidance
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:58]{index=58}

## North Carolina — Department of Public Instruction
- Press releases; Standard Course of Study / Standards updates
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:59]{index=59}

## North Dakota — Department of Public Instruction
- Press releases; Standards/Curriculum
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:60]{index=60}

## Ohio — Department of Education and Workforce
- Press releases; Learning Standards / Model Curricula + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:61]{index=61}

## Oklahoma — State Department of Education
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:62]{index=62}

## Oregon — Department of Education
- Press releases; Academic Content Standards / Frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:63]{index=63}

## Pennsylvania — Department of Education
- Press releases; Academic Standards / SAS-aligned resources (as applicable)
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:64]{index=64}

## Rhode Island — Department of Education
- Press releases; Standards/Curriculum frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:65]{index=65}

## South Carolina — Department of Education
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:66]{index=66}

## South Dakota — Department of Education
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:67]{index=67}

## Tennessee — Department of Education
- Press releases; Academic Standards / Frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:68]{index=68}

## Texas — Texas Education Agency
- Press releases; Standards (“TEKS”) + SBOE actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:69]{index=69}

## Utah — State Board of Education
- Press releases; Core Standards / Standards + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:70]{index=70}

## Vermont — Agency of Education
- Press releases; Standards/Frameworks
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:71]{index=71}

## Virginia — Department of Education
- Press releases; Standards (“SOL”) + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:72]{index=72}

## Washington — Office of Superintendent of Public Instruction
- Press releases; Learning Standards + SBE/OSPI actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:73]{index=73}

## West Virginia — Department of Education
- Press releases; College- & Career-Readiness Standards + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:74]{index=74}

## Wisconsin — Department of Public Instruction
- Press releases; Academic Standards revisions + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:75]{index=75}

## Wyoming — Department of Education
- Press releases; Standards/Curriculum + board actions
- Fetch: RSS/RSSHub/page-diff + aggregation alerts :contentReference[oaicite:76]{index=76}

---

# H. Common Core Standards (Federal/Common Core reference set)

## Official “Read the Standards”
- Read the Standards landing page :contentReference[oaicite:77]{index=77}
- Math standards section :contentReference[oaicite:78]{index=78}

## Canonical PDFs
- CCSSO-hosted Math Standards PDF :contentReference[oaicite:79]{index=79}

## Development/background (useful for product/policy framing)
- Common Core development process page :contentReference[oaicite:80]{index=80}

**Fetch**
- Page-diff the key pages/PDFs (and/or RSS if a feed is available)
- Add news API alerts for “Common Core” + “CCSSO” + relevant policy terms :contentReference[oaicite:81]{index=81}

---

## I. Recommended implementation blueprint (minimal effort, maximum coverage)

1) **RSS MCP**: primary ingestion for:
   - top publications
   - vendor blogs/release notes
   - any SEA news pages that publish RSS
   - any government RSS feeds you identify :contentReference[oaicite:82]{index=82}

2) **One news MCP** (choose one):
   - NewsAPI MCP for broad monitoring, or
   - Google News MCP (SerpAPI) for query-centric monitoring, or
   - GDELT MCP for large-scale event/trend monitoring :contentReference[oaicite:83]{index=83}

3) **Page-diff backstop**
   - For SEAs without RSS
   - For standards landing pages and PDF updates (most common pattern)

4) **Verification workflow**
   - Treat aggregation hits as “signals”
   - Verify on primary-source SEA / board documents before acting

---

## Source directory references used
- CCSSO SEA Directory (all states + DC list) :contentReference[oaicite:84]{index=84}
- Common Core “Read the Standards” pages :contentReference[oaicite:85]{index=85}
- CCSSO-hosted Common Core Math PDF :contentReference[oaicite:86]{index=86}
- MCP availability examples (RSS, NewsAPI, Google News, GNews, GDELT) :contentReference[oaicite:87]{index=87}
