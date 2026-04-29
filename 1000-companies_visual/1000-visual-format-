# Question 2 — Proposal: Sourcing 1000 Federer-Profile Companies in 30 Days

*Vaibhav Kumar Singh — DeepThought BA Assignment Part B*

---

## 1. Executive Summary

> **Mission:** Source **1,000 verified Federer-profile companies** from ~3,500–4,000 candidates across India in 30 days using Land + Labor + Capital triangulation + AI-assisted scoring.

| Metric | Target |
|---|---|
| 🎯 Final delivered list | **1,000 companies** |
| 🔍 Starting universe | **3,500–4,000** |
| ✅ Target precision | **≥85%** (≥850 of 1,000 verified) |
| 💰 Total budget | **Rs. 18,000–22,000** |
| 📅 Timeline | **30 calendar days** |
| 👥 Team | 1 Analyst (Wk 1–4) + 0.5 QA Reviewer (Wk 3–4) |

---

## 2. The Funnel — End-to-End Flow

```mermaid
flowchart TD
    A(["🌐 SOURCING UNIVERSE\n~3,500–4,000 companies\n7 channels combined"])
    B["⚙️ STAGE 1 — Mechanical Pre-Filter\nWeek 1 → ~1,500–1,800\nRegex on size/state/sector\nDrop rate: 56%"]
    C["🤖 STAGE 2 — AI First-Pass Scoring\nWeek 2 → ~1,100–1,200\nClaude Haiku scores 6 criteria\nDrop <40/60 | Drop rate: 30%"]
    D["🔁 STAGE 3A — AI Re-Scoring\nWeek 3 → ~400–500 borderline\nClaude Sonnet resolves 40–48 band\nHigher context model"]
    E["👁️ STAGE 3B — Human QA\nWeek 3 → 100-company sample\nStratified across tiers\nDrop rate: 4%"]
    F["🧹 STAGE 4 — Final Assembly\nWeek 4 → 1,000 companies\nDedup + format + gap-fill\nDrop rate: 9%"]
    G(["✅ FINAL DELIVERABLE\n1,000 Verified Federer Companies\nCSV + Excel + PostgreSQL"])

    A --> B --> C --> D --> E --> F --> G

    style A fill:#2C3E50,color:#fff
    style G fill:#27AE60,color:#fff
    style B fill:#2980B9,color:#fff
    style C fill:#8E44AD,color:#fff
    style D fill:#E67E22,color:#fff
    style E fill:#E74C3C,color:#fff
    style F fill:#16A085,color:#fff
```

### Funnel Yield at Each Stage

```mermaid
xychart-beta
    title "Company Count Through Funnel Stages"
    x-axis ["Universe", "Post Pre-Filter", "Post AI Haiku", "Post Re-Score", "Post QA", "Final List"]
    y-axis "Company Count" 0 --> 4000
    bar [3750, 1650, 1150, 1100, 1050, 1000]
```

### Stage-by-Stage Drop Summary

| Stage | Input | Output | Drop Rate | Reason |
|---|---|---|---|---|
| Sourcing | — | 3,750 | — | 7 sources after first dedup |
| Mechanical Pre-Filter | 3,750 | 1,650 | **56%** | Size/state/sector mismatch via regex |
| AI First-Pass (Haiku) | 1,650 | 1,150 | **30%** | Score <40/60 dropped |
| AI Re-Score (Sonnet) | 480 borderline | +360 net | — | 40–48 band resolved |
| Human QA (10%) | 1,150 | 1,100 | **4%** | AI mis-classifications caught |
| Final Assembly | 1,100 | 1,000 | **9%** | Dedup + format + fill |

---

## 3. Sourcing Plan — 7-Channel Mix

```mermaid
mindmap
  root((7 Sourcing\nChannels))
    Capital["💰 Capital Signals"]
      DSIR["1. DSIR R&D Registry\n800–1,000 yield | Free"]
      BSE["2. BSE SME + NSE Emerge\n400–500 yield | Free"]
      MCA["3. MCA via Tofler/Zauba\n1,000–1,500 yield | Rs.4,000"]
      USFDA["7. USFDA/EU-GMP/WHO-PQ\n300–400 yield | Free"]
    Land["🏗️ Land Signals"]
      MIDC["4. State Industrial Dirs\n500–600 yield | Free"]
      PLI["5. PLI Awardee Lists\n300–400 yield | Free"]
    Labor["👷 Labor Signals"]
      LI["6. LinkedIn Sales Navigator\n400–600 yield | Rs.7,000"]
```

