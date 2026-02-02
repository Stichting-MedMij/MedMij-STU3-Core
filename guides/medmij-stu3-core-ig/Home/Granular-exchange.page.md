---
topic: GranularExchange
---

# Granular exchange

## Ambition and goals
It is the ambition of MedMij to exchange healthcare data in a granular (modular) way as much as possible, within the frameworks of the [MedMij Afsprakenstelsel](https://afsprakenstelsel.medmij.nl/). This ensures a flexible and scalable approach with respect to data services, as less or possible no 'bundled' data services are needed, such as the BgZ or BgLZ.

Granular exchange happens between service provider in the healthcare providers domain (DVA) and personal health environment (PHE or DVP), and takes into account which data is actually available and supported by both parties. Moreover, it provides patients (via DVP) access to data that is relevant for a specific care domain (such as Long-term Healthcare).

This page explains the way in which granular exchange takes place in the context of MedMij. Note that the focus of granular exchange is on retrieving data (i.e. the function ['Verzamelen'](https://afsprakenstelsel.medmij.nl/asverplicht/mmverplicht/verzamelen)).

## Principles
- Each granular data service is linked to a single Clinical Information Model (CIM), which is often a zib but could possibly be any other functional model. A CIM is either domain overarching or only applicable to a single domain. Technically, each CIM corresponds to one or more FHIR profiles.
- We distinguish two types of granular data services:
    - *Cross-domain data services* are part of MedMij Core and are reusable across care domains.
    - *Domain-specific data services* are data services that are only applicable within a certain domain, and are specified (both functionally and technically) in the corresponding IG on domain level (e.g the IG for Long-term Healthcare). These data services might be derived from a cross-domain data service by tailoring it to a specific domain. Note that there also exist non-granular domain-specific data services (i.e. the 'traditional' data services, such as Medication Process or Documents), but these are out of scope for this section.
- For each granular data service, the context of the data that is exchanged (e.g. care type, care setting, clinically relevant date/time, performer, source) is mainly provided in the FHIR resource(s) corresponding to the CIM, via elements such as `.subject`/`.patient`, `.effectiveDateTime`, `.performer` and `.author`. Moreover, the Provenance resource might be used to specify contextual elements which cannot be conveyed in those FHIR resources. In particular, the care type is made available via `.meta.tag`, which is described in more detail below. The care type categorizes the healthcare provider responsible for the delivered care, or more specifically, it indicates the specialty of the department and/or health professional that delivered care (e.g. dental care, hospital, general practitioner). It helps patients and systems to interpret the origin and context of data.
- The MedMij Healthcare Provider List (Zorgaanbiederslijst, abbreviated ZAL) and OAuth Client List (OCL) determine which granular data services are available per healthcare provider and which are supported by the DVP, respectively. The set of available/supported data services is called the *capability* of the actor. By taking into account the capabilities of both DVA and DVP better alignment is possible.
- The DVP determines the set of granular data services to retrieve. Hence, the responsibility for orchestration lies with the DVP, consistent with the MedMij principles. Moreover, the FHIR queries for retrieving the underlying data remain unchanged, as no additional search parameter for domain is required.

## Publication of granular data services
This section describes how cross-domain and domain-specific CIMs are defined and published as separate data services. It focuses on the representation of these data services in the ZAL and the Data Service Name List (Gegevensdienstnamenlijst, abbreviated GNL) of MedMij. It aligns with the two-layer model, consisting of cross-domain and domain-specific data services.

Cross-domain data services are published as generic data services on the ZAL, and are given a display name of the form '[Function] MedMij Core - [CIM name in Dutch] ([Suffix]) [Data service version]', for instance 'Verzamelen MedMij Core - Bloeddruk (zib2017/STU3) 1.0.0'. The suffix is an optional addition to the data service name necessary to differentiate data services that have multiple variants (for instance, different functional versions or different FHIR versions). In case a granular data service corresponds to a zib, the corresponding baseline is used as suffix, e.g. 'zib2017/STU3'. 

On the other hand, domain-specific data services are registered on the ZAL per domain. This is reflected in the display name, which is of the form '[Function] [Domain name in Dutch] - [CIM name in Dutch] ([Suffix]) [Data service version]', for instance 'Verzamelen Langdurige Zorg - Dagrapportage 1.0.0'. 

Note that in this IG, mainly the English names for the granular data services are used.

The following metadata is added to the ZAL and GNL for each granular data service:
- The *Id* contains the data service number. The exact format of this number for granular data services still needs to be decided upon.
- The *Data service name* (Gegevensdienstnaam) is the display name of the data service, and follows the formats described above.

## Overview of granular data services
The table below gives an overview of all cross-domain granular data services that use FHIR STU3 in their technical implementation.

| Id | Data service name without version (English) | Data service name without version (Dutch) | Data service version|
| --- | --- | --- | --- |
| TBD | {{pagelink: Alert, text: Retrieve MedMij Core - Alert (zib2017/STU3)}} | Verzamelen MedMij Core - Alert (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: BloodPressure, text: Retrieve MedMij Core - Blood pressure (zib2017/STU3)}} | Verzamelen MedMij Core - Bloeddruk (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: BodyHeight, text: Retrieve MedMij Core - Body height (zib2017/STU3)}} | Verzamelen MedMij Core - Lichaamslengte (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: BodyTemperature, text: Retrieve MedMij Core - Body temperature (zib2017/STU3)}} | Verzamelen MedMij Core - Lichaamstemperatuur (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: BodyWeight, text: Retrieve MedMij Core - Body weight (zib2017/STU3)}} | Verzamelen MedMij Core - Lichaamsgewicht (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: FluidBalance, text: Retrieve MedMij Core - Fluid balance (zib2017/STU3)}} | Verzamelen MedMij Core - Vochtbalans (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: LivingSituation, text: Retrieve MedMij Core - Living situation (zib2017/STU3)}} | Verzamelen MedMij Core - Woonsituatie (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: NutritionAdvice, text: Retrieve MedMij Core - Nutrition advice (zib2017/STU3)}} | Verzamelen MedMij Core - Voedingsadvies (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: Payer, text: Retrieve MedMij Core - Payer (zib2017/STU3)}} | Verzamelen MedMij Core - Betaler (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: PulseRate, text: Retrieve MedMij Core - Pulse rate (zib2017/STU3)}} | Verzamelen MedMij Core - Polsfrequentie (zib2017/STU3) | 1.0.0-beta.1 |
| TBD | {{pagelink: Respiration, text: Retrieve MedMij Core - Respiration (zib2017/STU3)}} | Verzamelen MedMij Core - Ademhaling (zib2017/STU3) | 1.0.0-beta.1 |

