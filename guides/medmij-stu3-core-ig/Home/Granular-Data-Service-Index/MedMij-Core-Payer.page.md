# Retrieve MedMij Core - Payer (zib2017/STU3)

## Overview
| | |
| --- | --- |
| **Id** | TBD |
| **Data service name without version (English)** | Retrieve MedMij Core - Payer (zib2017/STU3) |
| **Data service name without version (Dutch)** | Verzamelen MedMij Core - Betaler (zib2017/STU3) |
| **Data service version** | 1.0.0-beta.1 |
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
| **FHIR profile(s)** | [http://nictiz.nl/fhir/StructureDefinition/zib-Payer](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019098) |
| **FHIR package** | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version** | STU3 |
| **Search request** | `GET [base]/Coverage` |
| **Must Support** | <ul> <li> `.identifier` <li> `.subscriber` (only reference to [nl-core-patient](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018966)) <li> `.beneficiary` <li> `.period` <li> `.payor` (including the [practitionerrole-reference extension](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018979)) |

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