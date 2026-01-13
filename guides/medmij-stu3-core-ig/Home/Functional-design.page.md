---
topic: FO
---

# Functioneel ontwerp

## Algemeen


## Granulair uitwisselen

### Ambitie
Onze ambitie is het granulair (modulair) uitwisselen van zorggegevens binnen de kaders van het MedMij Afsprakenstelsel, met inachtneming van de uitgangspunten voor hergebruik, privacy flexibiliteit, en schaalbaarheid. In dit document wordt de toepassing toegelicht aan de hand van de domeinen Mondzorg en Langdurige zorg. Focus ligt op het ‘verzamelen’ van gegevens. 

### Uitgangspunten
- Elke gegevensdienst is gekoppeld aan één of meerdere FHIR-profielen, die gebaseerd zijn op een zib of een ander klinisch concept (zoals ASA-score).
- We hanteren twee lagen: domeinoverstijgend (MedMij-core) en domeinspecifieke gegevensdiensten.
    - Domeinoverstijgende gegevensdiensten: één gegevensdienst per klinisch concept, en herbruikbaar over zorgdomeinen.
        - MedMij‑core is méér dan de som van gegevensdiensten: het duidt tevens de werkwijze rondom granulaire uitwisseling en andere MedMij‑brede onderwerpen die in een IG thuishoren.
- Domeinspecifieke gegevensdiensten: afgeleide gegevensdiensten die een gegevensdienst uit MedMij-core toespitsen op een specifiek domein of gegevensdiensten die uitsluitend van toepassing zijn binnen een specifiek domein.
- De context (bijv. zorgaanbiederstype, zorgsetting, uitvoerder, bron, etc.) wordt meegegeven in de FHIR-resources, via elementen als .subject, .effective[x] en .performer, en de Provenance-resource. Het zorgaanbiederstype wordt beschikbaar gemaakt via .meta.tag.  De Zorgaanbiederstype is de categorie van de organisatie die verantwoordelijk is voor de geleverde zorg (bijv. tandartspraktijk, ziekenhuis). Het helpt burgers en systemen om de herkomst en context van gegevens te duiden.
- De MedMij Zorgaanbiederslijst en de OAuthClientlijst bepalen welke gegevensdiensten beschikbaar zijn per zorgaanbieder en ondersteund worden door de DVP. Dit noemen we de capability van een actor. In het MedMij netwerk zijn de volgende actoren actief:
    - DVP
    - DVA i.c.m. de zorgaanbieder
    - Burger
- DVP bepaalt de op te halen set van gegevensdiensten.
    - Geen extra query parameter voor domein nodig. De FHIR‑requests blijven standaard zoekvragen per FHIR-resource.

### Doelstellingen
- Patiënten (via DVP) toegang geven tot gegevens relevant voor een bepaald zorgdomein (zoals Langdurige Zorg of Mondzorg).
- Gegevens granulair uitwisselen tussen DVA (zorgaanbieder) en DVP (PGO), afgestemd op wat daadwerkelijk ondersteund wordt per zorgaanbieder.

### Voordelen van deze aanpak
- Flexibel en schaalbaar (geen gebundelde BgZ of BgLZ gegevensdiensten nodig);
- Betere afstemming tussen DVP-capaciteit (OAuthClientlijst) en DVA-aanbod (Zorgaanbiederslijst);
- Context blijft beschikbaar via FHIR-standaardvelden, zoals .meta.tag en referenties. Of via de Provenance-resource; 
- Verantwoordelijkheid voor orkestratie ligt bij de DVP, passend bij de MedMij-principes.

### Uitwerking domeinoverstijgend en domeinspecifieke klinische concepten
Dit hoofdstuk beschrijft hoe domeinoverstijgende en domeinspecifieke klinische concepten als afzonderlijke gegevensdiensten worden vastgelegd en gepubliceerd. Het richt zich op weergave in de Zorgaanbiederslijst (ZAL) en de Gegevensdienstnamenlijst (GNL) van MedMij. Het sluit aan op het tweelaags model, dat bestaat uit MedMij‑core (voor generieke, domeinoverstijgende concepten) en domeinspecifieke gegevensdiensten (voor concepten die uitsluitend in een domein van toepassing zijn of extra aanscherping behoeven).

Domeinoverstijgend:
Doel: MedMij‑core bevat zibs of gestructureerde datasets die domeinoverstijgend zijn. Deze worden als generieke gegevensdiensten gepubliceerd op de Zorgaanbiederslijst.


Domeinspecifiek:
Doel: Zibs die alleen binnen één domein gelden, én zibs die domeinoverstijgend zijn maar in verschillende domeinen een andere functionele of profielinvulling hebben, worden per domein op de ZAL geregistreerd. Voorbeelden: Mondzorg – Mondhygiëne, Langdurige Zorg – Dagrapportage.


