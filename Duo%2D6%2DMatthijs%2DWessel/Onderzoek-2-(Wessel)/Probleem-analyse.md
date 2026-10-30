# 1. Probleemanalyse

## 1.1 Probleemcontext

Binnen de productie- en logistieke omgeving van Viscon Group worden goederen verplaatst tussen verschillende hygiënezones. Iedere zone beschikt over een eigen robotvloot. Omdat de hygiënevoorschriften dit vereisen, mogen robots niet buiten hun toegewezen zone rijden.

Om goederen toch tussen de zones te kunnen verplaatsen, wordt gebruikgemaakt van een gezamenlijk overdrachtspunt. Een robot uit zone A levert bijvoorbeeld een pallet af, waarna een robot uit zone B deze verder transporteert. Dit proces werkt ook andersom voor lege pallets en kratten.

Om deze overdrachten goed te laten verlopen, moeten de besturingssystemen van beide robotvloten informatie met elkaar kunnen uitwisselen. Hierbij moeten berichten over onder andere transportaanvragen, de beschikbaarheid van robots en de status van overdrachten betrouwbaar worden verstuurd.

Een belangrijk probleem ontstaat wanneer de communicatie wordt onderbroken of wanneer berichten niet op tijd aankomen. Hierdoor kunnen opdrachten blijven hangen, meerdere keren worden uitgevoerd of niet correct worden afgerond. Er moet daarom worden onderzocht welke communicatiemethode geschikt is om de samenwerking tussen de robotvloten betrouwbaar te laten verlopen.

## 1.2 Belang

- **Continuïteit van het productieproces:** Wanneer communicatieberichten niet aankomen, kunnen goederen niet op tijd worden overgedragen. Hierdoor kunnen vertragingen ontstaan in het logistieke proces of kan een productielijn stil komen te staan.
- **Betrouwbaarheid van opdrachten:** Het is belangrijk dat iedere transportopdracht correct wordt verwerkt. Dubbele of ontbrekende opdrachten kunnen ervoor zorgen dat robots verkeerde handelingen uitvoeren.
- **Veiligheid en hygiëne:** De communicatie mag er nooit toe leiden dat een robot buiten zijn eigen hygiënezone wordt ingezet. Ook moeten conflicten bij het overdrachtspunt worden voorkomen.
- **Controleerbaarheid:** Alle overdrachten moeten achteraf gecontroleerd kunnen worden. Hiervoor moeten berichten en opdrachten op een betrouwbare manier worden geregistreerd.
- **Technisch ontwerp:** De keuze voor een communicatiemethode heeft invloed op de verdere ontwikkeling van de robotvloot. De resultaten van dit onderzoek kunnen worden gebruikt om een geschikte communicatieoplossing te kiezen.

## 1.3 Literatuuronderzoek (samenvatting)

Voor dit onderzoek is gekeken naar bestaande informatie over TCP en MQTT. Beide communicatiemethoden kunnen worden gebruikt om gegevens tussen afzonderlijke systemen uit te wisselen.

TCP is een communicatieprotocol dat zorgt voor een betrouwbare en geordende overdracht van gegevens. Wanneer gegevens verloren gaan tijdens het versturen, kan TCP deze opnieuw verzenden. Hierdoor is TCP geschikt voor toepassingen waarbij gegevens volledig en in de juiste volgorde moeten aankomen (IETF, 2022).

MQTT is een lichtgewicht communicatieprotocol dat gebruikmaakt van een publish/subscribe-systeem. Hierbij worden berichten via een centrale broker uitgewisseld. MQTT heeft drie verschillende Quality of Service-niveaus (QoS). Deze niveaus bepalen hoe betrouwbaar berichten worden afgeleverd. Bij QoS 0 is aflevering niet gegarandeerd, bij QoS 1 kunnen berichten dubbel aankomen en bij QoS 2 wordt dubbele aflevering op protocolniveau voorkomen (OASIS, 2019).

