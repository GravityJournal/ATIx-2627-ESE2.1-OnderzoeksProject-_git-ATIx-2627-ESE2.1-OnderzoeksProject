Deelvraag 2: Welke communicatietechnieken zijn het meest geschikt voor het uitwisselen van informatie tussen de twee robotvloten(/ robots)?

Om deze deelvraag te beantwoorden, zijn drie communicatietechnieken onderzocht: TCP-sockets, MQTT en ROS 2 met DDS.

Deze technieken bieden verschillende mogelijkheden. TCP levert een betrouwbare gegevensverbinding, MQTT is gericht op berichtenuitwisseling via een broker en ROS 2 biedt communicatiefuncties die specifiek aansluiten bij robotica.

### 3.3.1 TCP-sockets

TCP is een transportprotocol dat een betrouwbare, geordende gegevensstroom tussen twee endpoints ondersteunt. Het protocol detecteert onder andere verloren gegevens en gebruikt hertransmissies om de betrouwbaarheid van de verbinding te verbeteren (IETF, 2022).

Een TCP-verbinding kan daarom geschikt zijn voor het rechtstreeks uitwisselen van transportopdrachten en bevestigingen tussen twee systemen.

Een belangrijk nadeel is dat TCP alleen de gegevensoverdracht regelt. De applicatie moet zelf bepalen hoe berichten worden opgebouwd, hoe opdrachten worden geïdentificeerd en hoe de communicatie wordt hersteld nadat een verbinding wegvalt.

Ook moeten functies zoals berichtbevestigingen op toepassingsniveau, het herkennen van dubbele opdrachten en het controleren van verouderde informatie zelf worden ontworpen.

TCP is daarmee een mogelijke oplossing wanneer beide robotvloten(/ robots) een eigen, rechtstreeks communicatieprotocol gebruiken. Voor een systeem met meerdere partijen die zich op verschillende soorten berichten abonneren, is een aanvullende berichtenarchitectuur nodig.

### 3.3.2 MQTT

MQTT is een lichtgewicht communicatieprotocol dat werkt met een publish/subscribe-model. Een verzender publiceert berichten bij een broker, waarna systemen die op de betreffende onderwerpen zijn geabonneerd de berichten kunnen ontvangen.

Hierdoor hoeven de twee robotvloten(/ robots) niet voortdurend rechtstreeks met elkaar verbonden te zijn. Beide kunnen bijvoorbeeld informatie over het overdrachtspunt publiceren en zich abonneren op de berichten die voor hun eigen transportplanning relevant zijn.

MQTT ondersteunt drie kwaliteitsniveaus voor berichtaflevering (OASIS, 2019):

| QoS-niveau | Werking | Geschikt voor |
|---|---|---|
| QoS 0 | Een bericht wordt maximaal één keer afgeleverd; verlies is mogelijk. | Niet-kritieke statusupdates waarbij een volgende update het verlies kan opvangen. |
| QoS 1 | Een bericht wordt ten minste één keer afgeleverd; dubbele ontvangst is mogelijk. | Transportopdrachten en belangrijke statusmeldingen wanneer de applicatie dubbele berichten correct verwerkt. |
| QoS 2 | Het protocol gebruikt een uitgebreidere uitwisseling om een bericht precies één keer af te leveren. | Berichten waarbij dubbele of verloren berichtaflevering niet aanvaardbaar is en de extra communicatieoverhead gerechtvaardigd is. |

MQTT 5.0 ondersteunt daarnaast onder andere het instellen van een verlooptermijn voor berichten. Hierdoor kunnen berichten die te lang bij de broker hebben gewacht, verlopen voordat ze bij een ontvanger worden afgeleverd.

Dit is belangrijk voor Viscon Group. Een oude melding dat het overdrachtspunt beschikbaar is, mag bijvoorbeeld niet alsnog worden gebruikt nadat het punt inmiddels voor onderhoud is gesloten.

Een aandachtspunt is dat de broker een belangrijk onderdeel van de communicatie wordt. Als deze niet bereikbaar is, kan de berichtuitwisseling worden onderbroken. De beschikbaarheid van de broker en de afhandeling van verbindingsproblemen moeten daarom in het ontwerp worden meegenomen.

Ook garandeert QoS 2 niet dat een fysieke transportopdracht over alle systemen en na iedere mogelijke storing precies één keer wordt uitgevoerd. Daarvoor zijn aanvullende controles op opdrachtniveau nodig.


### 3.3.3 ROS 2 met DDS

ROS 2 is een softwareframework voor robotica. De communicatie gebruikt middleware op basis van DDS, waarmee berichten tussen verschillende onderdelen van een robotsysteem kunnen worden uitgewisseld.

ROS 2 biedt verschillende Quality of Service-instellingen waarmee het gedrag van de communicatie kan worden afgestemd op de toepassing (Open Robotics, z.d.).

Belangrijke instellingen zijn:

- **Reliability:** bepaalt of berichten zo betrouwbaar mogelijk worden afgeleverd of dat het systeem minder betrouwbare, maar mogelijk lichtere communicatie gebruikt.
- **Lifespan:** bepaalt hoe lang een bericht bruikbaar blijft. Berichten die verlopen zijn voordat ze worden ontvangen, worden niet afgeleverd.
- **Deadline:** geeft aan met welke maximale tussenpozen berichten worden verwacht.
- **Liveliness:** helpt vaststellen of een communicatieonderdeel nog actief is.

