# Federal Gazette (BBl)

The *Federal Gazette (BBl)* is according to the [lexicon of parliamentary terms](https://www.parlament.ch/en/%C3%BCber-das-parlament/parlamentsw%C3%B6rterbuch/parlamentsw%C3%B6rterbuch-detail?WordId=24#q=federal%20gaz) a general bulletin published by the Confederation, that includes the following texts:

- dispatches from the Federal Council with drafts of laws and other decisions for submission to the Federal Assembly
- reports by Federal Assembly committees with draft proposals and the relevant opinions of the Federal Council
- decrees and acts approved by the Federal Assembly that are subject to an optional or a mandatory referendum, with the exception of federal acts declared to be urgent, which are published in the Official Compilation
- rulings by the Federal Chancellery on the preliminary examination, success or failure of popular initiatives and referendums
- decrees issued by the Federal Council on the results of the popular votes (including all cantonal results)
- reports by the Federal Council on the National Council elections (including all cantonal results) submitted to the National Council
- instructions issued by the Federal Council

The abbreviation BBl is the official English abbreviation according to [Termdat](https://register.ld.admin.ch/termdat/57194) but origins from the German "Bundesblatt".

:::{admonition} Hint for legal laypersons
:class: hint
Federal Gazette, Official Compilation and Classified Compilation are the three main publications in the legislation process. The basic idea (greatly simplified) is the following:

- the Federal Gazette is used to publish the reasons for a legislative process and documents the process
- the [Official Compilation](official_compilation.md) is the legally binding publication of all legislation in chronologically order with only the delta (changes) to already existing legislation
- the [Classified Compilation](classified_compilation.md) is sorted by topics and contains the consolidated legislation (only the currently valid legislation)

During the legislative process, these three publications are of different importance. During development, the Federal Gazette is the most important, for entry into force, the Official Compilation (OC) and for working with the current state of the law, the Classified Compilation (CC).
:::

## Example

Throughout this sub-page, the federal council dispatch to the change in the federal constitution for a 13th monthly pension payment.

- URI: https://fedlex.data.admin.ch/eli/fga/2022/1485
- URL: https://www.fedlex.admin.ch/eli/fga/2022/1485
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Feli%2Ffga%2F2022%2F1485)

## URI

The URI of an entry in the Federal Gazette contains the following parts:

- Standard namespace and path: `https://fedlex.data.admin.ch/eli/`
- the part `fga/` denotes the Federal Gazette, meaning that this URI identifies something that is part of the Federal Gazette
- `YYYY/` is the year of the publication
- `ID` an identifier that has no specific meaning but is restarting every new year, for older entries there are also combined numbers possible like `https://fedlex.data.admin.ch/eli/fga/1849/3_215__` that refer to pages in the pulication.

## General Structure

Every entry in the Federal Gazette is of type jolux:Act.

:::{admonition} jolux:Act
:class: note
:name: Act
The owl:Class **jolux:Act** is used for entries in the Federal Gazette and the Official Compilation. It is of the same [abstraction level](abstraction_levels.md) as [jolux:Work](#Work) and all jolux:Act are also jolux:Work.
:::

For jolux:Act in the Federal Gazette, the additional [abstraction levels](abstraction_levels.md) jolux:Expression and jolux:Manifestation are also available for all entries in the Federal Gazette.

The following figure shows the general structure of an entry in the Federal Gazette:

:::{figure-md} fga_general

<img src="img/fga_general.png" class="max-width-500">

General structure of an entry in the Federal Gazette.
:::

As the Federal Gazette is published in a sequential and chronologically order, the sequence within the current year is annotated via jolux:sequenceInTheYearOfPublication:

:::{admonition} jolux:sequenceInTheYearOfPublication
:class: note
:name: sequenceInTheYearOfPublication
The data property **jolux:sequenceInTheYearOfPublication** is used to connect the [jolux:Act](#Act) of the Federal Gazette to the number of the sequence in the current year.
:::

Each entry in the Federal Gazette is the result of publication process that is linked via jolux:legalResourceWasPublishedByPublicationProcess:

:::{admonition} jolux:legalResourceWasPublishedByPublicationProcess
:class: note
:name: legalResourceWasPublishedByPublicationProcess
The object property **jolux:legalResourceWasPublishedByPublicationProcess** is used to connect an entry in the Federal Gazette to the publication process that led to the publication of this entry.
:::

## Datatype Properties

- [jolux:publicationDate](#publicationDate)
- [jolux:dateDocument](#dateDocument)
- [jolux:sequenceInTheYearOfPublication](#sequenceInTheYearOfPublication)

## Object Properties

Object properties that point to a vocabulary entry:

- [jolux:processType](#procedure-types)
- [jolux:typeDocument](#text-types)
- [jolux:legalResourceFamilyType](#resource-family)
- [jolux:legalResourcePublicationCompleteness](#publication-completeness)
- [jolux:legalResourceGenre](#act-types)
- [jolux:responsibilityOf](#legal-institution)

Object properties that point to an individual:

- [jolux:legalResourceWasPublishedByPublicationProcess](#legalResourceWasPublishedByPublicationProcess)
- [jolux:isRealizedBy](#isRealizedBy)
- [jolux:isPartOf](#isPartOf)

## SPARQL Examples

The following SPARQL query shows the 10 latest federal council dispatches in the Federal Gazette with Italian titles:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>

SELECT ?dispatch ?date ?title WHERE {

	?dispatch jolux:legalResourceFamilyType <https://fedlex.data.admin.ch/vocabulary/resource-family/fga> ;
        jolux:typeDocument <https://fedlex.data.admin.ch/vocabulary/resource-type/23> ;
        jolux:publicationDate ?date ;
        jolux:isRealizedBy ?expression .
  
  ?expression jolux:title ?title ;
        jolux:language <http://publications.europa.eu/resource/authority/language/ITA> .
  
} ORDER BY DESC(?date) LIMIT 10
```