### Channel Detail Table

| # | Source | Signal | Yield | Cost |
|---|--------|--------|-------|------|
| 1 | DSIR R&D Registry | 💰 Capital | 800–1,000 | Free |
| 2 | BSE SME + NSE Emerge | 💰 Capital | 400–500 | Free |
| 3 | MCA Filings (Tofler) | 💰 Capital | 1,000–1,500 | Rs. 4,000 |
| 4 | State Industrial Dirs | 🏗️ Land | 500–600 | Free |
| 5 | PLI Awardee Lists | 🏗️ Land | 300–400 | Free |
| 6 | LinkedIn Sales Nav | 👷 Labor | 400–600 | Rs. 7,000 |
| 7 | USFDA/EU-GMP/WHO-PQ | 💰 Capital | 300–400 | Free |

### Enrichment Layer (Mid-Funnel, Stage 2 Only)

```mermaid
flowchart LR
    BORDER["⚠️ Borderline Companies\nScore: 40–48 band\n~480 companies"]

    BORDER --> EV["⚙️ Equipment Vendor\nCase Studies\nAgilent, Waters, Haas"]
    BORDER --> TF["🎪 Trade Fair\nExhibitor Lists\nCPHI, India Chem"]
    BORDER --> IA["🤝 Industry Association\nDirectories\nIDMA, CHEMEXCIL, IDA"]

    EV --> VERDICT{"Triangulation\nResult?"}
    TF --> VERDICT
    IA --> VERDICT

    VERDICT -->|"Confirmed ✅"| PASS["Score ↑ → Pass Tier"]
    VERDICT -->|"Not Found ❌"| FAIL["Score ↓ → Drop"]

    style BORDER fill:#E67E22,color:#fff
    style PASS fill:#27AE60,color:#fff
    style FAIL fill:#E74C3C,color:#fff
```

> 📌 **Customs/Trade-Flow data (Zauba/ExportGenius)** is deferred to Stage 3 verification only — *not* used for primary discovery — to minimize **DPDP Act 2023** compliance risk.

---

## 4. Tooling Stack

```mermaid
flowchart TD
    subgraph SCRAPING ["🕷️ Data Collection Layer"]
        P["Python + Playwright\nHeadless browser scraping"]
        BS["BeautifulSoup4 + lxml\nStatic HTML parsing"]
    end

    subgraph ENGINEERING ["⚙️ Data Engineering Layer"]
        PD["Pandas + DuckDB\nDedup, normalize, aggregate"]
        GS["Google Sheets + GitHub\nAudit trail + source-of-record"]
    end

    subgraph AI ["🤖 AI Scoring Layer"]
        H["Claude Haiku\n1,650 companies × 6 criteria\nFast + cheap | Rs.1,500–2,000"]
        S["Claude Sonnet\n480 borderline companies\nHigher context | Rs.2,500–3,500"]
    end

    subgraph PAID ["💳 Paid Subscriptions"]
        T["Tofler\nBulk MCA data | Rs.4,000"]
        LN["LinkedIn Sales Navigator\nHiring enrichment | Rs.7,000"]
    end

    SCRAPING --> ENGINEERING --> AI
    PAID --> ENGINEERING
```

### Budget Breakdown

```mermaid
pie title Total Project Budget — Rs.18,000–22,000
    "LinkedIn Sales Navigator" : 7000
    "Tofler Subscription" : 4000
    "Claude Sonnet (borderline)" : 3000
    "Claude Haiku (first pass)" : 1750
    "Buffer / Misc / Web-search API" : 4250
```

### Why the 2-Tier AI Model Split?

| Approach | Cost | Precision | Verdict |
|---|---|---|---|
| All 1,650 on Sonnet | Rs. 9,000–11,000 | High | ❌ Wasteful — clear pass/fail don't need it |
| All 1,650 on Haiku | Rs. 2,475 | Medium | ❌ Borderline cases mis-scored |
| **Haiku (1st pass) + Sonnet (borderline)** | **Rs. 4,000–5,500** | **High** | ✅ 60% cost saving, same precision |

