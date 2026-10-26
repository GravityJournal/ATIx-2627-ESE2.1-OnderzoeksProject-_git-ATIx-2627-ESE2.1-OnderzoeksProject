# Hoofdvraag
Wat is het meest efficiënte communicatieprotocol voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging en data-overhead?

# Doelstelling onderzoek
Het bepalen van het meest efficiënte communicatieprotocol (TCP versus UDP sockets in C++) voor realtime data-uitwisseling en overdrachtsstatussen tussen twee vlootbeheerders/robots, gemeten in vertraging (round-trip time in ms) en data-overhead.

# Scope
*   Enkel een C++ netwerksimulatie die draait op één computer (localhost) of tussen twee gekoppelde pc's.
*   Focus op het verschil tussen TCP- en UDP-sockets en berichtindeling (binaire struct vs. tekst/JSON).
*   Buiten scope: Fysieke robots, hardware-besturing en draadloze 5G/Wi-Fi veldmetingen.