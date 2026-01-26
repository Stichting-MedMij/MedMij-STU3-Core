---
topic: GranularExchange
---

# Granular exchange

## Ambition and goals
It is the ambition of MedMij to exchange healthcare data in a granular (modular) way as much as possible, within the frameworks of the [MedMij Afsprakenstelsel](https://afsprakenstelsel.medmij.nl/). This ensures a flexible and scalable approach with respect to data services, as less or possible no 'bundled' data services are needed, such as the BgZ or BgLZ.

Granular exchange happens between DVA (healthcare provider) and DVP (PHE), and takes into account which data is actually available and supported by both parties. Moreover, it provides patients (via DVP) access to data that is relevant for a specific care domain (such as Long-term Healthcare).

This page explains the way in which granular exchange takes place in the context of MedMij. Note that the focus of granular exchange is on collecting data (i.e. the use cases of type 'Verzamelen').

## Principles
- Each granular data service is linked to a single Clinical Information Model (CIM), which is often a zib but could possibly be any other functional model. A CIM is either domain overarching or only applicable to a single domain. Technically, each CIM corresponds to one or more FHIR profiles.
- We distinguish two types of granular data services:
    - *Cross-domain data services* are part of MedMij Core and are reusable across care domains.
    - *Domain-specific data services* are data services that are only applicable within a certain domain, and are specified (both functionally and technically) in the corresponding IG on domain level (e.g the IG for Long-term Healthcare). These data services might be derived from a cross-domain data service by tailoring it to a specific domain. Note that there also exist non-granular domain-specific data services (i.e. the 'traditional' data services, such as Medication Process or Documents), but these are out of scope for this section.
- For each granular data service, the context of the data that is exchanged (e.g. care type, care setting, clinically relevant date/time, performer, source) is mainly provided in the FHIR resource(s) corresponding to the CIM, via elements such as `.subject`/`.patient`, `.effectiveDateTime`, `.performer` and `.author`. Moreover, the Provenance resource might be used to specify contextual elements which cannot be conveyed in those FHIR resources. In particular, the care type is made available via `.meta.tag`, which is described in more detail below. The care type categorizes the healthcare provider responsible for the delivered care, or more specifically, it indicates the specialty of the department and/or health professional that delivered care (e.g. dental care, hospital, general practitioner). It helps patients and systems to interpret the origin and context of data.
- The MedMij Healthcare Provider List (Zorgaanbiederslijst, abbreviated ZAL) and OAuth Client List (OCL) determine which granular data services are available per healthcare provider and which are supported by the DVP, respectively. The set of available/supported data services is called the *capability* of the actor. By taking into account the capabilities of both DVA and DVP better alignment is possible.
- The DVP determines the set of granular data services to retrieve. Hence, the responsibility for orchestration lies with the DVP, consistent with the MedMij principles. Moreover, the FHIR queries for retrieving the underlying data remain unchanged, as no additional search parameter for domain is required.

## Publication of granular data services
This section describes how cross-domain and domain-specific CIMs are defined and published as separate data services. It focuses on the representation of these data services in the ZAL and the Data Service Name List (Gegevendienstnamenlijst, abbreviated GNL) of MedMij. It aligns with the two-layer model, consisting of cross-domain and domain-specific data services.

Cross-domain data services are published as generic data services on the ZAL, and are given a display name of the form 'MedMij Core - [CIM name in Dutch]', for instance 'MedMij Core - Bloeddruk'. On the other hand, domain-specific data services are registered on the ZAL per domain. This is reflected in the display name, which is of the form '[Domain name in Dutch] - [CIM name in Dutch]', for instance 'Langdurige Zorg - Dagrapportage'.

The following metadata is added to the ZAL and GNL for each granular data service:
- The *Id* contains the data service number. The exact format of this number for granular data services still needs to be decided upon.
- The *Data service name* (Gegevensdienstnaam) is the display name of the data service, and follows the formats described above.
- The *FHIR version* states in what version of FHIR the profile(s) corresponding to the CIM have been created. For all data services mentioned in or linked to from this IG, the FHIR version will be *STU3*.
- The *functional version* indicates the version of the CIM. For a CIM that is a zib, this version is of the form 'v*x.y*([zib publication])', e.g. 'v3.1(2017)'. For CIMs that are defined by MedMij as a Logical Model, the version of the corresponding FHIR package is suitable as the functional version.

## Overview of granular data services
The table below gives an overview of all granular data services that use FHIR STU3 in their technical implementation. Hence the FHIR version for these data services is set to *STU3*.

| Data service name | Functional version| FHIR profile(s) |
| --- | --- | --- |
| MedMij Core - Patient | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/nl-core-patient](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018966) |
| MedMij Core - Zorgaanbieder | v3.1.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/nl-core-organization](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018965) |
| MedMij Core - Zorgverlener | v3.2(2017) | [http://nictiz.nl/fhir/StructureDefinition/nl-core-practitioner](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018968) <br/> [http://nictiz.nl/fhir/StructureDefinition/nl-core-practitionerrole](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018969) |
| MedMij Core - Bloeddruk | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-BloodPressure](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019007) |
| MedMij Core - Lichaamsgewicht | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-BodyWeight](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019010) |
| MedMij Core - Lichaamslengte | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-BodyHeight](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019008) |
| MedMij Core - Alert | v3.2(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-Alert](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019001) |
| MedMij Core - Voedingsadvies | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-NutritionAdvice](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019091) |
| MedMij Core - Lichaamstemperatuur | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-BodyTemperature](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019009) |
| MedMij Core - Vochtbalans | v1.0(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-FluidBalance](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019038) |
| MedMij Core - Ademhaling | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019114) |
| MedMij Core - Polsfrequentie | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-PulseRate](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019113) |
| MedMij Core - Betaler | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-Payer](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019098) |
| MedMij Core - Contact | v3.1(2017) | [http://nictiz.nl/fhir/StructureDefinition/zib-Encounter](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019026) |
| Langdurige Zorg - Dagrapportage | TBD | [https://nuts.nl/fhir/StructureDefinition/nl-core-nursingreport](https://simplifier.net/anw/nl-core-nursingreport) |

**Table 1: Granular data services**

## Metatags for care type
Purpose: `.meta.tag` indicates for each exchanged data element which type of healthcare provider is responsible (e.g., “dental and maxillofacial surgery,” “primary care,” “pharmacy”). This makes the origin and context clear for the citizen and helps DVPs with filtering, grouping, and logging. Metatags are included with every FHIR resource. For the definition of care type, we use VEKTIS AGB (table COD016), which encodes the specialty of the (performing) healthcare provider. For example code 1100: Dental specialists in dental diseases and dental and maxillofacial surgery.

How to read the metatag:
- 11 = the provider type
- Qualification (optional): in addition to the type, a qualification code can be provided for further clarification of the organization category. Example: Military hospitals - 0630.