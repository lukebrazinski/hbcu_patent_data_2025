# hbcu_patent_data_2025
# HBCU Patent Portfolio Analysis

A dataset and analysis of USPTO patent applications filed by Historically Black Colleges and Universities (HBCUs), covering 21 institutions from 2001–2025. This research was conducted by [Arrowpoint Labs](https://arrowpointlabs.com) to assess innovation output and commercialization potential across the HBCU ecosystem.

**This analysis was conducted on November 20, 2025.**

---

## Dataset Overview

| Metric | Value |
|--------|-------|
| Institutions covered | 21 |
| Total patent applications | 1,106 |
| Date range | 2001–2025 |
| Data source | USPTO Patent Center |
| Classification system | CPC (Cooperative Patent Classification) |

### Institutions Included

R1, R2, and aspiring R2 HBCUs with documented research and PhD output:

| University | R1/R2/Emerging | Patent Count | Earliest Filing | Latest Filing |
|------------|---------------|-------------|-----------------|---------------|
| Morehouse School of Medicine | Medical | 218 | 3/20/2003 | 3/18/2025 |
| Howard University | R1 | 196 | 10/31/2008 | 4/22/2025 |
| Florida A&M University | R2 | 119 | 9/7/2004 | 3/13/2025 |
| North Carolina A&T State University | R2 | 100 | 11/27/2002 | 4/25/2025 |
| Morgan State University | R2 | 94 | 10/11/2012 | 10/10/2024 |
| Xavier University of Louisiana | Emerging | 64 | 1/21/2005 | 9/20/2024 |
| Meharry Medical College | Medical | 61 | 4/4/2002 | 4/21/2025 |
| Tuskegee University | Emerging | 54 | 7/7/2011 | 1/23/2024 |
| North Carolina Central University | Emerging | 38 | 2/10/2006 | 4/30/2025 |
| Hampton University | R2 | 32 | 6/21/2001 | 6/27/2022 |
| Clark Atlanta University | R2 | 26 | 5/3/2007 | 10/7/2024 |
| Jackson State University | R2 | 21 | 7/23/2001 | 2/4/2025 |
| Texas Southern University | R2 | 20 | 12/26/2007 | 4/18/2024 |
| Fayetteville State University | Emerging | 17 | 12/10/2009 | 9/27/2022 |
| Delaware State University | R2 | 16 | 10/4/2007 | 12/16/2024 |
| University of the District of Columbia | Emerging | 7 | 4/8/2022 | 10/27/2023 |
| Norfolk State University | Emerging | 6 | 12/11/2006 | 8/7/2019 |
| University of Maryland Eastern Shore | Emerging | 6 | 3/6/2013 | 10/15/2020 |
| Southern University and A&M College | R2 | 5 | 5/19/2016 | 2/6/2024 |
| Morehouse College | Emerging | 3 | 5/18/2015 | 3/12/2021 |
| Bowie State University | Emerging | 3 | 4/29/2002 | 12/15/2022 |

*R1 = Carnegie R1 research university. R2 = Carnegie R2 research university. Emerging = institutions with documented R&D expenditure and PhD output working toward R2 classification. Medical = specialized medical schools included for their research output.*

### Technology Areas

Patent activity is classified using CPC codes and mapped to the following technology areas:

| Technology Area | Patent Count | Share |
|----------------|-------------|-------|
| Medical Science/Healthcare | 371 | 33.5% |
| Unclassified (PCT/Provisional) | 345 | 31.2% |
| Organic Chemistry | 198 | 17.9% |
| Biochemistry/Biotechnology | 148 | 13.4% |
| Measuring/Testing/Sensing | 148 | 13.4% |
| Other Technologies | 126 | 11.4% |
| Agriculture/Food | 74 | 6.7% |
| Computing/Data Processing/AI | 59 | 5.3% |
| Polymers/Macromolecular Chemistry | 45 | 4.1% |
| Separation/Mixing/Chemical Processes | 37 | 3.3% |
| Materials/Metallurgy | 37 | 3.3% |
| Communications/Networks/Wireless | 36 | 3.3% |
| Electrical Engineering | 33 | 3.0% |
| Nanotechnology | 29 | 2.6% |
| Transportation Technology | 14 | 1.3% |
| Information/Communication Technology | 12 | 1.1% |
| Physics/Optics | 4 | 0.4% |

*Percentages are out of 1,106 distinct patents and sum to more than 100% because patents can be classified under multiple technology areas.*
Health sciences dominate the portfolio, with Medical Science/Healthcare, Biochemistry/Biotechnology, and Organic Chemistry together accounting for **65% of classified patents**.

#### About "Unclassified (PCT/Provisional)"

A separate category of **345 records (31% of the dataset)** falls into "Unclassified (PCT/Provisional)" because they lack CPC classification codes in the USPTO export. This is a known limitation of patent data, not a gap in the underlying research:

- **Provisional applications** are placeholder filings used to establish a priority date. They are not examined by the USPTO and therefore never receive CPC classifications.
- **PCT (international) applications** receive IPC classifications from WIPO rather than CPC codes from the USPTO, so they appear without CPC data in this export.

These records still represent real research output — Howard University, for example, has 90 unclassified records covering coronavirus diagnostics, drug delivery systems, and encryption technologies. They are simply not classifiable through the CPC subclass mapping used here. Future iterations of this dataset may incorporate IPC-to-technology-area mapping to recover this information for PCT filings.

The proportion of unclassified records varies significantly by institution, ranging from 0% (UDC, Southern University, Bowie State) to 67% (Norfolk State). Institutions with active medical schools or international research collaborations tend to have higher PCT filing rates and therefore higher unclassified counts.

#### What's in "Other Technologies"?

After separating out PCT/Provisional records, the **Other Technologies** category contains patents that have CPC codes but fall outside the 16 named technology buckets. Rather than a single coherent field, it represents genuine breadth across the HBCU research portfolio. The major clusters within it are:

**Energy & Combustion** — The largest single cluster, driven primarily by Morgan State University's sustained work in biomass combustion and biofuel systems (CPC codes F23G, F23C, C10L, C10G), alongside wind energy research (F03D, F05B) from Bowie State University.

**Automation & Control Systems** — Patents covering process control, smart grid automation, and autonomous systems (G05D, G05B, G05F), with notable contributions from Florida A&M (AI valet systems) and Howard University (smart/micro grid testbed platforms).

**Specialty Fluids & Lubricants** — Howard University's research into nanofluids and organogels as lubricant media (C10M), reflecting materials science work at the intersection of chemistry and mechanical engineering.

**Refrigeration & Thermal Systems** — Morgan State's work on mobile shellfish cooling systems (F25D, F25B), part of a broader aquaculture and food systems research thread.

**Advanced Manufacturing & Coatings** — Additive manufacturing / 3D printing research (B33Y) from Florida A&M, high-performance coating processes (B05D, B05B) from Tuskegee, and mechanical transmission systems (F16H) also from Tuskegee.

**Aerospace & Propulsion** — A small but notable cluster at Tuskegee (F02K, B05B) covering jet propulsion injection systems.

**Rare Earth & Magnetic Separation** — Florida A&M's work on magnetic-based separation of rare earth metals (B03C).

**Other Miscellaneous** — Includes cleaning systems (B08B), specialty dyes and luminescent materials (C09K, C09B), fiber manufacturing (D01F), waste handling (B65F), safety tracking systems (G08B), and a small number of cross-reference legacy codes (Y10T, Y10S) used by USPTO for older patent classifications.

---

## Files

```
├── hbcu_patents.json                # Full patent application records (1,106 records, JSONL format)
├── patent_count_by_university.csv   # Patent counts per institution with date ranges
├── patents_by_year.csv              # Annual filing counts from 2001–2025
├── cpc_subclass.csv                 # Patent counts by technology area
└── README.md                        # This file
```

### `hbcu_patents.json`

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
