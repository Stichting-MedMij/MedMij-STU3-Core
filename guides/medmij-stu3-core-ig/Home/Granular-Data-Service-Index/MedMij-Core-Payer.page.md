---
topic: Payer
---

# Retrieve MedMij Core - Payer (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | 900000407 |
| **Data service name without version (English)** | Retrieve MedMij Core - Payer (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Betaler (zib2017/STU3) |
| **Data service version** | 1.0.0-rc.3 |
| **System role(s)** | MMC-PAR-zib2017/STU3-rc.3 (PHR) <br/> MMC-PAB-zib2017/STU3-rc.3 (XIS) |
| **Used in Implementation Guide(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib Payer](https://zibs.nl/wiki/Payer-v3.1(2017EN)) |
| **Functional version** | 3.1(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/tr-2.16.840.1.113883.2.4.3.11.60.7.4.2.1.1-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-Payer](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Payer&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Coverage` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subscriber` (only reference to [http://fhir.nl/fhir/StructureDefinition/nl-core-patient](https://simplifier.net/resolve?canonical=http://fhir.nl/fhir/StructureDefinition/nl-core-patient&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2)) <li> `.beneficiary` <li> `.period` <li> `.payor` <li> `.meta.tag` (only the {{pagelink: GranularExchange, text: care type, anchor: CareType}}) |
| **CapabilityStatement(s)** | {{pagelink: CapabilityStatementsIndex, text: Payer (Retrieve), anchor: PayerRetrieve}} <br/> {{pagelink: CapabilityStatementsIndex, text: Payer (Serve), anchor: PayerServe}} |

The FHIR profile is included below.

{{page:resource-view-tree-zib-no-examples, canonical:http://nictiz.nl/fhir/StructureDefinition/zib-Payer}}