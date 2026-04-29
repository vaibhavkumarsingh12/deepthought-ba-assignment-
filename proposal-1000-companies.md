# Question 2 — Proposal: Sourcing 1000 Federer-Profile Companies in 30 Days

*Vaibhav Kumar Singh — DeepThought BA Assignment Part B*

---

## 1. Executive summary

This proposal outlines a 30-day execution plan to source **1,000 verified Federer-profile companies** from a starting universe of ~3,500–4,000 candidates across India, using a **Land + Labor + Capital triangulation** sourcing approach combined with AI-assisted scoring and human quality assurance.

| Metric | Target |
|---|---|
| Final delivered list size | 1,000 companies |
| Starting universe | 3,500–4,000 |
| Target precision | ≥85% (≥850 of 1000 verified pass on full 6-criterion check) |
| Total budget | Rs.18,000–22,000 (tool subscriptions + AI API) |
| Timeline | 30 calendar days |
| Team configuration | 1 analyst (Weeks 1–4) + 0.5 QA reviewer (Weeks 3–4) |

---

## 2. The funnel

```
                        SOURCING UNIVERSE
                          ~3,500–4,000
                                │
                                ▼
                     MECHANICAL PRE-FILTER
                       (Stage 1 — Week 1)
                          ~1,500–1,800
                                │
                                ▼
                     AI FIRST-PASS SCORING
                       (Stage 2 — Week 2)
                          ~1,100–1,200
                                │
                                ▼
                  AI RE-SCORING (Borderline only)
                       (Stage 3 — Week 3)
                            ~400–500
                                │
                                ▼
                    HUMAN QA SAMPLE (10%)
                       (Stage 3 — Week 3)
                            100 sample
                                │
                                ▼
                    FINAL ASSEMBLY + DEDUP
                       (Stage 4 — Week 4)
                              1,000
```

### Yield assumptions per stage

| Stage | Input | Output | Drop rate | Why |
|---|---|---|---|---|
| Sourcing | — | 3,750 | — | Aggregate of 7 sources after first dedup |
| Mechanical pre-filter | 3,750 | 1,650 | 56% | Auto-disqualify on size/state/sector mismatch using regex + simple rules |
| AI first-pass scoring | 1,650 | 1,150 | 30% | AI scores each company on 6 criteria; companies scoring <40/60 dropped |
| AI re-scoring (borderline 40–48 score band) | 480 | 360 net add | — | Higher-context model resolves borderline cases |
| Human QA on 10% sample | 1,150 → 1,100 | 1,100 | 4% | QA catches AI mis-classifications |
| Final assembly + dedup + format | 1,100 | 1,000 | 9% | Final dedup, format consistency, gap-fill |

The 10% QA sample drives a **systematic correction factor** — if QA finds X% false-positive rate in the sample, the same rate is assumed across the full list and an equivalent number of borderline-tier companies are added back from the re-scoring queue. This protects precision without re-running QA across all 1,150 companies.

---

## 3. Sourcing plan — the 7-channel mix

Sources mapped to the **Land / Labor / Capital** triangulation framework. Each source's expected yield is the count of *unique candidates surfaced before any filtering* — overlap is significant and is handled in dedup.

| # | Source | Signal type | Expected unique yield | Access method | Cost |
|---|--------|-------------|----------------------|---------------|------|
| 1 | DSIR R&D Recognition Registry | Capital (R&D investment) | 800–1,000 | Direct download (`dsir.gov.in`), Excel parse | Free |
| 2 | BSE SME + NSE Emerge listings | Capital (transparency) | 400–500 | Exchange filings download, DRHP parse | Free |
| 3 | MCA filings via Tofler / ZaubaCorp | Capital (financial scale) | 1,000–1,500 | API or paid scraper | Rs.4,000 (Tofler subscription, 1 month) |
| 4 | State industrial directories — MIDC + GIDC + KIADB + TIDCO | Land (physical presence) | 500–600 | Web scrape state portals | Free |
| 5 | PLI awardee lists | Land (capacity expansion) | 300–400 | Government press releases + ministry websites | Free |
| 6 | LinkedIn Sales Navigator (filtered) | Labor (hiring activity) | 400–600 | Sales Navigator API/exports | Rs.7,000 (1 month) |
| 7 | USFDA + EU-GMP + WHO-PQ + CDSCO databases | Capital (regulatory grade) | 300–400 | Direct database scraping | Free |

