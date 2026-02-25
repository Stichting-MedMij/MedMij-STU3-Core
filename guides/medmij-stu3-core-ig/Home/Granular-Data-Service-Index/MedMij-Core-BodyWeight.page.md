---
topic: BodyWeight
---

# Retrieve MedMij Core - Body weight (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | 900000403 |
| **Data service name without version (English)** | Retrieve MedMij Core - Body weight (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Lichaamsgewicht (zib2017/STU3) |
| **Data service version** | 1.0.0-beta.2 |
| **System role(s)** | MMC-BWR-zib2017/STU3-1.0.0-beta.2-FHIR (PHR) <br/> MMC-BWB-zib2017/STU3-1.0.0-beta.2-FHIR (XIS) |
| **Relevant domain(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib BodyWeight](https://zibs.nl/wiki/BodyWeight-v3.1(2017EN)) |
| **Functional version** | 3.1(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.12.1-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-BodyWeight](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-BodyWeight&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Observation?code=http://loinc.org|29463-7` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subject` <li> `.effective[x]` <li> `.performer` (including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) <li> `.valueQuantity` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | [MedMij Core BodyWeight Retrieve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-BodyWeight-Retrieve&scope=medmij.fhir.nl.stu3.core@1.0.0) <br/> [MedMij Core BodyWeight Serve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-BodyWeight-Serve&scope=medmij.fhir.nl.stu3.core@1.0.0) |

The FHIR profile is included below.

<tabs>
    <tab title="Tree view" active="true">
      {{tree:http://nictiz.nl/fhir/StructureDefinition/zib-BodyWeight, buttons}}
    </tab>
    <tab title="Xml">
      {{xml:http://nictiz.nl/fhir/StructureDefinition/zib-BodyWeight}}
    </tab>
    <tab title="Json">
      {{json:http://nictiz.nl/fhir/StructureDefinition/zib-BodyWeight}}
    </tab>
</tabs>