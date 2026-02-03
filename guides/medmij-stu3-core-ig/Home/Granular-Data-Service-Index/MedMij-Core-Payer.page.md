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
| **Data service version** | 1.0.0-beta.1 |
| **System role(s)** | MMC-PAR-zib2017/STU3-1.0.0-beta.1-FHIR (PHR) <br/> MMC-PAB-zib2017/STU3-1.0.0-beta.1-FHIR (XIS) |
| **Relevant domain(s)** | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
| | |
| --- | --- |
| **CIM** | [zib Payer](https://zibs.nl/wiki/Payer-v3.1(2017EN)) |
| **Functional version** | 3.1(2017) |

The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.1.1-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-Payer](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/zib-Payer&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Coverage` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subscriber` (only reference to [http://fhir.nl/fhir/StructureDefinition/nl-core-patient](https://simplifier.net/resolve?canonical=http://fhir.nl/fhir/StructureDefinition/nl-core-patient&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2)) <li> `.beneficiary` <li> `.period` <li> `.payor` (including the [practitionerrole-reference](https://simplifier.net/resolve?canonical=http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference&scope=nictiz.fhir.nl.stu3.zib2017@2.3.2) extension) |

The FHIR profile is included below.

<tabs>
    <tab title="Tree view" active="true">
      {{tree:http://nictiz.nl/fhir/StructureDefinition/zib-Payer, buttons}}
    </tab>
    <tab title="Xml">
      {{xml:http://nictiz.nl/fhir/StructureDefinition/zib-Payer}}
    </tab>
    <tab title="Json">
      {{json:http://nictiz.nl/fhir/StructureDefinition/zib-Payer}}
    </tab>
</tabs>