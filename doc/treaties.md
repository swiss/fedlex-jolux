# International Treaties

:::{admonition} Under construction
:class: danger
This sub-page is under heavy construction...
:::


According to [Termdat](https://www.termdat.bk.admin.ch/entry/109678), an international treaty is an "international agreement concluded between states in written form and governed by international law, whether embodied in a single instrument or in two or more related instruments and whatever its particular designation".

:::{admonition} Hint for legal laypersons
:class: hint
International Treaties are sometimes approbated into the [Official Compilation](official_compilation.md).
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

Entities of class jolux:TreatyProcess have different jolux:TaskForTreaty added.

:::{admonition} jolux:TaskForTreaty
:class: note
:name: TaskForTreaty
The owl:Class **jolux:TaskForTreaty** is used as class for all the tasks that are necessary for concluding a treaty.
:::

The possible types of tasks are given in the section [SPARQL Example](#sparql-example).

The result of an international treaty is always a jolux:TreatyDocument.

:::{admonition} jolux:TreatyDocument
:class: note
:name: TreatyDocument
The owl:Class **jolux:TreatyDocument** is used for the resulting treaty of the [jolux:TreatyProcess](#TreatyProcess).
:::

## SPARQL Example

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
