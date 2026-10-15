1 Probleemcontext
Binnen de casus Automated Logistics Across Hygiene Zones moeten producten en goederen tussen twee verschillende hygiënezones worden vervoerd. Iedere zone heeft een eigen robotvloot. Omdat elke robotvloot verantwoordelijk is voor zijn eigen gebied, mogen de robots de grens naar de andere zone niet overschrijden. Wanneer producten of goederen moeten worden overgedragen, wordt hiervoor een gedeeld overdrachtspunt gebruikt.

Het probleem onstaat doordat producten / goederen in allebij de richtingen moeten worden vervoerd. daarnaast heb je het probleem dat het overdrachtspunt tijdelijk niet beschikbaar kan zijn door reiniging of onderhoud. het transportsyteem moet daarom rekening houden met de beschikbaarheid van het overdrachtspunt en geplande transportopdrachten hierop aanpasssen.

Voor dit onderzoek wordt gekeken naar de infrastructuur, computernetwerken en datacommunicatie die nodig zijn om de transportopdrachten tussen beide robotvloten betrouwbaar te coördineren. Het is nog onduidelijk hoe de robotvloten informatie uitwisselen over beschikbare goederen, de status van robots en de beschikbaarheid van het overdrachtspunt. Ook moet worden onderzocht hoe het systeem omgaat met communicatievertragingen of een tijdelijke netwerkstoring.

2 Belang
Een betrouwbare coördinatie tussen de robotvloten is belangrijk om te voorkomen dat goederen onnodig lang moeten wachten en het overdrachtspunt inefficiënt wordt gebruikt. Wanneer het overdrachtspunt tijdelijk gesloten is, moeten de robotvloten op tijd weten dat overdrachten moeten worden uitgesteld of opnieuw moeten worden ingepland.

Voor Viscon Group kan een goede oplossing ervoor zorgen dat het transport van goederen soepeler en betrouwbaarder verloopt. Ook is het belangrijk dat informatie over transportopdrachten correct wordt uitgewisseld, zodat opdrachten niet verloren gaan of dubbel worden uitgevoerd.

Daarnaast moet de oplossing voldoen aan de hygiëne-eisen. Communicatieproblemen of een tijdelijke onbeschikbaarheid van het overdrachtspunt mogen er nooit toe leiden dat een robot opdrachten krijgt die buiten zijn eigen hygiënezone vallen. Wanneer het transportsysteem niet goed functioneert, kan dit namelijk leiden tot stilstand van het proces en daarmee tot inkomstenverlies.

3 Literatuuronderzoek + literature gap

Uit onderzoek van Chen et al. (2020) blijkt dat het goed plannen en verdelen van transporttaken belangrijk is wanneer meerdere automatische voertuigen samenwerken. Ook beschrijft de ROS 2-documentatie hoe communicatie tussen robots betrouwbaarder kan worden gemaakt, bijvoorbeeld door instellingen voor het afleveren van berichten (Open Robotics, z.d.).

Daarnaast is het belangrijk om rekening te houden met gedeelde middelen. Als meerdere robots hetzelfde overdrachtspunt gebruiken, moet duidelijk zijn wanneer het beschikbaar is en welke robot er gebruik van kan maken. Een goede planning kan helpen om te voorkomen dat robots op elkaar moeten wachten.

Wat nog onderzocht moet worden, is hoe deze oplossingen werken in de situatie van Viscon Group. Twee aparte robotvloten moeten goederen in beide richtingen vervoeren via hetzelfde overdrachtspunt, dat soms tijdelijk gesloten is. Er moet daarom worden onderzocht hoe de robots hierover informatie uitwisselen en hoe de transportplanning wordt aangepast als het overdrachtspunt niet beschikbaar is.

Bronnen: (gevonden door prompts via ai, zelf daarna gecontroleerd) https://www.sciencedirect.com/science/article/abs/pii/S0968090X19313531?via%3Dihub https://github.com/ros2/ros2_documentation/blob/rolling/source/ROS-Framework/interfaces/topics/About-Quality-of-Service-Settings.rst

Een vloeiende robotsamenwerking staat of valt met een goede transportplanning en betrouwbare communicatie. Bij Viscon Group moet nog worden onderzocht hoe twee robotvloten informatie uitwisselen en hun taken afstemmen wanneer een overdrachtspunt niet beschikbaar is. Daarnaast is het belangrijk de planning te optimaliseren om wachttijden te voorkomen en het transport soepel te laten verlopen.


4 Doelstelling van het onderzoek
Het doel van dit onderzoek is om te er achter te komen hoe de twee robotvloten informatie met elkaar kunnen uitwisselen terwijl ze transportopdrachten uitvoeren. Het hoofddoel ligt hierbij op situaties waarin het overdrachtspunt tijdelijk niet beschikbaar is. Er wordt onderzocht hoe de robots hierop moeten reageren en hoe het transportsysteem zich aan deze situatie kan aanpassen.

Aan het einde van het het onderzoek is het doel dat duidelijk is welke communicatiemethode het beste past in deze situatie. hierbij kijken we vooral of er geken wordt of de informatie op tijd aankomt en het system goed blijft functioneren wanneer er problemen optreden zoals bijvoorbeeld netwerkverbinding of wanneer de verbinding tijdelijk wegvalt

5 Afbakening
in dit onderzoek is het hoofddoel de communicatie tussen de robotvloten en het overdrachtspunt. Er wordt onderzocht hoe informatie wordt doorgegeven en wat er gebeurt wanneer het overdrachtspunt tijdelijk niet beschikbaar is.


De volgende onderwerpen worden meegenomen:

- Welke gegevens de robotvloten met elkaar moeten uitwisselen.
- Hoe de communicatie betrouwbaar kan blijven functioneren.
- Hoe het systeem reageert wanneer het overdrachtspunt tijdelijk gesloten is.
- Hoe wordt omgegaan met een slechte of weggevallen netwerkverbinding.

Het bouwen en ontwerpen van de robots zelf valt buiten de scope van dit onderzoek. Ook wordt niet ingegaan op het volledige navigatiesysteem of de technische constructie van het overdrachtspunt. Wel wordt rekening gehouden met de geldende hygiënevoorschriften en wordt ervoor gezorgd dat de robots binnen hun eigen hygiënezone blijven.