# Day 1 Task — First Verified Pass-Row

**Goal of today:** Produce ONE complete, fully-verified pass-row in `companies.csv` for the company **Aquapharm Chemicals Pvt. Ltd.**

**Time budget:** 90 minutes
**Why this company first:** It is on your DSIR Promising-14 list, MIDC Bhosari address (operationally Pune), specialty water-treatment chemicals (clear Basket A fit), unlisted (proves you can verify private companies — the harder case), and has a defensible C3 angle (phosphonate chemistry is a niche specialty). If you can produce a strong pass-row for Aquapharm, you can produce one for any of the remaining 24.

---

## The discipline you are practising today

The first pass-row is a workflow rehearsal, not just a research task. You are testing whether your verification pipeline can produce a defensible row in a defensible time-budget. By the end of today you should know:
- How long ONE company actually takes you (so you can plan Days 2–3 accurately)
- Which sources reliably yield each piece of evidence
- Which fields are easy to populate vs. hard
- Where AI helps vs. where AI hallucinates and you have to override it

**Document everything in `/scratch/aquapharm-research-notes.md` as you go.** This becomes raw material for your `methodology.md` and `prompts.md` documents later.

---

## The 7-step research pipeline (run in this exact order)

The order matters. Each step is designed to fail-fast — if a step shows the company is a disqualify, you stop and log the fail before wasting time on later steps. For Aquapharm I expect every step to pass, but you should still run them all so the discipline is built into your workflow before you face borderline cases.

### Step 1 — Website screening (5 min)

