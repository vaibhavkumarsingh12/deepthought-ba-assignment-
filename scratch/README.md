# DeepThought BA Assignment — Execution Plan

**Candidate:** Vaibhav Kumar Singh
**Target city:** Pune
**Target segments:** Basket A — (i) Custom synthesis & specialty chemicals (ii) Specialty diagnostics & life-science tools
**Total time available:** 5 days (per assignment brief)
**Plan-B trigger:** if after researching 30 candidates, fewer than 10 pass → switch to Vadodara/Ahmedabad specialty chemicals

---

## What you are submitting (the actual deliverables)

There are **6 things** you submit, in **2 places**.

| # | Deliverable | Format | Where it goes |
|---|------------|--------|---------------|
| 1 | CSV of 25 scored Pune companies | `companies.csv` | GitHub repo |
| 2 | Methodology document | `methodology.md` | Same GitHub repo |
| 3 | Code/prompts you used | `prompts.md` + any scripts | Same GitHub repo |
| 4 | Sourcing-methods answer (Q1) | Plain text | Internshala chat |
| 5 | 1000-company proposal (Q2) | `proposal-1000-companies.md` | Same GitHub repo |
| 6 | **Hand-drawn diagram** of the 1000-company plan | Photo of paper sketch | Internshala chat — **mandatory, no review without it** |

The GitHub repo link is shared on Internshala. So Internshala chat ends up with: GitHub link + Q1 text + diagram photo.

---

## The core risk you must manage

The brief says four times that they will verify your claims, and that 90% of submissions get rejected for being copy-pasted AI output. So the *real* deliverable is not the CSV — it is **a CSV plus a paper trail proving every score is grounded in a real, citable source**. If any single revenue figure, certification, or founder credential is fabricated, the application is dead.

This means the entire plan is designed around one principle: **Source first. AI second. Verify before you write.** Never let an LLM generate a fact you have not personally seen on a primary source.

---

## Repo structure (build this on Day 0)

```
deepthought-ba-assignment/
├── README.md                         ← what's in this repo + how to read it
├── companies.csv                     ← Part A primary deliverable (25 companies)
├── methodology.md                    ← how you found them, what you learned
├── prompts.md                        ← every prompt you used + guardrails
├── proposal-1000-companies.md        ← Part B Question 2 write-up
├── sources/
│   ├── dsir-pune-extract.csv         ← your DSIR pull (already done)
│   ├── bse-sme-maharashtra.csv       ← BSE SME listing pull
│   ├── usfda-maharashtra-extract.md  ← USFDA list (already uploaded)
│   ├── midc-pune-chem-list.csv       ← MIDC directory pull
│   └── README.md                     ← what each source is, when accessed
├── research-log/
│   ├── companies-investigated.csv    ← all 75-100 companies looked at, pass/fail + reason
│   └── disqualifications.md          ← why each fail company failed (drives narrative quality)
└── scratch/                          ← your working notes, not in final review
```

---

## Day-by-day plan

### Day 0 (today, ~2 hours) — Setup and seed list

1. Create the GitHub repo with the structure above. Push a placeholder README. Get the link.
2. Drop your DSIR extract and the USFDA list into `/sources/`.
3. Pre-triage the DSIR list — mark every entry as **Disqualify / Promising / Verify**. Pre-triage output is in the next section.
4. Build a 24-row research log skeleton in `/research-log/companies-investigated.csv`.
5. Open one tab to **Tofler.in** (or **ZaubaCorp** as backup) — these are the MCA-data viewers you will use to verify revenue and ownership.
6. Open Tofler accounts. Both have free tiers; Tofler shows revenue and director-level ownership for free.

Stop here on Day 0. Do not start company-by-company research yet. The next day starts with two more sourcing layers.

### Day 1 — Sourcing breadth (~5 hours)

Goal of the day: end with **80–120 unique candidate names** in your research log, before doing any deep research.

