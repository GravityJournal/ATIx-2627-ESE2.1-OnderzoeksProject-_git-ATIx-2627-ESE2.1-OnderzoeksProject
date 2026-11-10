### 3.3 Deelvraag 2: Welke communicatietechnieken zijn het meest geschikt voor het uitwisselen van informatie tussen de twee robotvloten?

Om deze deelvraag te beantwoorden, worden drie mogelijke communicatieoplossingen onderzocht en met elkaar vergeleken: rechtstreekse communicatie via eigen applicatieprotocol op basis van TCP-sockets, MQTT en ROS 2 met DDS.
Deze oplossingen verschillen in de manier waarop communicatie wordt georganiseerd. TCP is een transportprotocol dat zorgt voor betrouwbare en geordende gegevensoverdracht. MQTT is een applicatieprotocol dat gebruikmaakt van TCP en berichten uitwisselt via een centrale broker. ROS 2 maakt gebruik van DDS als communicatiemiddleware en biedt verschillende instellingen om de communicatie af te stemmen op robottoepassingen.
Omdat de oplossingen op verschillende niveaus van de communicatie werken, worden ze niet uitsluitend op hun technische eigenschappen vergeleken. Er wordt vooral gekeken naar de geschiktheid voor de situatie van Viscon Group. Hierbij zijn betrouwbaarheid, het verwerken van verouderde berichten, de afhandeling van dubbele opdrachten, implementatiecomplexiteit en de mogelijkheden voor communicatie tussen twee afzonderlijke robotvloten van belang.
Om tot een onderbouwde keuze te komen, worden de drie oplossingen eerst afzonderlijk onderzocht. Vervolgens worden ze met behulp van een Multi Criteria Analyse (MCA) beoordeeld.

#### 3.3.1 Rechtstreekse communicatie via eigen applicatieprotocol op basis van TCP-sockets

TCP (Transmission Control Protocol) is een transportprotocol dat een betrouwbare en geordende gegevensstroom tussen twee systemen ondersteunt. Wanneer gegevens verloren gaan tijdens de overdracht, kan TCP deze opnieuw verzenden. Hierdoor worden gegevens in de juiste volgorde afgeleverd zolang de verbinding beschikbaar blijft (IETF, 2022).
Met TCP-sockets kan een directe verbinding tussen een client en een server worden opgezet. Dit maakt het mogelijk om transportopdrachten, statusupdates en bevestigingen rechtstreeks tussen de twee robotvloten uit te wisselen.
Een belangrijk voordeel van deze oplossing is dat er geen aanvullende berichtenbroker nodig is. De communicatie kan relatief eenvoudig worden ingericht wanneer twee systemen rechtstreeks gegevens met elkaar moeten uitwisselen.
Een nadeel is dat TCP zelf geen applicatieberichten of transportopdrachten herkent. Het protocol verstuurt namelijk een gegevensstroom. De applicatie moet daarom zelf bepalen hoe berichten worden opgebouwd en waar een bericht begint en eindigt.
Ook moeten aanvullende functies zelf worden ontwikkeld. Denk hierbij aan:
*   Het identificeren van transportopdrachten met unieke ID's.
    
*   Het bevestigen van ontvangen en verwerkte opdrachten.
    
*   Het herkennen en voorkomen van dubbele opdrachten.
    
*   Het controleren van tijdstempels en verouderde berichten.
    
*   Het herstellen van de communicatie nadat een verbinding is weggevallen.
    
Voor de situatie van Viscon Group betekent dit dat TCP-sockets een mogelijke oplossing zijn voor rechtstreekse communicatie tussen twee robotvloten. De betrouwbaarheid van de gegevensoverdracht wordt door TCP ondersteund, maar de betrouwbaarheid van de volledige transportafhandeling is afhankelijk van de aanvullende software die wordt ontwikkeld.

#### 3.3.2 MQTT

