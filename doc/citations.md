# Citations

Legal texts often refer other legislative resources in the form of citations. In JOLux, citations are modelled as [jolux:Citation](#Citation).

:::{admonition} jolux:Citation
:class: note
:name: Citation
A **jolux:Citation** is used to model citations between legislative resources.
:::

The following figure shows the general structure of a citation:

:::{figure-md} citation_fig

<img src="img/citation.png">

General structure of a citation. The dashed lines mean either one of the outgoing connections can be set.
:::

The citations for an entry in the [Classified Compilation](classified_compilation.md) can be shown with the following URL (example for the Federal Constitution): https://www.fedlex.admin.ch/eli/cc/1999/404/de/quotes. These pages are only available in German, French, and Italian.

## From and To

A citation *from* means the citing resource whereas *to* means the cited resource. So if a legislative resource cites the Federal Constitution, the citation goes *from* this resource *to* the Federal Constitution.

:::{admonition} jolux:citationFromLegalResource
:class: note
:name: citationFromLegalResource
The object property **jolux:citationFromLegalResource** is used to connect a [jolux:Citation](#Citation) to a [jolux:LegalResourceSubdivision](#LegalResourceSubdivision) that is the **citing** document.
:::

:::{admonition} jolux:citationToLegalResource
:class: note
:name: citationToLegalResource
The object property **jolux:citationToLegalResource** is used to connect a [jolux:Citation](#Citation) to a [jolux:LegalResourceSubdivision](#LegalResourceSubdivision) that is the **cited** document.
:::

The Citation can either go from a [jolux:Act](#Act) or a [jolux:Consolidation](#Consolidation) to another [jolux:Act](#Act) or [jolux:ConsolidationAbstract](#ConsolidationAbstract). All combinations are possible. But on the *to* side, there is no direct [jolux:Consultation](#Consultation) possible, so if the cited resource is in the [Classified Compilation](classified_compilation.md), it is always the [jolux:ConsolidationAbstract](#ConsolidationAbstract) that is cited.

## SPARQL Examples

The following SPARQL query shows all the [jolux:ConsolidationAbstract](#ConsolidationAbstract) with its German titles that cite the Federal Constitution:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT * WHERE {
	?citation jolux:citationToLegalResource/jolux:legalResourceSubdivisionIsPartOf <https://fedlex.data.admin.ch/eli/cc/1999/404>;
                                        jolux:citationFromLegalResource/jolux:legalResourceSubdivisionIsPartOf/jolux:isMemberOf ?consolidationAbstractFrom.
  ?citation jolux:descriptionFrom ?descriptionFrom;
            jolux:language <http://publications.europa.eu/resource/authority/language/DEU>.
  ?consolidationAbstractFrom jolux:isRealizedBy ?expressionFrom.
  ?expressionFrom jolux:language <http://publications.europa.eu/resource/authority/language/DEU>;
              jolux:title ?titleFrom.
}
```

The following SPARQL query shows the first 100 [jolux:Citation](#Citation) between two [jolux:Act](#Act):

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
SELECT DISTINCT * WHERE {
    ?citation a jolux:Citation;
  	    jolux:citationFromLegalResource/jolux:legalResourceSubdivisionIsPartOf/rdf:type jolux:Act;
	    jolux:citationToLegalResource/jolux:legalResourceSubdivisionIsPartOf/rdf:type jolux:Act.
}
limit 100
```