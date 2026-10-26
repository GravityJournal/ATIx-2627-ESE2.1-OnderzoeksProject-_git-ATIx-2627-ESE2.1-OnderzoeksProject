# Hoofdvraag
Wat is het meest efficiënte communicatieprotocol voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging en data-overhead?

# Doelstelling onderzoek
Het bepalen van het meest efficiënte communicatieprotocol (TCP versus UDP sockets in C++) voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging (round-trip time in ms) en data-overhead.

# Deelvraag 1
Wat is het verschil in gemiddelde reactietijd (round-trip time in ms) tussen een TCP- en een UDP-gebaseerde C++ socketverbinding bij het uitwisselen van overdrachtsstatussen?

# Deelvraag 2
Hoeveel data-overhead (in bytes per bericht) introduceren binaire C++ structs vergeleken met een string/JSON-formaat bij het communiceren van overdrachtsgegevens?