MQTT (Message Queuing Telemetry Transport) is een applicatieprotocol dat gebruikmaakt van een publish/subscribe-model. Bij deze communicatiemethode worden berichten niet rechtstreeks naar een andere robotvloot gestuurd, maar gepubliceerd bij een centrale broker.
Systemen die geïnteresseerd zijn in bepaalde informatie kunnen zich abonneren op specifieke onderwerpen, ook wel topics genoemd. De broker zorgt ervoor dat gepubliceerde berichten bij de juiste ontvangers terechtkomen.
Voor Viscon Group kan dit bijvoorbeeld als volgt worden toegepast:
*   De eerste robotvloot publiceert een bericht wanneer het overdrachtspunt beschikbaar of gesloten is.
    
*   De tweede robotvloot abonneert zich op de status van het overdrachtspunt.
    
*   Beide robotvloten kunnen transportopdrachten en bevestigingen via afzonderlijke topics uitwisselen.
    
*   Wanneer het overdrachtspunt tijdelijk wordt gesloten voor reiniging of onderhoud, kan deze status via de broker aan beide robotvloten worden doorgegeven.
    
Een voordeel van MQTT is dat beide robotvloten niet rechtstreeks met elkaar verbonden hoeven te zijn. Hierdoor is het eenvoudiger om meerdere systemen aan de communicatie toe te voegen.
MQTT ondersteunt drie Quality of Service-niveaus (QoS) voor de aflevering van berichten (OASIS, 2019):
| QoS-niveau | Werking | Mogelijke toepassing |
| --- | --- | --- |
| QoS 0 | Een bericht wordt maximaal één keer afgeleverd. Verlies is mogelijk. | Niet-kritieke statusupdates. |
| QoS 1 | Een bericht wordt ten minste één keer afgeleverd. Dubbele ontvangst is mogelijk. | Transportopdrachten en belangrijke statusmeldingen, mits dubbele berichten worden herkend. |
| QoS 2 | Het protocol gebruikt een uitgebreidere uitwisseling om een bericht precies één keer af te leveren. | Berichten waarbij de extra communicatieoverhead gerechtvaardigd is. |

Daarnaast ondersteunt MQTT 5.0 een Message Expiry Interval. Hiermee kan worden ingesteld hoelang een bericht geldig blijft. Wanneer deze termijn verloopt voordat het bericht wordt afgeleverd, hoeft het niet meer bij de ontvanger aan te komen.
Dit is relevant voor Viscon Group, omdat verouderde informatie tot verkeerde beslissingen kan leiden. Een melding dat het overdrachtspunt beschikbaar is, mag bijvoorbeeld niet alsnog worden gebruikt wanneer het punt inmiddels gesloten is voor onderhoud.
Een aandachtspunt bij MQTT is de afhankelijkheid van de broker. Wanneer deze niet bereikbaar is, kan de berichtuitwisseling tussen de robotvloten worden onderbroken. Daarom moet bij een daadwerkelijke implementatie rekening worden gehouden met de beschikbaarheid van de broker en het herstellen van verbindingen.
Ook biedt QoS 2 geen garantie dat een fysieke transportopdracht binnen het volledige transportsysteem precies één keer wordt uitgevoerd. De applicatie moet daarom zelf controleren of een opdracht al eerder is verwerkt.

#### 3.3.3 ROS 2 met DDS

ROS 2 (Robot Operating System 2) is een softwareframework dat specifiek is ontwikkeld voor robottoepassingen. Voor de communicatie tussen verschillende onderdelen maakt ROS 2 gebruik van DDS (Data Distribution Service) als middleware.
DDS ondersteunt communicatie tussen verschillende onderdelen van een robotsysteem. Hierbij kunnen berichten worden uitgewisseld zonder dat alle onderdelen rechtstreeks aan elkaar gekoppeld hoeven te zijn.
ROS 2 biedt verschillende Quality of Service-instellingen waarmee het gedrag van de communicatie kan worden afgestemd op de toepassing (Open Robotics, z.d.).
De belangrijkste instellingen zijn:
*   **Reliability:** bepaalt of berichten betrouwbaar worden afgeleverd of dat een minder betrouwbare, maar lichtere vorm van communicatie wordt gebruikt.
    