#### publicatie op de Zorgaanbiederslijst (ZAL) en Gegevensdienstnamemlijst (GNL)
ID:
- Gegevensdienstnummer

Weergavenaam:
- Domeinoverstijgend: MedMij‑core - <KlinischConceptNaam>.
    - Voorbeeld Medmij-core - ASA-score
- Domeinspecifiek: <Domein> - <KlinischConceptNaam>.
    - Voorbeeld Mondzorg - Mondhygiëne

Versie:
- FHIR-versie
    - Voorbeeld: STU3
- De functionele versie van het klinische concept
    - Voorbeeld: v3.2(2020)

Tabel 1: Domeinoverstijgende gegevensdiensten Mondzorg en Langdurige Zorg

| Weegavenaam | Canonical URL | FHIR-versie | Functionele versie|
| --- | --- | --- | --- |
| MedMij-core-Patient | [nl-core-patient](https://simplifier.net/nictizstu3-zib2017/nl-core-patient) | STU3 | v3.1(2017) |
| MedMij-core-Zorgaanbieder | [nl-core-organization](https://simplifier.net/nictizstu3-zib2017/nl-core-organization) | STU3 | v3.1(2017) |
| MedMij-core-Zorgverlener | [nl-core-practitioner](https://simplifier.net/nictizstu3-zib2017/nl-core-practitioner) | STU3 | v3.2(2017) |
| MedMij-core-Bloeddruk | [Zib-BloodPressure](https://simplifier.net/nictizstu3-zib2017/zib-bloodpressure) | STU3 | v3.1(2017) |
| MedMij-core-Lichaamsgewicht | [Zib-BodyWeight](https://simplifier.net/nictizstu3-zib2017/zib-bodyweight) | STU3 | v3.1(2017) |
| MedMij-core-Lichaamslengte | [Zib-BodyHeight](https://simplifier.net/nictizstu3-zib2017/zib-bodyheight) | STU3 | v3.1(2017) |
| MedMij-core-Alert | [Zib-Alert](https://simplifier.net/nictizstu3-zib2017/zib-alert) | STU3 | v3.1(2017) |
| MedMij-core-Voedingsadvies | [Zib-NutritionAdvice](https://simplifier.net/nictizstu3-zib2017/zib-alert) | STU3 | v3.1(2017) |
| MedMij-core-Lichaamstemperatuur | [Zib-BodyTemperature](https://simplifier.net/nictizstu3-zib2017/zib-bodytemperature) | STU3 | v3.1(2017) |
| MedMij-core-Vochtbalans | [Zib-FluidBalance](https://simplifier.net/nictizstu3-zib2017/zib-fluidbalance) | STU3 | v1.0(2017) |
| MedMij-core-Ademhaling | [Zib-Respiration](https://simplifier.net/nictizstu3-zib2017/zib-respiration) | STU3 | v3.1(2017) |
| MedMij-core-Polsfrequentie | [Zib-PulseRate](https://simplifier.net/nictizstu3-zib2017/zib-respiration) | STU3 | v3.1(2017) |
| MedMij-core-Betaler | [Zib-Payer](https://simplifier.net/nictizstu3-zib2017/zib-payer) | STU3 | v3.1(2017) |
| MedMij-core-Contact | [Zib-Encounter] | STU3 | v3.1(2017) |

Tabel 2: Domeinspecifieke gegevensdiensten Mondzorg en Langdurige Zorg
| Weegavenaam | Canonical URL | FHIR-versie | Functionele versie|
| --- | --- | --- | --- |
| Langdurige Zorg-Dagrapportage | [nl-core-nursingreport] | STU3 | onbekend |


### Metatags voor zorgaanbiederstype
Doel: De .meta.tag geeft voor elk uitgewisseld gegeven aan wat voor type zorgaanbieder verantwoordelijk is (bijv. “kaakchirurgie”, “huisarts”, “apotheek”). Dit maakt de herkomst en context voor de burger duidelijk en helpt DVP’s bij filteren, groeperen en logging. Metatags worden bij elke FHIR-resource meegeleverd. Voor de definitie van het zorgaanbiederstype hanteren we VEKTIS AGB (tabel COD016), waarmee het specialisme van de (uitvoerende) zorgaanbieder wordt gecodeerd. Bijvoorbeeld code 1100: Tandartsspecialisten mondziekten en kaakchirurgie. 

Zo lees je de metatag:
- 11 = het zorgaanbiedertype
- kwalificatie (optioneel): naast het type kan een kwalificatiecode worden meegegeven voor nadere duiding van de organisatiecategorie. Voorbeeld 0630 - Militaire ziekenhuizen. 