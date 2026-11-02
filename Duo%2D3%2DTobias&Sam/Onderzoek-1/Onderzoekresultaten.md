# 3. Data verzamelen

## 3.1 Inleiding

In deze fase van ons faseplan wordt onderzocht hoe twee robotvloten (/ robots) informatie met elkaar kunnen uitwisselen en hoe het transportsysteem betrouwbaar kan blijven werken wanneer het gedeelde overdrachtspunt tijdelijk niet beschikbaar is (door bijvoorbeeld: onderhoud of schoonmaak).

Voor het beantwoorden van de deelvragen is gebruikgemaakt van technische documentatie en wetenschappelijk onderzoek. Hierbij is gekeken naar communicatie tussen automatische voertuigen, verschillende communicatietechnieken en manieren om berichtenverlies, vertragingen en netwerkuitval op te vangen.

De verzamelde informatie wordt per deelvraag besproken. Vervolgens worden de mogelijke oplossingen vergeleken om te bepalen welke technieken het beste aansluiten bij de situatie van Viscon Group.

## 3.2 Deelvraag 1: Welke informatie moeten de twee robotvloten(/ robots) met elkaar uitwisselen om het transport via het gedeelde overdrachtspunt goed te laten verlopen?

Om transport tussen twee gescheiden robotvloten(/robots) goed te laten verlopen, moet het systeem niet alleen weten welke goederen moeten worden vervoerd, maar ook wat de actuele status van het overdrachtspunt en de betrokken transportopdrachten is.

Chen et al. (2020) beschrijven hoe automatische voertuigen en andere geautomatiseerde systemen hun werkzaamheden moeten afstemmen om transporttaken efficiënt uit te voeren. Hun onderzoek laat zien dat de planning van verschillende voertuigen onderling afhankelijk is. Dit is ook relevant voor Viscon Group, omdat beide robotvloten(/robots) hetzelfde overdrachtspunt gebruiken en transportopdrachten in beide richtingen moeten uitvoeren.

Op basis hiervan zijn vijf categorieën informatie belangrijk.

### 3.2.1 Status van het overdrachtspunt

De robotvloten(/ robots) moeten kunnen vaststellen of het overdrachtspunt beschikbaar is voor een nieuwe overdracht.

De status moet minimaal onderscheid maken tussen beschikbaar, bezet, gesloten voor reiniging of onderhoud, en buiten gebruik door een storing. Daarnaast is het belangrijk dat bekend is wanneer de status voor het laatst is bijgewerkt.

Wanneer het overdrachtspunt tijdelijk gesloten is, moeten beide robotvloten(/ robots) deze wijziging ontvangen. Zo wordt voorkomen dat een robot met een nieuwe overdracht begint terwijl het overdrachtspunt niet beschikbaar is.

Alleen een melding dat het overdrachtspunt beschikbaar is, is niet voldoende. Het systeem moet ook voorkomen dat beide robotvloten(/ robots) tegelijkertijd aanspraak maken op dezelfde overdrachtsmogelijkheid. Hiervoor moet een overdracht kunnen worden gereserveerd en bevestigd.

### 3.2.2 Transportopdrachten

Voor iedere transportopdracht moet duidelijk zijn wat er moet worden vervoerd en tussen welke zones de overdracht plaatsvindt.

De volgende gegevens zijn hiervoor nodig:

- Een uniek identificatienummer van de transportopdracht.
- De identificatie van het goed, de krat of de pallet.
- De brongebied en de bestemmingsgebied.
- De prioriteit van de opdracht en eventueel de gewenste uitvoeringstijd.
- De actuele status van de opdracht, bijvoorbeeld aangemaakt, toegewezen, wachtend op overdracht, overgedragen of afgerond.

Met een uniek identificatienummer kan het systeem herkennen of een ontvangen bericht bij een bestaande opdracht hoort. Dit helpt voorkomen dat dezelfde transportopdracht meerdere keren wordt aangemaakt of uitgevoerd.

De opdracht moet bovendien altijd de juiste bron- en bestemmingszone bevatten. Een robotvloot mag uitsluitend opdrachten uitvoeren die binnen de eigen hygiënezone vallen. De overdracht tussen zones moet via het daarvoor aangewezen overdrachtspunt plaatsvinden.

### 3.2.3 Status en beschikbaarheid van robots

De robotvloten(/ robots) moeten voldoende informatie uitwisselen om te bepalen of een transportopdracht kan worden uitgevoerd.

Daarvoor zijn met name de beschikbaarheid van een robot, de actuele opdrachtstatus en eventuele storingen relevant. Een indicatie van de verwachte aankomsttijd kan daarnaast helpen om transportopdrachten beter op elkaar af te stemmen.

