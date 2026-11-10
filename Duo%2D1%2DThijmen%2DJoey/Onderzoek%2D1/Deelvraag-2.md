# Welke meetmethode en prestatie-indactoren zijn geschikt om de betrouwbaarheid van de commincatie te beoordelen?

##1. Inleiding
------------
Binnen onze robotvloot is betrouwbare communicatie tussen de centrale controlunit (CCU) en de robots belangrijk. De CCU ontvangt gegevens zoals de locatie en status van de robots en gebruikt deze informatie voor de centrale routeplanning en taakverdeling.

Om te kunnen onderzoeken welke invloed de fysieke locatie van de CCU heeft op de communicatiebetrouwbaarheid, moeten we eerst bepalen hoe deze betrouwbaarheid gemeten kan worden.

Hiervoor onderzoeken we bestaande wetenschappelijke onderzoeken waarin de communicatieprestaties van landbouwrobots en andere autonome mobiele systemen worden gemeten.
Daarnaast onderzoeken we welke meetmethode het beste aansluit op de communicatiearchitectuur van onze robotvloot

##2. Literatuuronderzoek
----------------------
### 2.1 Wat is een betrouwbare communicatie.
Om de betrouwbaarheid van de communicatie tussen de centrale controlunit (CCU) en de robots te kunnen beoordelen, moet eerst worden vastgesteld wat betrouwbare communicatie inhoudt.

Volgens de internationale standaard [8]ITU-T Y.1540 (2019) kunnen de prestaties van communicatie binnen IP-netwerken worden beoordeeld aan de hand van vier eigenschappen:
- **Snelheid**: Hoe snel gegevens van de verzender naar de ontvanger worden overgedragen.
- **Nauwkeurigheid:** hoe corrent de gegevns worden overgedragen (zonder fouten).
- **Betrouwbaarheid:** de mate waarin de gegevensoverdracht corrent en volgens verwachting verloopt.
- **Beschikbaarheid:** de mate waarin de communicatiedienst beschikbaar is om gegevens uit te wisselen

deze eigenschappen vormen volgens [8]ITU-T Y.1540 (2019) een basis voor het veoordelen van prestaties van IP-communicatie

#### Relevantie tot de gekozen netwerk-architectuur
Binnen het systeem communiceren een rooier en twee overslagwagens via een centrale control unite. De CCU ontvangt informatie van de robots en gebruikt voor deze voor onder andre de routeplanning en taakverdeling.

voor deze toepassing is het be;angrijk dat informatie tijdig en correct wordt ontvangen en dat de communicatie voldoende beschikbaar blijft.

Wanneer berichten vertraagd aankomen gaat de CCU beslissingen nemen op verouderde informatie. wanneer berichten verloren gaan of de communicatie is tijdelijk niet beschikbaar, kan dit gevolgen hebben en leiden tot vertraging in het gehele oogst process.

op basis van  [8]ITU-T Y.1540 (2019) kan communicatie betrouwbaarheid voor de robotvloot worden beschowud als de mate waarin gegevens tijdig, correct en met volgoende continuiteit tussen de CCU en de robots kunnen worden uitgewisseld.

Om deze eigenschappen objectief te beoordelen, moet worden onderzocht welke meetpare indicatoren hiervoor geschikt zijn en wat de communicatie mogelijk kan beinvloeden.

### 2.2 Welke factoren beinvloeden de kwaliteit van de communicatie
De kwaliteit van een draadlooze connectie wordt beinvloed door verschillende factoren. Om te onderzoeken welke invloed de fysieke locatie van de CCU heeft op de communicatie betrouwbaarheid, is het belangrijk om te weten welke factoren de communicatie prestatie kan beinvloeden.

####Binnen 5g privaat netwerk
Binnen het onderzoek [9] ainelli, G. P., & Underberg, L. (2023) werd prestaties binnen een privaat 5g netwerk onderzocht.

De onderzoekers voerden metingen uit met industriële 5G-apparatuur onder realistische omstandigheden. Hierbij onderzochten zij de vertraging van gegevensoverdracht.

Uit het onderzoek blijkt dat de netwerk prestaties afhankelijk kunnen zijn van de verkeersrichting en de gelijke belasting van de verbinding. De onderzoekers kwamen er achter dat uplink- en downlinkverkeer elkaar kunnen beïnvloeden.

dit onderzoek laat ziet dat niet alleen fysieke omstandigheden, maar ook de gelijktijdige belastig en gebruik van het netwerk van belang is.

###Invloed van fysieke locatie en netwerkbelasting
In het onderzoek van Bodur et al. (2026) hebben ze end-to-end latency binnen een privaat 5G-netwerk onderzocht.
De onderzoekers voerden metingen uit op  7 verschillende fysieke locaties binnen een industriële testomgeving. Daarnaast werden verschillende niveaus van netwerkverkeer onderzocht.

Uit de resultaten blijkt dat zowel de fysieke meetlocatie als de netwerkbelasting invloed had op de gemeten latency.

De netwerkbelasting bleek binnen deze specifieke testomgeving de grootste invloed te hebben. De verschillen tussen fysieke locaties waren kleiner, maar wel meetbaar.
Hieruit blijkt dat de fysieke locatie van communicatieapparatuur invloed kan hebben op de netwerkprestaties, maar dat ook andere factoren moeten worden meegenomen bij het beoordelen van de resultaten.

**Relevantie voor hey systeem**
Uit de onderzochte/gelezen onderzoeken blijkt dat de kwaliteit van draadloze communicatie betrouwbaarheid beinvloed baar is door meerdere factoren. Voor onze robotvloot zijn vooral de fysieke locatie, obstakels, signaalkwaliteit en netwerkbelasting relevant.

Omdat we willen onderzoeken welke invloed de locatie van de Centrale Control Unit(CCU) heeft op de communicatiebetrouwbaarheid, is het belangrijk om tijdens de experimenten andere factoren zo veel mogelijk gelijk te houden.

Daarom worden de locaties van de gesimuleerde robots, de netwerkconfiguratie en de meetinstellingen tijdens de PoC zo veel mogelijk hetzelfde gehouden. Op deze manier kunnen we de verschillen in communicatie prestatie beter koppelen aan de onderzochte CCU locatie.


### 2.3 Welke meet-methode/indicatoren worden in bestaande onderzoeken en standaarden gebruikt
Om de betrouwbaarheid van de communicatie te kunnen beoordelen, worden in de al gebruikte onderzoeken en technische standaarden verschillende meetbare indicatoren gebruikt.

De internationale standaard [8]ITU-T Y.1540 (2019) beschijft verschillende indicatoren waarmee de prestaties van een ip-netwerk beoordeelt mee kan worden. hieronden vallen onder andere:
- Latency (vertraging): de tijd een pakket nodig heeft om van een verzender naar ontvanger te worden overgedragen.
- Packet Loss (pakketverlies): Het percentage IP-paketten dat tijdens overdracht verloren gaan.
- Packet Delay Variation (jitter): de variatie in vertraging tussen overdraging van pakketten.
- Packet error Ratio: de verhouding tussen foutif ontvangen pakketten en het totale aantal correcten pakketen
- Beschikbaarheid: zie -> 2.1






##3. Relevante meetmethoden voor communicatie betrouwbaarheid

##4. meetmethode selectie 

##5. Conclusie