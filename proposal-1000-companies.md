# Proposal: Scaling to 1,000 Companies

## Part B – Question 2

### Problem Statement

Design a repeatable, scalable research process to identify and profile 1,000 export-oriented SMEs across India's specialty chemicals and pharma-intermediates sector.

---

## 1. Why This Is Hard at Scale

| Challenge | Impact |
|---|---|
| No single authoritative directory covers all SMEs | Requires multi-source aggregation |
| Company data (employees, revenue, exports) is often stale or missing | Increases manual verification burden |
| Contact data degrades quickly (turnover, role changes) | Reduces outreach conversion |
| Sector definitions vary across databases | Causes duplicates and misclassification |

---

## 2. Proposed Architecture

### Phase 1 – Data Aggregation (Automated)

- **Sources to ingest**: DSIR, BSE/NSE SME listings, USFDA Drug Establishment Register, APEDA, CHEMEXCIL member list, MIDC/GIDC/KIADB industrial directories, MCA21 CIN filings, Zauba import-export data
- **Method**: Write scraping scripts or use structured API pulls where available; store raw data in a central CSV/database
- **Output**: ~5,000–8,000 raw company records

### Phase 2 – Automated Filtering

Apply rule-based filters programmatically:
- State/city from registered address
- NIC code mapping to target sectors (NIC 20xx, 21xx)
- Revenue band from MCA annual returns (where available)
- Export flag from USFDA registration or Zauba trade data

**Output**: ~2,000–3,000 candidates passing automated filters

### Phase 3 – Enrichment (Semi-Automated)

- Use LinkedIn Sales Navigator or Apollo.io to bulk-enrich with employee count, contact names, designations
- Use Dun & Bradstreet or Tracxn for revenue validation
- AI-assisted summarisation of company websites for export market confirmation

**Output**: ~1,500 enriched records with confidence scores

### Phase 4 – Human QA & Final Selection

- Analyst review of borderline cases (score near threshold)
- Remove subsidiaries of large groups (check parent company via MCA)
- Spot-check 10% of records for accuracy
- Final curation to 1,000 records

---

## 3. Tooling Stack

| Step | Tool |
|---|---|
| Scraping / ingestion | Python (BeautifulSoup, Selenium), Google Sheets API |
| Data storage | Airtable or PostgreSQL |
| Enrichment | LinkedIn Sales Navigator, Apollo.io |
| AI filtering/summarisation | GPT-4 API with structured prompts |
| QA tracking | Airtable views with flagging workflow |

---

## 4. Team & Timeline

| Role | Responsibility | Est. Effort |
|---|---|---|
| Data Engineer | Build ingestion and filter pipeline | 2 weeks |
| Research Analyst ×2 | Manual QA, enrichment review | 3 weeks |
| BA Lead | Criteria definition, final sign-off | Ongoing |

**Total estimated timeline**: 6–8 weeks for first run; 2–3 weeks for subsequent quarterly refreshes.

---

## 5. Quality Metrics

- **Coverage**: % of known target companies captured (benchmark against CHEMEXCIL export awards list)
- **Accuracy**: % of records with correct employee band (validated via spot-check)
- **Contact reachability**: % of contacts with valid email / LinkedIn (measured at outreach stage)

---

## 6. Key Risks & Mitigations

| Risk | Mitigation |
|---|---|
| Source data goes stale | Schedule quarterly refresh; timestamp all pulls |
| AI hallucination in enrichment | Human review gate before final export |
| LinkedIn scraping ToS | Use official Sales Navigator API or manual export |
