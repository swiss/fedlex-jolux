# Vocabularies

In RDF, a vocabulary is a **set of predefined terms**, that is used to describe resources. These terms are defined in a way that allows them to be used **consistently across different datasets**. In the case of JOLux, vocabularies are specifically used only on the object position of RDF triples.

Fedlex defines and makes use of multiple vocabularies. This sub-page lists an overview and the main vocabularies and its associated properties that are used in describing the legislative resources.

## Available Vocabularies

As all vocabularies are modelled as having the class [skos:ConceptScheme](https://www.w3.org/TR/skos-reference/#schemes), the metadata viewer can give all the vocabularies as incoming relations to skos:ConceptScheme and therefore serves as an [overview on all available vocabularies](https://fedlex.data.admin.ch/de-CH/metadata?value=http:%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23ConceptScheme).

In addition, the following SPARQL query shows all vocabularies with its name in English, German and French. The name is either `dcterms:title` where available and otherwise `rdfs:label` or empty if there is neither:

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
SELECT DISTINCT ?vocabulary ?name_en ?name_de ?name_fr WHERE {
    ?vocabulary a skos:ConceptScheme.
  
  # English title
  OPTIONAL {
    ?vocabulary dcterms:title ?title_en .
    FILTER(LANG(?title_en) = "en")
  }
  
  # German title
  OPTIONAL {
    ?vocabulary dcterms:title ?title_de .
    FILTER(LANG(?title_de) = "de")
  }
  
  # French title
  OPTIONAL {
    ?vocabulary dcterms:title ?title_fr .
    FILTER(LANG(?title_fr) = "fr")
  }
  
  # English label
  OPTIONAL {
    ?vocabulary rdfs:label ?label_en .
    FILTER(LANG(?label_en) = "en")
  }
  
  # German label
  OPTIONAL {
    ?vocabulary rdfs:label ?label_de .
    FILTER(LANG(?label_de) = "de")
  }
  
  # French label
  OPTIONAL {
    ?vocabulary rdfs:label ?label_fr .
    FILTER(LANG(?label_fr) = "fr")
  }
  
  # Use ?title if available and otherwise ?label
  BIND(COALESCE(?title_en, ?label_en) AS ?name_en)
  BIND(COALESCE(?title_de, ?label_de) AS ?name_de)
  BIND(COALESCE(?title_fr, ?label_fr) AS ?name_fr)
}
```

## Hierarchical Vocabularies

Some vocabularies are modelled as hierarchy or taxonomy of entries. The following SPARQL query lists all vocabularies that use a hierarchy:

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
SELECT DISTINCT ?vocabulary ?name_en WHERE {
    ?vocabulary a skos:ConceptScheme;
                skos:hasTopConcept ?top_concept.
  ?top_concept skos:narrower ?narrow.
  
  # English title
  OPTIONAL {
    ?vocabulary dcterms:title ?title_en .
    FILTER(LANG(?title_en) = "en")
  }
  
  # English label
  OPTIONAL {
    ?vocabulary rdfs:label ?label_en .
    FILTER(LANG(?label_en) = "en")
  }
  
  # Use ?title if available and otherwise ?label
  BIND(COALESCE(?title_en, ?label_en) AS ?name_en)
}
```

## Act Types

:::{admonition} Act Types
:class: important
:name: act-types
- URI: https://fedlex.data.admin.ch/vocabulary/legal-resource-genre
- Description: The **act types** vocabulary is used to classify the type of a jolux:Act.
- Predicates: jolux:legalResourceGenre
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Flegal-resource-genre)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/legal-resource-genre>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

## Consultation Status

:::{admonition} Consultation Status
:class: important
:name: consultation-status
- URI: https://fedlex.data.admin.ch/vocabulary/consultation-status
- Description: The **consultation status** vocabulary is used to classify the current status of a [jolux:Consultation](#Consultation).
- Predicates: jolux:consultationStatus
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fconsultation-status)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/consultation-status>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

## Countries

:::{admonition} Countries
:class: important
:name: countries
- URI: https://fedlex.data.admin.ch/vocabulary/country
- Description: The **countries** vocabulary is used to link to a specific country.
- Predicates: jolux:treatyPartyCountry
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fcountry)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/country>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

## Draft Document Types

:::{admonition} Draft Document Types
:class: important
:name: draft-document-types
- URI: https://fedlex.data.admin.ch/vocabulary/draft-document-type
- Description: The **draft document types** vocabulary is used to classify the different types in a [jolux:Consultation](#Consultation).
- Predicates: jolux:draftProcessDocumentType
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fdraft-document-type)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/draft-document-type>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "de")
}
```

As this is a hierarchical vocabulary, the following SPARQL query shows the hierarchy of the entries:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT (GROUP_CONCAT(CONCAT(STR(?endpoint_level), ": ", STR(?endpoint_label)); separator = " <---- ") AS ?hierarchy) WHERE {
    SELECT * WHERE {
        ?endpoint skos:narrower* ?intermediate;
            skos:prefLabel ?endpoint_label.
        FILTER(lang(?endpoint_label) = "de")
        {
            SELECT ?endpoint (COUNT(?endpoint) as ?endpoint_level) WHERE {
                BIND (<https://fedlex.data.admin.ch/vocabulary/draft-document-type> as ?root)
                ?root skos:hasTopConcept/skos:narrower* ?intermediate.
                ?intermediate skos:narrower* ?endpoint.
            } GROUP BY ?endpoint ORDER BY ?endpoint_level
        }
    } ORDER BY ?intermediate ?endpoint_level
} GROUP BY ?intermediate ORDER BY ?hierarchy
```

