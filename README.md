# hbcu_patent_data_2025
# HBCU Patent Portfolio Analysis

A dataset and analysis of USPTO patent applications filed by Historically Black Colleges and Universities (HBCUs), covering 21 institutions from 2001–2025. This research was conducted by [Arrowpoint Labs](https://arrowpointlabs.com) to assess innovation output and commercialization potential across the HBCU ecosystem.

**This analysis was conducted on November 20, 2025.**

---

## Dataset Overview

| Metric | Value |
|--------|-------|
| Institutions covered | 21 |
| Total patent applications | 1,441 |
| Date range | 2001–2025 |
| Data source | USPTO Patent Center |
| Classification system | CPC (Cooperative Patent Classification) |

### Institutions Included

All R1, R2, and aspiring R2 HBCUs with documented research and PhD output:

| University | Patent Count | Earliest Filing | Latest Filing |
|------------|-------------|-----------------|---------------|
| Morehouse School of Medicine | 218 | 3/20/2003 | 3/18/2025 |
| Howard University | 196 | 10/31/2008 | 4/22/2025 |
| Florida A&M University | 119 | 9/7/2004 | 3/13/2025 |
| North Carolina A&T State University | 100 | 11/27/2002 | 4/25/2025 |
| Morgan State University | 94 | 10/11/2012 | 10/10/2024 |
| Xavier University of Louisiana | 64 | 1/21/2005 | 9/20/2024 |
| Meharry Medical College | 61 | 4/4/2002 | 4/21/2025 |
| Tuskegee University | 54 | 7/7/2011 | 1/23/2024 |
| North Carolina Central University | 38 | 2/10/2006 | 4/30/2025 |
| Hampton University | 32 | 6/21/2001 | 6/27/2022 |
| Clark Atlanta University | 26 | 5/3/2007 | 10/7/2024 |
| Jackson State University | 21 | 7/23/2001 | 2/4/2025 |
| Texas Southern University | 20 | 12/26/2007 | 4/18/2024 |
| Fayetteville State University | 17 | 12/10/2009 | 9/27/2022 |
| Delaware State University | 16 | 10/4/2007 | 12/16/2024 |
| University of the District of Columbia | 7 | 4/8/2022 | 10/27/2023 |
| Norfolk State University | 6 | 12/11/2006 | 8/7/2019 |
| University of Maryland Eastern Shore | 6 | 3/6/2013 | 10/15/2020 |
| Southern University and A&M College | 5 | 5/19/2016 | 2/6/2024 |
| Morehouse College | 3 | 5/18/2015 | 3/12/2021 |
| Bowie State University | 3 | 4/29/2002 | 12/15/2022 |

### Technology Areas

Patent activity is classified using CPC codes and mapped to the following technology areas:

| Technology Area | Patent Count | Share |
|----------------|-------------|-------|
| Medical Science/Healthcare | 362 | 25.1% |
| Organic Chemistry | 198 | 13.7% |
| Other Technologies | 176 | 12.2% |
| Biochemistry/Biotechnology | 148 | 10.3% |
| Measuring/Testing/Sensing | 146 | 10.1% |
| Agriculture/Food | 74 | 5.1% |
| Computing/Data Processing/AI | 59 | 4.1% |
| Polymers/Macromolecular Chemistry | 45 | 3.1% |
| Materials/Metallurgy | 41 | 2.8% |
| Separation/Mixing/Chemical Processes | 37 | 2.6% |
| Communications/Networks/Wireless | 36 | 2.5% |
| Electrical Engineering | 33 | 2.3% |
| Nanotechnology | 29 | 2.0% |
| Physics/Optics | 24 | 1.7% |
| Information/Communication Technology | 21 | 1.5% |
| Transportation Technology | 13 | 0.9% |
| Environmental Technology | 1 | 0.1% |

Health sciences dominate the portfolio, with Medical Science/Healthcare, Biochemistry/Biotechnology, and Organic Chemistry together accounting for nearly **50% of all patents**.

---

## Files

```
├── hbcu_patents_cleaned.json        # Full patent application records (1,441 records, JSONL format)
├── hbcu_applications.json           # Subset with enriched fields including abstracts and CPC classifications
├── patent_count_by_university.csv   # Patent counts per institution with date ranges
├── patents_by_year.csv              # Annual filing counts from 2001–2025
├── cpc_subclass.csv                 # Patent counts by technology area
└── README.md                        # This file
```

### `hbcu_patents_cleaned.json`

The primary dataset. Each line is a valid JSON object representing one patent application. Fields include:

| Field | Description |
|-------|-------------|
| `applicationNumberText` | USPTO application number |
| `applicationMetaData` | Filing date, status, inventor name, art unit, application type |
| `assignmentBag` | Assignee (institution) information |
| `pgpubDocumentMetaData` | Pre-grant publication metadata |
| `grantDocumentMetaData` | Grant metadata (where applicable) |
| `eventDataBag` | Prosecution history events |
| `parentContinuityBag` | Parent application references |
| `childContinuityBag` | Child application references |
| `correspondenceAddressBag` | Correspondence address |
| `filingDate` | Application filing date |
| `patentNumber` | Granted patent number (where applicable) |
| `lastIngestionDateTime` | Timestamp of data ingestion |

> **Note:** Two fields present in the raw USPTO export — `recordAttorney` (14.6 MB) and `patentTermAdjustmentData` (8.4 MB) — were removed from this file as they are not analytically relevant to portfolio analysis. All other fields are unchanged. Record count and field-level checksums were verified before and after removal.

### `hbcu_applications.json`

A curated subset of 296 records with enriched fields particularly useful for technology classification and natural language analysis:

| Field | Description |
|-------|-------------|
| `application_number` | USPTO application number |
| `invention_title` | Title of the invention |
| `abstract` | Full patent abstract |
| `cpc_classifications` | Structured CPC classification codes (section, class, subclass, group) |
| `ipc_classifications` | IPC classification codes |
| `inventors` | Inventor names |
| `assignees` | Assignee institution(s) |
| `University` | Normalized institution name |
| `filing_date` | Application filing date |
| `publication_number` / `publication_date` | Publication details |

---

## Key Findings

**Patent activity is real but highly concentrated.** The top 3 institutions — Morehouse School of Medicine, Howard University, and Florida A&M — account for a disproportionate share of total output. Many institutions file patents through individual researchers rather than through organized technology transfer offices, leading to significant undercounting in standard database queries.

**Naming conventions are a critical data quality issue.** USPTO records reflect how institutions register themselves at time of filing, which varies considerably. For example, "North Carolina Agricultural and Technical State University," "NC A&T State University," and "North Carolina A&T" all appear as distinct assignees in the raw data. Systematic resolution of these variations was essential to arriving at accurate counts — initial queries captured as few as 8 patents for institutions that had filed substantially more.

**Growth trend is significant.** Annual filings grew from single digits in the early 2000s to a peak of 93 in 2019, with sustained activity through 2024. The apparent decline after 2021 partly reflects USPTO's ~18-month publication lag rather than a true drop in activity.

**Health sciences and chemistry dominate.** The concentration in Medical Science, Biochemistry, and Organic Chemistry reflects the outsized role of medical schools (Morehouse School of Medicine, Meharry Medical College, Howard) and STEM-focused institutions in the R2 category.

---

## Data Notes & Limitations

- **Publication lag:** USPTO typically publishes applications 18 months after filing. Patent counts for 2023–2025 are therefore understated and will grow as more applications are published.
- **Assignee name variations:** Counts reflect best-effort normalization of institutional name variants. Some patents filed by HBCU-affiliated researchers under personal names or corporate spinout entities may not be captured.
- **Coverage gaps:** Some institutions may have patents filed under subsidiary entities, research consortia, or joint arrangements with other universities that are not captured here.
- **Classification mapping:** CPC-to-technology-area mapping uses subclass-level codes. A single patent may have multiple CPC classifications and therefore appear in more than one technology area.

---

## Contact

**Arrowpoint Labs**
For questions about the dataset or the broader platform, reach out via [arrowpointlabs.com](https://arrowpointlabs.com).
