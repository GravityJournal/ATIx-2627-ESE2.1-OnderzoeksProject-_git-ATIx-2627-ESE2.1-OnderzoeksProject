# Hoofdvraag
Wat is het meest efficiënte communicatieprotocol voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging en data-overhead?

# Doelstelling onderzoek
Het bepalen van het meest efficiënte communicatieprotocol (TCP versus UDP sockets in C++) voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging (round-trip time in ms) en data-overhead, onder verschillende netwerkbelastingen.
    
# Deelvraag 1
Wat is het verschil in gemiddelde reactietijd (round-trip time in ms), jitter en betrouwbaarheid tussen een TCP- en een UDP-gebaseerde C++ socketverbinding bij het uitwisselen van overdrachtsstatussen onder oplopende netwerkbelasting?

# Deelvraag 2
Hoeveel data-overhead (in bytes per bericht) introduceren binaire C++ `struct`'s vergeleken met een string/JSON-formaat bij het communiceren van overdrachtsgegevens en wat heeft dit voor invloed op de round-trip time?

# Scope
* Een C++ netwerksimulatie (client/server) die draait via localhost of tussen twee gekoppelde pc's in een netwerk.   
* Focus op het vergelijken van TCP- en UDP-sockets, berichtindelingen (binaire C++ struct vs. tekst/JSON) en netwerkbelasting (10, 100, 1000 en 10000 verzoeken per seconde).
* Buiten scope: Fysieke robots, hardware-besturing en draadloze 5G/Wi-Fi veldmetingen.

# Onderzoeks- en analysemethoden

## Deelvraag 1: Protocolprestaties (RTT en pakketverlies)
* **Simulatie en Testomgeving:** In C++ worden een TCP- en een UDP-client/server-architectuur opgezet. Er worden geautomatiseerde testruns uitgevoerd waarbij de netwerkbelasting wordt gemaximaliseerd voor een zo groot mogelijke throughput.
    
* **Verzamelde gegevens:** Per bericht worden de volgende metingen weggeschreven naar een CSV-bestand:
    * Round-Trip Time in milliseconden.
    * Of het pakket wel of niet is aangekomen.
        
* **Analyse:** De resultaten worden statistisch geanalyseerd op basis van gemiddelden, medianen, minimum/maximum waarden en standaardafwijkingen. De data wordt visueel onderbouwd met behulp van boxplots en spreidingsdiagrammen.
        

## Deelvraag 2: Berichtindeling en Data-overhead
* **Analyse:** De byte-grootte van de binaire C++ `struct` wordt vergeleken met de byte-lengte van het alternatieve JSON-stringformaat.
* **Verzamelde gegevens:**
    * Vaste geheugengrootte in bytes van de binaire struct (`sizeof`). 
    * Karakterlengte / byte-grootte van het JSON-serialisatieformaat.
* **Analyse:** De overhead per bericht wordt direct afgezet tegen de netwerkcapaciteit, om te berekenen hoeveel bandbreedte bespaard wordt bij grotere vloten.
    

# Benodigde middelen
* **Software:**
    * C++ ontwikkelomgeving (GCC / MSVC).  
    * Eigen C++ netwerk client/server scripts.  
    * Git voor versiebeheer.  
    * Spreadsheetsoftware / Python (Pandas & Seaborn) voor data-analyse en visualisatie van de CSV-resultaten.
* **Hardware:**
    * Ontwikkelcomputer / test-pc's.  
    * Lokale netwerkomgeving (of cross-device verbinding via LAN/IP).
* **Data:**
    * Simulatielogs en geëxporteerde CSV-bestanden met RTT-metingen per bericht.  
    * Netwerk- en belastingparameters (request rates, protocol- en formatkeuzes).
        

# Analysecriteria
Voor het bepalen van het meest efficiënte communicatieprotocol worden de volgende criteria gehanteerd:
* **Round-Trip Time (RTT):** Gemiddelde en mediaan in ms (lager = beter).
* **Uitschieters:** Standaardafwijking van de RTT tussen simulatieruns (weinig schommelingen = beter).
* **Data-overhead:** Vaste byte-grootte per bericht (lager = beter).
* **Betrouwbaarheid:** Percentage pakketverlies onder hoge belasting van het aantal verzoeken/sec (lager = beter).