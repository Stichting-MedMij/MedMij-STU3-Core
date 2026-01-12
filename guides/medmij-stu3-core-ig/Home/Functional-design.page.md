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
- We hanteren twee lagen: MedMij-core (domeinoverstijgend) en domeinspecifieke gegevensdiensten.
    - Domeinoverstijgende gegevensdiensten (MedMij-core): één gegevensdienst per klinisch concept, en herbruikbaar over zorgdomeinen.
        - MedMij‑core is méér dan de som van gegevensdiensten: het duidt tevens de werkwijze rondom granulaire uitwisseling en andere MedMij‑brede onderwerpen die in een IG thuishoren.
- Domeinspecifieke gegevensdiensten: afgeleide gegevensdiensten die een gegevensdienst uit MedMij-core toespitsen op een specifiek domein of gegevensdiensten die uitsluitend van toepassing zijn binnen een specifiek domein.
- De context (bijv. zorgaanbiederstype, zorgsetting, uitvoerder, bron, etc.) wordt meegegeven in de FHIR-resources, via elementen als .subject, .effective[x] en .performer, en de Provenance-resource. Het zorgaanbiederstype wordt beschikbaar gemaakt via .meta.tag.  De Zorgaanbiederstype is de categorie van de organisatie die verantwoordelijk is voor de geleverde zorg (bijv. tandartspraktijk, ziekenhuis, VVT-instelling). Het helpt patiënten en systemen om de herkomst en context van gegevens te duiden.
- De MedMij Zorgaanbiederslijst en de OAuthClientlijst bepalen welke gegevensdiensten beschikbaar zijn per zorgaanbieder en ondersteund worden door de DVP. Dit noemen we de capability van een actor. In het MedMij netwerk zijn de volgende actoren actief:
    - DVP
    - DVA i.c.m. de zorgaanbieder
    - Burger
    - De zorganbieder ontbreekt in het netwerk. Maar onze wens is dat de zorgaanbieder ook onderdeel gaat worden van het netwerk. Dit is echter buiten scope van dit project. 
- DVP bepaalt de op te halen set van gegevensdiensten.
    - Geen extra query parameter voor domein nodig. De FHIR‑requests blijven standaard zoekvragen per FHIR-resource.

### Doelstellingen
- Patiënten (via DVP) toegang geven tot gegevens relevant voor een bepaald zorgdomein (zoals Langdurige Zorg of Mondzorg).
- Gegevens granulair uitwisselen tussen DVA (zorgaanbieder) en DVP (PGO), afgestemd op wat daadwerkelijk ondersteund wordt per zorgaanbieder.

### Voordelen van deze aanpak
- Flexibel en schaalbaar (geen gebundelde BgZ of BgLZ nodig);
- Betere afstemming tussen DVP-capaciteit (OAuthClientlijst) en DVA-aanbod (Zorgaanbiederslijst);
- Context blijft beschikbaar via FHIR-standaardvelden, zoals .meta.tag en referenties. Of via de Provenance-resource; 
- Verantwoordelijkheid voor orkestratie ligt bij de DVP, passend bij de MedMij-principes.

### Uitwerking domeinoverstijgend en domeinspecifieke klinische concepten
Dit hoofdstuk beschrijft hoe domeinoverstijgende en domeinspecifieke klinische concepten als afzonderlijke gegevensdiensten worden vastgelegd en gepubliceerd. Het richt zich op weergave in de Zorgaanbiederslijst (ZAL) en de Gegevensdienstnamenlijst (GNL) van MedMij. Het sluit aan op het tweelaags model, dat bestaat uit MedMij‑core (voor generieke, domeinoverstijgende concepten) en domeinspecifieke gegevensdiensten (voor concepten die uitsluitend in een domein van toepassing zijn of extra aanscherping behoeven).

Domeinoverstijgend:
Doel: MedMij‑core bevat zibs of gestructureerde datasets die domeinoverstijgend zijn. Deze worden als generieke gegevensdiensten gepubliceerd op de Zorgaanbiederslijst.

Registratie op ZAL: Per zorgaanbieder wordt vastgelegd welke MedMij‑core-gegevensdiensten worden ondersteund, inclusief versie.

Domeinspecifiek:
Doel: Zibs die alleen binnen één domein gelden, én ZIBs die domeinoverstijgend zijn maar in verschillende domeinen een andere functionele of profielinvulling hebben, worden per domein op de ZAL geregistreerd. Voorbeelden: Mondzorg – Mondhygiëne, Langdurige Zorg – Dagrapportage.

Registratie op ZAL: Per zorgaanbieder wordt vastgelegd welke domeinspecifieke gegevensdiensten worden ondersteund, inclusief versie.

#### publicatie op de ZAL
ID

Gegevensdienstnummer

Weergavenaam
- Domeinoverstijgend: MedMij‑core - <KlinischConceptNaam>.
    - Voorbeeld Medmij-core - ASA-score
- Domeinspecifiek: <Domein> - <KlinischConceptNaam>.
    - Voorbeeld Mondzorg - Mondhygiëne

Versie
- FHIR-versie
    - Voorbeeld: STU3
- De functionele versie van de bouwsteen
    - Voorbeeld: v3.2(2020)

Tabel 1: Domeinoverstijgende gegevensdiensten Mondzorg en Langdurige Zorg

| Weegavenaam | Canonical URL | FHIR-versie | Functionele versie|
| --- | --- | --- | --- |
| MedMij‑core - Patient | url | STU3| v3.2(2020) |


### Metatags
Metatags worden uitgewisseld bij elke FHIR-resource. Onze metatags zijn gebaseerd op de identificerende kenmerken van de zorgaanbieder. 

Doel: Het zorgaanbiederstype wordt als metadata meegeleverd zodat DVP en eindgebruiker de herkomst kunnen duiden en DVP op type kan filteren. 

