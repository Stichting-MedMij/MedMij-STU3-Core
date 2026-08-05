---
topic: Respiration
---

# Retrieve MedMij Core - Respiration (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | 900000411 |
| **Data service name without version (English)** | Retrieve MedMij Core - Respiration (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Ademhaling (zib2017/STU3) |
| **Data service version** | 1.0.0-rc.3 |
| **System role(s)** | MMC-RER-zib2017/STU3-rc.3 (PHR) <br/> MMC-REB-zib2017/STU3-rc.3 (XIS) |
| **Used in Implementation Guide(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib Respiration](https://zibs.nl/wiki/Respiration-v3.1(2017EN)) |
| **Functional version** | 3.1(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/tr-2.16.840.1.113883.2.4.3.11.60.7.4.2.12.5-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Respiration&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) <br/> [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) <br/> [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Observation?code=http://snomed.info/sct|422834003` <br/> Specific guidance on the response message is provided {{pagelink: Respiration, text: below, anchor: SpecificXISResponseMessage}}. |
| **Must Support** | Observation <ul> <li> `.identifier` <li> `.subject` <li> `.effective[x]` <li> `.performer` (including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) <li> `.component:BreathingFrequency` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) </ul> DeviceUseStatement <ul> <li> `.identifier` <li> `.subject` <li> `.whenUsed` <li> `.device` <li> `.extension:reasonReference` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) </ul> Device <ul> <li> `.identifier` <li> `.patient` <li> `.type` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | [MedMij Core Respiration Retrieve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-Respiration-Retrieve&scope=medmij.fhir.nl.stu3.core@1.3.0) <br/> [MedMij Core Respiration Serve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-Respiration-Serve&scope=medmij.fhir.nl.stu3.core@1.3.0) |

The FHIR profiles are included below.

{{page:resource-view-tree-zib-no-examples, canonical:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration}}

{{page:resource-view-tree-zib-no-examples, canonical:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice}}

{{page:resource-view-tree-zib-no-examples, canonical:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct}}

### Specific technical specifications
#### <a name="SpecificXISResponseMessage"></a> XIS: response message
Even though the PHR only requests the Observation resources corresponding to the Respiration CIM, the XIS SHALL include all DeviceUseStatement resources corresponding to the AdministrationDevice concept (NL-CM:12.5.13) in the Bundle (provided the medical device data is present in the source system). Moreover, the XIS is encouraged to also include the Device resources referenced from these DeviceUseStatement resources via `.device`, but is not required to do so, as these can alternatively be retrieved by the PHR via a `read`.