1. **Pull BSE SME + NSE Emerge listings filtered to Maharashtra chem/pharma/diagnostics.** Both exchanges publish company lists. BSE SME at `bsesme.com`, NSE Emerge at `nseindia.com/companies-listing/sme-emerge`. Filter by state = Maharashtra and industry = Pharmaceuticals / Chemicals / Healthcare. Save to `/sources/bse-sme-maharashtra.csv`. Expect ~30–50 names.
2. **Pull the MIDC directory for Pune district** via `maharashtradirectory.com` for the queries: `specialty chemicals Pune`, `pharmaceutical intermediates Pune`, `diagnostic kits Pune`, `fine chemicals Pune`, `enzyme manufacturer Pune`. Save what you find.
3. **Cross-reference your DSIR list against the USFDA list** — any company appearing in both gets a *very* high prior of passing. From your uploads I can already see one immediate hit: **Cipla Kurkumbh** (USFDA) — but Cipla is auto-disqualified for size, so it doesn't help. Look for smaller cross-hits like Okasa Pharma (Satara — outside Pune district per the brief's "operational presence" rule, but worth flagging).
4. **De-duplicate.** Same company often appears under slightly different names across sources. Build the master list in `/research-log/companies-investigated.csv`.
5. **Apply pre-filter** — auto-disqualify obvious fails *without* opening the website yet:
   - Anything where you already know revenue >Rs.500Cr (Lupin, Serum, Cipla, Tata Chemicals, Hikal, Sudarshan, Alkyl Amines, etc.)
   - Anything where the registered office is Mumbai/elsewhere AND no clear Pune R&D or factory (City rule — operational presence required)
   - PSUs (Hindustan Antibiotics)
   - Subsidiaries of large groups (Fujifilm Sericol = Fujifilm Japan)
   - Anything that is obviously a CRO from the name (e.g. "Preclinical Research" in the name)

End of Day 1: ~50 names auto-disqualified, ~50–70 surviving names to investigate.

### Day 2 — Deep research, batch 1 (~7 hours)

Research **40 companies** today. Yes, that's aggressive. The trick is to triage fast and only go deep on companies that survive the first two minutes.

For each company use this pipeline, in this order:

1. **Open the website (60 seconds).** Two questions only — *(a) is it a manufacturer or a service provider?* *(b) is the website fresh (copyright 2024–2026, news in last 12 months)?* If either is no → log as fail with reason, move on. This kills ~30% in 60 seconds.
2. **Tofler/ZaubaCorp lookup (90 seconds).** Pull last-3-FY revenue + director list + paid-up capital. Three checks: revenue Rs.30–500Cr, no PE/VC director appointments in last 3 years, founder/family on board. If revenue >500Cr or PE-controlled → fail, log reason. This kills another ~30%.
3. **DM background (3 minutes).** Find the founder/MD on LinkedIn. Look for: PhD, IIT/NIT/IISc/BITS, ex-DRDO/ISRO/CSIR, prior technical employer (pharma/chem company). Note the specific institution and year. This is C4 evidence.
4. **Differentiation evidence (5 minutes).** Specific named products. USFDA / EU-GMP / DSIR / WHO-GMP / CDSCO / NABL / ISO 13485 / AS9100. *Specific certifications, not "ISO certified".* Patent count from `ipindia.gov.in` if available. "First/only/pioneer" claims with year and source. This is C3 evidence.
5. **Growth signals (5 minutes).** Company news section, Press releases, LinkedIn company page. Look for: new facility in last 18 months, capacity expansion, new certification, hiring posts on LinkedIn/Naukri, recent funding/IPO, export market expansion. This is C6 evidence.
6. **Sector tailwind (already known per segment).** Specialty chem → China+1, PLI for chemicals/pharma, exports. Diagnostics → CDSCO IVD framework, Make-in-India medical devices, ICMR push. Just write the line that applies. This is C5 evidence.
7. **Personalization hook.** Pick the single most specific recent fact from steps 4 or 5 that could open a sales email. *"You inaugurated a new fermentation facility in Chakan in March 2025"* — that kind of specificity. Not *"you are growing fast in your sector"*.