**Plus an enrichment layer** applied to the mid-funnel (~Stage 2) candidates:
- Trade-fair exhibitor lists (CPHI India, India Chem, Medical Fair India)
- Industry-association member directories (IDMA, CHEMEXCIL, IDA)
- Equipment-vendor reference customer mining (Agilent, Waters, Haas case studies)

These enrichment sources are not high-volume primary discovery — they are *verification* signals applied selectively to companies in the borderline 40–48 scoring band, raising or lowering the score based on triangulation confirmation.

**Customs / trade-flow data** (Zauba/ExportGenius/Volza) is *deferred* to Stage 3 verification only — not used for primary discovery — to minimize DPDP Act 2023 compliance exposure on commercial use of trade-bill data referencing specific corporate entities.

---

## 4. Tooling stack

| Layer | Tool | Purpose | Cost |
|---|------|---------|------|
| Scraping orchestration | Python + Playwright | Headless browser scraping for sites with JS-heavy rendering | Free |
| HTML parsing | Beautiful Soup 4 + lxml | Parsing static HTML (DSIR, MIDC, exchange filings) | Free |
| Data engineering | Pandas + DuckDB | Dedup, normalization, score aggregation | Free |
| AI scoring (first pass) | Claude Haiku via Anthropic API | Fast/cheap scoring of 1,650 companies × ~6 criteria | Rs.1,500–2,000 |
| AI re-scoring (borderline) | Claude Sonnet via Anthropic API | Higher-context resolution of borderline 40–48 scores | Rs.2,500–3,500 |
| Financial data lookup | Tofler subscription | Bulk MCA data access | Rs.4,000 |
| LinkedIn enrichment | Sales Navigator | Hiring + decision-maker lookup | Rs.7,000 |
| Project tracking | Google Sheets + GitHub | Audit trail, source-of-record list | Free |
| **Total tooling cost** | | | **Rs.15,000–16,500** |
| Buffer (web-search API, misc) | | | Rs.3,000–5,500 |
| **Total project budget** | | | **Rs.18,000–22,000** |

### Why this AI tier-split

Single-model scoring of 1,650 companies on Sonnet would cost ~Rs.9,000–11,000 and would mostly waste capacity on clear pass/fail cases. The two-tier approach uses Haiku (~Rs.1.50 per company including caching) for first-pass elimination, then escalates only the borderline 40–48 score band (~480 companies) to Sonnet (~Rs.6 per company). Net cost is ~60% lower without precision loss, because clear pass/fail cases don't benefit from the higher-tier model.

---

## 5. AI scoring methodology

### The scoring rubric

Each company is scored on the same 6 criteria from Part A:

| Criterion | Score range | What AI sees |
|---|---|---|
| C1 — Manufacturer | 0–10 | Website extract (8K tokens), product page, "About Us" |
| C2 — India-based | 0–5 | Registered address, factory address, MCA state filing |
| C3 — Differentiation | 0–15 | Certifications, patents, niche product names, "first/only" claims |
| C4 — Technical DM | 0–10 | LinkedIn profile of MD/founder, company About-Us bios |
| C5 — Sector tailwind | 0–10 | Sector classification + standard tailwind dataset (PLI, China+1, exports) |
| C6 — Active growth | 0–10 | Recent news, hiring count, certification/expansion announcements last 18 months |
| **Total** | **0–60** | Pass threshold: 48; Re-score band: 40–48; Fail: <40 |

### Anti-hallucination protocol — built into every prompt

Every AI scoring prompt prepends a hard-rules block:

```
HARD RULES:
(a) Do not fabricate revenue figures. If revenue not explicitly visible in
    provided context, output "Unknown".
(b) Do not infer founder credentials from name alone — require institution
    name in provided LinkedIn/About context.
(c) If company is part of a larger group, parent revenue >Rs.500Cr,
    or recently PE-acquired — auto-fail with reason flag.
(d) Do not classify CRO/services/testing-lab as manufacturer.
(e) Each score must cite the specific phrase or fact from provided context.
(f) If uncertain, score lower and flag for re-scoring.
```

