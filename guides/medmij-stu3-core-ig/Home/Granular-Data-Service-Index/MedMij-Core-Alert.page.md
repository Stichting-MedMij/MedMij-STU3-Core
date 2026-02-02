---
topic: Alert
---

# Retrieve MedMij Core - Alert (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | TBD |
| **Data service name without version (English)** | Retrieve MedMij Core - Alert (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Alert (zib2017/STU3) |
| **Data service version** | 1.0.0-beta.1 |
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
| **FHIR profile(s)** | {{link: http://nictiz.nl/fhir/StructureDefinition/zib-Alert, title: http://nictiz.nl/fhir/StructureDefinition/zib-Alert}} |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Flag` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subject` (only reference to {{link: http://fhir.nl/fhir/StructureDefinition/nl-core-patient, title: nl-core-patient}}) <li> `.period` <li> `.author` (only reference to {{link: http://fhir.nl/fhir/StructureDefinition/nl-core-organization, title: nl-core-organization}} and {{link: http://fhir.nl/fhir/StructureDefinition/nl-core-practitioner, title: nl-core-practitioner}}, including the {{link: http://nictiz.nl/fhir/StructureDefinition/practitionerrole-reference, title: practitionerrole-reference extension}}) |

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