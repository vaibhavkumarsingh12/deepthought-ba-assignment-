# Prompts & Guardrails

This file documents every prompt used during AI-assisted research, along with the guardrails applied to prevent hallucination or bias.

---

## General Guardrails

- All AI-generated company names were **independently verified** via official websites, MCA filings, or BSE/NSE listings before inclusion.
- No company was added to `companies.csv` solely on the basis of an AI suggestion.
- AI was used only for **filtering logic, query construction, and summarisation** — not as a primary data source.

---

## Prompts Used

### 1. Initial Sector Scoping

**Prompt:**
> "List sub-sectors within specialty chemicals and pharma intermediates that are most active in Maharashtra, India. Focus on export-oriented segments."

**Purpose:** Build the sector taxonomy for screening.
**Guardrail:** Output cross-checked against CHEMEXCIL and Pharmexcil export data.

---

### 2. DSIR List Filtering

**Prompt:**
> "From the following list of DSIR-recognised companies [paste], identify those in specialty chemicals or pharma APIs located in Maharashtra with fewer than 500 employees. Return company name, city, and reason for inclusion."

**Purpose:** Reduce DSIR extract to relevant candidates.
**Guardrail:** Employee counts verified via LinkedIn / MCA annual returns.

---

### 3. BSE SME Screening

**Prompt:**
> "From this BSE SME listing data [paste], filter for Maharashtra-based companies in chemicals or pharmaceuticals. Flag any with revenue between ₹10 Cr and ₹500 Cr."

**Purpose:** Identify listed SMEs within the revenue band.
**Guardrail:** Revenue figures verified against BSE annual report filings.

---

### 4. Disqualification Reasoning

**Prompt:**
> "Given these screening criteria [paste criteria], explain why each of the following companies [paste list] does not qualify. Be specific about which criterion fails."

**Purpose:** Generate structured disqualification notes for `research-log/disqualifications.md`.
**Guardrail:** Each disqualification reason reviewed and corrected manually before logging.

---

### 5. Contact Finding

**Prompt:**
> "For the company [Company Name], find the name and designation of the most relevant business development or export head. Use only publicly available information (LinkedIn, company website, press releases)."

**Purpose:** Populate the `key_contact` and `contact_designation` fields in `companies.csv`.
**Guardrail:** Contact details verified on LinkedIn and company website before recording.
