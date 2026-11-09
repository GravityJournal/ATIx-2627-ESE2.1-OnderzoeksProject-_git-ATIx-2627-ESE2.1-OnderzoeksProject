# Literatuuronderzoek – Betrouwbare communicatie tussen twee robotvloten

## Zoekstrategie

Voor dit literatuuronderzoek is gezocht naar informatie over betrouwbare communicatie tussen afzonderlijke systemen. Hierbij is gebruikgemaakt van technische documentatie, officiële standaarden en wetenschappelijke publicaties.

Er is onder andere gezocht via Google Scholar en IEEE Xplore. Daarnaast zijn de officiële documentatie van TCP en MQTT en de VDA 5050-standaard geraadpleegd.

De belangrijkste onderwerpen binnen het literatuuronderzoek zijn berichtaflevering, bevestigingen, verbindingsproblemen, systeemuitval en het voorkomen van dubbele opdrachten.

## Deelvraag 1 – Welke eigenschappen en verschillen hebben TCP en MQTT bij het uitwisselen van berichten tussen twee afzonderlijke systemen?

### TCP

TCP (Transmission Control Protocol) is een communicatieprotocol dat zorgt voor een betrouwbare en geordende overdracht van gegevens tussen twee systemen. TCP gebruikt volgnummering, bevestigingen (ACK) en het opnieuw verzenden van verloren gegevens om ervoor te zorgen dat de gegevensstroom correct aankomt (Eddy, 2022).

Een belangrijk voordeel van TCP is dat de applicatie niet zelf hoeft te controleren of afzonderlijke netwerkpakketten verloren zijn gegaan. TCP regelt dit op transportniveau.

Er is wel een belangrijk verschil tussen een TCP-bevestiging en een bevestiging vanuit de applicatie. Een TCP-ACK geeft aan dat gegevens door de TCP-ontvanger zijn ontvangen. Dit betekent niet automatisch dat de applicatie het bericht heeft verwerkt of dat een overdrachtsopdracht is uitgevoerd. Daarvoor is een aanvullende bevestiging vanuit de applicatie nodig (Eddy, 2022).

### MQTT

MQTT (Message Queuing Telemetry Transport) is een lichtgewicht communicatieprotocol dat gebruikmaakt van een publish/subscribe-systeem. Hierbij verstuurt een systeem berichten naar een centrale broker. Andere systemen kunnen zich abonneren op onderwerpen (topics) en ontvangen vervolgens de bijbehorende berichten (OASIS, 2019).

MQTT heeft drie verschillende Quality of Service-niveaus (QoS):

- QoS 0 – At most once: het bericht wordt maximaal één keer verzonden. Er is geen bevestiging en het bericht kan verloren gaan.
- QoS 1 – At least once: het bericht wordt minimaal één keer afgeleverd. Wanneer een bevestiging uitblijft, kan het bericht opnieuw worden verzonden. Hierdoor kan het dubbel aankomen.
- QoS 2 – Exactly once: het MQTT-protocol gebruikt meerdere berichten en bevestigingen om dubbele aflevering binnen de MQTT-communicatie te voorkomen (OASIS, 2019).

MQTT biedt daarnaast mogelijkheden om sessiegegevens en nog niet afgehandelde berichten te bewaren. Hierdoor kan communicatie na een tijdelijke verbindingsonderbreking worden hervat. Dit is afhankelijk van de ingestelde sessieduur en de ondersteuning van de client en broker (OASIS, 2019).

Een belangrijk aandachtspunt is dat QoS 2 niet automatisch garandeert dat een fysieke of andere applicatiehandeling nooit dubbel wordt uitgevoerd. Het protocol regelt de berichtaflevering, maar de applicatie moet zelf bijhouden welke opdrachten al zijn verwerkt.

### Vergelijking TCP en MQTT

TCP en MQTT hebben allebei mogelijkheden om betrouwbare communicatie te ondersteunen, maar werken op een andere manier.

TCP richt zich op het betrouwbaar en in de juiste volgorde versturen van gegevens. MQTT biedt daarnaast een berichtenstructuur met een broker, topics en verschillende afleveringsgaranties.

Voor de casus van Viscon Group is vooral belangrijk dat een overdrachtsverzoek niet verloren gaat en niet dubbel wordt uitgevoerd. Daarom moet niet alleen naar de aflevering van berichten worden gekeken, maar ook naar de verwerking ervan.

