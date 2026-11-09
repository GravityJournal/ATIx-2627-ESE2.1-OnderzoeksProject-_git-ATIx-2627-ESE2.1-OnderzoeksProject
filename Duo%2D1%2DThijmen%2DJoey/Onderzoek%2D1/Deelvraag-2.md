#Hoe kunnen we de betrouwbaarheid van de communicatie tussen de CCU en de robots meten?

##1. Inleiding
------------
Binnen onze robotvloot is betrouwbare communicatie tussen de centrale controlunit (CCU) en de robots belangrijk. De CCU ontvangt gegevens zoals de locatie en status van de robots en gebruikt deze informatie voor de centrale routeplanning en taakverdeling.

Om te kunnen onderzoeken welke invloed de fysieke locatie van de CCU heeft op de communicatiebetrouwbaarheid, moeten we eerst bepalen hoe deze betrouwbaarheid gemeten kan worden.

Hiervoor onderzoeken we bestaande wetenschappelijke onderzoeken waarin de communicatieprestaties van landbouwrobots en andere autonome mobiele systemen worden gemeten.

We richten ons voornamelijk op drie meetwaarden: latency, pakketverlies en beschikbaarheid.
Daarnaast onderzoeken we welke meetmethode het beste aansluit op de communicatiearchitectuur van onze robotvloot.

##2. Literatuuronderzoek
----------------------
### 2.1 Communicatiebetrouwbaarheid bij autonome mobiele robots
In het onderzoek van Natmeladze et al. (2025) [8] wordt de betrouwbaarheid van draadloze communicatie bij autonome mobiele robots onderzocht.

De onderzoekers vergelijken hiervoor twee netwerktechnologieën: WiFi 6E en een privaat 5G Standalone-netwerk.

Tijdens de experimenten reed een autonome mobiele robot langs verschillende meetpunten. Met behulp van een zelfgeschreven Python-programma werden de volgende communicatieparameters geregistreerd:
*   **Latency:** De vertraging van de communicatie, gemeten als round-trip time (RTT).
    
*   **Packet loss:** Het percentage verzonden netwerkverzoeken waarop geen antwoord werd ontvangen.
    
*   **Jitter:** De variatie tussen opeenvolgende vertragingen.
    
*   **RSSI:** De ontvangen signaalsterkte.

De latency en het pakketverlies werden gemeten met behulp van ping. Daarnaast werden de positie van de robot en het tijdstip van de metingen opgeslagen.

Uit de resultaten bleek dat de WiFi-verbinding onder de onderzochte omstandigheden meer variatie in latency en vaker pakketverlies vertoonde dan het private 5G-netwerk (Natmeladze et al., 2025) [8].



### 2.2 Meten van communicatieprestaties met UDP

### 2.3 Communicatieprestaties meten op verschillende fysieke locaties