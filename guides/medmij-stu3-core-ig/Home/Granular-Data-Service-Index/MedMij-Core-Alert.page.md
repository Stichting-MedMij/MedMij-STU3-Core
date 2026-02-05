---
topic: Alert
---

# Retrieve MedMij Core - Alert (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | 900000404 |
| **Data service name without version (English)** | Retrieve MedMij Core - Alert (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Alert (zib2017/STU3) |
| **Data service version** | 1.0.0-beta.1 |
| **System role(s)** | MMC-ALR-zib2017/STU3-1.0.0-beta.1-FHIR (PHR) <br/> MMC-ALB-zib2017/STU3-1.0.0-beta.1-FHIR (XIS) |
| **Relevant domain(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib Alert](https://zibs.nl/wiki/Alert-v3.2(2017EN)) |
| **Functional version** | 3.2(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.8.3-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-Alert](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Alert&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Flag` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subject` (only reference to [http://fhir.nl/fhir/StructureDefinition/nl-core-patient](https://simplifier.net/resolve?canonical=http://fhir.nl/fhir/StructureDefinition/nl-core-patient&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2)) <li> `.period` <li> `.author` (only reference to [http://fhir.nl/fhir/StructureDefinition/nl-core-organization](https://simplifier.net/resolve?canonical=http://fhir.nl/fhir/StructureDefinition/nl-core-organization&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) and [http://fhir.nl/fhir/StructureDefinition/nl-core-practitioner](https://simplifier.net/resolve?canonical=http://fhir.nl/fhir/StructureDefinition/nl-core-practitioner&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2), including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | [MedMij Core Alert Retrieve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-Alert-Retrieve&scope=medmij.fhir.nl.stu3.core@1.0.0) <br/> [MedMij Core Alert Serve](https://simplifier.net/resolve?canonical=http://medmij.nl/fhir/CapabilityStatement/medmij-core-Alert-Serve&scope=medmij.fhir.nl.stu3.core@1.0.0) |

The FHIR profile is included below.

<tabs>
    <tab title="Tree view" active="true">
      {{tree:http://nictiz.nl/fhir/StructureDefinition/zib-Alert, buttons}}
    </tab>
    <tab title="Xml">
      {{xml:http://nictiz.nl/fhir/StructureDefinition/zib-Alert}}
    </tab>
    <tab title="Json">
      {{json:http://nictiz.nl/fhir/StructureDefinition/zib-Alert}}
    </tab>
</tabs>