*   **Lifespan:** bepaalt hoelang een bericht geldig blijft. Berichten die verlopen zijn voordat ze worden ontvangen, worden niet meer afgeleverd.
    
*   **Deadline:** geeft aan binnen welke tijdsperiode nieuwe berichten worden verwacht.
    
*   **Liveliness:** helpt vaststellen of een communicatieonderdeel nog actief is.
    
Deze instellingen kunnen worden gebruikt om ervoor te zorgen dat de robotvloten met actuele informatie werken. Wanneer bijvoorbeeld een statusbericht van het overdrachtspunt te oud is, kan de lifespan-instelling voorkomen dat dit bericht alsnog wordt afgeleverd.
Een voordeel van ROS 2 met DDS is dat de communicatiemogelijkheden goed aansluiten bij robottoepassingen. Daarnaast kunnen verschillende onderdelen van een robotsysteem onafhankelijk van elkaar communiceren.
Een aandachtspunt is dat de Quality of Service-instellingen van de verzender en ontvanger op elkaar moeten aansluiten. Wanneer deze instellingen niet compatibel zijn, kunnen berichten niet worden uitgewisseld.
Voor Viscon Group is ROS 2 met DDS vooral interessant wanneer de bestaande robotvloten al gebruikmaken van ROS 2. Wanneer beide robotvloten met verschillende leverancierssystemen werken, moet eerst worden onderzocht of deze systemen met ROS 2 en DDS kunnen integreren.
Net als bij MQTT moeten aanvullende controles op opdrachtniveau worden ontwikkeld. De communicatie-instellingen alleen voorkomen namelijk niet dat een fysieke transportopdracht dubbel wordt uitgevoerd.

#### 3.3.4 Selectie en weging van de MCA-criteria

Om de drie communicatieoplossingen op een gestructureerde manier te vergelijken, is een Multi Criteria Analyse (MCA) opgesteld. Met deze methode worden de verschillende oplossingen beoordeeld op basis van meerdere criteria die belangrijk zijn voor de situatie van Viscon Group.
De criteria zijn opgesteld aan de hand van de probleemcontext, de technische eisen uit deelvraag 1 en de eigenschappen die uit het literatuuronderzoek naar voren zijn gekomen.
Er zijn zes criteria geselecteerd:
**1. Betrouwbaarheid van de berichtoverdracht**
Dit criterium beoordeelt in hoeverre de communicatieoplossing ondersteuning biedt om berichten correct bij de ontvanger af te leveren. Hierbij wordt gekeken naar mechanismen voor betrouwbare berichtoverdracht en het omgaan met verloren gegevens.
**2. Omgaan met verouderde berichten**
Dit criterium beoordeelt of de communicatieoplossing mogelijkheden biedt om berichten na een bepaalde termijn ongeldig te maken. Dit is belangrijk wanneer de status van het overdrachtspunt verandert door bijvoorbeeld reiniging, onderhoud of een storing.
**3. Afhandeling van dubbele berichten en opdrachten**
Dit criterium beoordeelt in hoeverre de communicatieoplossing ondersteuning biedt bij het herkennen en verwerken van dubbele berichten. Dit is belangrijk om te voorkomen dat dezelfde transportopdracht meerdere keren wordt uitgevoerd.
**4. Implementatiecomplexiteit**
Dit criterium beoordeelt hoeveel aanvullende software en configuratie nodig is om de communicatieoplossing werkend te krijgen. Hierbij wordt gekeken naar de hoeveelheid functionaliteit die zelf ontwikkeld moet worden en de benodigde aanvullende componenten.
**5. Geschiktheid voor communicatie tussen robotvloten**
Dit criterium beoordeelt in hoeverre de oplossing aansluit bij de communicatiebehoefte van Viscon Group. Hierbij wordt gekeken naar het uitwisselen van transportopdrachten, statusupdates en bevestigingen tussen twee afzonderlijke robotvloten.
**6. Afhankelijkheden en integratiemogelijkheden**
Dit criterium beoordeelt in hoeverre de communicatieoplossing afhankelijk is van aanvullende software, infrastructuur of specifieke frameworks. Ook wordt gekeken naar de mogelijkheden om verschillende systemen met elkaar te verbinden.

