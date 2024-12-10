# Dates

Concerning legislation, there are a number of dates that are important during the legislative process. All the date literals are modelled with datatype `xsd:date`.

## Dates relevant to jolux:Work

On the abstraction level of [jolux:Work](#Work), the following dates are important:

:::{admonition} jolux:publicationDate
:class: note
:name: publicationDate
The property jolux:publicationDate denotes the date of first publication in one of the collections. If the same document is republished, this date does not change: it is always the date of the initial publication that is decisive.

On the other hand, for consolidations, several publication dates may exist: each new publication of the file generates a new date.
:::

:::{admonition} jolux:dateEntryInForce
:class: note
:name: dateEntryInForce
The property jolux:dateEntryInForce denotes the date on which the law takes legal effect.
:::

:::{admonition} jolux:dateNoLongerInForce
:class: note
:name: dateNoLongerInForce
The property jolux:dateNoLongerInForce denotes the date on which the law stops to have a legal effect.

Compared to [jolux:dateEndApplicability](#dateEndApplicability) this denotes the first day where the jolux:work is no longer in force.
:::

:::{admonition} jolux:dateDocument
:class: note
:name: dateDocument
The jolux:dateDocument property is used to indicate the decision date of an act, or the date on which the document was adopted.

For bills, where there is no formal adoption date, the Document Date is used as the reference date.
:::

## Dates relevant to jolux:Consolidation

:::{admonition} jolux:dateApplicability
:class: note
:name: dateApplicability
The property jolux:dateApplicability denotes the date from which a jolux:Consolidation takes effect.
:::

:::{admonition} jolux:dateEndApplicability
:class: note
:name: dateEndApplicability
The property jolux:dateEndApplicability denotes the date from which a jolux:Consolidation or a jolux:ConsolidationAbstract no longer takes effect. 

Compared to [jolux:dateNoLongerInForce](#dateNoLongerInForce) this denotes the last day where the consolidation is applicable.
:::

## Dates relevant to jolux:LegalResourceImpact

:::{admonition} jolux:legalResourceImpactHasDateEntryInForce
:class: note
:name: legalResourceImpactHasDateEntryInForce
The property jolux:legalResourceImpactHasDateEntryInForce denotes the effective date of an jolux:LegalResourceImpact.
:::
