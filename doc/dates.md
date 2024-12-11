# Dates

Concerning legislation, there are a number of dates that are important during the legislative process. All the date literals are modelled with datatype `xsd:date`. The following list tries to give the most important date properties according the lifetime of a legal resource.

:::{admonition} jolux:dateDocument
:class: note
:name: dateDocument
The property jolux:dateDocument is used to indicate the decision date of an act, or the date on which the document was adopted. For bills, where there is no formal adoption date, the Document Date is used as the reference date.
:::

:::{admonition} jolux:publicationDate
:class: note
:name: publicationDate
The property jolux:publicationDate denotes the date of first publication in one of the collections. If the same document is republished, this date does not change: it is always the date of the initial publication that is decisive. On the other hand, for consolidations, several publication dates may exist: each new publication of the file generates a new date.
:::

:::{admonition} Hint for legal laypersons
:class: hint
During introduction of a new law, there are two similar but different dates relevant: the date of the **entry into force** and the date of the **applicability** of the law. These two dates can differ. It can happen that the entry into force comes before the law is applicable. This is mainly to allow for preparing the necessary changes in the affected organizations. During this period of time there could be some transitional provisions in place.
:::

:::{admonition} jolux:dateEntryInForce
:class: note
:name: dateEntryInForce
The property jolux:dateEntryInForce denotes the date on which the law starts to have a legal effect (see above).
:::

:::{admonition} jolux:dateApplicability
:class: note
:name: dateApplicability
The property jolux:dateApplicability denotes the date from which a law is applicable (see above).
:::

:::{admonition} Hint for legal laypersons
:class: hint
During cancellation of a law, there are two similar but different dates relevant: the date of the **end of applicability** and the date of the **no longer in force**. The end of applicability is the last day where the law is applicable. The no longer in force date is the first day that the law has no more a legal effect. These two dates can differ in both direction. It could be that the law is first no more applicable and no longer in force later or vice versa.
:::

:::{admonition} jolux:dateEndApplicability
:class: note
:name: dateEndApplicability
The property jolux:dateEndApplicability denotes the last day where a law is applicable.
:::

:::{admonition} jolux:dateNoLongerInForce
:class: note
:name: dateNoLongerInForce
The property jolux:dateNoLongerInForce denotes the first day on which the law has no more a legal effect.
:::

## Special Dates

:::{admonition} jolux:legalResourceImpactHasDateEntryInForce
:class: note
:name: legalResourceImpactHasDateEntryInForce
The property jolux:legalResourceImpactHasDateEntryInForce denotes the effective date of an [jolux:LegalResourceImpact](#LegalResourceImpact).
:::