# Weging van de criteria

Niet ieder criterium is even belangrijk voor het transportsysteem van Viscon Group. Betrouwbare communicatie en het voorkomen van verkeerde beslissingen op basis van verouderde informatie zijn belangrijke voorwaarden.
Daarom zijn de criteria voorzien van een wegingspercentage. De weging geeft aan hoeveel invloed een criterium heeft op de uiteindelijke beoordeling.
| Criterium | Weging |
| --- | --- |
| Betrouwbaarheid van de berichtoverdracht | 20% |
| Omgaan met verouderde berichten | 15% |
| Afhandeling van dubbele berichten en opdrachten | 15% |
| Implementatiecomplexiteit | 15% |
| Geschiktheid voor communicatie tussen robotvloten | 20% |
| Afhankelijkheden en integratiemogelijkheden | 15% |
| **Totaal** | **100%** |
Betrouwbaarheid en geschiktheid voor communicatie tussen robotvloten krijgen de hoogste weging, omdat deze criteria direct aansluiten op het onderzoeksprobleem. De overige criteria zijn eveneens belangrijk, omdat het systeem moet kunnen omgaan met netwerkproblemen, verouderde informatie en verschillende softwareomgevingen.

##### Scoringsmethode

Voor ieder criterium wordt een score toegekend op een schaal van 1 tot en met 5.
| Score | Betekenis |
| --- | --- |
| 1 | Zeer ongeschikt |
| 2 | Ongeschikt |
| 3 | Voldoende |
| 4 | Geschikt |
| 5 | Zeer geschikt |

De score wordt bepaald op basis van de eigenschappen van de onderzochte communicatieoplossingen en de mate waarin deze aansluiten bij de eisen van Viscon Group.
De gewogen score wordt berekend door de behaalde score te vermenigvuldigen met het wegingspercentage van het betreffende criterium. De gewogen scores worden vervolgens bij elkaar opgeteld.
De berekening is als volgt:
# **Gewogen score = score × wegingsfactor**
De maximale eindscore bedraagt 5,00 punten. De oplossing met de hoogste eindscore sluit volgens deze beoordeling het beste aan bij de gestelde eisen.

#### 3.3.5 Resultaten van de Multi Criteria Analyse

Op basis van de onderzochte technische eigenschappen zijn de drie communicatieoplossingen beoordeeld. De onderstaande scores vormen een kwalitatieve beoordeling op basis van de technische documentatie en de eisen van Viscon Group. Het betreft geen resultaten van praktijktests tussen de drie oplossingen.
| Criterium | Weging | TCP-sockets | MQTT 5.0 | ROS 2 met DDS |
| --- | --- | --- | --- | --- |
| Betrouwbaarheid van de berichtoverdracht | 20% | 4 | 4 | 5 |
| Omgaan met verouderde berichten | 15% | 2 | 5 | 5 |
| Afhandeling van dubbele berichten en opdrachten | 15% | 2 | 3 | 3 |
| Implementatiecomplexiteit | 15% | 3 | 4 | 2 |
| Geschiktheid voor communicatie tussen robotvloten | 20% | 3 | 4 | 5 |
| Afhankelijkheden en integratiemogelijkheden | 15% | 4 | 4 | 2 |
| **Gewogen eindscore** | **100%** | **3,00** | **4,00** | **3,80** |

