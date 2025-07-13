
# Methods

This research used a Systematic Literature Review approach inspired by Kitchenham et al., with the process steps outlined in Figure 1. Also, the steps related to the selection of papers are documented in the PRISMA diagram (Preferred Reporting Items for Systematic Reviews and Meta-Analyses) shown in Figure 2.

![Systematic Literature Review Process Steps][https://github.com/erfan-el/SLRO/blob/main/Research%20Method/PRISMA%20Model.png](https://github.com/erfan-el/SLRO/blob/main/Research%20Method/PRISMA%20Model.png)

We conducted an automated search on four databases: Scopus, Web of Science, IEEE Xplore, and ACM Digital Library. As shown in Table 1, the search keywords can be categorized as either related to PM or DM. In the queries, the `*` symbol is used to substitute multiple characters within a word. Proximity operators such as `W/2` and `NEAR/2` yield results when two words or phrases appear within two words of each other. The operator `EXCLUDE(DOCTYPE, 'cr')` is used in Scopus to filter out articles classified as Conference Reviews. Table 2 shows the search queries per database, together with the number of results and search dates. The queries were customized according to each database's search capabilities. We further conducted a limited manual search to incorporate relevant articles that were not found in the database search; we discuss this in the Inclusion Criteria section.

![PRISMA diagram describing the selection of primary studies](https://github.com/erfan-el/SLRO/blob/main/Research%20Method/PRISMA%20Model.png)

### Table 1. Keywords and synonyms used in the automated search

| ID | Concept         | Synonyms                   | Query terms                                                                                      |
|----|-----------------|----------------------------|--------------------------------------------------------------------------------------------------|
| 1  | Decision Mining | Decision Mining, Decision Extraction, Decision Extracting, Decision Discovery, Decision Discovering, Decision Retrieval, Decision Retrieving, Business Rule Mining, Business Rule Extraction, Business Rule Discovery, Business Rule Discovering, Business Rule Retrieval | (decision* OR “business rule*”) W/2 (mining OR extracti* OR discover* OR retriev*) |
| 2  | Process Mining  | Process Mining, Process Discovery | “process mining” OR “process discovery” |

### Table 2. The search queries of the automated search process

| ID | Search query | Database | Result | Search Date |
|----|--------------|----------|--------|-------------|
| 1 | `TITLE-ABS-KEY ((“process mining” OR “process discovery”) AND ((decision* OR “business rule*”) W/2 (mining OR extracti* OR discover* OR retriev*))) AND (EXCLUDE (DOCTYPE , “cr”))` | Scopus | 91 | 2024-05-23 |
| 2 | `TS=((“process mining” OR “process discovery”) AND ((decision* OR “business rule*”) NEAR/2 (mining OR extracti* OR discover* OR retriev*)))` | Web of Science | 52 | 2024-05-25 |
| 3 | Complex NEAR/2 queries for metadata fields in IEEE Xplore | IEEE Xplore | 68 | 2024-06-04 |
| 4 | `AllField:("process mining" AND ("decision mining" OR "decision discovery" OR "business rule"))` | ACM | 32 | 2024-06-05 |

## Exclusion and Inclusion Criteria

### Exclusion Criteria

Articles meeting the following criteria were excluded from the systematic review:

1. **Publication Venue and Timeframe**: Articles not published in international peer-reviewed journals or conference proceedings, or published before 2006 (i.e., the first publication on DM).
2. **Language**: Articles not written in comprehensible English.
3. **Nature of the Article**: Reviews, opinion pieces, or theoretical papers.
4. **Relevance to DM**: Articles that do not focus on DM, or that do not align with our definition of DM (e.g., mining process models rather than decisions).
5. **Evaluation**: Articles without adequate details regarding evaluation methods and datasets.

### Inclusion Criteria

The following types of articles were included via manual search:

- The seminal work by Rozinat et al. (2006), despite being a technical report.
- Articles found through backward snowballing from references.
- Articles related to DM plugins in ProM, identified from the [ProM plugin list](https://promtools.org/development/prom-6-10-release/prom-6-10-plug-in-variants/).

## Paper Selection

The extraction phase included both automated and manual search steps. The identification phase involved deduplication, while the screening phase applied the exclusion criteria based on titles, abstracts, and full-text reviews. Selected articles were managed using the [Covidence](https://app.covidence.org/) platform.

## Included Articles

A total of 25 articles were selected for final review from an initial collection of 253.

### Table: List of Selected DM Papers

| Ref. | Authors | Title | Year | Type |
|------|---------|-------|------|------|
| [1] | Rozinat and Van Der Aalst | Decision mining in business processes | 2006 | R |
| [2] | Rozinat and Van Der Aalst | DM in ProM | 2006 | C |
| [3] | Crerie et al. | Discovering business rules through process mining | 2009 | C |
| [4] | Jareevongpiboon and Janecek | Enhancing decision patterns discovered by process mining | 2011 | C |
| [5] | De Leoni and Van Der Aalst | Data-aware process mining using alignments | 2013 | C |
| [6] | Sarno et al. | DM for multi-choice workflow patterns | 2013 | C |
| ... | ... | ... | ... | ... |
| [25] | Banham et al. | Comparing Conformance Checking for DM | 2024 | J |

> *Note: Types - J = Journal, C = Conference, R = Report*
