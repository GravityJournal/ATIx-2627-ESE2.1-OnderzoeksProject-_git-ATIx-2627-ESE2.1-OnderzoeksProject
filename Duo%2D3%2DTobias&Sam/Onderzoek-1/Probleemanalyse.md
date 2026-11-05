1 Probleemcontext
Binnen de casus Automated Logistics Across Hygiene Zones van Viscon Group moeten goederen tussen twee verschillende hygiënezones worden vervoerd. Iedere zone heeft een eigen robotvloot. De robots mogen de grens tussen de zones niet overschrijden. Daarom worden goederen via een gedeeld overdrachtspunt overgedragen.

Het transport vindt in beide richtingen plaats. Naast volle goederen moeten ook lege kratten en pallets terug worden vervoerd. Het gedeelde overdrachtspunt kan tijdelijk niet beschikbaar zijn, bijvoorbeeld door reiniging of onderhoud.
Om dit transport goed te laten verlopen, moeten de twee robotvloten informatie met elkaar kunnen uitwisselen. Denk hierbij aan transportopdrachten, de beschikbaarheid van het overdrachtspunt en bevestigingen van uitgevoerde overdrachten.
Het is momenteel nog onduidelijk welke communicatietechniek hiervoor het meest geschikt is en hoe betrouwbaar de communicatie blijft wanneer er netwerkproblemen optreden. Denk hierbij aan vertragingen, pakketverlies en tijdelijke verbindingsuitval.

Dit onderzoek richt zich daarom op de datacommunicatie tussen de twee robotvloten en de betrouwbaarheid hiervan onder verschillende netwerkcondities.

2 Belang
Een betrouwbare coördinatie tussen de robotvloten is belangrijk om te voorkomen dat goederen onnodig lang moeten wachten en het overdrachtspunt inefficiënt wordt gebruikt. Wanneer het overdrachtspunt tijdelijk gesloten is, moeten de robotvloten op tijd weten dat overdrachten moeten worden uitgesteld of opnieuw moeten worden ingepland.

Voor Viscon Group kan een goede oplossing ervoor zorgen dat het transport van goederen soepeler en betrouwbaarder verloopt. Ook is het belangrijk dat informatie over transportopdrachten correct wordt uitgewisseld, zodat opdrachten niet verloren gaan of dubbel worden uitgevoerd.

Daarnaast moet de oplossing voldoen aan de hygiëne-eisen. Communicatieproblemen of een tijdelijke onbeschikbaarheid van het overdrachtspunt mogen er nooit toe leiden dat een robot opdrachten krijgt die buiten zijn eigen hygiënezone vallen. Wanneer het transportsysteem niet goed functioneert, kan dit namelijk leiden tot stilstand van het proces en daarmee tot inkomstenverlies.

Betrouwbare communicatie is belangrijk om te voorkomen dat robotvloten werken met verouderde informatie of transportopdrachten verkeerd verwerken. Wanneer het overdrachtspunt tijdelijk gesloten is, moeten beide robotvloten hiervan op de hoogte zijn.

Wanneer berichten verloren gaan of te laat aankomen, kan dit leiden tot onnodige wachttijden, dubbele opdrachten of stilstand van het transportsysteem.
Voor Viscon Group is het daarom belangrijk dat de gekozen communicatietechniek betrouwbaar informatie kan uitwisselen en dat het systeem veilig reageert wanneer de netwerkverbinding tijdelijk niet beschikbaar is.

3 Literatuuronderzoek + literature gap (verdiepen over onderzoeken)

Uit onderzoek van Chen et al. (2020) blijkt dat het goed plannen en verdelen van transporttaken belangrijk is wanneer meerdere automatische voertuigen samenwerken. Ook beschrijft de ROS 2-documentatie hoe communicatie tussen robots betrouwbaarder kan worden gemaakt, bijvoorbeeld door instellingen voor het afleveren van berichten (Open Robotics, z.d.).

Daarnaast is het belangrijk om rekening te houden met gedeelde middelen. Als meerdere robots hetzelfde overdrachtspunt gebruiken, moet duidelijk zijn wanneer het beschikbaar is en welke robot er gebruik van kan maken. Een goede planning kan helpen om te voorkomen dat robots op elkaar moeten wachten.

Wat nog onderzocht moet worden, is hoe deze oplossingen werken in de situatie van Viscon Group. Twee aparte robotvloten moeten goederen in beide richtingen vervoeren via hetzelfde overdrachtspunt, dat soms tijdelijk gesloten is. Er moet daarom worden onderzocht hoe de robots hierover informatie uitwisselen en hoe de transportplanning wordt aangepast als het overdrachtspunt niet beschikbaar is.

Een vloeiende robotsamenwerking staat of valt met een goede transportplanning en betrouwbare communicatie. Bij Viscon Group moet nog worden onderzocht hoe twee robotvloten informatie uitwisselen en hun taken afstemmen wanneer een overdrachtspunt niet beschikbaar is. Daarnaast is het belangrijk de planning te optimaliseren om wachttijden te voorkomen en het transport soepel te laten verlopen.


4 Doelstelling van het onderzoek
Het doel van dit onderzoek is om te er achter te komen hoe de twee robots informatie met elkaar kunnen uitwisselen terwijl ze transportopdrachten uitvoeren. Het hoofddoel ligt hierbij op situaties waarin het overdrachtspunt tijdelijk niet beschikbaar is. Er wordt onderzocht hoe de robots hierop moeten reageren en hoe het transportsysteem zich aan deze situatie kan aanpassen.

Aan het einde van het het onderzoek is het doel dat duidelijk is welke communicatiemethode het beste past in deze situatie. hierbij kijken we vooral of er gekeken wordt of de informatie op tijd aankomt en het systeem goed blijft functioneren wanneer er problemen optreden zoals bijvoorbeeld netwerkverbinding of wanneer de verbinding tijdelijk wegvalt

5 Afbakening

Dit onderzoek richt zich op de datacommunicatie tussen twee afzonderlijke robotvloten en de betrouwbaarheid van deze communicatie.
Binnen het onderzoek worden de volgende onderwerpen meegenomen:
*   De informatie die tussen beide robotvloten moet worden uitgewisseld.
    
*   De technische eigenschappen en geschiktheid van TCP, MQTT en ROS 2 met DDS.
    
*   Het testen van TCP-communicatie met behulp van een softwareprototype.
    
*   De invloed van netwerkvertragingen en pakketverlies op de communicatie.
    
Het daadwerkelijk bouwen van robots, het navigatiesysteem, de fysieke inrichting van het overdrachtspunt en de volledige transportplanning vallen buiten de scope.
Ook wordt geen volledige implementatie binnen de bestaande infrastructuur van Viscon Group gerealiseerd. Het prototype dient uitsluitend om de communicatie onder gecontroleerde testomstandigheden te onderzoeken.