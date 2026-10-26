# Wat is al bekend in de literatuur?

In de bestaande literatuur over netwerkcommunicatie binnen geautomatiseerde robotomgevingen en het Internet of Things (IoT) is veel onderzoek gedaan naar de prestatieverschillen tussen transportprotocollen en berichtformaten _(Pereira et al., 2021)_.
Op het niveau van transportprotocollen wordt in de literatuur een duidelijke scheiding gemaakt tussen TCP (Transmission Control Protocol) en UDP (User Datagram Protocol) _(IntechOpen, 2021)_:
*   **TCP** garandeert dat gegevenspakketten in de juiste volgorde en zonder verlies aankomen door gebruik te maken van handshakes en automatische herverzending _(IntechOpen, 2021)_. Het nadeel hiervan is dat deze mechanismen extra netwerk-overhead en een hogere reactietijd (round-trip time in ms) introduceren _(Pereira et al., 2021)_.
    
*   **UDP** is een _connectionless_ protocol dat data direct verzendt zonder handshakes of controle op aankomst _(IntechOpen, 2021)_. Dit resulteert in een extreem lage latency en minimale overhead, maar brengt het risico met zich mee dat pakketten verloren kunnen raken _(Pereira et al., 2021)_.
    
Op het niveau van datastructuren en berichtformaten laat onderzoek zien dat de manier waarop gegevens worden ingepakt (geserialiseerd) grote invloed heeft op de netwerkbelasting _(IEEE, 2026)_:
*   **Tekstgebaseerde formaten (zoals JSON of XML)** zijn mensleesbaar en flexibel, maar bevatten veel overtollige karakters (zoals haakjes en veldnamen), wat leidt tot een hogere data-overhead per bericht en extra verwerkingstijd (parsing) bij de ontvanger _(IEEE, 2026)_.
    
*   **Binaire formaten (zoals C++ `structs` of Protocol Buffers)** zetten gegevens direct om naar een compacte reeks bytes _(IEEE, 2026)_. Dit reduceert de byte-grootte per bericht aanzienlijk en vraagt minimale CPU-rekenkracht van de client en server _(IEEE, 2026)_.
    
Daarnaast toont recent vergelijkend onderzoek aan dat directe, socketgebaseerde communicatie (peer-to-peer / push-pull) snellere en stabielere reactietijden behaalt dan broker-gebaseerde middleware (zoals MQTT), omdat er geen tussenliggende server/broker is die verwerkingsvertraging veroorzaakt _(MDPI, 2025)_.

# Literature gap
Hoewel de theoretische eigenschappen van TCP, UDP en JSON versus binaire data bekend zijn, ontbreekt in de literatuur specifieke kwantitatieve meetdata over directe C++ socket-implementaties voorgescheiden multi-zone robotvlote _(Viscon Group, 2024)_.