Wanneer een robot vertraagd is of een storing heeft, kan het systeem daarmee rekening houden. Het kan bijvoorbeeld een opdracht uitstellen, een andere geschikte robot inzetten of voorkomen dat het overdrachtspunt onnodig lang bezet blijft.

Niet alle interne robotgegevens hoeven hiervoor te worden uitgewisseld. Alleen informatie die nodig is voor de transportcoördinatie hoeft tussen de robotvloten(/ robots) beschikbaar te zijn.

### 3.2.4 Bevestigingen van overdrachten

Het systeem moet kunnen vaststellen of een transportopdracht daadwerkelijk is uitgevoerd.

Daarvoor zijn bevestigingen nodig bij belangrijke momenten in het overdrachtsproces. Denk aan het accepteren van een opdracht, het gereedzetten van een goed, het overnemen van het goed door de ontvangende robotvloot en het afronden van de overdracht.

Een ontvangen bericht betekent namelijk niet automatisch dat de fysieke overdracht is uitgevoerd. De status van de transportopdracht moet daarom pas worden gewijzigd wanneer de bijbehorende stap daadwerkelijk is bevestigd.

Iedere overdracht moet daarnaast worden geregistreerd met het tijdstip, de betrokken robots en het gebruikte overdrachtspunt. Dit sluit aan bij de randvoorwaarden van Viscon Group, waarin achteraf aantoonbaar moet zijn hoe een overdracht heeft plaatsgevonden.

### 3.2.5 Actualiteit van informatie en verbindingsstatus

Ten slotte moet het systeem kunnen vaststellen of de ontvangen informatie nog actueel is.

Bij belangrijke berichten zijn daarom een tijdstip, een uniek bericht- of opdrachtnummer en eventueel een versienummer van de status nuttig. Hierdoor kan het systeem herkennen dat een ontvangen bericht ouder is dan de informatie die al beschikbaar is.

Ook moet duidelijk zijn wanneer een robotvloot of communicatiesysteem niet meer bereikbaar is. Hiervoor kunnen periodieke statusberichten of heartbeats worden gebruikt.

Als de verbinding uitvalt en de actuele status van het overdrachtspunt niet meer kan worden vastgesteld, mag het systeem niet zonder meer aannemen dat het overdrachtspunt nog beschikbaar is.

### Antwoord op deelvraag 1

 
De twee robotvloten moeten berichten uitwisselen om transportopdrachten, het gedeelde overdrachtspunt en de voortgang van overdrachten te coördineren. Op basis van de onderzochte informatie zijn de volgende technische eisen opgesteld.
**1. Status van het overdrachtspunt**
Het systeem moet de status van het overdrachtspunt bijhouden. Hiervoor zijn minimaal de statussen `OPEN`, `RESERVED`, `CLOSED` en `FAULT` nodig. Bij `OPEN` is het punt beschikbaar, bij `RESERVED` is het gereserveerd (voor bijvoorbeeld een overdracht), bij `CLOSED` is het gesloten voor bijvoorbeeld reiniging of onderhoud en bij `FAULT` is er een storing.
Voordat een overdracht begint, moet het systeem controleren of het overdrachtspunt beschikbaar is en correct is gereserveerd. Beide robotvloten moeten statuswijzigingen ontvangen. Als de status onbekend is of niet betrouwbaar kan worden vastgesteld, mag geen nieuwe overdracht worden gestart.
**2. Transportopdrachten**
Iedere transportopdracht moet minimaal de volgende gegevens bevatten:
*   Een uniek opdracht-ID.
    
*   De identificatie van het te vervoeren goed, de krat of de pallet.
    
*   De bron- en bestemmingszone.
    
*   De actuele status van de opdracht.
    
*   Een tijdstempel van het bericht.
    
