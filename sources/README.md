# Sources Directory

This folder contains raw data extracts from each primary research source.

| File | Source | Description | Date Accessed |
|---|---|---|---|
| `dsir-pune-extract.csv` | Dept. of Scientific & Industrial Research (DSIR), Govt. of India | List of DSIR-recognised R&D companies in Pune / Maharashtra in the chemicals & pharma sectors | *(fill in)* |
| `bse-sme-maharashtra.csv` | BSE SME Platform (Bombay Stock Exchange) | SME-listed companies headquartered in Maharashtra; filtered for chemicals and pharma sectors | *(fill in)* |
| `usfda-maharashtra-extract.md` | U.S. FDA Drug Establishment Registration database | Maharashtra-based pharma manufacturers with active USFDA registrations (proxy for export orientation) | *(fill in)* |
| `midc-pune-chem-list.csv` | MIDC (Maharashtra Industrial Development Corporation) online directory | Chemical and pharma companies registered in MIDC industrial areas in Pune and surrounding districts | *(fill in)* |

## How to Reproduce Each Pull

### DSIR
1. Visit https://www.dsir.gov.in/siro-list
2. Filter by State: Maharashtra and Technology Area: Chemicals / Pharmaceuticals
3. Export or manually copy the listing

### BSE SME
1. Visit https://www.bseindia.com/markets/equity/EQReports/SMECorpInfo.html
2. Filter by state (Maharashtra) and industry group
3. Download the CSV

### USFDA
1. Visit https://www.accessdata.fda.gov/scripts/cder/drls/
2. Search by Country: India, filter results for Maharashtra addresses
3. Export listing

### MIDC
1. Visit https://www.midcindia.org/industry-directory
2. Filter by District: Pune / Aurangabad and Category: Chemicals
3. Export or scrape directory listing