## Deelvraag 2 – Hoe gaan TCP en MQTT om met netwerkproblemen en het opnieuw opstarten van een systeem tijdens het uitwisselen van overdrachtsberichten?

### TCP bij verbindingsproblemen

TCP probeert verloren netwerkgegevens opnieuw te verzenden. Wanneer een verbinding tijdelijk problemen heeft, kan TCP hierdoor alsnog zorgen voor een correcte gegevensoverdracht. TCP biedt echter geen ingebouwde garantie dat een applicatie na een verbroken verbinding precies weet welke opdrachten al zijn verwerkt (Eddy, 2022).

Een voorbeeld hiervan is wanneer zone A een overdrachtsverzoek verstuurt en zone B het verzoek ontvangt. Als de bevestiging vanuit zone B verloren gaat, weet zone A niet zeker of het verzoek al is verwerkt.

Zone A kan het verzoek opnieuw versturen. Zonder aanvullende controle kan zone B hetzelfde verzoek daardoor meerdere keren verwerken.

Dit laat zien waarom een applicatiebevestiging en een uniek berichtnummer belangrijk kunnen zijn.

### MQTT bij verbindingsproblemen

MQTT biedt verschillende mogelijkheden om met verbindingsproblemen om te gaan. Bij QoS 1 en QoS 2 worden berichten en bevestigingen gebruikt om de aflevering te controleren. Wanneer een bevestiging uitblijft, kan een bericht opnieuw worden verzonden (OASIS, 2019).

MQTT 5.0 ondersteunt ook het bewaren van sessiegegevens na het verbreken van een verbinding. Met de Session Expiry Interval kan worden ingesteld hoelang een sessie beschikbaar blijft. Hierdoor kunnen onder andere abonnementen en nog niet afgehandelde berichten behouden blijven (OASIS, 2019).

Het opnieuw opstarten van een systeem vraagt wel extra aandacht. Wanneer een client of broker niet de juiste gegevens bewaart, kunnen berichten of sessiegegevens alsnog verloren gaan. De betrouwbaarheid hangt daarom niet alleen af van het QoS-niveau, maar ook van de instellingen en de opslagmogelijkheden van de gebruikte software.

### Voorkomen van dubbele opdrachten

Voor beide communicatiemethoden is het belangrijk om onderscheid te maken tussen het ontvangen van een bericht en het uitvoeren van een opdracht.

Een mogelijke oplossing is het gebruik van een uniek ID per overdrachtsverzoek. De ontvangende applicatie kan controleren of een opdracht-ID al eerder is verwerkt. Als hetzelfde bericht opnieuw binnenkomt, kan het systeem herkennen dat het om een bestaande opdracht gaat.

De VDA 5050-standaard gebruikt bijvoorbeeld een orderId en orderUpdateId om transportopdrachten en updates daarvan te identificeren. Hierdoor kunnen systemen herkennen bij welke opdracht een bericht hoort (VDA & VDMA, 2026).

Dit principe is interessant voor de casus van Viscon Group. Een uniek overdrachtsnummer kan ervoor zorgen dat een opnieuw ontvangen verzoek niet automatisch als een nieuwe opdracht wordt behandeld.

## Deelvraag 3 – Welke communicatiemethode is op basis van betrouwbaarheid, prestaties en implementatie het meest geschikt voor de overdracht tussen de twee robotvloten?

### Bestaande toepassingen

De VDA 5050 is een standaard voor communicatie tussen een centraal fleetmanagementsysteem en mobiele robots. De standaard beschrijft hoe opdrachten en statusinformatie tussen deze systemen worden uitgewisseld. MQTT wordt hierbij gebruikt als communicatieprotocol (VDA & VDMA, 2026).

De standaard laat zien dat MQTT in de intralogistiek kan worden toegepast. Ook wordt gebruikgemaakt van opdrachtidentificatie met orderId en orderUpdateId.

De VDA 5050 richt zich echter op de communicatie tussen fleet control en mobiele robots. De specifieke communicatie en overdracht van opdrachten tussen twee afzonderlijke robotvloten valt niet automatisch binnen deze standaard.

### Betrouwbaarheid en prestaties

Uit de technische documentatie blijkt dat TCP en MQTT verschillende eigenschappen hebben op het gebied van berichtaflevering.

Bij TCP wordt de betrouwbaarheid geregeld door het protocol zelf. Voor het controleren van de daadwerkelijke verwerking van een overdrachtsopdracht is daarnaast een applicatiebevestiging nodig (Eddy, 2022).