De opdrachtstatus moet aangeven of een opdracht bijvoorbeeld is aangemaakt, geaccepteerd, wachtend op overdracht of afgerond. Het systeem moet aan de hand van het opdracht-ID kunnen controleren of een opdracht al eerder is ontvangen of verwerkt. Hierdoor wordt voorkomen dat een opnieuw ontvangen bericht automatisch leidt tot een dubbele uitvoering.
**3. Beschikbaarheid van robots**
De robotvloten moeten informatie kunnen uitwisselen over de beschikbaarheid van robots, actieve transportopdrachten en eventuele storingen. Indien nodig kan ook de verwachte aankomsttijd worden meegestuurd om het gebruik van het overdrachtspunt te coördineren.
Een robot mag alleen opdrachten uitvoeren die binnen de eigen hygiënezone vallen. Het overdrachtspunt vormt de aangewezen locatie voor overdrachten tussen de zones.
**4. Bevestigingen van berichten en overdrachten**
Het systeem moet onderscheid maken tussen een bevestiging dat een bericht is ontvangen en een bevestiging dat een fysieke overdracht is uitgevoerd. Belangrijke gebeurtenissen, zoals het accepteren van een opdracht, het reserveren van het overdrachtspunt en het afronden van een overdracht, moeten afzonderlijk worden geregistreerd.
Iedere gebeurtenis moet gekoppeld zijn aan het betreffende opdracht-ID en een tijdstempel bevatten. Hierdoor kan achteraf worden vastgesteld welke stappen zijn uitgevoerd en waar eventuele vertragingen of fouten zijn ontstaan.
**5. Actualiteit en verbindingsstatus**
Berichten moeten een tijdstempel en een unieke identificatie bevatten. Voor statusupdates moet het systeem kunnen bepalen of een bericht nieuwer is dan de laatst verwerkte status. Dit voorkomt dat verouderde informatie een recentere status overschrijft.
Daarnaast moeten de robotvloten periodiek statusberichten (_heartbeats_) versturen. Wanneer deze berichten gedurende een ingestelde termijn uitblijven, moet het systeem de verbinding als mogelijk verstoord markeren.
**6. Afhandeling van netwerkuitval**
Wanneer de verbinding wegvalt, moeten nog niet afgeronde transportopdrachten geregistreerd blijven. Na herstel van de verbinding moeten de robotvloten hun actuele status en openstaande opdrachten controleren voordat het transport wordt hervat.
Als niet kan worden vastgesteld of het overdrachtspunt beschikbaar is, moet het systeem wachten totdat de status opnieuw betrouwbaar bekend is. Het opnieuw ontvangen van een opdracht mag niet automatisch leiden tot een tweede uitvoering.
Deze technische eisen bepalen welke gegevens de robotvloten moeten uitwisselen en welke controles nodig zijn om het tweerichtingsvervoer betrouwbaar te coördineren. Ze vormen tevens de basis voor het ontwerp van het prototype en de bijbehorende tests.

## 3.3 Deelvraag 2: Welke communicatietechnieken zijn het meest geschikt voor het uitwisselen van informatie tussen de twee robotvloten(/ robots)?

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

onderweg

## 3.4 Deelvraag 3: Hoe kan betrouwbare communicatie tussen de twee robotvloten(/ robots) worden bewaard bij vertragingen of tijdelijke netwerkuitval?

Uit de technische documentatie blijkt dat een betrouwbare communicatieoplossing uit meerdere onderdelen moet bestaan. Alleen een protocol gebruiken dat berichten kan herverzenden, is niet voldoende. Het systeem moet ook omgaan met oude berichten, dubbele opdrachten en een tijdelijk onbereikbare robotvloot.

### 3.4.1 Berichten opnieuw versturen en bevestigen

Wanneer een belangrijk bericht niet aankomt, moet het systeem kunnen herkennen dat de overdracht van het bericht niet succesvol is verlopen.

MQTT QoS 1 ondersteunt bevestiging van berichtaflevering en herverzending wanneer dat nodig is. Hierbij kan hetzelfde bericht meerdere keren aankomen. Daarom moet de ontvanger dubbele berichten kunnen herkennen.

Voor transportopdrachten kan dit worden opgelost door iedere opdracht een uniek identificatienummer te geven. Wanneer dezelfde opdracht opnieuw binnenkomt, controleert het systeem of de opdracht al is verwerkt. De opdracht wordt dan niet opnieuw uitgevoerd als dat tot een dubbele fysieke overdracht zou leiden.

Ook moet onderscheid worden gemaakt tussen een bevestiging dat een bericht is ontvangen en een bevestiging dat de bijbehorende transportactie is uitgevoerd. Dat zijn twee verschillende gebeurtenissen.

### 3.4.2 Controleren of informatie nog actueel is

Een belangrijk risico ontstaat wanneer berichten te laat aankomen.

Stel dat het overdrachtspunt aanvankelijk beschikbaar is, maar vervolgens wordt gesloten voor reiniging. Wanneer de melding over de eerdere beschikbare status later alsnog binnenkomt, kan een robotvloot een verkeerde beslissing nemen als het systeem de oudste informatie accepteert.

Daarom moeten berichten voorzien zijn van een tijdstip of andere informatie waarmee de volgorde kan worden bepaald. Ook moet het systeem een geldigheidsduur vastleggen voor tijdgevoelige informatie.

MQTT 5.0 ondersteunt een message expiry interval waarmee de levensduur van berichten kan worden beperkt. ROS 2 biedt met de lifespan-instelling een vergelijkbare mogelijkheid om verouderde berichten niet meer af te leveren (OASIS, 2019; Open Robotics, z.d.).