##### Onderbouwing van de scores

**TCP-sockets – 3,00 punten**
TCP-sockets behalen een voldoende score op betrouwbaarheid, omdat TCP gebruikmaakt van hertransmissies en geordende gegevensoverdracht. Het protocol biedt echter geen standaardfunctionaliteit om applicatieberichten te laten verlopen of dubbele transportopdrachten te herkennen. Deze functies moeten zelf worden ontwikkeld.
Een voordeel is dat TCP-sockets relatief weinig aanvullende componenten nodig hebben. Er is geen centrale broker of specifiek robotframework vereist. Hierdoor kan een directe verbinding tussen twee systemen worden opgezet.
De implementatie van de volledige communicatieafhandeling vraagt echter extra ontwikkelwerk. Daarom scoort TCP-socketcommunicatie lager dan MQTT en ROS 2 met DDS.
**MQTT 5.0 – 4,00 punten**
MQTT behaalt de hoogste eindscore in de MCA. Dit komt voornamelijk door het publish/subscribe-model, de verschillende QoS-niveaus en de mogelijkheid om berichten een verlooptermijn mee te geven.
Hierdoor sluit MQTT goed aan bij de situatie van Viscon Group. Beide robotvloten kunnen informatie publiceren en ontvangen zonder dat zij voortdurend rechtstreeks met elkaar verbonden hoeven te zijn.
Een nadeel is dat een broker nodig is en dat de applicatie zelf dubbele transportopdrachten moet herkennen. Ondanks deze aandachtspunten biedt MQTT veel mogelijkheden voor de uitwisseling van statusinformatie en transportgebeurtenissen.
**ROS 2 met DDS – 3,80 punten**
ROS 2 met DDS behaalt eveneens een hoge score. Dit komt doordat de communicatiemiddleware speciaal geschikt is voor robottoepassingen en verschillende Quality of Service-instellingen ondersteunt.
Met instellingen zoals Reliability, Lifespan, Deadline en Liveliness kan de communicatie worden afgestemd op de eisen van het transportsysteem.
Een aandachtspunt is de integratie met bestaande robotsystemen. Wanneer de robotvloten niet op ROS 2 zijn gebaseerd, kan aanvullende software en configuratie nodig zijn. Hierdoor is de implementatie mogelijk complexer dan bij MQTT.
Daarnaast moeten dubbele transportopdrachten op applicatieniveau nog steeds worden afgehandeld.

## Analyse van de MCA-resultaten

Uit de MCA blijkt dat MQTT 5.0 met een gewogen eindscore van 4,00 punten het beste aansluit bij de onderzochte eisen van Viscon Group. ROS 2 met DDS volgt met 3,80 punten. TCP-sockets behalen een score van 3,00 punten.
MQTT scoort vooral goed doordat het verschillende communicatiemogelijkheden combineert. Het publish/subscribe-model maakt het mogelijk om informatie tussen meerdere systemen uit te wisselen. Daarnaast bieden QoS en berichtvervaltermijnen ondersteuning bij het betrouwbaar en actueel houden van de gegevensuitwisseling.
ROS 2 met DDS biedt vergelijkbare mogelijkheden op het gebied van berichtbetrouwbaarheid en actualiteit. De techniek is vooral interessant wanneer de robotvloten al gebruikmaken van ROS 2. De afhankelijkheid van het framework en de benodigde integratie kunnen de implementatie echter complexer maken.
TCP-sockets bieden een eenvoudige basis voor rechtstreekse communicatie. Het grootste nadeel is dat aanvullende functionaliteit, zoals berichtvervaltermijnen en het herkennen van dubbele opdrachten, zelf moet worden ontwikkeld.
De MCA geeft daarmee een onderbouwde vergelijking van de theoretische geschiktheid van de drie communicatieoplossingen. De scores zijn gebaseerd op de beschikbare documentatie en de eisen van de toepassing. Er zijn geen vergelijkende praktijktests uitgevoerd waarmee de daadwerkelijke prestaties van MQTT en ROS 2 met DDS ten opzichte van TCP kunnen worden vastgesteld.

