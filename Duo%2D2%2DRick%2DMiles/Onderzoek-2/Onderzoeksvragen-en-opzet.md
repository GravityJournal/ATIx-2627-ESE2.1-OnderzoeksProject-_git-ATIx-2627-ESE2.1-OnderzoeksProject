# Hoofdvraag 
Wat is het meest efficiënte communicatieprotocol voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging en data-overhead? 

# Doelstelling onderzoek 
Het bepalen van het meest efficiënte communicatieprotocol (TCP versus UDP sockets in C++) voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging (round-trip time in ms) en data-overhead. 

# Scope 
*   Enkel een C++ netwerksimulatie die draait op één computer via localhost of tussen twee gekoppelde pc's.
*   Focus op het verschil tussen TCP- en UDP-sockets en berichtindeling (binaire struct vs. tekst/JSON).
*   Buiten scope: Fysieke robots, hardware-besturing en draadloze 5G/Wi-Fi veldmetingen.
    

# Onderzoeksopzet
In C++ worden twee netwerkprogramma's geschreven: een TCP-client/server en een UDP-client/server. Met behulp van std::chrono::high_resolution_clock wordt gemeten hoeveel milliseconden het duurt om een overdrachtsbericht (zoals "Robot A staat klaar bij Sluis 1") te versturen en een bevestiging terug te krijgen. Dit testen we met verschillende hoeveelheden berichten per seconde (bijv. 10, 100 en 1000 verzoeken/sec) om de latency en de byte-grootte per bericht te vergelijken. 

# Deelvraag 1
Wat is het verschil in gemiddelde reactietijd (round-trip time in ms) tussen een TCP- en een UDP-gebaseerde C++ socketverbinding bij het uitwisselen van overdrachtsstatussen? 

# Deelvraag 2
Hoeveel data-overhead (in bytes per bericht) introduceren binaire C++ structs vergeleken met een string/JSON-formaat bij het communiceren van overdrachtsgegevens?