Met deze instellingen kan een robotsysteem onderscheid maken tussen actuele en verouderde informatie. Ook kan het systeem signaleren wanneer een communicatieonderdeel niet meer op tijd berichten verstuurt.

Een belangrijk aandachtspunt is dat de Quality of Service-instellingen op elkaar moeten aansluiten. Incompatibele instellingen kunnen ervoor zorgen dat berichten niet worden afgeleverd.

ROS 2 met DDS is vooral interessant als de robotvloten(/ robots) al op ROS 2 zijn gebaseerd. In dat geval kan gebruik worden gemaakt van bestaande robotcommunicatie en de bijbehorende configuratiemogelijkheden. Wanneer de robotvloten(/ robots) verschillende gesloten leverancierssystemen gebruiken, moet eerst worden onderzocht of integratie mogelijk is.


### 3.3.4 Vergelijking van de communicatietechnieken

De drie technieken kunnen op basis van de gevonden documentatie als volgt worden vergeleken.

| Criterium | TCP-sockets | MQTT 5.0 | ROS 2 met DDS |
|---|---|---|---|
| Communicatiemodel | Rechtstreekse gegevensverbinding | Publish/subscribe via broker | Robotgerichte communicatie tussen nodes |
| Betrouwbare berichtoverdracht | Ja, op transportniveau | Instelbaar via QoS 0, 1 of 2 | Instelbaar via Quality of Service |
| Berichten laten verlopen | Zelf implementeren op applicatieniveau | Ondersteund via berichtvervaltermijn | Ondersteund via de lifespan-instelling |
| Afhandeling van dubbele opdrachten | Zelf implementeren | Nodig bij onder andere QoS 1 | Afhandeling op applicatieniveau blijft nodig |
| Afhankelijkheden | Eigen protocol en verbindingsbeheer | Broker en MQTT-clients | ROS 2-, DDS- en netwerkconfiguratie |
| Toepassing bij Viscon | Mogelijk voor een eigen communicatieprotocol | Geschikt voor uitwisseling van status en transportgebeurtenissen tussen systemen | Vooral geschikt wanneer de robotvloten(/ robots) al ROS 2 gebruiken |

De tabel is een vergelijking op basis van de documentatie en protocolkenmerken. Er zijn nog geen metingen uitgevoerd waarmee de daadwerkelijke vertraging of prestaties van deze technieken binnen de installatie van Viscon Group kunnen worden vastgesteld.

### Antwoord op deelvraag 2

Op basis van de onderzochte communicatietechnieken zijn TCP-sockets, MQTT en ROS 2 met DDS alle drie geschikt voor het uitwisselen van informatie tussen afzonderlijke systemen. De verschillen zitten voornamelijk in de manier waarop berichten worden verstuurd, de beschikbare betrouwbaarheidsinstellingen en de hoeveelheid functionaliteit die zelf moet worden geïmplementeerd.

TCP-sockets bieden betrouwbare en geordende gegevensoverdracht, maar vereisen dat de applicatie zelf verantwoordelijk is voor de berichtstructuur, bevestigingen op opdrachtniveau en het herstellen van de communicatie na een verbindingsstoring. Hierdoor moet relatief veel functionaliteit zelf worden ontwikkeld.
MQTT sluit goed aan op de situatie van Viscon Group, omdat het publish/subscribe-model het mogelijk maakt om transportopdrachten en statusupdates via een centrale broker uit te wisselen. Beide robotvloten kunnen zich abonneren op relevante berichten, zoals wijzigingen in de status van het overdrachtspunt en nieuwe transportopdrachten. Daarnaast bieden QoS-instellingen en berichtvervaltermijnen mogelijkheden om de berichtafhandeling betrouwbaarder te maken. Wel blijft de beschikbaarheid van de broker een belangrijk aandachtspunt.

ROS 2 met DDS biedt uitgebreide mogelijkheden voor communicatie binnen robotsystemen. De verschillende Quality of Service-instellingen maken het mogelijk om communicatie af te stemmen op de eisen van het transportsysteem. Deze techniek is vooral geschikt wanneer de robotvloten al gebruikmaken van ROS 2. Wanneer de bestaande robotsoftware andere communicatiesystemen gebruikt, moet eerst worden onderzocht of integratie mogelijk is.
Voor het softwareprototype is gekozen voor TCP-socketcommunicatie. Hiermee kan een directe verbinding tussen een client en server worden opgezet, waarmee de invloed van netwerkvertragingen en pakketverlies op de gegevensuitwisseling kan worden onderzocht.

Het prototype maakt geen gebruik van MQTT. De specifieke functionaliteiten van MQTT, zoals de broker, het publish/subscribe-model en de Quality of Service-instellingen, worden daarom niet praktisch getest.
Omdat MQTT gebruikmaakt van TCP/IP, kunnen de resultaten van het TCP-prototype wel inzicht geven in het gedrag van een onderliggende TCP-verbinding. De resultaten kunnen echter niet worden gebruikt om de specifieke betrouwbaarheid van MQTT te beoordelen.