---

## 5. AI Scoring Methodology

### The 6-Criterion Scoring Rubric

```mermaid
flowchart LR
    CO["🏢 Company\nContext\n8K token input"] --> C1["C1 — Manufacturer\n0–10 pts\nWebsite + product page"]
    CO --> C2["C2 — India-Based\n0–5 pts\nRegistered + factory address"]
    CO --> C3["C3 — Differentiation\n0–15 pts\nCerts + patents + niche claims"]
    CO --> C4["C4 — Technical DM\n0–10 pts\nMD/Founder LinkedIn bio"]
    CO --> C5["C5 — Sector Tailwind\n0–10 pts\nPLI + China+1 + exports"]
    CO --> C6["C6 — Active Growth\n0–10 pts\nNews + hires + certs last 18m"]

    C1 --> TOTAL["🎯 Total Score\nout of 60"]
    C2 --> TOTAL
    C3 --> TOTAL
    C4 --> TOTAL
    C5 --> TOTAL
    C6 --> TOTAL

    TOTAL --> PASS["≥48 → ✅ PASS"]
    TOTAL --> RESCORE["40–47 → 🔁 RE-SCORE"]
    TOTAL --> FAIL["<40 → ❌ FAIL"]

    style PASS fill:#27AE60,color:#fff
    style RESCORE fill:#F39C12,color:#fff
    style FAIL fill:#E74C3C,color:#fff
```

### Criterion Weight Visualization

```mermaid
xychart-beta
    title "Score Weight per Criterion (out of 60 total)"
    x-axis ["C1 Manufacturer", "C2 India-Based", "C3 Differentiation", "C4 Technical DM", "C5 Tailwind", "C6 Growth"]
    y-axis "Max Points" 0 --> 20
    bar [10, 5, 15, 10, 10, 10]
```

> 🔍 **C3 — Differentiation** carries the highest weight (15 pts / 25%) — the core of the Federer distinction.

### Anti-Hallucination Protocol

```mermaid
flowchart TD
    PROMPT["AI Scoring Prompt"] --> HR["🔒 HARD RULES BLOCK\n(prepended to every prompt)"]

    HR --> R1["(a) No fabricated revenue\n→ output 'Unknown' if not visible"]
    HR --> R2["(b) No founder inference\nfrom name alone — require institution"]
    HR --> R3["(c) Parent rev >Rs.500Cr\nor PE-acquired → auto-fail"]
    HR --> R4["(d) CRO/testing lab ≠ manufacturer\n→ auto-fail with flag"]
    HR --> R5["(e) Every score must cite\nspecific phrase from context"]
    HR --> R6["(f) If uncertain → score lower\nand flag for re-scoring"]

    R1 & R2 & R3 & R4 & R5 & R6 --> OUTPUT["📋 Scored Output\n+ Citation per criterion\n+ Source URL\n+ Retrieval timestamp"]

    style HR fill:#E74C3C,color:#fff
    style OUTPUT fill:#27AE60,color:#fff
```

---

## 6. Quality Assurance Protocol

```mermaid
flowchart TD
    LIST["1,150 AI-Scored Companies"] --> SAMPLE["🎲 Stratified Random Sample\n100 companies\nProportional across tiers"]

    SAMPLE --> QA["👁️ Human QA Reviewer\nWeek 3 — Manual Verification"]

    QA --> Q1["i. Revenue band\n→ cross-check MCA filing"]
    QA --> Q2["ii. Ownership / group\n→ Google + Tofler director check"]
    QA --> Q3["iii. C1 manufacturer status\n→ confirm physical production"]
    QA --> Q4["iv. Cert / patent citation\n→ match primary database"]

    Q1 & Q2 & Q3 & Q4 --> FIND{"Error Found?"}

    FIND -->|"Revenue/Ownership Error"| FIX1["Re-run filter\nacross full 1,150 list\n~3 hrs automated"]
    FIND -->|"Differentiation Error"| FIX2["Refine AI prompt\nRe-score relevant tier"]
    FIND -->|"Source Pattern Error"| FIX3["Audit that source's\npre-filter rules"]
    FIND -->|"No Errors"| OK["✅ QA Passed\nProceed to assembly"]

    FIX1 & FIX2 & FIX3 --> CORRECT["📐 Systematic Correction Factor\nIf N% false-positive in sample\n→ add back (1,150 × N%) borderline\ncandidates to maintain precision"]

    style QA fill:#2980B9,color:#fff
    style CORRECT fill:#E67E22,color:#fff
    style OK fill:#27AE60,color:#fff
```