**Table 1: Granular data services**

In the {{pagelink: GranularDataServiceIndex, text: Granular data service index}} each granular data service is described in more detail.

Note that domain-specific data services are not included here, as these are not part of MedMij STU3 Core. Instead, these are further specified within the respective IGs corresponding to their domain. For instance, the granular data service 'Long-term Healthcare - Nursing report' is described in the IG of [MedMij STU3 Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare).

## <a name="MustSupport"></a> Must Support

For each granular data service within the {{pagelink: GranularDataServiceIndex, text: Granular data service index}}, one or more elements of the corresponding FHIR resources might be indicated as *Must Support*. Such elements have to be supported, which means that the DVA SHALL convey these in the FHIR resource if the corresponding data is present in the source system, and that the DVP SHALL process (the information in) these elements.

Note that currently, it is only (textually) indicated in this IG whether an element needs to be supported, and no MedMij Core profiles that include the FHIR-native `mustSupport` flag have been created. One of the reasons for this approach is that some FHIR profiles in the [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) package are based on international profiles which use the `mustSupport` flag. These flags are inherited by the zib profiles, and would also be inherited by the MedMij Core profiles, thus making it unclear which elements need to be supported in the manner described above.

## Care type
In the transition from traditional to granular data services the context of exchanged data becomes less evident, as this context would normally be provided by the data service itself and its underlying use cases. In order to make the origin and context of data clear, the corresponding care type SHOULD be conveyed. This helps DVPs with filtering, grouping and logging, and makes it easier for citizens to interpret their data.

Technically, the `.meta.tag` element (which is available in all FHIR resources) is used to indicate the type of healthcare provider that is responsible for the data present in the respective FHIR resource (e.g. dental care, primary care, pharmacy). The care type is conveyed by using the medical specialties defined by Vektis (AGB) in table [COD016-VEKT](https://www.vektis.nl/standaardisatie/codelijsten/COD016-VEKT), and thus specifies the specialty of the department and/or health professional that delivered care. The codes within this table consist of four digits, of which the first two specify the healthcare provider type, while the last two are a further specification of that type. For instance, the code *0300* pertains to 'Medisch specialisten, niet nader gespecificeerd' (i.e. 'Medical specialists, not further specified'), while code *0320* pertains to 'Medisch specialisten, cardiologie' (i.e. 'Medical specialists, cardiology'). The corresponding FHIR Valueset is the {{link: http://decor.nictiz.nl/fhir/ValueSet/2.16.840.1.113883.2.4.3.11.60.40.2.17.2.4--20171231000000, title: AfdelingSpecialismeCodelijst}}, which is also used in the {{link: http://fhir.nl/fhir/StructureDefinition/nl-core-organization, title: nl-core-organization}} profile on `.type`.

Note that it is possible to include multiple `.meta.tag` elements in case (the data within) a resource pertains to multiple care types. Moreover, at least one `.meta.tag` SHOULD be added to each FHIR resource, provided the care type is known in the source system. If the care type is unknown in the source system for the data in a certain resource, no `.meta.tag` containing a code from the COD016-VEKT table is provided in that resource.

The code snippet below provides an example of the `.meta.tag` element.

```xml
<meta>
    <tag>
        <system value="urn:oid:2.16.840.1.113883.2.4.6.7"/>
        <code value="0320"/>
        <display value="Medisch specialisten, cardiologie"/>
    </tag>
</meta>
```