## Enforcement Status

:::{admonition} Enforcement Status
:class: important
:name: enforcement-status
- URI: https://fedlex.data.admin.ch/vocabulary/enforcement-status
- Description: The **enforcement status** vocabulary is used to classify the type of a [jolux:ConsolidationAbstract](#ConsolidationAbstract).
- Predicates: jolux:inForceStatus
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fenforcement-status)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/enforcement-status>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

## Impact Types

:::{admonition} Impact Types
:class: important
:name: impact-types
- URI: https://fedlex.data.admin.ch/vocabulary/impact-type
- Description: The **impact types** vocabulary is used to classify the type of a jolux:LegalResourceImpact.
- Predicates: jolux:legalResourceImpactHasType
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fimpact-type)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/impact-type>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

## Information Sources

:::{admonition} Information Sources
:class: important
:name: information-sources
- URI: https://fedlex.data.admin.ch/vocabulary/information-source
- Description: The **information sources** vocabulary is used to give the information source of a jolux:LegalResourceImpact.
- Predicates: jolux:informationSource
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Finformation-source)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/information-source>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

There is a special case where the predicate [jolux:informationSource](#information-sources) is used with a predicate that is not in the vocabulary. The following SPARQL query shows the first 100 entries with this object:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT * {
    ?act jolux:informationSource <https://fedlex.data.admin.ch/vocabulary/information-source/data-from-ff-excel> .
} LIMIT 100
```

## Legal Institution

:::{admonition} Legal Institution
:class: important
:name: legal-institution
- URI: https://fedlex.data.admin.ch/vocabulary/legal-institution
- Description: The **legal institution** vocabulary is used to add the responsibility of an institution for [jolux:Act](#Act).
- Predicates: jolux:responsibilityOf, jolux:isOpinionOf, jolux:jolux:institutionInChargeOfTheEvent, jolux:institutionInChargeOfTheEventLevel2
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Flegal-institution)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/legal-institution>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

As this is a hierarchical vocabulary, the following SPARQL query shows the hierarchy of the entries:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT (GROUP_CONCAT(CONCAT(STR(?endpoint_level), ": ", STR(?endpoint_label)); separator = " <---- ") AS ?hierarchy) WHERE {
    SELECT * WHERE {
        ?endpoint skos:narrower* ?intermediate;
            skos:prefLabel ?endpoint_label.
        FILTER(lang(?endpoint_label) = "de")
        {
            SELECT ?endpoint (COUNT(?endpoint) as ?endpoint_level) WHERE {
                BIND (<https://fedlex.data.admin.ch/vocabulary/legal-institution> as ?root)
                ?root skos:hasTopConcept/skos:narrower* ?intermediate.
                ?intermediate skos:narrower* ?endpoint.
            } GROUP BY ?endpoint ORDER BY ?endpoint_level
        }
    } ORDER BY ?intermediate ?endpoint_level
} GROUP BY ?intermediate ORDER BY ?hierarchy
```

## Legal Taxonomy

:::{admonition} Legal Taxonomy
:class: important
:name: legal-taxonomy
- URI: https://fedlex.data.admin.ch/vocabulary/legal-taxonomy
- Description: The **legal taxonomy** vocabulary is used to classify entries of a [jolux:ConsolidationAbstract](#ConsolidationAbstract).
- Predicates: jolux:classifiedByTaxonomyEntry 
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Flegal-taxonomy)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/legal-taxonomy>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

