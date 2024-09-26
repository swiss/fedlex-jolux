# Vocabularies

In RDF, a vocabulary is a **set of predefined terms**, that is used to describe resources. These terms are defined in a way that allows them to be used **consistently across different datasets**. In the case of JOLux, vocabularies are specifically used only on the object position of RDF triples.

Fedlex defines and makes use of multiple vocabularies. This sub-page lists an overview and the main vocabularies and its associated properties that are used in describing the legal resources.

## All Available Vocabularies

As all vocabularies are modelled as having the class [skos:ConceptScheme](https://www.w3.org/TR/skos-reference/#schemes), the metadata viewer can give all the vocabularies as incoming relations to skos:ConceptScheme and therefore serves as an [overview on all available vocabularies](https://fedlex.data.admin.ch/de-CH/metadata?value=http:%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23ConceptScheme).

## Act Types

- URI: https://fedlex.data.admin.ch/vocabulary/legal-resource-genre
- Description: The **act types** vocabulary is used to classify the type of a jolux:Act.
- Predicates: jolux:legalResourceGenre
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Flegal-resource-genre)

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT ?term ?label WHERE {
    ?term skos:inScheme <https://fedlex.data.admin.ch/vocabulary/legal-resource-genre>;
        skos:prefLabel ?label.
    FILTER NOT EXISTS {?term a skos:Collection}
    FILTER (lang(?label) = "en")
}
```

## Impact Types

- URI: https://fedlex.data.admin.ch/vocabulary/impact-type
- Description: The **impact types** vocabulary is used to classify the type of a jolux:LegalResourceImpact.
- Predicates: jolux:legalResourceImpactHasType
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fimpact-type)

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT ?term ?label WHERE {
    ?term skos:inScheme <https://fedlex.data.admin.ch/vocabulary/impact-type>;
        skos:prefLabel ?label.
    FILTER NOT EXISTS {?term a skos:Collection}
    FILTER (lang(?label) = "en")
}
```

## Procedure Types

- URI: https://fedlex.data.admin.ch/vocabulary/type-procedure
- Description: The **procedure types** vocabulary is used to classify the type of a jolux:Act.
- Predicates: jolux:processType
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Ftype-procedure)

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT ?term ?label WHERE {
    ?term skos:inScheme <https://fedlex.data.admin.ch/vocabulary/type-procedure>;
        skos:prefLabel ?label.
    FILTER NOT EXISTS {?term a skos:Collection}
    FILTER (lang(?label) = "en")
}
```

## Subdivision Types

- URI: https://fedlex.data.admin.ch/vocabulary/subdivision-type
- Description: The **subdivision types** vocabulary is used to classify the type of a jolux:LegalResourceSubdivision.
- Predicates: jolux:legalResourceSubdivisionType
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fsubdivision-type)

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT ?term ?label WHERE {
    ?term skos:inScheme <https://fedlex.data.admin.ch/vocabulary/subdivision-type>;
        skos:prefLabel ?label.
    FILTER NOT EXISTS {?term a skos:Collection}
    FILTER (lang(?label) = "en")
}
```

## Text Types

- URI: https://fedlex.data.admin.ch/vocabulary/resource-type
- Description: The **text types** vocabulary is used to classify the text type of a jolux:Work.
- Predicates: jolux:typeDocument, jolux:historicalTypeDocument
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fresource-type)

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT ?term ?label WHERE {
    ?term skos:inScheme <https://fedlex.data.admin.ch/vocabulary/resource-type>;
        skos:prefLabel ?label.
    FILTER NOT EXISTS {?term a skos:Collection}
    FILTER (lang(?label) = "en")
}
```