---

## 7. Week-by-Week Execution Schedule

```mermaid
gantt
    title 30-Day Execution Plan — Federer Profile Sourcing
    dateFormat  D
    axisFormat  Day %d

    section Week 1 — Sourcing + Scraping
    Setup Python/Playwright + Tofler API      :w1a, 1, 2d
    Scrape MIDC/GIDC/KIADB/TIDCO             :w1b, 3, 1d
    Pull BSE SME + NSE Emerge + DRHP         :w1c, 4, 1d
    LinkedIn Sales Navigator export          :w1d, 5, 1d
    USFDA/EU-GMP/WHO-PQ scrapes              :w1e, 6, 1d
    Dedup Pass 1 — Combine all sources       :w1f, 7, 1d

    section Week 2 — Pre-Filter + AI Scoring
    Mechanical pre-filter (regex rules)      :w2a, 8, 1d
    Build + validate AI scoring prompt       :w2b, 9, 1d
    Claude Haiku batch scoring (1,650 cos)   :w2c, 10, 3d
    Quality spot-check 50 random             :w2d, 13, 1d
    Buffer + re-run failed scrapes           :w2e, 14, 1d

    section Week 3 — Re-Score + QA + Enrich
    Sonnet re-score 480 borderline           :w3a, 15, 2d
    Apply enrichment signals                 :w3b, 17, 1d
    Human QA — 100-company sample            :w3c, 18, 2d
    Apply correction factor + fix errors     :w3d, 20, 1d
    Buffer                                   :w3e, 21, 1d

    section Week 4 — Assembly + Handover
    Final dedup + entity matching            :w4a, 22, 2d
    Format harmonization (28 columns)        :w4b, 24, 1d
    Final assembly to 1,000 list             :w4c, 25, 1d
    Documentation + audit trail              :w4d, 26, 1d
    Handover (CSV + Excel + PostgreSQL)      :w4e, 27, 1d
    Buffer                                   :w4f, 28, 1d
```

### Weekly Deliverables Summary

| Week | Key Activity | Deliverable |
|---|---|---|
| **Week 1** | Scraping + sourcing all 7 channels | Master CSV — 3,500–4,000 candidates + provenance |
| **Week 2** | Pre-filter + Claude Haiku scoring | 1,150 AI-scored companies + criterion citations |
| **Week 3** | Sonnet re-score + QA + enrichment | 1,100 QA-validated, precision-managed companies |
| **Week 4** | Dedup + format + handover | **1,000 verified Federer companies — full audit trail** |

---

## 8. Risk Register

```mermaid
quadrantChart
    title Risk Matrix — Likelihood vs Impact
    x-axis Low Likelihood --> High Likelihood
    y-axis Low Impact --> High Impact
    quadrant-1 "🔴 Act Now"
    quadrant-2 "🟠 Monitor Closely"
    quadrant-3 "🟡 Low Priority"
    quadrant-4 "🟠 Have Contingency"
    R1-Sourcing Yield Short: [0.45, 0.80]
    R3-AI Hallucination: [0.40, 0.85]
    R2-Scraping Blocks: [0.75, 0.50]
    R4-False Negatives: [0.50, 0.45]
    R5-Dedup Errors: [0.45, 0.45]
    R8-LinkedIn Rate-Limit: [0.55, 0.25]
    R6-Data Freshness: [0.20, 0.20]
    R7-DPDP Compliance: [0.20, 0.55]
```

### Full Risk Register

