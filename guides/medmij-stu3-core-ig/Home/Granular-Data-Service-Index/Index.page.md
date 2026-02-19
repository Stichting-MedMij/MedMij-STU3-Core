---
topic: GranularDataServiceIndex
---

# Granular data service index

This index contains all active granular data services that use FHIR STU3 in their technical implementation. The following is specified for each data service:

- **Overview**
    - **Id** - the id of the data service that is used to uniquely define it in the [MedMij Catalogus](https://catalogus.medmij.nl/overzicht/actueel/actuele-catalogus).
    - **Data service name without version** - the name of the data service, both in English and Dutch, of which the Dutch one, appended with the data service version, is used in the MedMij Catalogus.
    - **Data service version** - the version assigned to the data service as a whole (not to be confused with the version of the corresponding functional model or the package version of the corresponding FHIR profiles).
    - **System role(s)** - the system roles corresponding to the different transactions within each data service. Each system is of the form 'MMC-[CIM abbreviation]\[Transaction indicator\](-[Suffix])-[Data service version]-FHIR', where:
        - 'MMC' refers to MedMij Core;
        - the CIM abbreviation consists of exactly two capital letters;
        - the Suffix is an optional addition, and is described in more detail {{pagelink: GranularExchange, text: here, anchor: PublicationGranularDataServices}};
        - the Transaction indicator is either 'R' or 'B', indicating a Retrieve (Dutch: Raadplegen) or Serve (Dutch: Beschikbaar stellen) transaction, respectively. The former transaction is intended for the PHR, while the latter is relevant for the XIS. As the corresponding transaction (group) can be derived from the system role, the transactions and transaction groups are not specified on the respective data service pages. Instead, these can be found in the [MedMij Catalogus](https://catalogus.medmij.nl/overzicht/actueel/actuele-catalogus).
    - **Relevant domain(s)** - the domains in which the granular data service is used, with links to the corresponding Simplifier projects.
- **Functional model**
    - **CIM** - the underlying Clinical Information Model, which is often a zib.
    - **Functional version** - the version of the CIM. For a CIM that is a zib, this version is of the form '*x.y*([zib publication])', e.g. '3.1(2017)'. For CIMs that are defined by MedMij as a Logical Model, the version of the corresponding FHIR package is suitable as the functional version.
    - Moreover, either a link to the functional model in ART-DECOR, or a Logical Model is included in this section.
- **Technical specification**
    - **FHIR profile(s)** - the FHIR profiles that are used to exchange the CIM.
    - **FHIR package** - the FHIR package in which the FHIR profiles have been published.
    - **FHIR version** - the version of FHIR in which the profiles corresponding to the CIM have been created; for all data services mentioned in or linked to from this IG, the FHIR version will be *STU3*.
    - **Search request** - the request to be executed by the PHR to retrieve the data corresponding to the granular data service.
    - **Must Support** - the elements that have to be supported in the manner described {{pagelink: GranularExchange, text: here, anchor: MustSupport}}.
    - **CapabilityStatement(s)** - the FHIR CapabilityStatements that describe the minimal requirements for a client or server to fulfill the corresponding transaction(s) defined within the data service.
    - Moreover, the relevant FHIR profiles are added in this section.