For each company write **one row** in `companies-investigated.csv` with: name | verdict (pass/fail) | reason in one line | sources cited | minutes-spent.

Even fails get logged with reason. The methodology document later tells the story of *which fails were instructive*.

End of Day 2 target: 40 companies investigated, ~12 passes, ~28 fails. Pass rate 30% = on track.

### Day 3 — Deep research, batch 2 + write up passes (~7 hours)

1. Research the next 35 companies (same pipeline). Target ~10 more passes — total ~22 by end of day.
2. Start writing the **passes** into `companies.csv` using the exact format from the sample CSV (28 columns — see "CSV format" section below).
3. If you are short of 25 passes by end-of-day, you have two options:
   - Pull more candidates from the BSE SME/MIDC reserve list
   - **Plan-B trigger** — if total pool exhausted at <20 passes, partial-switch to Vadodara/Ahmedabad and add 5–10 Gujarat names. Document the switch in the methodology — *demonstrating* you noticed the yield problem and adjusted is itself the kind of judgment they're testing for.

End of Day 3 target: 25 passes profiled in CSV, ~75 companies investigated total in research log.

### Day 4 — Methodology document + Part B (~7 hours)

Switch from research to writing.

1. **Methodology document (~3 hours)** — see structure in next section.
2. **Q1 — Sourcing methods answer (~1 hour)** — 8–12 distinct methods, each with name + why it fits this ICP + one concrete limitation.
3. **Q2 — 1000-company proposal (~3 hours)** — written up to the level of the sample proposal already in the brief (you have it as reference).

### Day 5 — Hand-drawn diagram + final QA + submit (~4 hours)

1. **Hand-drawn diagram (~30 minutes).** Pen, paper, A4 sheet. Photograph in good light. Show: sources fan-in → universe → AI-scoring → QA → final 1000, plus week-by-week timeline, plus tools at each step. Detail in "Diagram structure" section below.
2. **Final QA pass (~2 hours)** — re-verify the 5 most surprising claims in your CSV (revenue, certification, founder credentials). The brief says they verify, so verify yourself first.
3. **Submit** — push final repo, copy GitHub link to Internshala, paste Q1 answer in Internshala chat, attach diagram photo.

---

## Pre-triage of your DSIR list (use this as your starting point)

I went through every entry in your DSIR pull. Here is the verdict:

### Auto-disqualify (do NOT waste research time — 16 names)

| Company | Reason |
|---|---|
| Tata Chemicals | Tata Group + too big |
| Hindustan Antibiotics | PSU, fails promoter-driven |
| Lupin Ltd | Way too big (~Rs.20,000Cr+) |
| Serum Institute of India | Way too big (~Rs.10,000Cr+) |
| Granules India | Hyderabad-listed, too big, Pune is one of many sites |
| Emcure Pharmaceuticals | IPO 2024, Bain Capital was holder, likely outgrew band |
| Hikal Ltd | Listed, ~Rs.2,000Cr — too big |
| Sudarshan Chemical Industries | Listed, ~Rs.2,500Cr — too big |
| Alkyl Amines Chemicals | Listed, ~Rs.1,500Cr — too big |
| Clean Science and Technology | Listed, likely above ceiling — verify current FY |
| Strand Life Sciences | Bengaluru + Eurofins-acquired |
| Enza Zaden India | Manufacturing in Bangalore, not Pune |
| Centaur Pharmaceuticals | Mumbai HQ + Mumbai primary manufacturing |
| Indian Oxides and Chemicals | Mumbai HQ — verify if Pune is operational not satellite |
| OmniActive Health Technologies | Mumbai HQ + multi-location |
| Fujifilm Sericol India | Subsidiary of Fujifilm Japan |

### Promising — investigate first (high prior of passing — 14 names)

These are the names I would research on Day 2 first, in roughly this order:

1. **Aquapharm Chemicals Pvt Ltd** — water-treatment specialty chem, Pune-based, unlisted, MIDC Bhosari
2. **Deepak Novochem Technologies** — specialty chem (different entity from Deepak Nitrite), Pune-based
3. **Elkay Chemicals Pvt Ltd** — specialty chem, MIDC Bhosari
4. **Enzene Biosciences** — Chakan Phase II, biologics manufacturing — verify ownership status (was Alkem-linked at one point)
5. **Gennova Biopharmaceuticals** — Hinjawadi, mRNA capability — verify if Emcure subsidiary kills it
6. **Murli Krishna Pharma** — Ranjangaon MIDC, formulation manufacturer
7. **Rasayani Biologics** — Mhalunge-Mulshi, biologics
8. **Ross Lifescience Ltd** — Bhosari, listed (ROSSARI / ROSS — verify which entity)
9. **Hi Tech Bio-Sciences India** — Paud-Mulshi
10. **Rathi Dye Chem** — specialty dye/chem, Pune HQ, Roha plant
11. **Nova ChemDrugs** — MIDC Bhosari
12. **Canpex Chemicals** — Pune HQ, Beed plant — verify if Beed counts as Pune operational
13. **BVG Life Sciences** — Pune-based diversified
14. **Accurate Diagnostics** — diagnostic-side candidate

### Verify — likely too small or services-trap (~13 names)

These you research only if your promising-list under-yields. Most are <Rs.30Cr or research-services rather than manufacturing.

- Kan Biosys, Ajay Bio-Tech, Rise N' Shine Biotech, Greenvention Biotech, Manshya Enviro Biotech, Sarvoshadhi Biotech, Jay Research & Biotech, AbGenics LifeSciences, Ahammune Biosciences, Green Vision Life Sciences, Regrow Biosciences, Isera Biological, M.J. Biopharm, Serigen Mediproducts, PRADO Preclinical, Intox Pvt Ltd, Mansoon Seeds, Ulink Agritech, Venky's, Agio Pharmaceuticals

A separate note on the 5 names you found via SME-IPO and MSME databases (Sujalam, Speciality Medicines, B.D. Industries, Eisen Pharmaceuticals, Everest Pharma): these are *strong* additions because the SME-IPO filing itself is verifiable C6 (growth) evidence with a public DRHP. Add these to the Promising list. **B.D. Industries is polymer/plastics — verify if it fits the specialty-chem segment vs. is a commodity plastic processor.**

---

## CSV format — what each column means

