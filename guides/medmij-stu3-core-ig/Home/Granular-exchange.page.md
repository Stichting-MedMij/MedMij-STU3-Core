---
topic: GranularExchange
---

# Granular exchange

## Ambition and goals
It is the ambition of MedMij to exchange healthcare data in a granular (modular) way as much as possible, within the frameworks of the [MedMij Afsprakenstelsel](https://afsprakenstelsel.medmij.nl/). This ensures a flexible and scalable approach with respect to data services, as less or possibly no 'bundled' data services are needed, such as the BgZ or BgLZ.

Granular exchange happens between service provider in the healthcare providers domain (DVA) and service provider in the public domain (DVP), and takes into account which data is actually available and supported by both parties. Moreover, it provides patients (via their personal health record, abbreviated PHR) access to data that is relevant for a specific care domain (such as Long-term Healthcare).

This page explains the way in which granular exchange takes place in the context of MedMij. Note that the focus of granular exchange is on retrieving data (i.e. the function ['Verzamelen'](https://afsprakenstelsel.medmij.nl/asverplicht/mmverplicht/verzamelen)).

## Principles
- Each granular data service is linked to a single Clinical Information Model (CIM), which is often a zib but could possibly be any other functional model. A CIM is either domain overarching or only applicable to a single domain. Technically, each CIM corresponds to one or more FHIR profiles.
- We distinguish two types of granular data services:
    - *Cross-domain data services* are part of MedMij Core and are reusable across care domains.
    - *Domain-specific data services* are data services that are only applicable within a certain domain, and are specified (both functionally and technically) in the corresponding IG on domain level (e.g the IG for Long-term Healthcare). These data services might be derived from a cross-domain data service by tailoring it to a specific domain. Note that there also exist non-granular domain-specific data services (i.e. the 'traditional' data services, such as Medication Process or Documents), but these are out of scope for this section.
- For each granular data service, the context of the data that is exchanged (e.g. care type, care setting, clinically relevant date/time, performer, source) is mainly provided in the FHIR resource(s) corresponding to the CIM, via elements such as `.subject`/`.patient`, `.effectiveDateTime`, `.performer` and `.author`. Moreover, the Provenance resource might be used to specify contextual elements which cannot be conveyed in those FHIR resources. In particular, the care type is made available via `.meta.tag`, which is described in more detail {{pagelink: GranularExchange, text: below, anchor: CareType}}. The care type categorizes the healthcare provider responsible for the delivered care, or more specifically, it indicates the specialty of the department and/or health professional that delivered care (e.g. dental care, hospital, general practitioner). It helps patients and systems to interpret the origin and context of data.
- The MedMij Healthcare Provider List (Zorgaanbiederslijst, abbreviated ZAL) and OAuth Client List (OCL) determine which granular data services are available per healthcare provider and which are supported by the DVP, respectively. The set of available/supported data services is called the *capability* of the actor. By taking into account the capabilities of both DVA and DVP better alignment is possible.
- The DVP determines the set of granular data services to retrieve. Hence, the responsibility for orchestration lies with the DVP, consistent with the MedMij principles. Moreover, the FHIR queries for retrieving the underlying data remain unchanged, as no additional search parameter for domain is required.

## <a name="PublicationGranularDataServices"></a> Publication of granular data services
This section describes how cross-domain and domain-specific CIMs are defined and published as separate data services. It focuses on the definition of these data services in this IG and domain-specific IGs, respectively, as well as their representation in the Data Service Name List (Gegevensdienstnamenlijst, abbreviated GNL) of MedMij.

The technical name of cross-domain data services (which is used in this IG) has the form '[Function] MedMij Core - [CIM name in English] ([Suffix]) [Data service version]', for instance 'Retrieve MedMij Core - Blood pressure (zib2017/STU3) 1.0.0'. The Suffix is an optional addition to the data service name necessary to differentiate data services that have multiple variants (for instance, different functional versions or different FHIR versions). In case a granular data service corresponds to a zib, the corresponding baseline is used as suffix, e.g. 'zib2017/STU3'.

On the other hand, domain-specific data services have a technical name of the form '[Function] [Domain name in English] - [CIM name in English] ([Suffix]) [Data service version]', for instance 'Retrieve Long-term Healthcare - Nursing report 1.0.0'.

The following metadata is added to the GNL for each granular data service:
- The *Id* contains the data service number. The exact format of this number for granular data services still needs to be decided upon.
- The *Data service name* is the (patient-friendly) display name of the data service, and follows the formats described below:
    - For cross-domain data services, the display name has the form '[CIM name in Dutch]', for instance 'Bloeddruk'. Note that multiple cross-domain data services might have the same display name (i.e. if CIMs with the same name are exchanged in both STU3 and R4), but that uniqueness of the data services is ensured by the id;
    - For domain-specific data services, the display name has the form '[Domain name in Dutch] - [CIM name in Dutch]', for instance 'Langdurige Zorg - Dagrapportage'.

### <a name="VersioningGranularDataServices"></a> Versioning
Whenever a data service is published, a version (simply called the *data service version*) is assigned to that data service. The data service version follows the [Semantic Versioning](https://semver.org/) principles, and indicates the maturity of the data service (e.g. by stating the iteration of the data service and by indicating whether it's a pre-release version). In particular, note that the appendices 'alpha.*x*', 'beta.*x*' and 'rc.*x*' (where *x* is an integer) are used to denote alpha, beta and release candidate versions, respectively.

For traditional data services the data service version often coincides with the version of the corresponding IG, since there exists a one-to-one relationship between the data service itself and the corresponding IG.

In the case of granular data services, versioning is somewhat more difficult.
- For instance, given a certain domain, some of the relevant granular data services might be domain overarching, while others might be domain specific. The former data services are defined in the MedMij Core IG, while the latter ones are defined in the domain-specific IG. If the cross-domain and domain-specific granular data services have simultaneously followed the same development process and are in the same development stage (which in particular means that their maturity is considered to be equal), it does not make sense to assign different data service versions, only based on the respective IGs in which the data services are defined.
- Conversely, not all granular data services that are defined within the same IG have to be in the same development stage. For instance, some data services might still be in an alpha phase, while others have been developed further and are already in a beta phase. In this case it does not make sense to assign the same data service version, only based on the IG in which the data services are defined.

Hence, as the name already suggests, the data service version needs to be viewed as a version of only the data service itself. In particular it is unrelated to other versions, such as the version of the IG in which the data service is specified, the version of the FHIR package in which the relevant FHIR artifacts have been published, or the version of the corresponding CIM. However, these latter versions are still specified as follows for each granular data service:
- The version of the CIM (i.e. the functional backbone of the data service) is designated as the *functional version* of the data service.
    - For a CIM that is a zib, this version is of the form '*x.y*([zib publication])', e.g. '3.1(2017)'.
    - For CIMs that are defined by MedMij as a Logical Model, the version of the corresponding FHIR package is suitable as the functional version (even though the FHIR package is mainly associated with the technical part of the data service), since the Logical Model is published as part of that FHIR package. For these, the functional version will coincide with the version of the IG in which the data service is published, as the versions of the IG and corresponding FHIR package are kept equal by convention.
- The version of the FHIR package in which the corresponding FHIR profiles have been published (or more precisely, the combination of the FHIR package name and version) can be viewed as the *technical version* of the data service.

Summarizing, each granular data service consists of a functional and technical component, both of which have their own version (as specified above). The data service version is the version of the data service as a whole, but it is not directly related to either the functional or technical version. Figure 1 gives an overview of all components and corresponding versions.

{{render: guides/medmij-stu3-core-ig/images/Overview versions.png}}

**Figure 1: Overview of versions**

**Examples**
- Suppose an initial beta version of the cross-domain data service Patient (based on the zib Patient from publication 2017) has been added to version '1.0.0' of the MedMij STU3 Core IG. In this case the data service version is '1.0.0-beta.1', while the functional version is '3.1(2017)' and the technical version is '1.0.0' (i.e. equal to the IG version).
- Suppose two domain-specific data services A and B are defined in the same (domain-specific) IG with version '1.2.3', and assume that these data services are based on CIMs defined by MedMij. Data service B is still in a beta phase, while data service A is deemed suitable for use in a pilot setting, which means that it is already in the release candidate phase. In this case the data service versions for A and B might be respectively '1.0.0-rc.1' and '1.0.0-beta.3', while the functional version and technical version for both data services are '1.2.3' (i.e. equal to the IG version).
- Suppose a new set of domain-specific data services in alpha phase is specified in a new IG, and assume that these data services are based on CIMs defined by MedMij. In this case, the IG version, data service version, functional version and technical version are all equal to '1.0.0-alpha.1'.

## Overview of granular data services
The table below gives an overview of all cross-domain granular data services that use FHIR STU3 in their technical implementation.

| Id | Data service name without version (English) | Data service name without version (Dutch) | Data service version|
| --- | --- | --- | --- |
| 900000404 | {{pagelink: Alert, text: Retrieve MedMij Core - Alert (zib2017/STU3)}} | Verzamelen MedMij Core - Alert (zib2017/STU3) | 1.0.0-rc.3 |
| 900000401 | {{pagelink: BloodPressure, text: Retrieve MedMij Core - Blood pressure (zib2017/STU3)}} | Verzamelen MedMij Core - Bloeddruk (zib2017/STU3) | 1.0.0-rc.3 |
| 900000402 | {{pagelink: BodyHeight, text: Retrieve MedMij Core - Body height (zib2017/STU3)}} | Verzamelen MedMij Core - Lichaamslengte (zib2017/STU3) | 1.0.0-rc.3 |
| 900000409 | {{pagelink: BodyTemperature, text: Retrieve MedMij Core - Body temperature (zib2017/STU3)}} | Verzamelen MedMij Core - Lichaamstemperatuur (zib2017/STU3) | 1.0.0-rc.3 |
| 900000403 | {{pagelink: BodyWeight, text: Retrieve MedMij Core - Body weight (zib2017/STU3)}} | Verzamelen MedMij Core - Lichaamsgewicht (zib2017/STU3) | 1.0.0-rc.3 |
| 900000410 | {{pagelink: FluidBalance, text: Retrieve MedMij Core - Fluid balance (zib2017/STU3)}} | Verzamelen MedMij Core - Vochtbalans (zib2017/STU3) | 1.0.0-rc.3 |
| 900000406 | {{pagelink: LivingSituation, text: Retrieve MedMij Core - Living situation (zib2017/STU3)}} | Verzamelen MedMij Core - Woonsituatie (zib2017/STU3) | 1.0.0-rc.3 |
| 900000405 | {{pagelink: NutritionAdvice, text: Retrieve MedMij Core - Nutrition advice (zib2017/STU3)}} | Verzamelen MedMij Core - Voedingsadvies (zib2017/STU3) | 1.0.0-rc.3 |
| 900000407 | {{pagelink: Payer, text: Retrieve MedMij Core - Payer (zib2017/STU3)}} | Verzamelen MedMij Core - Betaler (zib2017/STU3) | 1.0.0-rc.3 |
| 900000412 | {{pagelink: PulseRate, text: Retrieve MedMij Core - Pulse rate (zib2017/STU3)}} | Verzamelen MedMij Core - Polsfrequentie (zib2017/STU3) | 1.0.0-rc.3 |
| 900000411 | {{pagelink: Respiration, text: Retrieve MedMij Core - Respiration (zib2017/STU3)}} | Verzamelen MedMij Core - Ademhaling (zib2017/STU3) | 1.0.0-rc.3 |

**Table 1: Granular data services**

In the {{pagelink: GranularDataServiceIndex, text: Granular data service index}} each granular data service is described in more detail.

Note that domain-specific data services are not included here, as these are not part of MedMij STU3 Core. Instead, these are further specified within the respective IGs corresponding to their domain. For instance, the granular data service 'Retrieve Long-term Healthcare - Nursing report' is described in the IG of [MedMij STU3 Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare).

## <a name="GeneralTechnicalSpecifications"></a> General technical specifications
For all granular data services the following technical specifications are applicable, unless deviations are explicitly mentioned on the page of the respective data service.

### PHR: request message
The PHR executes an HTTP search conform the [FHIR specification](https://hl7.org/fhir/STU3/search.html) against the endpoint of the XIS using a URL of the form:

```
GET [base]/[type]{?[parameters]}
```

Here, `[parameters]` represents a series of encoded name-value pairs representing the filter for the query. The base request for the granular data services is specified on their respective pages. The PHR MAY supply additional query parameters (i.e. the query parameters defined for the corresponding FHIR resource by the core FHIR specification), but the XIS is not required to be capable of processing these parameters, unless specified in the respective data service.

### XIS: response message
The XIS returns an HTTP Status code appropriate to the processing outcome as well as a Bundle, with `Bundle.type` equal to *searchset*, including the resources matching the search query. The resources included in the Bundle SHALL conform to the profiles listed in the respective data service.

The matching resources almost always contain *literal references*, which are references to other FHIR resources that use the `.reference` element. These referenced resources are called *secondary resources* and often are either Patient, Practitioner(Role) or Organization resources. Such resources support and contextualize the data exchanged via the granular data services listed above. Whenever these resources are referenced from other resources, they SHALL be resolvable, either by supporting a `read` interaction or by being explicitly included in the Bundle. Moreover they SHALL be regarded in the same context as the resource that contains the references. This is in line with the MedMij FHIR IGs defined by Nictiz, version [2020.01](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_IG#Use_of_the_Reference_datatype) and [2020.02](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.02/FHIR_IG#Use_of_the_Reference_datatype).

The previous in particular holds for secondary resources that are referenced by elements of data type Reference that are marked as Must Support. The corresponding resources are explicitly specified in the CapabilityStatements corresponding to the data service.

## <a name="MustSupport"></a> Must Support
For each granular data service within the {{pagelink: GranularDataServiceIndex, text: Granular data service index}}, one or more elements of the corresponding FHIR resources might be indicated as *Must Support*. Such elements have to be supported, which means that the DVA SHALL convey these in the FHIR resource if the corresponding data is present in the source system, and that the PHR SHALL process (the information in) these elements.

Note that currently, it is only (textually) indicated in this IG whether an element needs to be supported, and no MedMij Core profiles that include the FHIR-native `mustSupport` flag have been created. One of the reasons for this approach is that some FHIR profiles in the [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) package are based on international profiles which use the `mustSupport` flag. These flags are inherited by the zib profiles, and would also be inherited by the MedMij Core profiles, thus making it unclear which elements need to be supported in the manner described above.

## <a name="CareType"></a> Care type
In the transition from traditional to granular data services the context of exchanged data becomes less evident, as this context would normally be provided by the data service itself and its underlying use cases. In order to make the origin and context of data clear, the corresponding care type SHOULD be conveyed. This helps PHRs with filtering, grouping and logging, and makes it easier for patients to interpret their data.

Technically, the `.meta.tag` element (which is available in all FHIR resources) is used to indicate the type of healthcare provider that is responsible for the data present in the respective FHIR resource (e.g. dental care, primary care, pharmacy). The care type is conveyed by using the medical specialties defined by Vektis (AGB) in table [COD016-VEKT](https://www.vektis.nl/standaardisatie/codelijsten/COD016-VEKT), and thus specifies the specialty of the department and/or health professional that delivered care. The codes within this table consist of four digits, of which the first two specify the healthcare provider type, while the last two are a further specification of that type. For instance, the code *0300* pertains to 'Medisch specialisten, niet nader gespecificeerd' (i.e. 'Medical specialists, not further specified'), while code *0320* pertains to 'Medisch specialisten, cardiologie' (i.e. 'Medical specialists, cardiology'). The corresponding FHIR Valueset is the [AfdelingSpecialismeCodelijst](https://simplifier.net/resolve?canonical=http://decor.nictiz.nl/fhir/ValueSet/2.16.840.1.113883.2.4.3.11.60.40.2.17.2.4--20171231000000&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2), which is also used in the [nl-core-organization](https://simplifier.net/resolve?canonical=http://fhir.nl/fhir/StructureDefinition/nl-core-organization&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) profile on `.type`.

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

### Care type for non-granular data services
Even though the exchange of the care type via `.meta.tag` has been introduced to convey the context of data within granular data services, it might also be used for non-granular data services. At first glance it might seem there are no direct benefits of adding the care type in the latter case, as the context is already clear when data is exchanged via a non-granular data service. However, it ensures that PHRs can use the same logic based on the context provided in `.meta.tag` to structure data within their system. Moreover, whenever a non-granular data service is converted to granular ones at a later point in time, these latter ones have the additional benefit of already including the context in `.meta.tag`.

Whenever a non-granular data service adopts the care type as described above, this will be specified in the corresponding IG.