| # | Risk | Likelihood | Impact | Mitigation |
|---|------|-----------|--------|------------|
| 1 | Sourcing yield <3,000 | Medium | 🔴 High | Activate trade-fair + assoc. lists as primary; +3-day buffer |
| 2 | Anti-bot scraping blocks | High | 🟠 Medium | Rotate user agents + residential proxy (~Rs.2,000 contingency) |
| 3 | AI hallucination → false positives | Medium | 🔴 High | QA sample + correction factor + every score cited |
| 4 | False negatives — real Federers dropped | Medium | 🟠 Medium | Wide 40–48 re-score band + enrichment layer |
| 5 | Dedup errors (parent-subsidiary) | Medium | 🟠 Medium | MCA CIN-based primary key + manual top-100 review |
| 6 | Data freshness drift mid-project | Low | 🟡 Low | Lock snapshot date at Week 1 Day 1 |
| 7 | DPDP customs data compliance delay | Low | 🟠 Medium | Customs data = verification only; removable without scope impact |
| 8 | LinkedIn rate-limit blocks | Medium | 🟡 Low | Sales Nav paid tier + Naukri as backup |

---

## 9. Deliverable Format

```mermaid
flowchart LR
    FINAL["✅ 1,000 Verified\nFederer Companies"] --> CSV["📄 CSV\nPrimary handover\n28 columns\nUTF-8 encoded"]
    FINAL --> XLS["📊 Excel\nConditional formatting\non score columns\nVisual triage-ready"]
    FINAL --> PG["🗄️ PostgreSQL Schema Dump\nSDR/CRM integration\nready format"]

    CSV & XLS & PG --> COLS["Each Row Contains:\n✅ 6-criterion score breakdown\n✅ Per-criterion source citation\n✅ Personalization hook (outreach line 1)\n✅ Data freshness timestamp\n✅ Provenance flag (which sources found this co.)"]
```

### Refresh Cadence Recommendation

| Company Band | Recommended Re-Score Frequency |
|---|---|
| Revenue < Rs.100 Cr | Quarterly |
| Revenue Rs.100–450 Cr | Quarterly |
| Revenue > Rs.450 Cr (near top of band) | Monthly — flag for outgrowth risk |

---

## 10. What This Proposal Does *Not* Commit To

```mermaid
flowchart LR
    OUT(["❌ Out of Scope"]) --> O1["100% Precision\n— Target is ≥85%\nClaiming 100% on\nAI-scored list = dishonest"]
    OUT --> O2["Personal Outreach\nDrafting\n— Sourcing only;\noutreach = separate workstream"]
    OUT --> O3["CRM Integration\n— PostgreSQL dump provided;\nSalesforce/HubSpot/Zoho\ninteg. = separate scope"]
    OUT --> O4["Real-Time Monitoring\n— This is a snapshot.\nContinuous monitoring\n= separate ongoing service"]

    style OUT fill:#E74C3C,color:#fff
```

---

## 11. Sourcing Approach — The Differentiator

```mermaid
flowchart TD
    subgraph STANDARD ["🔵 Standard Approach (Most Candidates)"]
        S1[Tier 1 Only\nDSIR + BSE + MCA + MIDC]
        S1 --> SP["~50% Precision\nSurfaces 'any manufacturer\nin segment'"]
    end

    subgraph THIS ["🟢 This Proposal — Triangulation Approach"]
        T1[Tier 1 — Build Universe]
        T2[+ Tier 2 — Land Signals\nPLI + Mega Park Allotments]
        T3[+ Tier 4 — Labor Signals\nLinkedIn R&D Hiring]
        T4[+ Tier 3 — Capital Signals\nUSFDA + Patents + Equipment]
        T5[+ Tier 5 — Trade Verification\nImport Bill Cross-Check]

        T1 --> T2 --> T3 --> T4 --> T5
        T5 --> TP["≥85% Precision\nNear-certain Federer\nTriangulated on all 3 axes"]
    end

    STANDARD -.->|"This proposal upgrades to"| THIS

    style SP fill:#E74C3C,color:#fff
    style TP fill:#27AE60,color:#fff
```

### Precision Source — Earned, Not Claimed

| Signal Combination | Estimated Precision |
|---|---|
| Tier 1 only | ~50% |
| Tier 1 + Land | ~65% |
| Tier 1 + Land + Labor | ~78% |
| Tier 1 + Land + Labor + Capital | ~90% |
| All 5 Tiers (with QA correction) | **≥85–96%** |

> ✅ **The ≥85% target is precision earned by triangulation** — not claimed in advance. The QA-driven systematic correction factor is the mechanism that makes this a *known-quality-managed* output.

---

*Proposal authored by Vaibhav Kumar Singh as part of the DeepThought Business Analytics Fellowship application.*