Open `aquapharm.com` (or whatever the actual URL is — verify, don't assume).

**Check three things:**

i. **Is it a manufacturer or services?** Look for explicit "manufacturing facility" / "production capacity" / specific product list with chemistry. NOT "we provide solutions" / "consulting" / "services." Aquapharm should pass clearly — they manufacture phosphonates and water-treatment chemicals.

ii. **Is the website fresh?** Footer copyright 2024–2026? Recent news/press section with posts in last 12 months? Stale = auto-disqualify.

iii. **What city is operationally primary?** Registered office, R&D, manufacturing — note all three. The brief's "operational presence, not registered office" rule means you need to confirm Pune is where the actual work happens.

**Log in scratch:**
- Website URL (verified, not assumed)
- One sentence on what they make (specific products, not category)
- Manufacturing facility addresses (all locations)
- Website-freshness flag (yes/no)

### Step 2 — MCA / Tofler revenue + ownership lookup (10 min)

Go to `tofler.in` → search "Aquapharm Chemicals." (Backup: `zaubacorp.com`)

**Three things you need:**

i. **Revenue band, last 3 FYs.** This determines C5/C6 evidence and whether the company is in the Rs.50–500Cr range. If revenue is Rs.300–500Cr, flag this as "watch-band" — fast-growing companies can jump above Rs.500Cr in one year.

ii. **Director list with appointment dates.** Look for: founder/family on board, no PE-fund-name director appointments in the last 3 years. PE appointments look like "Aditya Singh - Multiples Alternate Asset Management" or "Director nominee - X Capital." If you see those, this company is PE-controlled → auto-disqualify.

iii. **Paid-up capital + incorporation year.** Helps triangulate scale and stage.

**Log in scratch:**
- FY23 revenue, FY24 revenue, FY25 revenue (with currency unit)
- Director list with names + dates appointed
- PE/VC presence: yes/no
- Source URL: the exact Tofler/Zauba page (this goes in CSV column "Evidence Sources")

**⚠️ Common AI hallucination trap:** If you ask Claude or Gemini "what is Aquapharm Chemicals revenue?" they will produce a number. **Do not trust it.** Use the number on the Tofler page only. If Tofler shows "FY24 Rs.420Cr" — that's the number. If Claude later says "Rs.380Cr" — Claude is wrong, even if it sounds confident.

### Step 3 — Decision-maker background (15 min)

Go to LinkedIn. Search "Aquapharm Chemicals" → find the company page → identify the founder/MD.

**You need three things:**

i. **Name + title + photo verification.** Make sure you have the *actual* founder/MD, not a sales person.

ii. **Education.** Specific institution name (IIT Bombay? Pune University? UDCT? IISc?). Year if available.

iii. **Prior employer.** Where did they work before founding/leading this company? Pharma/chem company? Lab? Multinational?

**The C4 evidence line should look like:** *"Anil Verma (founder & MD) — UDCT/ICT Mumbai chemical engineering, ex-Hindustan Lever process chemist, founded company in 1994."*

**It should NOT look like:** *"Founder has chemistry background"* — that's an AI-grade non-statement. The brief explicitly says *"specific institution + specific prior employer."*

**Log in scratch:** DM name, title, education with institution, prior employer, LinkedIn URL.

### Step 4 — Differentiation / C3 evidence (15 min)

This is the criterion most candidates fake. You will not.

**Look for:**

i. **Specific product specialization.** "Phosphonate-based scale inhibitors" not "specialty chemicals." "Reverse osmosis antiscalants" not "water treatment products."

ii. **Specific certifications.** USFDA / EU-GMP / WHO-GMP / DSIR / ISO 9001 / NSF / Halal / Kosher. *Name the certificate, the year, the issuing body.*

iii. **Verifiable credentials in primary databases:**
   - DSIR — already verified for Aquapharm (TU/IV-RD/1059, valid till 31-03-2026)
   - USFDA — search `fda.gov` Establishment Inspection Reports (less likely for Aquapharm — they're chemicals not pharma)
   - Patents — `ipindia.gov.in` patent search
   - Export listings — directorate of trade or company's own export-market page

iv. **"First / only / pioneer" claims.** From their own website OR press releases. If they claim "India's first manufacturer of XYZ" — note it but verify against at least one independent source before citing.

**The C3 evidence line should look like:** *"DSIR-recognized in-house R&D unit (TU/IV-RD/1059, valid till March 2026). Manufactures specialty phosphonate scale inhibitors and reverse-osmosis antiscalants — exports to >40 countries per company website. ISO 9001:2015 certified. Niche product portfolio in water-treatment specialty chemistry."*

**Log in scratch:** Each certification with body + year, each product specialization, each pioneer/first claim with source.

### Step 5 — Sector tailwind / C5 evidence (5 min)

This one is largely pre-determined by your segment choice but tailor the wording per company.

**For specialty chemicals: pick one or two from these tailwinds:**
- China+1 supply chain shift (specifically chemicals)
- PLI Scheme for Bulk Drugs and Specialty Chemicals
- Indian export growth in specialty chemicals (~9.5% YoY per IBEF)
- Make-in-India for specialty manufacturing
- Water-treatment market growth (specifically for Aquapharm) — Indian water treatment chemicals market projected to grow Rs.X by Y year

**The C5 evidence line should look like:** *"Specialty water-treatment chemicals beneficiary of China+1 supply chain shift; Indian specialty chemicals exports growing ~9.5% YoY (IBEF data). Domestic municipal and industrial water-treatment demand expanding."*

**Log in scratch:** which tailwind, what specific evidence (statistic + source).

### Step 6 — Growth signals / C6 evidence (15 min)

This is the most-faked criterion in weak submissions, and the easiest to verify well.

**Where to look (in order):**

i. **Company news / press section** on their own website. Filter for posts dated in the last 18 months. Look for: new facility, capacity expansion, new certification, new product launch, awards.

ii. **LinkedIn company page → Posts.** Recent posts about hiring, expansion, certifications.

iii. **Naukri / LinkedIn Jobs.** Search the company name. Multiple open technical roles = active hiring = growth signal. Note count and types of roles.

iv. **Google News.** Search `"Aquapharm Chemicals" 2024 OR 2025`. Filter for last 24 months.

v. **MCA filings if they raised capital.** Search Tofler for any equity-issuance events in last 24 months.

**The C6 evidence line should look like:** *"Hiring 12+ technical roles on LinkedIn/Naukri (Process Chemist, QA Manager, Production Engineer) as of [today's date]. Inaugurated additional capacity at MIDC Bhosari in [month/year if confirmed]. Active in Indian Chemical Council member events 2024–2025."*

**It should NOT look like:** *"Company appears to be growing."* If you don't have a dated, specific event — write *Moderate* or *Weak* on C6 score and explain in the verdict reasoning.

**Log in scratch:** each growth event with date, source URL.

### Step 7 — Personalization hook (5 min)

This is the one-liner that goes in the last column. The brief explicitly says it must be usable as line 1 of an email.

**Pick the SINGLE most specific, recent, true fact about this company.** Not the most flattering — the most *specific*.

**Good hook examples:**
- *"Inaugurated a new fermentation line at MIDC Chakan in March 2025 — capacity for high-purity probiotic strains."*
- *"DSIR-recognized R&D unit pioneering phosphonate chemistry for boiler water-treatment in India."*
- *"One of India's few specialty-chemical manufacturers exporting RO antiscalants to >40 countries."*

**Bad hook examples (do not write these):**
- *"You're a leading specialty chemicals company in India."* (Generic, applies to 500 others)
- *"You have a strong R&D focus."* (Asserts without evidence)
- *"Congratulations on your growth."* (Reveals nothing — sounds like a bot)

**Log in scratch:** The chosen hook + why you chose it over alternatives.

---

## Now write the CSV row

Once steps 1–7 are done, you have everything you need. Open `companies.csv` and add the row. Match the 28-column format from the sample CSV in the brief exactly — column order, capitalization, spacing.

**Suggested row for Aquapharm (sample — verify each cell yourself, do not copy blind):**

| Column | Suggested value |
|---|---|
| Company Name | Aquapharm Chemicals Pvt. Ltd. |
| Website | aquapharm.com |
| City | Pune |
| Segment | Custom synthesis & specialty chemicals |
| What They Make | Specialty phosphonate scale inhibitors, RO antiscalants, corrosion inhibitors, biocides for industrial water treatment |
| Revenue Band | [verify on Tofler — likely Rs.300-500Cr] |
| Decision Maker | [verify on LinkedIn] |
| DM Title | Founder / MD / CEO |
| DM Background | [Institution + prior employer — from LinkedIn] |
| C1 Manufacturer Score | Strong |
| C1 Evidence | In-house specialty-chemicals manufacturing facility at MIDC Bhosari, Pune. Multiple plant locations. Not a trader/services company — owns process IP and produces finished phosphonate molecules. |
| C2 India Score | Strong |
| C2 Evidence | Pune HQ (Sadhu Vaswani Road); manufacturing at MIDC Bhosari, Pune. |
| C3 Differentiation Score | Strong |
| C3 Evidence | DSIR-recognized in-house R&D unit (TU/IV-RD/1059, valid till March 2026). Specialty phosphonate chemistry — narrow technical niche. Exports to 40+ countries per company website. ISO certifications. |
| C4 Tech DM Score | [Strong/Moderate/Weak based on what you find] |
| C4 Evidence | [Specific institution + prior employer] |
| C5 Tailwind Score | Strong |
| C5 Evidence | Specialty water-treatment chemicals beneficiary of China+1; Indian specialty chemicals exports growing ~9.5% YoY (IBEF). Industrial water-treatment market expansion. |
| C6 Growth Score | [Strong/Moderate based on hiring + facility data] |
| C6 Evidence | [Dated specific events] |
| Verdict | [Strong Pass / Pass / Borderline] |
| Verdict Reasoning | [One paragraph: why Federer + caveats] |
| Personalization Hook | [Your chosen one-liner] |
| Evidence Sources | aquapharm.com; tofler.in/aquapharm-chemicals-pvt-ltd; LinkedIn company page; DSIR R&D Recognition List (TU/IV-RD/1059); [specific URLs you opened] |

---

## Self-check before declaring this row done

Before moving to company #2, run this checklist on the Aquapharm row:

- [ ] Every score has a specific, factual evidence line — no vague language ("appears to be", "seems strong")
- [ ] Revenue band came from Tofler/MCA, not from any LLM
- [ ] DM credentials cite a specific institution name, not "engineering background"
- [ ] C3 evidence names at least one specific certification with the issuing body
- [ ] C6 evidence has at least one *dated* event (month/year)
- [ ] Personalization hook is specific enough that it could not apply to 50 other specialty chem companies
- [ ] Evidence Sources column has actual URLs of pages you opened — not "Google search"
- [ ] You spent ≤ 90 minutes on this row

If any item fails, fix it before moving on. The discipline you bake in here propagates to all 24 remaining companies.

---

## Common failure modes to avoid (these will sink your submission)

i. **Trusting AI-generated revenue figures.** If Claude says "Aquapharm revenue is ~Rs.350Cr" — Claude is guessing from training data that may be 2 years stale. Always cross-check Tofler.

ii. **Misclassifying ownership.** If a director list shows "Aditya Birla Capital" or "Multiples Alternate Asset Management" or any fund-name nominee, the company is institutionally controlled and fails the Federer test. Aquapharm should be founder-driven but verify.

iii. **Confusing the company with similar-named entities.** "Aquapharm" is a common business name. Aquapharm Chemicals Pvt Ltd ≠ Aquapharm International ≠ Aquapharm Industries. Always verify CIN (Corporate Identification Number) on Tofler matches the company you intend.

iv. **Counting the registered office as "operational presence."** The brief is explicit: registered office is not enough. If Aquapharm's primary R&D and manufacturing are at MIDC Bhosari (Pune) and registered office is elsewhere — Pune still counts. But document this in the C2 Evidence line.

v. **Padding C5 (tailwind) with generic claims.** "Indian specialty chemicals industry growing" — every Indian specialty chemical company is in this tailwind. The recruiter will ignore this. Be specific: "China+1 specifically benefits phosphonate manufacturers because [supply chain reason]."

---

## What to do after Aquapharm is done

When you have a satisfactory Aquapharm row in `companies.csv`:

i. Reflect for 10 minutes — what part of the workflow took longest? What part was easy? Did you find any source that should be added to your sourcing layer (e.g., a new directory, new database)?

ii. Update `methodology.md` with one paragraph in the "AI discipline applied" section: name one place where you caught an AI hallucination during this research, and how the verification process caught it. (If you didn't catch any, fabricate the *test* — ask Claude to estimate Aquapharm revenue, then compare to Tofler. The discrepancy is itself the methodology evidence.)

iii. Tell me when done. We move to companies 2–4 next, in parallel-track style — three companies per session — using the same workflow but compressed to 30–40 minutes per company once the pattern is internalized.

---

*Day 1 task locked. The next 90 minutes determine the quality of the whole submission.*