The sample CSV has **28 columns**. Match them exactly, in this order. (Column order matters for the recruiter's eyeballing.)

| # | Column | Notes |
|---|--------|-------|
| 1 | Company Name | Full legal name |
| 2 | Website | Domain only, e.g. `aquapharm.com` |
| 3 | City | Pune (or operational presence statement if HQ elsewhere) |
| 4 | Segment | Use the brief's exact wording: *Custom synthesis & specialty chemicals* OR *Specialty diagnostics & life-science tools* |
| 5 | What They Make | Specific products. NOT "specialty chemicals" — say "phosphonate-based water treatment chemicals exported to >40 countries" |
| 6 | Revenue Band | Use the band tags from the brief: `<Rs.30Cr` / `Rs.30-100Cr` / `Rs.100-300Cr` / `Rs.300-500Cr` / `>Rs.500Cr` / `Unknown` |
| 7 | Decision Maker | Name |
| 8 | DM Title | Founder / MD / CEO etc. |
| 9 | DM Background | Education + prior employer in one line, with institution names |
| 10 | C1 Manufacturer Score | Strong / Moderate / Weak |
| 11 | C1 Evidence | One-line evidence with specific facility location |
| 12 | C2 India Score | Always Strong if Pune-operational |
| 13 | C2 Evidence | HQ location + specific manufacturing site address |
| 14 | C3 Differentiation Score | Strong / Moderate / Weak |
| 15 | C3 Evidence | Specific certifications + specific products + first/only claim |
| 16 | C4 Tech DM Score | Strong / Moderate / Weak |
| 17 | C4 Evidence | Specific institution + specific prior employer |
| 18 | C5 Tailwind Score | Strong / Moderate / Weak |
| 19 | C5 Evidence | Name the specific tailwind: PLI scheme code / China+1 / export markets |
| 20 | C6 Growth Score | Strong / Moderate / Weak |
| 21 | C6 Evidence | Dated growth event: "inaugurated Rs.X facility in [month year]" |
| 22 | Verdict | `Strong Pass` / `Pass` / `Borderline` |
| 23 | Verdict Reasoning | One paragraph: why Federer + any caveat |
| 24 | Personalization Hook | One sentence usable as line 1 of an email — must be specific, true, dated |
| 25 | Evidence Sources | Semi-colon-separated list of actual URLs/filings consulted |

(The original sample shows 25 distinct columns. Match exactly. If a sample column doesn't appear above, look at the sample row in the brief and add it.)

---

## Anti-hallucination protocol (the actual discipline)

Adopt these as hard rules — write them at the top of `prompts.md` and never break them:

**i.** Never let an LLM produce a revenue figure. Revenue comes only from BSE/NSE filings, MCA filings via Tofler/ZaubaCorp, the company's own annual report, or a press release with a specific FY number. If none of those have it, the band is "Unknown" — that is a valid answer.

**ii.** Never let an LLM produce a certification claim without you seeing the certifying body's database list it. USFDA → `fda.gov` Establishment Inspection Reports. WHO-GMP → WHO PQ list. DSIR → your DSIR extract. EU-GMP → EUDRA-GMDP database. AS9100 → IAQG OASIS database.

**iii.** Never let an LLM produce a founder credential without a LinkedIn profile *or* a primary source (university alumni page, company "About Us") confirming the institution name.

**iv.** Every cell in column "Evidence Sources" must be a URL you actually opened. If you didn't open it, it doesn't go in the CSV. Period.

**v.** When you cite a company website fact, copy the exact phrase into your `/scratch/` notes with the URL. If the brief says they verify, they will paste the phrase into Google and check.

**vi. Negative-prompting cheat sheet** for every prompt you write:
> *Do not invent revenue numbers. Do not infer founder education from name alone. Do not assume a company is a manufacturer because it is in a chemical-related industry — verify production facility. Do not classify a CRO as a manufacturer. Do not score a company as "differentiated" without naming the specific certification, year, and issuing body. If a fact is uncertain, say "Unknown" — do not guess.*

This block goes verbatim at the top of every Claude/Gemini prompt you use in the project.

---

## Methodology document — what to write

`methodology.md` should be 1500–2500 words structured as:

i. **City/segment selection.** Tell the story: considered Bengaluru biotech, ran a density check, found the universe heavily PE-controlled and CRO-dominated, pivoted. Considered Gujarat specialty chem, judged verification cost too high for 5-day timeline. Selected Pune Basket A two-segment. **This is the highest-ROI paragraph in the entire submission** — it shows judgment, not output.

ii. **Sourcing layers used.** DSIR R&D recognition list (~50 Pune entries), BSE SME / NSE Emerge for Maharashtra (~X entries), MIDC industrial directory for Pune district, USFDA Maharashtra extract, MSME-award and SME-IPO databases, LinkedIn for DM verification. State the count surfaced from each source.

iii. **Funnel arithmetic.** *Universe ~120 → pre-filter eliminated ~40 → investigated ~75 → 25 passes (33% yield, slightly above brief's 30% expectation).*

iv. **What an instructive fail looks like.** Pick 3 disqualified companies and explain why. Mirror the brief's Suven Pharma example exactly: "X looks like a Federer because [criterion], but fails because [specific PE/size/CRO/subsidiary issue]."

v. **AI discipline applied.** Show the negative-prompting block. Show one example prompt that worked and one that produced a hallucination you caught. The brief explicitly asks where you disagreed with AI — *this is where you answer that*.

vi. **Limitations.** Honest about what you couldn't verify (private companies' current-year revenue, ownership structure for PE-recent), and how you flagged those (Borderline verdict, "Unknown" revenue band).

vii. **What you learned about Pune Basket A.** One paragraph capturing the segment's actual texture — e.g. *"Pune specialty chem skews toward pharma/agrochem intermediates, with the densest cluster in MIDC Kurkumbh and Bhosari. Diagnostics is thinner — most Pune diagnostic plays are services or genomics-as-a-service rather than kit manufacturing."* This shows you actually *read* the data instead of running a script over it.

---

## Part B Question 1 — sourcing methods (~600 words)

Format: 8–12 numbered methods. For each: name + why ICP-fit + one limitation.

Suggested methods (you'll refine in writing):

1. **DSIR R&D recognition list** (`dsir.gov.in`) — every recognised in-house R&D unit. Strong filter for differentiated manufacturers. *Limitation: skews to formal/older companies; newer specialty plays not yet recognised.*
2. **BSE SME + NSE Emerge listings** — captures sub-Rs.500Cr listed companies with verifiable revenue/promoter-shareholding data. *Limitation: lists only companies that chose to IPO.*
3. **USFDA / EU-GMP / WHO-PQ facility databases** — proves regulatory-grade manufacturing. *Limitation: only relevant for pharma/biotech, not specialty chem broadly.*
4. **MCA filings via Tofler/ZaubaCorp** — verifies revenue band, paid-up capital, director list. *Limitation: free-tier limits; some private companies file delayed.*
5. **MIDC / GIDC / KIADB industrial directories** — captures the unlisted manufacturing universe by physical industrial cluster. *Limitation: out-of-date for newer admissions.*
6. **PLI scheme awardee lists** (chemicals, medical devices, electronics, white goods) — every awardee has a public-domain capacity-expansion plan. *Limitation: awardees skew to mid-large companies; misses sub-Rs.50Cr.*
7. **Industry-association member directories** — IDMA, CHEMEXCIL, IDA, AMTZ, ABLE-India. Self-curated by domain. *Limitation: pay-walled in some cases.*
8. **Trade-fair exhibitor lists** — CPHI India, India Chem, Medical Fair India, Bangalore India Bio. Companies that pay to exhibit are growth-mode by definition. *Limitation: archival lists are scattered.*
9. **Patent filings via `ipindia.gov.in`** — recent filings by sub-Rs.500Cr Indian-applicant manufacturers. *Limitation: high false-positive rate, requires manual filter.*
10. **LinkedIn Sales Navigator** — filter by company size + headquarters city + technical job-titles ("Process Chemist", "QA Manager"). The hiring activity itself is C6 evidence. *Limitation: licence cost.*
11. **NABL / CDSCO / AYUSH approval databases** — for diagnostics and pharma specifically. *Limitation: domain-specific.*
12. **Specialty B2B marketplaces** (IndiaMART verified-manufacturer tier, Mfg.com) — useful for cross-checking C1 manufacturer status. *Limitation: low signal-to-noise.*

---

## Part B Question 2 — 1000-company proposal structure

The sample proposal in the brief is your reference. Match its level of detail. Sections:

i. **Funnel.** Universe ~3500–4000 → pre-filter ~1500 → AI score ~1100 → QA → final 1000. Yield assumptions explicit at each stage.

ii. **Sources** (use Q1 list, weighted). For each, expected count + cost + access method.

iii. **Tooling.** Python + Playwright/Beautiful Soup for scraping → Anthropic API (Claude Haiku for first-pass scoring, Sonnet for borderline 40–48 score band) → manual QA on a 10% sample. Don't use Antigravity for this — it's not the right tool.

iv. **Cost.** Approximate token math. Be conservative — Rs.5,000–8,000 total in API costs with intentional caching.

v. **Week-by-week.** Week 1 sourcing + scraping. Week 2 first-pass AI scoring. Week 3 borderline re-scoring + QA. Week 4 final assembly + dedup + handover format.

vi. **Risk register.** 6–8 risks with mitigations: yield-rate miss, scraping blocks, AI hallucination, dedup failure, data freshness, regulatory-database update lag, false-positive on manufacturer-vs-trader, false-negative on companies without strong web presence.

vii. **Deliverable format.** What the final 1000-company file looks like — column structure, evidence-source rigour, refresh cadence, handover protocol to the SDR team.

---

## Hand-drawn diagram structure

A4 sheet, landscape orientation. Pen, not pencil. Black ballpoint preferred for photo contrast.

**Layout (rough):**

```
┌─────────────────────────────────────────────────────────────────┐
│   1000-COMPANY SOURCING PLAN — WEEK FUNNEL                       │
│                                                                  │
│   [Source 1]──┐                                                  │
│   [Source 2]──┤                                                  │
│   [Source 3]──┼──► UNIVERSE ──► PRE-FILTER ──► AI SCORE ──► QA  │
│   [Source 4]──┤    ~3500-4000     ~1500        ~1100      1000   │
│   [Source 5]──┤                                                  │
│   [Source 6]──┤                                                  │
│   [Source 7]──┘                                                  │
│                                                                  │
│   ── Week 1 ──── Week 2 ──── Week 3 ──── Week 4 ──              │
│   sourcing       scrape +    re-score +   final QA               │
│   + scrape       Haiku       Sonnet       + assembly             │
│                  scoring     borderline                          │
│                                                                  │
│   Tools: Python+Playwright | Claude Haiku | Sonnet | Tofler API  │
│                                                                  │
│   Quality gates: ▲ false-positive trap (CRO)                     │
│                  ▲ revenue-band drift (>500Cr)                   │
│                  ▲ ownership-trap (PE acquired)                  │
└─────────────────────────────────────────────────────────────────┘
```

**Things it must show:**
- Sources fanning into universe
- Funnel stages with rough numbers at each step
- Week-by-week timeline mapped under the funnel
- Tools written next to the relevant stage
- Quality gates / failure modes called out as warnings

The brief says explicitly: *"It doesn't need to be beautiful. It needs to show that you thought through the problem yourself."* Don't perfectionate. 15 minutes max.

---

## Final QA checklist (Day 5, before submission)

Run through each item, tick when done.

- [ ] Every revenue figure in the CSV has a source URL in the Evidence Sources column
- [ ] Every certification claim names the specific issuing body and (where possible) year
- [ ] Every founder credential names a specific institution (not "engineering background")
- [ ] No CRO / testing lab / pure services company sneaked into the 25
- [ ] No company has registered office in Pune but factory elsewhere — *unless* you've stated the operational-presence reasoning
- [ ] No company is over Rs.500Cr current-year revenue — re-checked the 5 closest-to-ceiling
- [ ] No company is PE-majority-owned — re-checked the 5 most-likely-acquired
- [ ] Methodology document tells the *judgment story*, not just lists what you did
- [ ] Q1 has 8+ methods, each with specific limitation
- [ ] Q2 proposal has explicit yield arithmetic, not vague language
- [ ] Hand-drawn diagram is photographed, legible, in good light
- [ ] GitHub repo is public (otherwise the recruiter cannot read it)
- [ ] README in the repo explains where each deliverable is

---

## What I'd actually do RIGHT NOW (next 30 minutes)

i. Create the GitHub repo skeleton — empty files for each deliverable, push to make it public.
ii. Drop the DSIR list and USFDA list into `/sources/`.
iii. Open the **promising 14** from the pre-triage above, and start a quick first-pass on the top 3 (Aquapharm, Deepak Novochem, Enzene Biosciences). Goal is one verified pass before the day ends — that one pass becomes your template/benchmark for all future entries.

The first verified pass-row is the most important single piece of work in the whole assignment. Once you have one row done well, the next 24 are pattern-replication. Don't move forward without it.

---

*Plan locked. Day 0 starts now.*
