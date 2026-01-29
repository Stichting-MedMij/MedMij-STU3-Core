# MedMij Core - Body height

## Overview
| | |
| --- | --- |
| **Id**                          | TBD |
| **Data service name (English)** | MedMij Core - Body height |
| **Data service name (Dutch)**   | MedMij Core - Lichaamslengte |
| **CIM**                         | [zib BodyHeight](https://zibs.nl/wiki/BodyHeight-v3.1(2017EN)) |
| **Functional version**          | 3.1(2017) |
| **Relevant domain(s)**          | [Long-term Healthcare](https://simplifier.net/medmij-stu3-long-term-healthcare/) |

## Functional model
The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.12.2-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)**             | [zib-BodyHeight](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019008) |
| **FHIR package version**        | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version**                | STU3 |

The corresponding FHIR search request is:

`GET [base]/Observation?code=http://loinc.org|8302-2`