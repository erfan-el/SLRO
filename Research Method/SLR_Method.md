
# Methods

This research used a Systematic Literature Review approach inspired by Kitchenham et al. (2015) [1], with the process steps outlined in **Figure 1**.

**Figure 1.** Systematic Literature Review Process Steps 
![Systematic Literature Review Process Steps](https://github.com/erfan-el/SLRO/blob/main/Research%20Method/Research%20Method%20Process.png)

Also, the steps related to the selection of papers are documented in the PRISMA diagram (Preferred Reporting Items for Systematic Reviews and Meta-Analyses Page et al. 2021) [2] shown in **Figure 2**.

**Figure 2.** PRISMA diagram describing the selection of primary studies 
![PRISMA diagram](https://github.com/erfan-el/SLRO/blob/main/Research%20Method/PRISMA%20Model.png)

We conducted an automated search on four databases: Scopus, Web of Science, IEEE Xplore, and ACM Digital Library. As shown in Table 1, the search keywords can be categorized as either related to PM or DM. In the queries, the `*` symbol is used to substitute multiple characters within a word. Proximity operators such as `W/2` and `NEAR/2` yield results when two words or phrases appear within two words of each other. The operator `EXCLUDE(DOCTYPE, 'cr')` is used in Scopus to filter out articles classified as Conference Reviews. Table 2 shows the search queries per database, together with the number of results and search dates. The queries were customized according to each database's search capabilities. We further conducted a limited manual search to incorporate relevant articles that were not found in the database search; we discuss this in the Inclusion Criteria section.

### Table 1. Keywords and synonyms used in the automated search

| ID | Concept         | Synonyms                   | Query terms                                                                                      |
|----|-----------------|----------------------------|--------------------------------------------------------------------------------------------------|
| 1  | Decision Mining | Decision Mining, Decision Extraction, Decision Extracting, Decision Discovery, Decision Discovering, Decision Retrieval, Decision Retrieving, Business Rule Mining, Business Rule Extraction, Business Rule Discovery, Business Rule Discovering, Business Rule Retrieval | (decision* OR “business rule*”) W/2 (mining OR extracti* OR discover* OR retriev*) |
| 2  | Process Mining  | Process Mining, Process Discovery | “process mining” OR “process discovery” |

### Table 2. The search queries of the automated search process

| ID | Search query | Database | Result |
|----|--------------|----------|--------|
| 1 | `TITLE-ABS-KEY ((“process mining” OR “process discovery”) AND ((decision* OR “business rule*”) W/2 (mining OR extracti* OR discover* OR retriev*))) AND (EXCLUDE (DOCTYPE , “cr”))` | Scopus | 91 |
| 2 | `TS=((“process mining” OR “process discovery”) AND ((decision* OR “business rule*”) NEAR/2 (mining OR extracti* OR discover* OR retriev*)))` | Web of Science | 52 |
| 3 | Complex NEAR/2 queries for metadata fields in IEEE Xplore | IEEE Xplore | 68 |
| 4 | `AllField:("process mining" AND ("decision mining" OR "decision discovery" OR "business rule"))` | ACM | 32 |


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

- The seminal work by Rozinat et al. (2006) [3], despite being a technical report.
- Articles found through backward snowballing from references.
- Articles related to DM plugins in ProM, identified from the [ProM plugin list](https://promtools.org/development/prom-6-10-release/prom-6-10-plug-in-variants/).

## Paper Selection

The extraction phase included both automated and manual search steps. The identification phase involved deduplication, while the screening phase applied the exclusion criteria based on titles, abstracts, and full-text reviews. Selected articles were managed using the [Covidence](https://app.covidence.org/) platform.

## Included Articles

A total of 25 articles were selected for final review from an initial collection of 253.

### Table: List of Selected DM Papers

|   Ref. | Authors                     | Title                                                                                                           |   Year | Type   |
|--------|-----------------------------|-----------------------------------------------------------------------------------------------------------------|--------|--------|
|    [3] | Rozinat and Van Der Aalst   | Decision mining in business processes                                                                           |   2006 | R      |
|   [40] | Rozinat and Van Der Aalst   | DM in ProM                                                                                                      |   2006 | C      |
|    [5] | Crerie et al.               | Discovering business rules through process mining                                                               |   2009 | C      |
|    [6] | Jareevongpiboon and Janecek | Enhancing decision patterns discovered by process mining with semantic related data                             |   2011 | C      |
|   [16] | De Leoni and Van Der Aalst  | Data-aware process mining: Discovering decisions in processes using alignments                                  |   2013 | C      |
|   [14] | Sarno et al.                | DM for multi choice workflow patterns                                                                           |   2013 | C      |
|   [19] | Sarno et al.                | Mining decision to discover the relation of rules among decision points in a non-free choice construct          |   2014 | C      |
|   [20] | Dunkl et al.                | A method for analyzing time series data in process mining: Application and extension of decision point analysis |   2015 | C      |
|   [12] | Mannhardt et al.            | DM revisited -- Discovering overlapping rules                                                                   |   2016 | C      |
|   [21] | Winter and Rinderle-Ma      | Discovering Instance-Spanning Constraints from Process Execution Logs Based on Classification Techniques        |   2017 | C      |
|   [22] | Khemiri et al.              | Improving business process in semiconductor manufacturing by discovering business rules                         |   2018 | C      |
|   [18] | Mertens et al.              | Discovering health-care processes using DeciClareMiner                                                          |   2018 | J      |
|    [7] | De Smedt et al.             | Holistic discovery of decision models from process execution data                                               |   2019 | J      |
|   [17] | Jouck et al.                | A Framework to Evaluate and Compare Decision-Mining Techniques                                                  |   2019 | C      |
|   [23] | Banham et al.               | xPM: A Framework for Process Mining with Exogenous Data                                                         |   2022 | C      |
|   [24] | Hasić et al.                | Decision as a Service (DaaS): A Service-Oriented Architecture Approach for Decisions in Processes               |   2022 | J      |
|   [25] | Martínez-Rojas et al.       | Analyzing Variable Human Actions for Robotic Process Automation                                                 |   2022 | C      |
|   [15] | Mertens et al.              | Integrated Declarative Process and Decision Discovery of the Emergency Care Process                             |   2022 | J      |
|   [26] | Nguyen Chan et al.          | Design and deployment of a customer journey management system: the CJMA approach                                |   2022 | C      |
|   [11] | Scheibel and Rinderle-Ma    | Online DM and Monitoring in Process-Aware Information Systems                                                   |   2022 | C      |
|   [10] | Scheibel and Rinderle-Ma    | DM with Time Series Data Based on Automatic Feature Generation                                                  |   2022 | C      |
|   [27] | Lukassen et al.             | Discovering Explicit Scale-Up Criteria in Crisis Response with DM                                               |   2023 | C      |
|    [9] | Park et al.                 | Explainable Predictive DM for Operational Support                                                               |   2023 | C      |
|   [13] | Portolani et al.            | A Novel DM Method Considering Multiple Model Paths                                                              |   2023 | C      |
|    [8] | Banham et al.               | Comparing Conformance Checking for DM: An Axiomatic Approach                                                    |   2024 | J      |

> *Note: Types - J = Journal, C = Conference, R = Report*



## References

[1] Barbara Ann Kitchenham, David Budgen, and Pearl Brereton. *Evidence-based software engineering and systematic reviews*. 1st Edition. Vol. 4. Chapman and Hall/CRC, 2015, p. 433. ISBN: 9780429157653. DOI: [10.1201/b19467](https://doi.org/10.1201/b19467)

[2] Matthew J Page et al. “The PRISMA 2020 statement: an updated guideline for reporting systematic reviews”. In: *BMJ* 372 (2021). DOI: [10.1136/bmj.n71](https://www.bmj.com/content/372/bmj.n71). [PDF](https://www.bmj.com/content/372/bmj.n71.full.pdf)

[3] A. Rozinat and W.M.P. van der Aalst. *Decision mining in business processes*. Eindhoven: Technische Universiteit Eindhoven, 2006. [PDF](https://research.tue.nl/files/1750830/609514.pdf)

[4] A. Rozinat and W.M.P. van der Aalst. “Decision Mining in ProM”. In: *Business Process Management*. Springer Berlin Heidelberg, 2006, pp. 420–425. DOI: [10.1007/11841760_33](https://doi.org/10.1007/11841760_33)

[5] Raphael Crerie, Fernanda Araujo Baião, and Flávia Maria Santoro. “Discovering Business Rules through Process Mining”. In: *Enterprise, Business-Process and Information Systems Modeling*. Springer Berlin Heidelberg, 2009, pp. 136–148. DOI: [10.1007/978-3-642-01862-6_12](https://doi.org/10.1007/978-3-642-01862-6_12)

[6] W. Jareevongpiboon and P. Janecek. “Enhancing decision patterns discovered by process mining with semantic related data”. In: *ICEB 2011 Proceedings*. AISeL, 2011, pp. 12–19. [URL](https://aisel.aisnet.org/iceb2011/5/)

[7] J. De Smedt, F. Hasić, S.K.L.M. vanden Broucke, and J. Vanthienen. “Holistic discovery of decision models from process execution data”. In: *Knowledge-Based Systems* 183 (2019), p. 104866. DOI: [10.1016/j.knosys.2019.104866](https://doi.org/10.1016/j.knosys.2019.104866)

[8] A. Banham et al. “Comparing Conformance Checking for Decision Mining: An Axiomatic Approach”. In: *IEEE Access* 12 (2024), pp. 60276–60298. DOI: [10.1109/ACCESS.2024.3391234](https://doi.org/10.1109/ACCESS.2024.3391234)

[9] Gyunam Park et al. “Explainable Predictive Decision Mining for Operational Support”. In: *ICSOC 2022 Workshops*. Springer Nature Switzerland, 2023, pp. 66–79. DOI: [10.1007/978-3-031-26507-5_6](https://doi.org/10.1007/978-3-031-26507-5_6)

[10] Beate Scheibel and Stefanie Rinderle-Ma. “Decision Mining with Time Series Data Based on Automatic Feature Generation”. In: *Advanced Information Systems Engineering*. Springer International Publishing, 2022, pp. 3–18. DOI: [10.1007/978-3-031-07472-1_1](https://doi.org/10.1007/978-3-031-07472-1_1)

[11] Beate Scheibel and Stefanie Rinderle-Ma. “Online Decision Mining and Monitoring in Process-Aware Information Systems”. In: *Conceptual Modeling*. Springer, 2022, pp. 271–280. DOI: [10.1007/978-3-031-17995-2_19](https://doi.org/10.1007/978-3-031-17995-2_19)

[12] F. Mannhardt et al. “Decision mining revisited – Discovering overlapping rules”. In: *Advanced Information Systems Engineering*. Springer, 2016, pp. 377–392. DOI: [10.1007/978-3-319-39696-5_23](https://doi.org/10.1007/978-3-319-39696-5_23)

[13] Pietro Portolani et al. “A Novel Decision Mining Method Considering Multiple Model Paths”. In: *Enterprise, Business-Process and Information Systems Modeling*. Springer, 2023, pp. 79–87. DOI: [10.1007/978-3-031-34241-7_6](https://doi.org/10.1007/978-3-031-34241-7_6)

[14] Riyanarto Sarno et al. “Decision mining for multi choice workflow patterns”. In: *IC3INA 2013*. IEEE, 2013, pp. 337–342. DOI: [10.1109/IC3INA.2013.6819197](https://doi.org/10.1109/IC3INA.2013.6819197)

[15] S. Mertens et al. “Integrated Declarative Process and Decision Discovery of the Emergency Care Process”. In: *Information Systems Frontiers* 24.1 (2022), pp. 305–327. DOI: [10.1007/s10796-020-10078-5](https://doi.org/10.1007/s10796-020-10078-5)

[16] M. de Leoni and W.M.P. van der Aalst. “Data-aware process mining: discovering decisions in processes using alignments”. In: *ACM SAC 2013*. ACM, pp. 1454–1461. DOI: [10.1145/2480362.2480633](https://doi.org/10.1145/2480362.2480633)

[17] Toon Jouck et al. “A Framework to Evaluate and Compare Decision-Mining Techniques”. In: *BPM Workshops 2019*. Springer, pp. 482–493. DOI: [10.1007/978-3-030-11641-5_38](https://doi.org/10.1007/978-3-030-11641-5_38)

[18] S. Mertens, F. Gailly, and G. Poels. “Discovering health-care processes using DeciClareMiner”. In: *Health Systems* 7.3 (2018), pp. 195–211. DOI: [10.1080/20476965.2017.1405876](https://doi.org/10.1080/20476965.2017.1405876)

[19] Riyanarto Sarno et al. “Mining decision to discover the relation of rules among decision points in a non-free choice construct”. In: *ICTS 2014*. IEEE, pp. 53–58. DOI: [10.1109/ICTS.2014.7010557](https://doi.org/10.1109/ICTS.2014.7010557)

[20] Reinhold Dunkl et al. “A Method for Analyzing Time Series Data in Process Mining”. In: *Information Systems Engineering in Complex Environments*. Springer, 2015, pp. 68–84. DOI: [10.1007/978-3-319-19270-3_5](https://doi.org/10.1007/978-3-319-19270-3_5)

[21] Karolin Winter and Stefanie Rinderle-Ma. “Discovering Instance-Spanning Constraints from Process Execution Logs”. In: *EDOC 2017*. IEEE, pp. 79–88. DOI: [10.1109/EDOC.2017.20](https://doi.org/10.1109/EDOC.2017.20)

[22] Abdelhak Khemiri et al. “Improving Business Process in Semiconductor Manufacturing by Discovering Business Rules”. In: *WSC 2018*. IEEE, pp. 3441–3448. DOI: [10.1109/WSC.2018.8632509](https://doi.org/10.1109/WSC.2018.8632509)

[23] Adam Banham et al. “xPM: A Framework for Process Mining with Exogenous Data”. In: *Process Mining Workshops*. Springer, 2022, pp. 85–97. DOI: [10.1007/978-3-030-98581-3_7](https://doi.org/10.1007/978-3-030-98581-3_7)

[24] F. Hasić et al. “Decision as a Service (DaaS): A Service-Oriented Architecture Approach for Decisions in Processes”. In: *IEEE Transactions on Services Computing* 15.2 (2022), pp. 904–917. DOI: [10.1109/TSC.2020.2965516](https://doi.org/10.1109/TSC.2020.2965516)

[25] A. Martínez-Rojas et al. “Analyzing Variable Human Actions for Robotic Process Automation”. In: *Business Process Management*. Springer, 2022, pp. 75–90. DOI: [10.1007/978-3-031-16103-2_8](https://doi.org/10.1007/978-3-031-16103-2_8)

[26] Nam Nguyen Chan et al. “Design and deployment of a customer journey management system: the CJMA approach”. In: *ICFNDS 2021*. ACM, 2022, pp. 8–16. DOI: [10.1145/3508072.3508075](https://doi.org/10.1145/3508072.3508075)

[27] Britt Lukassen, Laura Genga, and Yingqian Zhang. “Discovering Explicit Scale-Up Criteria in Crisis Response with Decision Mining”. In: *Learning and Intelligent Optimization*. Springer, 2023, pp. 459–474. DOI: [10.1007/978-3-031-44505-7_31](https://doi.org/10.1007/978-3-031-44505-7_31)
