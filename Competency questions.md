# Competency questions for DM-KG
---

## Role: DM practitioner

### My case involves temporal decisions. How can I mine decision rules involving temporal aspects?

Run the DL query: 
```
targetsDecisionType value TemporalDecisions
```

Which asks for _DMSolutions_ that target-as-decision-type **TemporalDecisions** (a _TypeOfDecision_ instance).  
This query returns the _DMSolution_ instance **TemporalDataTimeSeries**.  

In its property assertions, you can find _solutionProposedBy_ relations with _Works_ that proposed the solution.  
Alternatively, to directly query for all these _Works_, you can run the following DL query that nests the above query:
```
proposesSolution some (targetsDecisionType value TemporalDecisions)
```


### How can I extend my event log with attributes needed for accurate decision rules?

Run the DL query:
```
solves value MissingContextData
```

Which asks for _DMSolutions_ that solves **MissingContextData** (a _DMProblem_ instance).  
This query returns a number of _DMSolutions_, such as **EventAttributeClassification**, **FeatureEngineering**, and **InjectData**.

In their property assertions, you can find _solutionProposedBy_ relations with _Works_ that proposed the solution.  
Alternatively, to directly query for all these _Works_, you can run the following DL query that nests the above query:
```
proposesSolution some (solves value MissingContextData)
```

**Note**: alternatively, the following DL query directly returns _Works_ that address the given problem:
```
addressesProblem value MissingContextData
```

You can then find the solutions proposed by these _Works_ as follows:
```
solutionProposedBy some (addressesProblem value MissingContextData)
``` 

### I believe some of the decisions cover multiple process instances. How can I mine these kinds of decisions?

Run the DL query:
```
solves value Instance-spanningConstraint
```

Which asks for _DMSolutions_ that solves **Instance-spanningConstraint** (a _DMProblem_ instance).  
This query returns the _DMSolution_ instance **IdentifyInstance-spanningDependencies**.

In its property assertions, you can find _solutionProposedBy_ relations with _Works_ that proposed the solution.  
Alternatively, to directly query for these _Works_, you can run the following DL query that nests the above query:
```
proposesSolution some (solves value Instance-spanningConstraint)
```

### I believe I am missing decisions in my process model. How can I identify these decisions?

Run the DL query:
```
solves value MissingDecisions
```

Which asks for _DMSolutions_ that solves **MissingDecisions** (a _DMProblem_ instance).  
This query returns a number of _DMSolutions_, such as **IdentifyVariable-activityDependencies**.

In their property assertions, you can find _solutionProposedBy_ relations with _Works_ that proposed the solution.  
Alternatively, to directly query for these _Works_, you can run the following DL query that nests the above query:
```
proposesSolution some (solves value MissingDecisions)
```

### I'm observing poor recall (fitness with the event log) of mined decision rules in DM. What could cause this problem?

Run the DL query:
```
possibleCauseOf value LowDecisionModelRecall
```

Which asks for _DMProblems_ that are a possible-cause-of **LowDecisionModelRecall** (a _DecisionModelIssue_ instance).  
This query returns a large number of _DMProblems_ instances, including **DeviatingLogs** and **DynamicDecisionRules**.

In their property assertions, you can find _solvedBy_ relations with _DMSolutions_ that aim to solve the problem.  
In turn, in the property assertions of those _DMSolutions_, you can find _solutionProposedBy_ relations with _Works_ that proposed the solution.

As before, you can also write a DL query to query for all those _Works_:
```
proposesSolution some (solves some (possibleCauseOf value LowDecisionModelRecall))
```

### What type of workflow model should I use as input into DM? 
(Or, what are the pros and cons of different types of workflow models regarding DM?)

To get the pros of a given type of workflow model, run the DL query:
```
proOf value DeclarativeProcessModel
```

Which asks for _ModelPro_ that are a pro-of **DeclarativeProcessModel** (a _WorkflowModel_ instance).  

To get the cons of a given type of workflow model, run the DL query:
```
conOf value PetriNets
```

Which asks for _ModelCons_ that are a con-of **PetriNets** (a _WorkflowModel_ instance).  

To get _Works_ that use a type of workflow model, run the DL query:
```
usesModel value DeclarativeProcessModel
```

To get all _Models_ that are used by the reviewed papers:
```
modelUsedBy some Work
```


### What tooling is available for DM?

Simply run the DL query:
```
DMTool
```
---
## Role: DM researcher
---

### What are the most well-studied problems in DM, ranked by their coverage in the literature?

Run the SPARQL Query:
```

PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX slr: <https://purl.archive.org/slr/decisionmining.owl#>
PREFIX fabio: <http://purl.org/spar/fabio/>

SELECT ?problem (STR(COUNT(?article)) AS ?numArticles)
WHERE {
    ?article rdf:type ?type .
    ?type rdfs:subClassOf* fabio:Work .
    ?article slr:addressesProblem ?problem .
}
GROUP BY ?problem
ORDER BY DESC(?numArticles)
```

Here is the steps of the SPARQL Query:

* WHERE section:

1. Find articles and check the type:
It looks for any entity (i.e., ?article) that has a type (a ?type, such as ScholarlyWork), and then ensures that this ?type is a subclass (i.e., rdfs:subClassOf*) of the fabio:Work class.

2. Find the problem:
For each ?article, it checks which problem (i.e., ?problem) it addresses using the property slr:addressesProblem.

* SELECT section:

3. Find each unique problem:
It lists every ?problem that was mentioned in the ?article.

4. Count articles:
For each ?problem, it counts the number of ?article instances (i.e., ?numArticles) that address it.

* GROUP BY section:

5. Group results:
It groups the results by each distinct ?problem so that the count of articles is calculated per problem.

* ORDER BY section:

