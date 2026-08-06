---
topic: FluidBalance
---

# Retrieve MedMij Core - Fluid balance (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | 900000410 |
| **Data service name without version (English)** | Retrieve MedMij Core - Fluid balance (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Vochtbalans (zib2017/STU3) |
| **Data service version** | 1.0.0-rc.3 |
| **System role(s)** | MMC-FBR-zib2017/STU3-rc.3 (PHR) <br/> MMC-FBB-zib2017/STU3-rc.3 (XIS) |
| **Used in Implementation Guide(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib FluidBalance](https://zibs.nl/wiki/FluidBalance-v1.0(2017EN)) |
| **Functional version** | 1.0(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/tr-2.16.840.1.113883.2.4.3.11.60.7.4.2.12.15-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-FluidBalance](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-FluidBalance&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Observation?code=http://snomed.info/sct|364396009` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subject` <li> `.effective[x]` <li> `.performer` (including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) <li> `.component:FluidTotalIn` <li> `.component:FluidTotalOut` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | {{pagelink: CapabilityStatementsIndex, text: Fluid Balance (Retrieve), anchor: FluidBalanceRetrieve}} <br/> {{pagelink: CapabilityStatementsIndex, text: Fluid Balance (Serve), anchor: FluidBalanceServe}} |

The FHIR profile is included below.

{{page:resource-view-tree-zib-no-examples, canonical:http://nictiz.nl/fhir/StructureDefinition/zib-FluidBalance}}