### Provenance tracking

Every AI score output is paired with:
- The source-text snippet that drove the score (citation)
- The source URL
- Timestamp of context retrieval

This makes every cell in the final 1,000-company list **defensibly verifiable** — the recruiter can ask "why did you score X's C3 as 14/15?" and the answer is the exact website paragraph cited.

---

## 6. Quality assurance protocol

### The 10% sample QA

A stratified random sample of 100 companies (selected proportionally across pass tier, re-score tier, and just-failed tier) is manually reviewed by a human QA reviewer in Week 3.

### What the QA reviewer checks per company

i. Revenue band: cross-check against MCA filing (independent of AI input)
ii. Ownership/group affiliation: independent Google + Tofler director check
iii. C1 manufacturer status: confirm physical production, not services/CRO
iv. At least one cited certification or patent matches a primary database

### What QA-found errors trigger

- Single error of revenue or ownership type → re-run that filter across full 1,150 list (~3 hours of automated re-checks)
- Single error of differentiation type → flag the AI prompt for refinement, re-score the relevant tier
- Pattern of errors in one source → audit that source's pre-filter rules

### The systematic correction factor

If QA finds N% false-positive rate in the 100-sample, the proposal assumes the same rate across the 1,150 unsampled companies and adds back (1,150 × N%) borderline candidates from the re-scoring band to maintain target precision. This is a *known-quality-managed* output, not an aspirational claim of zero defects.

---

## 7. Week-by-week execution schedule

### Week 1 — Sourcing + scraping

| Day | Activity |
|---|---|
| Mon-Tue | Set up Python/Playwright environment; configure Tofler API; download DSIR registry; build dedup pipeline |
| Wed | Scrape MIDC + GIDC + KIADB + TIDCO directories |
| Thu | Pull BSE SME + NSE Emerge listings + DRHP filings |
| Fri | LinkedIn Sales Navigator export (saved searches: technical hiring + city filter) |
| Sat | USFDA/EU-GMP/WHO-PQ/CDSCO database scrapes |
| Sun | Buffer + dedup pass 1 — combine all sources, normalize company names, drop obvious duplicates |

**Week 1 deliverable:** Master CSV of 3,500–4,000 unique candidate companies with source provenance.

### Week 2 — Pre-filter + AI first-pass scoring

| Day | Activity |
|---|---|
| Mon | Apply mechanical pre-filter (regex on size/state/sector) — drop ~2,100 obvious fails |
| Tue | Build AI scoring prompt, validate on 30 known-pass and 30 known-fail companies |
| Wed-Fri | Run Claude Haiku scoring on 1,650 companies (batch, ~3-second per company including 8K token web scrape) |
| Sat | Quality spot-check on ~50 random scored companies |
| Sun | Buffer + re-run failed scrapes |

**Week 2 deliverable:** 1,150 AI-scored companies with criterion-level scores and source citations.

### Week 3 — Re-scoring + QA + enrichment

| Day | Activity |
|---|---|
| Mon-Tue | Sonnet re-score the 480 borderline (40–48 score) companies with extended context |
| Wed | Apply enrichment signals (trade-fair exhibitor cross-reference; equipment-vendor reference cross-reference) |
| Thu-Fri | QA reviewer manual verification of 100-sample stratified across tiers |
| Sat | Apply systematic correction factor; resolve QA-found errors |
| Sun | Buffer |

**Week 3 deliverable:** 1,100 corrected, QA-validated companies; precision-quality-managed.

### Week 4 — Final assembly + dedup + handover

| Day | Activity |
|---|---|
| Mon-Tue | Final dedup (multi-entity matching, parent-subsidiary collapse) |
| Wed | Format harmonization to handover schema (28 columns matching Part A) |
| Thu | Final assembly to 1,000-company list (drop lowest-scoring 100 above target) |
| Fri | Documentation: methodology note, source-list register, QA log, audit trail |
| Sat | Handover to SDR team in agreed format (CSV + Excel + PostgreSQL dump) |
| Sun | Buffer |

