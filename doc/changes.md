# Changes

The term **changes** is used to list all changes to a specific entry in the [Classified Compilation](classified_compilation.md) on the level of single articles.

There is the possibility to see all changes of a specific entry in the [Classified Compilation](classified_compilation.md) in the web frontend by adding `/changes` to the URL of the entry. E.g. for seeing all the changes of the Federal Constitution (not available in English), the URL would be `https://www.fedlex.admin.ch/eli/cc/1999/404/de/changes`.

Changes are extracted from [jolux:Impact](#Impact). There are two methods used to depict the concerned articles depending on the date of the change.

## Older Changes

The concerned articles of older changes are modelled via a [jolux:impactToLegalResourceComment](#impactToLegalResourceComment):

:::{admonition} jolux:impactToLegalResourceComment
:class: note
:name: impactToLegalResourceComment
The datatype property **jolux:impactToLegalResourceComment** lists the impacted articles on the legislative resource from the [jolux:Impact](#Impact) as `rdf:langString`.
:::

## Newer Changes

For newer changes, the impacted articles are modelled as [jolux:LegalResourceSubdivision](#LegalResourceSubdivision) and connected via [jolux:impactToLegalResource](#impactToLegalResource).

## SPARQL Examples

The following sparql query lists all the impacts on the Federal Constitution. The concerned articles are either given in the [jolux:impactToLegalResourceComment](#impactToLegalResourceComment) or modelled as [jolux:LegalResourceSubdivision](#LegalResourceSubdivision):

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT * WHERE {

    ?subdivision jolux:legalResourceSubdivisionIsPartOf <https://fedlex.data.admin.ch/eli/cc/1999/404>.
    ?impact jolux:impactToLegalResource ?subdivision;
        jolux:impactFromLegalResource/jolux:legalResourceSubdivisionIsPartOf ?act;
        jolux:legalResourceImpactHasType ?type.
  
    OPTIONAL {
        ?impact jolux:impactToLegalResourceComment ?comment.
    }
    
    FILTER (!BOUND(?comment) || lang(?comment) = "de")
}
```