6. Sort the results:
It sorts the results in descending order based on ?numArticles, showing the problems addressed by the most articles first.


*Note: The * is a wildcard that means any depth of subclass (direct or indirect).
**Note: STR() function turns that number into a string.


### What different types of decisions have been studied in DM literature?

Run the DL query:
```
TypeOfDecision
```

Which asks for list all _TypeOfDecision_ (that is, the classified types of decision in process) that are used by the reviewed papers.


### Which existing works have applied neural networks for DM?

Run the DL query:
```
proposesSolution some (usesAlgorithm value NeuralNetworks)
```

The inner query asks for _DMSolutions_ that used **NeuralNetworks** (an _Algorithm_ instance).
This query returns a _DMSolutions_ that utilize neural networks: **AdvancedML**.
Next, in their property assertions, you can find _solutionProposedBy_ relations with _Works_ that proposed the solution.
Alternatively, in the outer query, the _proposesSolution_ relations are used to directly query for all _Works_ instances that apply neural networks for DM.

This query returns the _Work_ instance: **Park_et_al.2023**


### What are the problems tackled by papers with Rinderle-Ma as a co-author over the years?

Run the DL query:
```
problemAddressedBy some (dcterms:creator value 'Stefanie Rinderle-Ma')
```

The inner query asks for _Works_ that **Stefanie Rinderle-Ma** (an _Author_ instance) is listed as one of the creators.
This query returns a set of _Works_ such as: **Dunkl_et_al.2015** and **Scheibel_et_al.Jun_2022**.
Next, in their property assertions, you can find _addressesProblem_ relations with _Work_ that address the problem.
Alternatively, in the outer query, the _problemAddressedBy_ relations are used to directly query for all these _DMProblem_ instances that are addressed in _Work_ instances, authored or co-authored by Stefanie Rinderle-Ma.

This query returns the _DMProblem_ instances such as: **DynamicDecisionRules**, and **Instance-spanningConstraint**.


### What are the types of algorithms applied for DM? (Essentially, list all algorithms.)

Run the DL query:
```
DMAlgorithm
```

Which simply returns all algorithms mentioned for DM in reviewed papers.


### I am interested in applying my new DM approach in the healthcare sector. Are there any existing datasets for evaluation in that domain?

Run the DL query:
```
dcterms:subject value Healthcare
```

Which asks for _Datasets_ that belong to the **Healthcare** (a _IndustryDomain_ instance).  
This query returns the _Dataset_ instances such as: **HealthRecord_EHR_SystemDataset**, and **SepsisDataset**.


### Where can I find the existing implementations of injecting time series data?

Run the DL query:
```
embodiedIn some (isRealizedBy some (proposesSolution value TemporalDataTimeSeries))
```

Starting from the innermost part, it asks for _Works_ that proposes **TemporalDataTimeSeries** (a _DMSolution_ instance). 
This query returns _Works_ instances such as: **Banham_et_al.2022**, and **Scheibel_et_al.Jun_2022**.

Next, in their property assertions, you can find _realization_ relations with _Work_.
Alternatively, the _isRealizedBy_ relations are used to directly query for all the _Expression_ instances that correspond with the returned _Works_.

Again, in their property assertions, you can find _embodiment_ relations with _Expression_.
Alternatively, in the outermost part of the query, the _embodiedIn_ relations are used to directly query for all the _Manifestation_ instances that correspond with the returned _Expression_ instances.

The whole query returns a _Manifestation_ instance: **bscheibel_edt-ts_Git_Manifestation**.
---

## Other SPARQL Queries:

### List of articles and problems they address

Run the SPARQL query:
```

PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dct: <http://purl.org/dc/terms/> 
PREFIX slr: <https://purl.archive.org/slr/decisionmining.owl#>
PREFIX fabio: <http://purl.org/spar/fabio/>
SELECT ?article ?problem
WHERE {
    ?article a ?type .
    ?type rdfs:subClassOf* fabio:Work .
    ?article slr:addressesProblem ?problem .
}

```

Here are the steps of the SPARQL Query:

* WHERE section:

1. Find articles and check the type:
It looks for any entity (i.e., ?article) that has a type (i.e., ?type), and then ensures that this ?type is a subclass (i.e., rdfs:subClassOf*) of the fabio:Work class.

2. Find the problem:
For each ?article, it checks which problem (i.e., ?problem) it addresses using the property slr:addressesProblem.

* SELECT section:

3.  Show each article and its problem:
Return lists of the ?article and the ?problem it addresses.


### List all problems, papers and their authors:

Run the SPARQL query:
```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dct: <http://purl.org/dc/terms/> 
PREFIX slr: <https://purl.archive.org/slr/decisionmining.owl#>
PREFIX fabio: <http://purl.org/spar/fabio/>

SELECT ?problem ?paper (GROUP_CONCAT(DISTINCT ?authorName; SEPARATOR=", ") AS ?authors)
WHERE {
    ?paper dct:creator ?author ;
           slr:addressesProblem ?problem .
    ?author rdfs:label ?authorName .
}
GROUP BY ?problem ?paper
ORDER BY ?problem
```

The steps of the SPARQL Query:

* WHERE section:

1. Find papers that address problems:
It identifies entities (i.e., ?paper) and the problems (i.e., ?problem) they address, using property slr:addressesProblem. 

2. Get the authors of each paper:
Then, links each ?paper to its author(s) (i.e., ?author) via property dct:creator.

 3. Get author names:
Next, it retrieves the readable name of each ?author  (i.e., the label of instances).

* SELECT section:

4. Return the problem, paper, and list of authors:
It returns a list of ?problem, ?paper, and a comma-separated list of all distinct ?author names for that ?paper (using GROUP_CONCAT).