### 3.3.6 Antwoord op deelvraag 2

## De deelvraag luidt: Welke communicatietechnieken zijn het meest geschikt voor het uitwisselen van informatie tussen de twee robotvloten?

Op basis van het literatuuronderzoek en de uitgevoerde Multi Criteria Analyse kan worden geconcludeerd dat MQTT 5.0 op basis van de onderzochte criteria het meest geschikt is voor de communicatie tussen de twee robotvloten van Viscon Group. MQTT behaalt met 4,00 punten de hoogste gewogen eindscore. ROS 2 met DDS volgt met 3,80 punten en TCP-sockets behalen 3,00 punten.
MQTT sluit goed aan bij de communicatiebehoefte van Viscon Group, omdat het publish/subscribe-model het mogelijk maakt om transportopdrachten, statusupdates en bevestigingen via een centrale broker uit te wisselen. Hierdoor kunnen beide robotvloten relevante informatie ontvangen zonder dat zij rechtstreeks met elkaar verbonden hoeven te zijn. De Quality of Service-instellingen en de berichtvervaltermijn bieden daarnaast mogelijkheden om de betrouwbaarheid en actualiteit van de berichtuitwisseling te verbeteren.

ROS 2 met DDS is eveneens een geschikte oplossing, vooral wanneer de bestaande robotvloten al gebruikmaken van ROS 2. De verschillende Quality of Service-instellingen bieden uitgebreide mogelijkheden om de communicatie af te stemmen op de eisen van een robotsysteem. De integratie met bestaande leverancierssystemen moet hierbij wel worden onderzocht.
TCP-sockets zijn vooral geschikt wanneer gekozen wordt voor een eigen, rechtstreekse communicatieverbinding tussen twee systemen. TCP zorgt voor betrouwbare en geordende gegevensoverdracht, maar aanvullende functies zoals berichtvervaltermijnen, opdrachtbevestigingen en het herkennen van dubbele opdrachten moeten zelf worden ontwikkeld.
Voor het softwareprototype is gekozen voor TCP-socketcommunicatie. Deze keuze is gemaakt omdat hiermee een directe verbinding tussen een client en server kan worden opgezet. Hierdoor kan de invloed van netwerkvertragingen en gesimuleerd pakketverlies op de onderliggende TCP-communicatie worden onderzocht.

De keuze voor een eigen applicatieprotocol op basis van TCP-sockets in het prototype betekent niet dat TCP op basis van de MCA de meest geschikte oplossing is voor de uiteindelijke praktijksituatie. De MCA laat juist zien dat MQTT op basis van de onderzochte criteria een betere theoretische aansluiting heeft. Het prototype heeft een andere functie, namelijk het praktisch onderzoeken van de betrouwbaarheid en prestaties van TCP onder verschillende netwerkcondities.
De specifieke functionaliteiten van MQTT, zoals de broker, het publish/subscribe-model en de QoS-instellingen, worden niet met het prototype getest. Ook de communicatiemogelijkheden van ROS 2 met DDS worden niet praktisch onderzocht.
De resultaten van het TCP-prototype geven daarom inzicht in de werking van TCP onder verschillende netwerkcondities, maar zijn niet voldoende om de daadwerkelijke prestaties van MQTT of ROS 2 met DDS te beoordelen.
Voor een definitieve implementatie bij Viscon Group moet aanvullend worden onderzocht welke communicatietechniek het beste aansluit op de bestaande robotsoftware en infrastructuur. Daarbij moet ook rekening worden gehouden met de beschikbaarheid van de broker of middleware, de afhandeling van dubbele opdrachten en het veilig hervatten van transport nadat een netwerkverbinding is hersteld.