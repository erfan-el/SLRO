# Competency questions for DM-KG

## Role: DM practitioner

### My case involves temporal decisions. How can I mine decision rules involving temporal aspects?

Run the DL query: 
```
targetsDecisionType value TemporalDecisions
```

Which asks for _DMSolutions_ that target-as-decision-type **TemporalDecisions** (a _TypeOfDecision_ instance).  
This query returns the _DMSolution_ instance **TemporalDataTimeSeries**.  

In its property assertions, you can find (inferred) _solutionProposedBy_ relations with _Works_ that proposed the solution.  
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
This query returns a large number of _DMProblem_ instances, including **DeviatingLogs** and **DynamicDecisionRules**.

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

Which asks for _ModelPros_ that are a pro-of **DeclarativeProcessModel** (a _WorkflowModel_ instance).  

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

## Role: DM researcher

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

**Note**: The * is a wildcard that means any depth of subclass (direct or indirect).


### What different types of decisions have been studied in DM literature?
Run the DL query:
```
TypeOfDecision
```

### Which existing works have applied neural networks for DM?
Run the DL query:
```
proposesSolution some (usesAlgorithm value NeuralNetworks)
```

### What are the problems tackled by papers with Rinderle-Ma as a co-author over the years?
Run the DL query:
```
inverse addressesProblem some (dcterms:creator value Stefanie.Rinderle-Ma)
```

### Are there problems that have only been tackled by a single group (i.e., with the same author involved in all works)?

Run the SPARQL Query:

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dct: <http://purl.org/dc/terms/> 
PREFIX slr: <https://purl.archive.org/slr/decisionmining.owl#>
PREFIX fabio: <http://purl.org/spar/fabio/>

SELECT ?problem (GROUP_CONCAT(DISTINCT ?paper; SEPARATOR=", ") AS ?papers) (GROUP_CONCAT(DISTINCT ?authorGroup; SEPARATOR=" | ") AS ?authorGroups)
WHERE {
  {
    SELECT ?problem ?paper (GROUP_CONCAT(DISTINCT ?authorName; SEPARATOR=", ") AS ?authorGroup)
    WHERE {
      ?paper slr:addressesProblem ?problem .
      ?paper dct:creator ?author .
      ?author rdfs:label ?authorName .
    }
    GROUP BY ?problem ?paper
  }
}
GROUP BY ?problem
HAVING (COUNT(DISTINCT ?authorGroup) = 1)
```

### What are the types of algorithms applied for DM? (Essentially, list all algorithms.)
Run the DL query:
```
DMAlgorithm
```

### I am interested in applying my new DM approach in the healthcare sector. Are there any existing datasets for evaluation in that domain?
Run the DL query:
```
dcterms:subject value Healthcare
```

### Where can I find the existing implementations of injecting missing context Knowledge?
Run the DL query:
```
inverse embodiment some (inverse realization some (proposesSolution value InjectDomainKnowledge))
```

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

### List all problems, papers and their authors:

Run the SPARQL query:
````
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