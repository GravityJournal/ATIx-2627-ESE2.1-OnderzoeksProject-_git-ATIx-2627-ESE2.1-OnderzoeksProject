Hoofdvraag
==========

Wat is het meest efficiënte communicatieprotocol voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging en data-overhead?

Doelstelling onderzoek
======================

Het bepalen van het meest efficiënte communicatieprotocol (TCP versus UDP sockets in C++) voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging (round-trip time in ms) en data-overhead.

Scope
=====

*   Enkel een C++ netwerksimulatie die draait op één computer via localhost of tussen twee gekoppelde pc's.
    
*   Focus op het verschil tussen TCP- en UDP-sockets en berichtindeling (binaire struct vs. tekst/JSON).
    
*   Buiten scope: Fysieke robots, hardware-besturing en draadloze 5G/Wi-Fi veldmetingen.
    

Onderzoeksopzet
===============

In C++ worden twee netwerkprogramma's geschreven: een TCP-client/server en een UDP-client/server. Om de deelvragen systematisch te beantwoorden en te kwantificeren, wordt de testomgeving ingericht aan de hand van een duidelijke set variabelen:
*   **Onafhankelijke variabelen (testparameters):**
    *   **Communicatieprotocol:** TCP vs. UDP.
        
    *   **Berichtformaat:** Binaire C++ `struct` versus een string/JSON-formaat.
        
    *   **Netwerkbelasting (Request Rate):** 10, 100 en 1000 verzoeken per seconde.
        
*   **Afhankelijke variabelen (meetwaarden):**
    *   **Round-Trip Time (RTT):** Gemeten in milliseconden (`Avg_RTT_ms`, aangevuld met `Min_RTT_ms` en `Max_RTT_ms` voor uitschieters) met behulp van `std::chrono::high_resolution_clock`.
        
    *   **Data-overhead:** De vaste byte-grootte per bericht.
        
    *   **Betrouwbaarheid:** Het percentage pakketverlies.
        
Tijdens de testruns worden deze variabelen per iteratie geregistreerd bij het versturen van een overdrachtsbericht (zoals _"Robot A staat klaar bij Sluis 1"_) en het ontvangen van de bevestiging. De verzamelde data wordt gestructureerd in een datamatrix, waarmee vergelijkende grafieken in Excel worden gegenereerd om de latency en overhead visueel te maken.

Deelvraag 1
===========

Wat is het verschil in gemiddelde reactietijd (round-trip time in ms) tussen een TCP- en een UDP-gebaseerde C++ socketverbinding bij het uitwisselen van overdrachtsstatussen?

Deelvraag 2
===========

Hoeveel data-overhead (in bytes per bericht) introduceren binaire C++ structs vergeleken met een string/JSON-formaat bij het communiceren van overdrachtsgegevens?
Hoe vind je deze combinatie? Wil je nu direct doorgaan met het inbouwen van de testloop (voor de 10, 100 en 1000 verzoeken per seconde) in je client?