Bij MQTT kan het QoS-niveau worden gekozen op basis van de gewenste afleveringsgarantie. QoS 1 biedt minimaal één aflevering, terwijl QoS 2 dubbele aflevering binnen het MQTT-protocol voorkomt. QoS 2 gebruikt hiervoor een uitgebreidere uitwisseling van bevestigingen (OASIS, 2019).

De keuze tussen deze methoden hangt daarom niet alleen af van de betrouwbaarheid, maar ook van de snelheid, complexiteit en manier waarop de applicatie berichten verwerkt.

### Vergelijking binnen het onderzoek

Om te bepalen welke methode het beste past bij de casus, worden TCP en MQTT met elkaar vergeleken binnen een eenvoudig prototype.

Het prototype bestaat uit twee afzonderlijke programma's die zone A en zone B voorstellen. Het ene programma verstuurt een overdrachtsverzoek en het andere programma ontvangt het verzoek en stuurt een bevestiging terug.

Binnen het prototype kunnen de volgende mogelijkheden worden onderzocht:

- TCP met een aanvullende applicatiebevestiging.
- MQTT met QoS 1.
- MQTT met QoS 2.

Bij de vergelijking wordt gekeken naar de betrouwbaarheid van de berichtaflevering, de snelheid van de communicatie, het gedrag bij verbindingsproblemen en de complexiteit van de implementatie.

Bij MQTT QoS 1 kan bijvoorbeeld worden onderzocht hoe dubbele berichten worden herkend met behulp van unieke opdracht-ID's. Bij QoS 2 kan worden gekeken naar de invloed van de extra bevestigingsstappen op de communicatiesnelheid.

De literatuur geeft inzicht in de werking van de verschillende methoden, maar de uiteindelijke geschiktheid voor de casus moet nog met het prototype worden onderzocht.

## Literature gap

Uit het literatuuronderzoek blijkt dat er veel informatie beschikbaar is over TCP, MQTT en betrouwbare berichtaflevering. Ook bestaan er standaarden zoals VDA 5050, waarin communicatie tussen fleetmanagementsystemen en mobiele robots wordt beschreven (VDA & VDMA, 2026).

Er is echter nog niet vastgesteld welke communicatiemethode het meest geschikt is voor de specifieke situatie van Viscon Group. De communicatie tussen twee afzonderlijke robotvloten, die via een overdrachtspunt goederen uitwisselen, vraagt om aanvullende aandacht.

De belangrijkste openstaande punten zijn gekoppeld aan de drie deelvragen:

| Gap | Wat is al bekend | Wat nog onderzocht moet worden | Deelvraag |
|---|---|---|---|
| 1 | De werking en eigenschappen van TCP en MQTT zijn beschreven in officiële standaarden. | Welke eigenschappen zijn het belangrijkst voor communicatie tussen twee afzonderlijke robotvloten? | Deelvraag 1 |
| 2 | TCP en MQTT hebben mogelijkheden om berichten opnieuw te verzenden en verbindingen te herstellen. | Hoe gedragen beide methoden zich bij verbindingsuitval en het opnieuw opstarten van systemen? | Deelvraag 2 |
| 3 | Er bestaan verschillende afleveringsgaranties en mogelijkheden om dubbele berichten te herkennen. | Welke methode biedt de beste combinatie van betrouwbaarheid, snelheid en implementatiegemak binnen de casus? | Deelvraag 3 |

Wat nog niet bekend is, is welke methode het beste aansluit bij de overdracht tussen zone A en zone B. Vooral het voorkomen van verloren of dubbel verwerkte opdrachten en het herstellen van communicatie na een storing zijn hierbij belangrijk.

Daarom worden TCP en MQTT binnen een eenvoudig prototype met elkaar vergeleken. De resultaten van dit onderzoek moeten uiteindelijk leiden tot een onderbouwde keuze voor de communicatiemethode.

## Bronnen

Eddy, W. (Red.). (2022). *Transmission Control Protocol (TCP)* (RFC 9293). Internet Engineering Task Force. https://doi.org/10.17487/RFC9293

OASIS. (2019). *MQTT Version 5.0* (OASIS Standard). https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html

VDA & VDMA. (2026). *VDA 5050: Interface for the communication between mobile robots and a fleet control* (Version 3.0.0). https://www.vda.de/en/topics/automotive-industry/vda-5050

Eclipse Paho. (z.d.). *Quality of service*. Eclipse Foundation. https://eclipse-paho.github.io/paho.mqtt.c/MQTTClient/html/qos.html