Daarnaast moet het systeem controleren of de ontvangen toestand nog voldoende actueel is. Als niet meer betrouwbaar kan worden vastgesteld of het overdrachtspunt beschikbaar is, moet de toestand als onbekend worden behandeld. Een robot mag dan niet uitsluitend op basis van een oude melding aannemen dat een overdracht veilig kan plaatsvinden.

### 3.4.3 Detecteren van verbindingsproblemen

De robotvloten(/ robots) moeten kunnen vaststellen wanneer de andere kant niet meer bereikbaar is.

Dit kan met periodieke statusberichten of heartbeats. Als een heartbeat gedurende een vooraf ingestelde periode uitblijft, kan het systeem de verbinding als verstoord beschouwen.

De maximale tijd die zonder een bericht mag verstrijken, moet worden afgestemd op de toepassing. Een te korte termijn kan onnodige storingsmeldingen veroorzaken. Een te lange termijn zorgt ervoor dat een netwerkprobleem mogelijk te laat wordt ontdekt.

Na het vaststellen van een storing moet het systeem de betreffende transportopdrachten veilig afhandelen. Opdrachten waarvoor de actuele status van het overdrachtspunt nodig is, mogen niet worden uitgevoerd zolang die status niet betrouwbaar kan worden vastgesteld.

### 3.4.4 Veilig omgaan met tijdelijke netwerkuitval

De randvoorwaarden van Viscon Group stellen dat communicatie-uitval nooit mag leiden tot opdrachten buiten de eigen hygiënezone of tot verloren of dubbel uitgevoerde opdrachten.

Daarom moet het systeem bij netwerkuitval een vooraf bepaalde veilige toestand bereiken. Wanneer niet kan worden vastgesteld of het overdrachtspunt beschikbaar is, wordt een nieuwe overdracht niet gestart op basis van verouderde informatie.

De transportopdrachten kunnen worden bewaard totdat de communicatie weer beschikbaar is. Daarbij moet iedere opdracht een uniek identificatienummer behouden en moet de actuele status worden opgeslagen.

Ook moet worden voorkomen dat het overdrachtspunt onbeperkt gereserveerd blijft voor een robot die door een storing niet meer kan aankomen. Een reservering kan daarom een geldigheidsduur krijgen. Nadat die termijn is verstreken, mag de reservering alleen worden vrijgegeven nadat is gecontroleerd dat het overdrachtspunt en de transportstatus weer veilig zijn.

De robots moeten ondertussen binnen hun eigen hygiënezone blijven. Bij eventuele alternatieve planning mag een robot nooit worden toegewezen aan een opdracht waarvoor hij niet bevoegd is.

### 3.4.5 Transport hervatten na herstel van de verbinding

Wanneer de netwerkverbinding wordt hersteld, moet het systeem eerst controleren welke opdrachten nog openstaan en welke stappen al zijn uitgevoerd.

Het is niet veilig om alle berichten die tijdens de storing zijn ontstaan zonder controle opnieuw uit te voeren. Sommige opdrachten kunnen inmiddels zijn geannuleerd of door een ander systeemdeel zijn afgehandeld.

Daarom moeten beide robotvloten(/ robots) hun actuele status uitwisselen en de geregistreerde opdrachten met elkaar vergelijken. Hierbij wordt gecontroleerd welke berichten zijn verwerkt, welke overdrachten zijn bevestigd en welke opdrachten nog moeten worden uitgevoerd.

Pas daarna worden de resterende opdrachten opnieuw ingepland. Hierdoor kan het systeem voorkomen dat transportopdrachten verloren gaan of dubbel worden uitgevoerd.

### 3.4.6 Overzicht van de maatregelen

| Probleem | Benodigde maatregel | Verwacht resultaat |
|---|---|---|
| Bericht komt niet aan | Bevestigingen en waar nodig herverzending | Belangrijke berichten kunnen opnieuw worden aangeboden |
| Bericht komt meerdere keren aan | Unieke opdracht-ID's en controle op reeds verwerkte opdrachten | Dubbele uitvoering wordt voorkomen |
| Bericht komt te laat aan | Tijdstempel, volgnummer en geldigheidsduur | Verouderde informatie wordt herkend |
| Robotvloot is niet bereikbaar | Heartbeats en time-outs | Verbindingsproblemen worden tijdig herkend |
| Overdrachtspunt is mogelijk gesloten | Veilige toestand en controle van de actuele status | Onveilige overdrachten worden voorkomen |
| Reservering blijft achter na storing | Reservering met geldigheidsduur en gecontroleerde vrijgave | Het overdrachtspunt blijft niet onnodig geblokkeerd |
| Verbinding wordt hersteld | Statusuitwisseling en controle van openstaande opdrachten | Transport kan gecontroleerd worden hervat |

### Antwoord op deelvraag 3

onderweg




