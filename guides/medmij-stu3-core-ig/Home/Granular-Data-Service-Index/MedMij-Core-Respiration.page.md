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
| **Data service version** | 1.0.0-beta.2 |
| **System role(s)** | MMC-RER-zib2017/STU3-1.0.0-beta.2-FHIR (PHR) <br/> MMC-REB-zib2017/STU3-1.0.0-beta.2-FHIR (XIS) |
| **Relevant domain(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib Respiration](https://zibs.nl/wiki/Respiration-v3.1(2017EN)) |
| **Functional version** | 3.1(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.12.5-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Respiration&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) <br/> [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) <br/> [http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Observation?code=http://snomed.info/sct|422834003` <br/> Specific guidance on the response message is provided {{pagelink: Respiration, text: below, anchor: SpecificXISResponseMessage}}. |
| **Must Support** | Observation <ul> <li> `.identifier` <li> `.subject` <li> `.effective[x]` <li> `.performer` (including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) <li> `.component:BreathingFrequency` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) </ul> DeviceUseStatement <ul> <li> `.identifier` <li> `.subject` <li> `.whenUsed` <li> `.device` <li> `.extension:reasonReference` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) </ul> Device <ul> <li> `.identifier` <li> `.patient` <li> `.type` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | [MedMij Core Respiration Retrieve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-Respiration-Retrieve&scope=medmij.fhir.nl.stu3.core@1.1.0) <br/> [MedMij Core Respiration Serve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-Respiration-Serve&scope=medmij.fhir.nl.stu3.core@1.1.0) |

The FHIR profiles are included below.

<tabs>
    <tab title="Tree view" active="true">
      {{tree:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration, buttons}}
    </tab>
    <tab title="Xml">
      {{xml:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration}}
    </tab>
    <tab title="Json">
      {{json:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration}}
    </tab>
</tabs>

<tabs>
    <tab title="Tree view" active="true">
      {{tree:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice, buttons}}
    </tab>
    <tab title="Xml">
      {{xml:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice}}
    </tab>
    <tab title="Json">
      {{json:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDevice}}
    </tab>
</tabs>

<tabs>
    <tab title="Tree view" active="true">
      {{tree:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct, buttons}}
    </tab>
    <tab title="Xml">
      {{xml:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct}}
    </tab>
    <tab title="Json">
      {{json:http://nictiz.nl/fhir/StructureDefinition/zib-Respiration-AdministeredOxygen-AdministrationDeviceProduct}}
    </tab>
</tabs>

### Specific technical specifications
#### <a name="SpecificXISResponseMessage"></a> XIS: response message
Even though the PHR only requests the Observation resources corresponding to the Respiration CIM, the XIS SHALL include all DeviceUseStatement resources corresponding to the AdministrationDevice concept (NL-CM:12.5.13) in the Bundle (provided the medical device data is present in the source system). Moreover, the XIS is encouraged to also include the Device resources referenced from these DeviceUseStatement resources via `.device`, but is not required to do so, as these can alternatively be retrieved by the PHR via a `read`.