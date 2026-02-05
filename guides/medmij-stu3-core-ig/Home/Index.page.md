## {{page-title}}

This is the implementation guide for MedMij STU3 Core. This is the generic layer defined by MedMij which forms a foundation for all data services that are exchanged in FHIR STU3. It contains guidance and requirements on data service-overaching topics, such as granular exchange and Logical Models. Moreover, it might contain FHIR artifacts that are relevant for multiple data services.

This IG thus builds upon the overarching MedMij functional designs (version [2020.01](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/Ontwerpen) and [2020.02](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.02/Ontwerpen)), as well as the MedMij FHIR Implementation Guide for STU3 (version [2020.01](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_IG) and [2020.02](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.02/FHIR_IG)), all defined by Nictiz. All data services that make use of (artifacts within) MedMij STU3 Core SHALL have a dependency on MedMij STU3 Core, either textually in their respective IG, or technically on the corresponding MedMij STU3 Core package.

Note that MedMij Core is defined separately for data services that are exchanged in FHIR R4. The specifications for MedMij R4 Core can be found [here](https://simplifier.net/medmij-r4-core).

For questions or feedback on the IG, please reach out to MedMij via [info@medmij.nl](mailto:info@medmij.nl).