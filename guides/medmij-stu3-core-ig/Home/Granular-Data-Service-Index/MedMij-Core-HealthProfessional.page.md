# MedMij Core - Health professional

## Overview
| | |
| --- | --- |
| **Id**                          | TBD |
| **Data service name (English)** | MedMij Core - Health professional |
| **Data service name (Dutch)**   | MedMij Core - Zorgverlener |
| **CIM**                         | [zib HealthProfessional](https://zibs.nl/wiki/HealthProfessional-v3.2(2017EN)) |
| **Functional version**          | v3.2(2017) |

## Functional model
The functional model can be found on [ART-DECOR](https://decor.nictiz.nl/pub/zib2017bbr/zib2017bbr-html-20211029T113909/ds-2.16.840.1.113883.2.4.3.11.60.40.3.17.1-2017-12-31T000000.html).

## Technical specification
| | |
| --- | --- |
| **FHIR profile(s)**             | [nl-core-practitioner](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018968) <br/> [nl-core-practitionerrole](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017/2.3.2/files/3018969) |
| **FHIR package version**        | [nictiz.fhir.nl.stu3.zib2017](https://simplifier.net/packages/nictiz.fhir.nl.stu3.zib2017) version 2.0.0 or compatible |
| **FHIR version**                | STU3 |

The corresponding FHIR search requests are:

`GET [base]/Practitioner`

and

`GET [base]/PractitionerRole`