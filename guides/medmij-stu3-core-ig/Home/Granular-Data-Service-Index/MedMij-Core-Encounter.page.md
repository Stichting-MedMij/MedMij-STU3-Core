# MedMij Core - Encounter

## Overview
| | |
| --- | --- |
| **Id**                          | TBD |
| **Data service name (English)** | MedMij Core - Encounter |
| **Data service name (Dutch)**   | MedMij Core - Contact |
| **CIM**                         | [zib Encounter](https://zibs.nl/wiki/Encounter-v3.1(2017EN)) |
| **Functional version**          | v3.1(2017) |

## Functional model
The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.15.1-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)**             | [zib-Encounter](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3019026) |
| **FHIR package version**        | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version**                | STU3 |

The corresponding FHIR search request is:

`GET [base]/Encounter`