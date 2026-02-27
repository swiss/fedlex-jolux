# Drafts

The process of a *draft* leads to a new or updated legislative resource.

## Example

Throughout this sub-page, the following draft that led to a change in the [SR 192.12](https://www.fedlex.admin.ch/eli/cc/2007/860) is used as an example.

- URI: https://fedlex.data.admin.ch/eli/dl/proj/7021/0317
- URL: No URL for jolux:Draft available
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Feli%2Fdl%2Fproj%2F7021%2F0317)

In the given example, the draft is about changing an already existing law, the necessary steps (independent from any JOLux modelling) included:

- 21-04-12: publication of opening of the consultation process, published in the [Federal Gazette (BBl)](https://www.fedlex.admin.ch/eli/fga/2021/761)
- execution of the consultation process, more details to this actual process are given [here](https://www.fedlex.admin.ch/de/consultation-procedures/ended/2021#https://fedlex.data.admin.ch/eli/dl/proj/2021/57/cons_1), consultation started on 21-03-31 and ended on 21-07-07
- 21-12-06: publication of the federal council dispatch from 21-11-24, published in the [Federal Gazette (BBl)](https://www.fedlex.admin.ch/eli/fga/2021/2805)
- 21-12-06: publication of the draft law, published in the [Federal Gazette (BBl)](https://www.fedlex.admin.ch/eli/fga/2021/2806)
- parliamentary process (no changes required), 22-03-10 until 22-06-17
- 22-06-28: publication of the changed law with decision from 22-06-17, published in the [Federal Gazette (BBl)](https://www.fedlex.admin.ch/eli/fga/2022/1564)
- 22-10-06: expiration of the referendum period
- 22-10-11: publication of the changed law with decision from 22-06-17 and entering into force on 22-11-01 in the [Official Compilation (OC)](https://www.fedlex.admin.ch/eli/oc/2022/572)
- 22-11-01:publication of the changed law in the [Classified Compilation (CC)](https://www.fedlex.admin.ch/eli/cc/2007/860)

## URI

The URI of a draft contains the following parts:

- Standard namespace and path: `https://fedlex.data.admin.ch/eli/`
- the part `dl/proj` is used as path for all drafts (dl stands for draft legislation and proj for project)
- `XXXX/YYYY` is an identifier

## General Structure

Every draft is of type jolux:Draft.

:::{admonition} jolux:Draft
:class: note
:name: Draft
The owl:Class **jolux:Draft** is used for drafts.
:::

The following figure shows the general structure of a draft:

:::{figure-md} fig_draft

<img src="img/draft.png" class="max-width-500">

General structure of a draft.
:::

As the draft process is closely related to the parliamentary process, the id for this process is given by jolux:parliamentDraftId:

:::{admonition} jolux:parliamentDraftId
:class: note
:name: parliamentDraftId
The data property **jolux:parliamentDraftId** is used to connect a [jolux:Draft](#Draft) to the identifier of the parliamentary process that leads to the new legal resource.
:::

For each draft, there is also a draft id registered that is also part of the URI but is given as separate property for easier access:

:::{admonition} jolux:draftId
:class: note
:name: draftId
The data property **jolux:draftId** is used to connect a [jolux:Draft](#Draft) to the identifier of the draft.
:::

The main result of the draft process is the draft law that is connected to the draft via jolux:hasResultingLegalResource and is from type jolux:Act:

:::{admonition} jolux:hasResultingLegalResource
:class: note
:name: hasResultingLegalResource
The object property **jolux:hasResultingLegalResource** is used to connect a [jolux:Draft](#Draft) to the resulting legal resource that is of type [jolux:Act](#Act). The draft law enters afterward the parliamentary process.
:::

The different tasks of the draft process are connected to the draft via jolux:draftHasLegislativeTask:

:::{admonition} jolux:draftHasLegislativeTask
:class: note
:name: draftHasLegislativeTask
The object property **jolux:draftHasLegislativeTask** is used to connect a [jolux:Draft](#Draft) to the different legislative tasks that are part of the draft process.
:::

## Datatype Properties

- [jolux:parliamentDraftId](#parliamentDraftId)
- [jolux:draftId](#draftId)

## Object Properties

Object properties that point to an individual:

- [jolux:hasResultingLegalResource](#hasResultingLegalResource)
- [jolux:draftHasLegislativeTask](#draftHasLegislativeTask)

## SPARQL Examples

The following SPARQL query retrieves the 10 latest drafts that involve a consultation process and have a published draft law:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>

SELECT DISTINCT ?draft ?date WHERE {
  ?draft a jolux:Draft ;
         jolux:draftHasLegislativeTask ?task ;
         jolux:hasResultingLegalResource/jolux:dateDocument ?date .
  ?task jolux:legislativeTaskType <https://fedlex.data.admin.ch/vocabulary/type-projet/1> . 
} ORDER BY DESC(?date) LIMIT 10
```

The following SPARQL query retrieves all drafts with their resulting legal resource and the type and date of the resulting legal resource, ordered by date of the resulting legal resource:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT DISTINCT * WHERE {

  ?draft a jolux:Draft;
         jolux:parliamentDraftId ?CuriaId ;
         jolux:hasResultingLegalResource ?act .
  ?act jolux:typeDocument/skos:prefLabel ?type ;
                         jolux:dateDocument ?date .
      
      FILTER(lang(?type) = "de")
  
} ORDER BY DESC(?date)
```