Naast de berichtaflevering is het herstellen van communicatie belangrijk. MQTT biedt mogelijkheden om sessies en berichten te bewaren wanneer een client tijdelijk niet verbonden is. De werking hiervan is afhankelijk van de instellingen van de broker en de client (OASIS, 2019; Eclipse Mosquitto, z.d.).

Uit de literatuur blijkt dat TCP en MQTT allebei mogelijkheden bieden voor betrouwbare communicatie, maar op een verschillende manier werken. TCP richt zich voornamelijk op het betrouwbaar versturen van gegevens, terwijl MQTT aanvullende mogelijkheden biedt voor het beheren en afleveren van berichten (IETF, 2022; OASIS, 2019).

Deze eigenschappen zijn relevant voor de casus van Viscon Group, omdat de twee robotvloten overdrachtsverzoeken en bevestigingen moeten kunnen uitwisselen, ook wanneer er communicatieproblemen optreden.

## 1.4 Literature gap

Uit het literatuuronderzoek blijkt dat er veel informatie beschikbaar is over de werking van TCP en MQTT en de mogelijkheden die beide communicatiemethoden bieden (IETF, 2022; OASIS, 2019). Er is echter nog niet vastgesteld welke methode het meest geschikt is voor de specifieke situatie van Viscon Group.

De bestaande documentatie beschrijft voornamelijk de algemene werking van de protocollen. Er is nog onvoldoende duidelijkheid over hoe TCP en MQTT presteren bij het uitwisselen van overdrachtsinformatie tussen twee afzonderlijke robotvloten in verschillende hygiënezones.

Vooral het omgaan met tijdelijke verbindingsproblemen, het opnieuw opstarten van systemen en het voorkomen van dubbel verwerkte overdrachtsverzoeken is hierbij belangrijk.

Dit onderzoek richt zich daarom op het vergelijken van TCP en MQTT binnen een eenvoudig prototype. Door beide communicatiemethoden in dezelfde situatie te onderzoeken, kan worden bepaald welke methode het beste aansluit bij de eisen van de casus.

## 1.5 Doelstelling

Het doel van dit onderzoek is om vast te stellen welke communicatiemethode het meest geschikt is voor het betrouwbaar uitwisselen van overdrachtsinformatie tussen twee afzonderlijke robotvloten.

Door verschillende communicatieoplossingen met elkaar te vergelijken, wordt onderzocht hoe berichten correct kunnen worden afgeleverd en verwerkt, ook wanneer er sprake is van netwerkproblemen of systeemuitval.

De resultaten worden gebruikt om een onderbouwde keuze te maken voor de communicatie tussen de robotvloten binnen het uiteindelijke technische ontwerp.

## 1.6 Afbakening

**Binnen scope**

- Het versturen en ontvangen van berichten tussen de besturingssystemen van zone A en zone B.
- Het uitwisselen van informatie over overdrachtsverzoeken, beschikbaarheid, overdrachtsbevestigingen en afgeronde opdrachten.
- Het vergelijken van verschillende communicatiemethoden, zoals TCP en MQTT.
- Het onderzoeken van berichtbevestigingen en het voorkomen van dubbele verwerking van opdrachten.
- Het testen van de communicatie bij netwerkvertragingen, verbindingsonderbrekingen en het opnieuw opstarten van systemen.
- Het meten van berichtvertraging, berichtverlies en de betrouwbaarheid van de communicatie.

**Buiten scope**

- Het daadwerkelijk besturen van fysieke AGV's.
- Navigatie, routeplanning en locatiebepaling van robots.
- Het mechanische ontwerp en de werking van het overdrachtspunt.
- Het verdelen en prioriteren van transportopdrachten.
- Het ontwerpen van de volledige netwerkinfrastructuur van de productielocatie.
- Uitgebreide netwerkbeveiliging en encryptie.
- Het ontwerpen van de volledige fleet management-software.