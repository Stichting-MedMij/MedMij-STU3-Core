---
topic: PulseRate
---

# Retrieve MedMij Core - Pulse rate (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | 900000412 |
| **Data service name without version (English)** | Retrieve MedMij Core - Pulse rate (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Polsfrequentie (zib2017/STU3) |
| **Data service version** | 1.0.0-rc.3 |
| **System role(s)** | MMC-PRR-zib2017/STU3-rc.3 (PHR) <br/> MMC-PRB-zib2017/STU3-rc.3 (XIS) |
| **Used in Implementation Guide(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib PulseRate](https://zibs.nl/wiki/PulseRate-v3.1(2017EN)) |
| **Functional version** | 3.1(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/tr-2.16.840.1.113883.2.4.3.11.60.7.4.2.12.7-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-PulseRate](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-PulseRate&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Observation?code=http://loinc.org|8893-0` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subject` <li> `.effective[x]` <li> `.performer` (including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) <li> `.valueQuantity` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | {{pagelink: CapabilityStatementsIndex, text: Pulse Rate (Retrieve), anchor: PulseRateRetrieve}} <br/> {{pagelink: CapabilityStatementsIndex, text: Pulse Rate (Serve), anchor: PulseRateServe}} |

The FHIR profile is included below.

{{page:resource-view-tree-zib-no-examples, canonical:http://nictiz.nl/fhir/StructureDefinition/zib-PulseRate}}