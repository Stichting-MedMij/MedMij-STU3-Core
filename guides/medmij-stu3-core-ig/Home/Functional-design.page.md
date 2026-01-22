---
topic: FO
---

# Functional design

## General


## Granular exchange

### Ambitie
Our ambition is to exchange healthcare data in a granular (modular) way within the frameworks of the MedMij Agreements System (MedMij Afsprakenstelsel), taking into account the principles of reuse, privacy flexibility, and scalability. This document explains the application using the domains Dental Care and Long-Term Care. The focus is on “collecting” data (Verzamelen).

### Principles
- Each data service is linked to one or more FHIR profiles, based on a zib or another clinical concept (such as ASA score).
- We apply two layers: cross-domain (MedMij-core) and domain-specific data services.
    - Cross-domain data services: one data service per clinical concept, reusable across care domains;
    - MedMij-core is more than the sum of data services: it also defones the working approach around granular exchange and other MedMij-wide topics that belong in an IG.
- Domain-specific data services: derived data services that tailor a data service from MedMij-core to a specific domain, or data services that apply exclusively within a specific domain.
- Context (e.g., care type, care setting, performer, source, etc.) is provided in the FHIR resources via elements such as .subject, .effective[x], and .performer, and via the Provenance resource. Care type is made available via .meta.tag. Care type is the category of the organization responsible for the delivered care (e.g., dental practice, hospital). It helps citizens and systems interpret the origin and context of data.
- The MedMij Healthcare Provider List (Zorgaanbiederslijst) and the OAuthClient list (OCL) determine which data services are available per provider and supported by the DVP. We call this the capability of an actor. In the MedMij network, the following actors are active:
    - DVP
    - DVA in combination with the healthcare provider
    - Citizen
- The DVP determines the set of data services to retrieve.
    - No additional query parameter for domain is required. The FHIR requests remain standard search queries per FHIR resource.

### Objectives
- Provide patients (via DVP) access to data that is relevant for a specific care domain (such as Long-Term Care or Dental Care).
- Exchange data granularly between DVA (healthcare provider) and DVP (PHE), aligned with what is actually supported per healthcare provider.

### Benefits of this approach
- Flexible and scalable (no bundled BgZ or BgLZ data services needed);
- Better alignment between DVP capability (OAuthClient list) and DVA offering (Healthcare Provider List);
- Context remains available via standard FHIR fields, such as .meta.tag and references, or via the Provenance resource;
- Responsibility for orchestration lies with the DVP, consistent with MedMij principles.

### Cross-domain and domain-specific clinical concepts
This chapter describes how cross-domain and domain-specific clinical concepts are defined and published as separate data services. It focuses on representation in the Healthcare Provider List (ZAL) and the Data Service Name List (GNL) of MedMij. It aligns with the two-layer model, consisting of MedMij-core (for generic, cross-domain concepts) and domain-specific data services (for concepts that apply only within a domain or require additional specialization).

Cross-domain:
Purpose: MedMij-core contains zibs or structured datasets that are cross-domain. These are published as generic data services on the Healthcare Provider List.


Domain-specific:
Purpose: zibs that apply only within one domain, and zibs that are cross-domain but have a different functional interpretation or profile implementation across domains, are registered per domain on the ZAL. Examples: Oral Healthcare – Oral Hygiene, Long-Term Care – Daily Report.


#### Publication in the Healthcare Provider List (ZAL) and Data Service Name List (GNL)
ID:
- Data service number

Display name:
- Cross-domain: MedMij‑core - <KlinischConceptNaam>.
    - Example Medmij-core - ASA-score
- Domain-specific: <Domein> - <KlinischConceptNaam>.
    - Example Mondzorg - Mondhygiëne

Version:
- FHIR version
    - Example: STU3
- The functional version of the clinical concept
    - Example: v3.2(2020)

Table 1: Cross-domain data services Oral Healthcare and Long-Term Care

| Display name | Canonical URL | FHIR version | Functional version|
| --- | --- | --- | --- |
| MedMij-core-Patient | [nl-core-patient](https://simplifier.net/nictizstu3-zib2017/nl-core-patient) | STU3 | v3.1(2017) |
| MedMij-core-Zorgaanbieder | [nl-core-organization](https://simplifier.net/nictizstu3-zib2017/nl-core-organization) | STU3 | v3.1(2017) |
| MedMij-core-Zorgverlener | [nl-core-practitioner](https://simplifier.net/nictizstu3-zib2017/nl-core-practitioner) | STU3 | v3.2(2017) |
| MedMij-core-Bloeddruk | [Zib-BloodPressure](https://simplifier.net/nictizstu3-zib2017/zib-bloodpressure) | STU3 | v3.1(2017) |
| MedMij-core-Lichaamsgewicht | [Zib-BodyWeight](https://simplifier.net/nictizstu3-zib2017/zib-bodyweight) | STU3 | v3.1(2017) |
| MedMij-core-Lichaamslengte | [Zib-BodyHeight](https://simplifier.net/nictizstu3-zib2017/zib-bodyheight) | STU3 | v3.1(2017) |
| MedMij-core-Alert | [Zib-Alert](https://simplifier.net/nictizstu3-zib2017/zib-alert) | STU3 | v3.1(2017) |
| MedMij-core-Voedingsadvies | [Zib-NutritionAdvice](https://simplifier.net/nictizstu3-zib2017/zib-alert) | STU3 | v3.1(2017) |
| MedMij-core-Lichaamstemperatuur | [Zib-BodyTemperature](https://simplifier.net/nictizstu3-zib2017/zib-bodytemperature) | STU3 | v3.1(2017) |
| MedMij-core-Vochtbalans | [Zib-FluidBalance](https://simplifier.net/nictizstu3-zib2017/zib-fluidbalance) | STU3 | v1.0(2017) |
| MedMij-core-Ademhaling | [Zib-Respiration](https://simplifier.net/nictizstu3-zib2017/zib-respiration) | STU3 | v3.1(2017) |
| MedMij-core-Polsfrequentie | [Zib-PulseRate](https://simplifier.net/nictizstu3-zib2017/zib-respiration) | STU3 | v3.1(2017) |
| MedMij-core-Betaler | [Zib-Payer](https://simplifier.net/nictizstu3-zib2017/zib-payer) | STU3 | v3.1(2017) |
| MedMij-core-Contact | [Zib-Encounter] | STU3 | v3.1(2017) |

Table 2: Domain-specific data services Oral Healthcare and Long-Term Care
| Display name | Canonical URL | FHIR version | Functional version|
| --- | --- | --- | --- |
| Long-Term care nursingreport| [nl-core-nursingreport] | STU3 | Unknown |


### Metatags for care type
Purpose: .meta.tag indicates for each exchanged data element which type of healthcare provider is responsible (e.g., “dental and maxillofacial surgery,” “primary care,” “pharmacy”). This makes the origin and context clear for the citizen and helps DVPs with filtering, grouping, and logging. Metatags are included with every FHIR resource. For the definition of care type, we use VEKTIS AGB (table COD016), which encodes the specialty of the (performing) healthcare provider. For example code 1100: Dental specialists in oral diseases and oral and maxillofacial surgery.

How to read the metatag:
- 11 = the provider type
- Qualification (optional): in addition to the type, a qualification code can be provided for further clarification of the organization category. Example: Military hospitals - 0630.