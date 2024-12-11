# International Treaties

According to [Termdat](https://www.termdat.bk.admin.ch/entry/109678), an international treaty is an "international agreement concluded between states in written form and governed by international law, whether embodied in a single instrument or in two or more related instruments and whatever its particular designation".

:::{admonition} Hint for legal laypersons
:class: hint
International Treaties are sometimes but not always approbated into the [Official Compilation](official_compilation.md).
:::

## Example

Throughout this sub-page, the following treaty process is used as an example.

- URI: https://fedlex.data.admin.ch/eli/treaty/2024/0311
- URL: https://www.fedlex.admin.ch/eli/treaty/2024/0311/de
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Feli%2Ftreaty%2F2024%2F0311)

## URI

The URI of a treaty process contains the following parts:

- Standard namespace and path: `https://fedlex.data.admin.ch/eli/`
- the part `treaty/` shows that it is about a treaty
- `YYYY/` is the year of the publication
- `ID` an identifier that has no specific meaning

## General Structure

Treaties evolve around a jolux:TreatyProcess.

:::{admonition} jolux:TreatyProcess
:class: note
:name: TreatyProcess
The owl:Class **jolux:TreatyProcess** is used group the important elements of an international treaty.
:::

The following figure shows the general structure of a treaty process:

:::{figure-md} treaty_process

<img src="img/treaty_process.png">

General structure of a treaty process.
:::

A jolux:TreatyProcess is described by the following properties:

:::{admonition} jolux:bilateral
:class: note
:name: bilateral
The datatype property **jolux:bilateral** is used to classify whether a treaty is bilateral. The datatype is xsd:boolean.
:::

:::{admonition} jolux:titleTreaty
:class: note
:name: titleTreaty
The datatype property **jolux:titleTreaty** links to the title of the treaty. The datatype is rdf:langString.
:::

:::{admonition} jolux:treatySignatureDate
:class: note
:name: treatySignatureDate
The datatype property **jolux:treatySignatureDate** links to the date of the signature of the treaty. The datatype is xsd:date.
:::

:::{admonition} jolux:treatySignaturePlace
:class: note
:name: treatySignaturePlace
The datatype property **jolux:treatySignaturePlace** links to the place of the signature of the treaty. The datatype is xsd:string.
:::

Entities of class jolux:TreatyProcess have different jolux:TaskForTreaty added.

:::{admonition} jolux:TaskForTreaty
:class: note
:name: TaskForTreaty
The owl:Class **jolux:TaskForTreaty** is used as class for all the tasks that are necessary for concluding a treaty.
:::

The tasks are linked to the process via jolux:treatyProcessHasTask.

:::{admonition} jolux:treatyProcessHasTask
:class: note
:name: treatyProcessHasTask
The object property **jolux:treatyProcessHasTask** links a jolux:TreatyProcess to a jolux:TaskForTreaty.
:::

The possible types of tasks are given in the section [SPARQL Example](#sparql-example).

The result of an international treaty is always a jolux:TreatyDocument.

:::{admonition} jolux:TreatyDocument
:class: note
:name: TreatyDocument
The owl:Class **jolux:TreatyDocument** is used for the resulting treaty of the [jolux:TreatyProcess](#TreatyProcess).
:::

The jolux:TreatyDocument is linked via jolux:treatyProcessHasResultingTreatyDocument.

:::{admonition} jolux:treatyProcessHasResultingTreatyDocument
:class: note
:name: treatyProcessHasResultingTreatyDocument
The object property **jolux:treatyProcessHasResultingTreatyDocument** links a jolux:TreatyProcess to a jolux:TreatyDocument.
:::

If there is an approbation into the [Official Compilation](official_compilation.md) The approbation act is linked to the treaty process via jolux:approbationAct.

:::{admonition} jolux:approbationAct
:class: note
:name: approbationAct
The object property **jolux:approbationAct** links a jolux:TreatyProcess to a jolux:Act in the [Official Compilation](official_compilation.md).
:::

## Datatype Properties for jolux:TreatyProcess

- [jolux:bilateral](#bilateral)
- [jolux:titleTreaty](#titleTreaty)
- [jolux:treatySignatureDate](#treatySignatureDate)
- [jolux:treatySignaturePlace](#treatySignaturePlace)

## Object Properties for jolux:TreatyProcess

Object properties that point to a vocabulary entry:

- [jolux:treatySubject](#treaty-subject-themes)
- [jolux:treatyType](#treaty-types)
- [jolux:treatyPartyCountry](#countries)
- [jolux:classifiedByTaxonomyEntry](#legal-taxonomy)

Object properties that point to an individual:

- [jolux:treatyProcessHasTask](#treatyProcessHasTask)
- [jolux:treatyProcessHasResultingTreatyDocument](#treatyProcessHasResultingTreatyDocument)
- [jolux:approbationAct](#approbationAct)  

## SPARQL Examples

The following SPARQL query shows all the different classes that are used on a jolux:TaskForTreaty to further segment these tasks:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT DISTINCT ?class WHERE {
  ?task a jolux:TaskForTreaty;
        a ?class.
  FILTER(?class != <http://data.legilux.public.lu/resource/ontology/jolux#Event>)
}
```

The class jolux:Event is filtered because all jolux:TaskForTreaty are also jolux:Event.