As this is a hierarchical vocabulary, the following SPARQL query shows the hierarchy of the entries:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT (GROUP_CONCAT(CONCAT(STR(?endpoint_level), ": ", STR(?endpoint_label)); separator = " <---- ") AS ?hierarchy) WHERE {
    SELECT * WHERE {
        ?endpoint skos:narrower* ?intermediate;
            skos:prefLabel ?endpoint_label.
        FILTER(lang(?endpoint_label) = "de")
        {
            SELECT ?endpoint (COUNT(?endpoint) as ?endpoint_level) WHERE {
                BIND (<https://fedlex.data.admin.ch/vocabulary/legal-taxonomy> as ?root)
                ?root skos:hasTopConcept/skos:narrower* ?intermediate.
                ?intermediate skos:narrower* ?endpoint.
            } GROUP BY ?endpoint ORDER BY ?endpoint_level
        }
    } ORDER BY ?intermediate ?endpoint_level
} GROUP BY ?intermediate ORDER BY ?hierarchy
```

As this is a very important vocabulary, there are also two special webpages that show these hierarchical legal taxonomy entries. One for [Swiss law](https://www.fedlex.admin.ch/en/cc/internal-law/1) and one for [international law](https://www.fedlex.admin.ch/en/cc/international-law/0.1).

## Procedure Types

:::{admonition} Procedure Types
:class: important
:name: procedure-types
- URI: https://fedlex.data.admin.ch/vocabulary/type-procedure
- Description: The **procedure types** vocabulary is used to classify the type of a jolux:Act.
- Predicates: jolux:processType
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Ftype-procedure)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/type-procedure>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

## Subdivision Types

:::{admonition} Subdivision Types
:class: important
:name: subdivision-types
- URI: https://fedlex.data.admin.ch/vocabulary/subdivision-type
- Description: The **subdivision types** vocabulary is used to classify the type of a jolux:LegalResourceSubdivision.
- Predicates: jolux:legalResourceSubdivisionType
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fsubdivision-type)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/subdivision-type>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

As this is a hierarchical vocabulary, the following SPARQL query shows the hierarchy of the entries:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT (GROUP_CONCAT(CONCAT(STR(?endpoint_level), ": ", STR(?endpoint_label)); separator = " <---- ") AS ?hierarchy) WHERE {
    SELECT * WHERE {
        ?endpoint skos:narrower* ?intermediate;
            skos:prefLabel ?endpoint_label.
        FILTER(lang(?endpoint_label) = "de")
        {
            SELECT ?endpoint (COUNT(?endpoint) as ?endpoint_level) WHERE {
                BIND (<https://fedlex.data.admin.ch/vocabulary/subdivision-type> as ?root)
                ?root skos:hasTopConcept/skos:narrower* ?intermediate.
                ?intermediate skos:narrower* ?endpoint.
            } GROUP BY ?endpoint ORDER BY ?endpoint_level
        }
    } ORDER BY ?intermediate ?endpoint_level
} GROUP BY ?intermediate ORDER BY ?hierarchy
```

## Text Types

:::{admonition} Text Types
:class: important
:name: text-types
- URI: https://fedlex.data.admin.ch/vocabulary/resource-type
- Description: The **text types** vocabulary is used to classify the text type of a jolux:Work.
- Predicates: jolux:typeDocument, jolux:historicalTypeDocument
- [Metadata viewer](https://fedlex.data.admin.ch/en-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fresource-type)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/resource-type>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "en")
}
```

As this is a hierarchical vocabulary, the following SPARQL query shows the hierarchy of the entries:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT (GROUP_CONCAT(CONCAT(STR(?endpoint_level), ": ", STR(?endpoint_label)); separator = " <---- ") AS ?hierarchy) WHERE {
    SELECT * WHERE {
        ?endpoint skos:narrower* ?intermediate;
            skos:prefLabel ?endpoint_label.
        FILTER(lang(?endpoint_label) = "de")
        {
            SELECT ?endpoint (COUNT(?endpoint) as ?endpoint_level) WHERE {
                BIND (<https://fedlex.data.admin.ch/vocabulary/resource-type> as ?root)
                ?root skos:hasTopConcept/skos:narrower* ?intermediate.
                ?intermediate skos:narrower* ?endpoint.
            } GROUP BY ?endpoint ORDER BY ?endpoint_level
        }
    } ORDER BY ?intermediate ?endpoint_level
} GROUP BY ?intermediate ORDER BY ?hierarchy
```

## Treaty Subject Themes

:::{admonition} Treaty Subject Themes
:class: important
:name: treaty-subject-themes
- URI: https://fedlex.data.admin.ch/vocabulary/treaty-subject-theme
- Description: The **treaty subject themes** vocabulary is used to classify the subject of a [jolux:TreatyProcess](#TreatyProcess).
- Predicates: jolux:treatySubject
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Ftreaty-subject-theme)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels (only in German because there are no English labels):

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/treaty-subject-theme>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "de")
}
```

## Treaty Types

:::{admonition} Treaty Types
:class: important
:name: treaty-types
- URI: https://fedlex.data.admin.ch/vocabulary/treaty-type
- Description: The **treaty types** vocabulary is used to classify the type of a [jolux:TreatyProcess](#TreatyProcess).
- Predicates: jolux:treatyType
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Ftreaty-type)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels (only in German because there are no English labels):

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/treaty-type>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "de")
}
```

## User Formats

:::{admonition} User Formats
:class: important
:name: user-formats
- URI: https://fedlex.data.admin.ch/vocabulary/user-format
- Description: The **user formats** vocabulary is used to classify the file type of a [jolux:Manifestation](#Manifestation).
- Predicates: jolux:userFormat
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Fvocabulary%2Fuser-format)
:::

The following SPARQL query shows all the entries of this vocabulary with its labels (only in German because there are no English labels):

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?term ?label WHERE {
    ?term a skos:Concept;
        skos:inScheme <https://fedlex.data.admin.ch/vocabulary/user-format>;
        skos:prefLabel ?label.
    FILTER (lang(?label) = "de")
}
```