**Week 4 deliverable:** 1,000 verified Federer-profile companies + complete audit trail.

---

## 8. Risk register

| # | Risk | Likelihood | Impact | Mitigation |
|---|------|-----------|--------|------------|
| 1 | Sourcing yield falls short (universe <3,000) | Medium | High | Activate enrichment-source primary use (trade fairs, industry associations); extend timeline 3 days |
| 2 | Scraping blocks (anti-bot on government / exchange sites) | High | Medium | Rotate user agents, headless browsers, IP rotation via residential proxy (~Rs.2,000 contingency); fallback to manual download for blocked sources |
| 3 | AI hallucination produces false positives in passing tier | Medium | High | QA sample design + systematic correction factor + every score paired with cited source-text snippet |
| 4 | False negatives — genuine Federers scored as fail | Medium | Medium | Re-scoring band (40–48) is intentionally wide to catch false negatives; enrichment layer at Stage 3 |
| 5 | Dedup errors (parent-subsidiary or multi-entity confusion) | Medium | Medium | MCA CIN-based matching as primary key; manual review of top-100 ambiguous cases |
| 6 | Data freshness drift (FY24 filings replaced by FY25 mid-project) | Low | Low | Lock data snapshot date at Week 1 Day 1; re-pull only if delta material |
| 7 | Compliance review on customs/trade data delays delivery | Low | Medium | Customs data is Stage 3 verification only, not primary discovery — removable without scope impact |
| 8 | LinkedIn rate-limit blocks technical hiring search | Medium | Low | Sales Navigator paid tier reduces blocks; Naukri as backup labor-signal source |

---

## 9. Deliverable format

Final 1,000-company list provided in three formats simultaneously:

i. **CSV** — primary handover format, 28 columns matching Part A schema, UTF-8 encoded
ii. **Excel** — same data, with conditional formatting on score columns for visual triage
iii. **PostgreSQL schema dump** — for SDR team integration into CRM

Each company row includes:
- 6-criterion score breakdown
- Per-criterion source citation (URL + extracted phrase)
- Personalization hook for outreach line 1
- Data freshness timestamp
- Provenance flag indicating which sources surfaced this company

**Refresh cadence recommendation:** Quarterly re-score on a rolling basis. Companies above the Rs.450Cr revenue band should be flagged for monthly re-check — these are most likely to outgrow the band.

---

## 10. What this proposal does *not* commit to

i. **100% precision.** Target is ≥85%, with QA-driven correction factor. Claiming 100% on a 1,000-company AI-scored list would be neither honest nor achievable.

ii. **Personal outreach drafting.** The list is sourcing-only. Outreach drafting is a separate workstream that can build on this dataset.

iii. **CRM integration.** PostgreSQL dump format is provided; integration with specific CRM (Salesforce, HubSpot, Zoho) is out of scope for the 30-day window but can be costed separately.

iv. **Real-time data monitoring.** This is a snapshot deliverable. Continuous monitoring (e.g., weekly hiring-signal refresh, MCA filing alerts) is a separate ongoing-service scope.

---

## 11. Sourcing approach summary — the differentiator

Most sourcing exercises rely on Tier 1 (DSIR, BSE, MCA, MIDC) — fast, free, and surface-level. This approach works for surfacing "any manufacturer in segment" but produces ~50% precision when filtered for the *Federer* profile specifically.

The triangulation approach — combining **Land** signals (industrial-park allotments, PLI awards), **Labor** signals (LinkedIn technical hiring, R&D-Lead postings), and **Capital** signals (patent filings, USFDA approvals, equipment-vendor references) — surfaces a substantially higher-precision candidate pool. The mechanism is that no single signal alone proves Federer status, but a company that triangulates positively on all three is *near-certain* to fit the ICP.

This is the basis for the ≥85% target precision in this proposal — precision earned by triangulation, not claimed in advance.

---

*Proposal authored by Vaibhav Kumar Singh as part of the DeepThought Business Analytics Fellowship application.*
