# Consultations

A *consultation* is the process of asking for feedback on a draft of a legislative resource.

## Example

Throughout this sub-page, the following consultation with a possible impact on the federal constitution is used as an example:

- URI: https://fedlex.data.admin.ch/eli/dl/proj/2022/59/cons_1
- URL: https://www.fedlex.admin.ch/de/consultation-procedures/ended/2022#https://fedlex.data.admin.ch/eli/dl/proj/2022/59/cons_1
- [Metadata viewer](https://fedlex.data.admin.ch/de-CH/metadata?value=https:%2F%2Ffedlex.data.admin.ch%2Feli%2Fdl%2Fproj%2F2022%2F59%2Fcons_1)

## URI

The URI of a consultation contains the following parts:

- Standard namespace and path: `https://fedlex.data.admin.ch/eli/`
- the part `dl/proj` is used as path for all consultations (dl stands for draft legislation and proj for project)
- `YYYY/` is the year of the consultation
- `ID` an identifier that has no specific meaning but restarts every year
- `cons_1` is used for every consultation

## General Structure

Every consultation is of type jolux:Consultation.

:::{admonition} jolux:Consultation
:class: note
:name: Consultation
The owl:Class **jolux:Consultation** is used for consultations.
:::

A jolux:Consultation has a foreseen impact to a legislative resource. This is given by jolux:foreseenImpactToLegalResource:

:::{admonition} jolux:foreseenImpactToLegalResource
:class: note
:name: foreseenImpactToLegalResource
The object property **jolux:foreseenImpactToLegalResource** is used to connect a [jolux:Consultation](#Consultation) to a [jolux:Work](#Work) (usually a [jolux:ConsolidationAbstract](#ConsolidationAbstract)).
:::

The jolux:Consultation is structured into different jolux:ConsultationTask that are connected to the jolux:Consultation with the object property jolux:hasSubTask:

:::{admonition} jolux:ConsultationTask
:class: note
:name: ConsultationTask
The owl:Class **jolux:ConsultationTask** is used for the different tasks of a jolux:Consultation.
:::

:::{admonition} jolux:hasSubTask
:class: note
:name: hasSubTask
The object property **jolux:hasSubTask** is used to connect a [jolux:Consultation](#Consultation) to a [jolux:ConsultationTask](#ConsultationTask).
:::

The following figure shows the general structure of a consultation:

:::{figure-md} fig_consultation

<img src="img/consultation.png" class="max-width-500">

General structure of a consultation.
:::

There are four types of jolux:ConsultationTask:

- jolux:ConsultationPreparation
- jolux:ConsultationPhase
- jolux:PositionStatementPublication
- jolux:ResultOfAConsultationPublication

:::{admonition} jolux:ConsultationPreparation
:class: note
:name: ConsultationPreparation
The owl:Class **jolux:ConsultationPreparation** is used for the preparation of a consultation. It contains mainly some metadata. It is not always present for every consultation.
:::

:::{admonition} jolux:ConsultationPhase
:class: note
:name: ConsultationPhase
The owl:Class **jolux:ConsultationPhase** is used to form the actual object of the consultation.
:::

The following figure shows the structure of the jolux:ConsultationPhase:

:::{figure-md} fig_consultation_phase

<img src="img/consultation_phase.png">

Structure of a jolux:ConsultationPhase. There are multiple documents of type jolux:DraftRelatedDocument.
:::

The most important properties for a jolux:ConsultationPhase are:

- jolux:opinionIsAboutDraftDocument
- jolux:opinionHasDraftRelatedDocument

:::{admonition} jolux:opinionIsAboutDraftDocument
:class: note
:name: opinionIsAboutDraftDocument
The property **jolux:opinionIsAboutDraftDocument** is used to connect the actual consultation document to the jolux:ConsultationPhase.
:::

:::{admonition} jolux:opinionHasDraftRelatedDocument
:class: note
:name: opinionHasDraftRelatedDocument
The property **jolux:opinionHasDraftRelatedDocument** is used to connect the accompanying documents to the different jolux:ConsultationTask (e.g. jolux:ConsultationPhase).
:::

All the jolux:DraftRelatedDocument from the jolux:ConsultationPhase have a jolux:draftProcessDocumentType that has the supercategory https://fedlex.data.admin.ch/vocabulary/draft-document-type/10

The most important documents of the jolux:ConsultationPhase have the following entries from the [draft document types vocabulary](#draft-document-types):

- the actual draft document: https://fedlex.data.admin.ch/vocabulary/draft-document-type/11
- the explanatory report: https://fedlex.data.admin.ch/vocabulary/draft-document-type/12
- The recipients list: https://fedlex.data.admin.ch/vocabulary/draft-document-type/14 

:::{admonition} jolux:PositionStatementPublication
:class: note
:name: PositionStatementPublication
The owl:Class **jolux:PositionStatementPublication** is used to publish the complete collected position statements of the consultation recipients.
:::

All the jolux:DraftRelatedDocument from the jolux:PositionStatementPublication have a jolux:draftProcessDocumentType that has the supercategory https://fedlex.data.admin.ch/vocabulary/draft-document-type/20

The most important document of the jolux:PositionStatementPublication has the following entry from the [draft document types vocabulary](#draft-document-types):

- the complete collected opinions from the consultation recipients: https://fedlex.data.admin.ch/vocabulary/draft-document-type/21

:::{admonition} jolux:ResultOfAConsultationPublication
:class: note
:name: ResultOfAConsultationPublication
The owl:Class **jolux:ResultOfAConsultationPublication** is used to publish the result of a consultation in form of a report of the consultation publishing authority.
:::

All the jolux:DraftRelatedDocument from the jolux:ResultOfAConsultationPublication have a jolux:draftProcessDocumentType that has the supercategory https://fedlex.data.admin.ch/vocabulary/draft-document-type/30

The most important document of the jolux:ResultOfAConsultationPublication has the following entry from the [draft document types vocabulary](#draft-document-types):

- the results report: https://fedlex.data.admin.ch/vocabulary/draft-document-type/31

## Datatype Properties

### jolux:Consultation

The [following SPARQL query](https://fedlex.data.admin.ch/de-CH/sparql#query=PREFIX+jolux%3A+%3Chttp%3A%2F%2Fdata.legilux.public.lu%2Fresource%2Fontology%2Fjolux%23%3E%0ASELECT+DISTINCT+%3Fp+WHERE+%7B%0A%0A%09%3Fcon+a+jolux%3AConsultation%3B%0A++++++%3Fp+%3Fo.%0A++%0A++FILTER(isLiteral(%3Fo))%0A%7D&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=%2Fsparqlendpoint&requestMethod=POST&tabTitle=Query&headers=%7B%7D&outputFormat=table) shows all different datatype properties for jolux:Consultation. These properties are self explanatory.

### jolux:ConsultationTask

- [jolux:eventEndDate](#eventEndDate)
- [jolux:eventStartDate](#eventStartDate)

## Object Properties

### jolux:Consultation

Object properties that point to a vocabulary entry:

- [jolux:consultationStatus](#consultation-status)
- [jolux:isOpinionOf](#legal-institution)

Object properties that point to an individual:

- [jolux:foreseenImpactToLegalResource](#foreseenImpactToLegalResource)
- [jolux:hasSubTask](#hasSubTask)

### jolux:ConsultationTask

Object properties that point to a vocabulary entry:

- [jolux:institutionInChargeOfTheEvent](#legal-institution)
- [jolux:institutionInChargeOfTheEventLevel2](#legal-institution)

Object properties that point to an individual:

- [jolux:opinionHasDraftRelatedDocument](#opinionHasDraftRelatedDocument)
- [jolux:opinionIsAboutDraftDocument](#opinionIsAboutDraftDocument)

## SPARQL Examples

The following SPARQL query shows all the jolux:Consultation with their title in French that have a foreseen impact to the federal constitution:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT * WHERE {

    ?consultation a jolux:Consultation;
        jolux:foreseenImpactToLegalResource <https://fedlex.data.admin.ch/eli/cc/1999/404>;
        jolux:eventTitle ?title.
  
    FILTER(lang(?title) = "fr")
}
```

The following SPARQL query shows all the planned consultations and the one that are in preparation with their title in German:

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT * WHERE {

	?consultation a jolux:Consultation;
        jolux:eventTitle ?title;
        jolux:consultationStatus ?status.
  
  VALUES ?status {
    <https://fedlex.data.admin.ch/vocabulary/consultation-status/0>
    <https://fedlex.data.admin.ch/vocabulary/consultation-status/1>
  }
   
  FILTER(lang(?title) = "de")
  }
```

The following SPARQL query gives the links to the Italian result reports of the 10 last closed consultations.

```sparql
PREFIX jolux: <http://data.legilux.public.lu/resource/ontology/jolux#>
SELECT ?title ?date ?url WHERE {

	?consultation a jolux:Consultation;
        jolux:eventTitle ?title;
        jolux:hasSubTask ?result_phase, ?consultation_phase.
  
    FILTER(lang(?title) = "it")

    ?result_phase a jolux:ResultOfAConsultationPublication;
        jolux:opinionHasDraftRelatedDocument ?result.
    ?result jolux:draftProcessDocumentType <https://fedlex.data.admin.ch/vocabulary/draft-document-type/31>;
        jolux:isRealizedBy ?expression.
    ?expression jolux:language <http://publications.europa.eu/resource/authority/language/ITA>;
        jolux:isEmbodiedBy ?manifestation.
    ?manifestation jolux:userFormat <https://fedlex.data.admin.ch/vocabulary/user-format/pdf-a>;
        jolux:isExemplifiedBy ?url.
    
    ?consultation_phase a jolux:ConsultationPhase;
          jolux:eventEndDate ?date.

} ORDER BY DESC(?date)
LIMIT 10
```
