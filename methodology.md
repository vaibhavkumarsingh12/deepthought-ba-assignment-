# Methodology

## Objective

Identify 25 companies in Maharashtra (focus: Pune / Mumbai) operating in the specialty chemicals or pharma-intermediates space, with 50–500 employees, actively exporting, and not yet well-covered by analyst reports.

---

## Sources Used

| Source | Type | Why Used |
|---|---|---|
| DSIR (Dept. of Scientific & Industrial Research) | Government directory | Lists R&D-recognised chemical/pharma firms |
| BSE SME Platform | Public listing data | SME-listed Maharashtra companies with financials |
| USFDA Drug Establishment Registration | Regulatory database | Maharashtra pharma exporters with US approval |
| MIDC (Maharashtra Industrial Development Corporation) | Industrial directory | Pune/Aurangabad chemical cluster firms |

---

## Screening Criteria

1. **Geography**: Registered or primary operations in Maharashtra (Pune, Mumbai, Aurangabad, Nagpur belt preferred)
2. **Sector**: Specialty chemicals, fine chemicals, pharma APIs/intermediates, agrochemicals
3. **Size**: 50–500 employees (or ₹10 Cr – ₹500 Cr revenue as proxy)
4. **Export activity**: Evidence of export (USFDA registration, export awards, foreign client mentions)
5. **Research gap**: Not covered by major sell-side equity research or widely profiled in media

---

## Research Process

1. Pulled raw lists from each source (see `sources/`)
2. Applied geography + sector filter to reduce to ~150 candidates
3. Manual web/LinkedIn check to verify employee count and export activity
4. Removed companies failing any hard criterion (logged in `research-log/`)
5. Final 25 selected based on research gap + data availability for outreach

---

## Key Learnings

- MIDC directory is the richest source for mid-size chemical manufacturers but has stale contact data
- BSE SME filings give reliable revenue/employee data but many listed firms are too large (>500 employees)
- USFDA registration is the best proxy for export orientation in pharma
- Several promising DSIR-listed firms turned out to be subsidiaries of large groups and were disqualified
