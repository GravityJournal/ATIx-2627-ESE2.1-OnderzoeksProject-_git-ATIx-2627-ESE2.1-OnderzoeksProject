# 1 Onderzoeksvraag

**Hoofdvraag:**
Hoe kan het geautomatiseerde transportsysteem van Viscon Group het tweerichtingsvervoer tussen hygiënezones efficiënt en betrouwbaar organiseren wanneer het gedeelde overdrachtspunt tijdelijk niet beschikbaar is door reiniging of onderhoud?

# 2 Deelvragen

Deelvraag 1
**Welke informatie moeten de twee robots met elkaar uitwisselen om het transport via het gedeelde overdrachtspunt goed te laten verlopen?**

Deze deelvraag is nodig om vast te stellen welke gegevens de robotvloten nodig hebben om het transport goed op elkaar af te stemmen. Hierbij kijken we bijvoorbeeld naar de beschikbaarheid van het overdrachtspunt, transportopdrachten en bevestigingen van overdrachten.

Deelvraag 2  
**Welke communicatietechnieken zijn het meest geschikt voor het uitwisselen van informatie tussen de twee robotvloten?**
Deze deelvraag onderzoekt welke communicatietechnieken het beste passen bij het transportsysteem van Viscon. Hierbij kijken we naar de snelheid, betrouwbaarheid en efficiëntie van de verschillende technieken. Het doel is om te bepalen hoe de robotvloten op een goede manier informatie kunnen uitwisselen over de status van het overdrachtspunt en de transportopdrachten.

Deelvraag 3  
**Hoe kan betrouwbare communicatie tussen de twee robotvloten worden bewaard bij vertragingen of tijdelijke netwerkuitval?**
Deze deelvraag richt zich op de manier waarop het systeem omgaat met vertraagde of verloren berichten als gevolg van netwerkproblemen. Hierbij wordt onderzocht hoe berichten opnieuw kunnen worden verzonden en/of hoe kan worden gecontroleerd of ontvangen informatie nog belangrijk en betrouwbaar is(een bericht van 10 minuten geleden moet niet bewaard worden). Het doel is om de communicatie tussen beide robotvloten zo betrouwbaar mogelijk te houden en te voorkomen dat beslissingen worden genomen op basis van verouderde of onvolledige informatie.


# 3 Onderzoeks- en analysemethoden

Deelvraag 1: Informatie-uitwisseling tussen de robotvloten

**Onderzoeksmethoden:**
- **Literatuuronderzoek:** informatie zoeken over communicatie tussen robots, netwerkprotocollen en het uitwisselen van statusinformatie.
- **Analyse van een bestaand systeem:** indien documentatie van Viscon beschikbaar is (of wordt), onderzoeken hoe de robotvloten en het overdrachtspunt met elkaar communiceren.
- **Prototyping:** een eenvoudige testopstelling of simulatie maken waarin twee robotvloten statusinformatie uitwisselen over het overdrachtspunt.

**Uitvoering:**
We onderzoeken welke berichten nodig zijn, wie deze verstuurt en hoe de ontvangende robotvloot weet of de informatie nuttig/actueel is. In het prototype testen we of de juiste informatie wordt gedeeld wanneer het overdrachtspunt beschikbaar of bezet is.

**Waarom deze methoden?**
Literatuuronderzoek geeft inzicht in bestaande oplossingen. Systeemanalyse laat zien wat er al beschikbaar is bij Viscon. Met een prototype kunnen we testen of de gekozen manier van communiceren in de praktijk werkt.

Deelvraag 2: Welke communicatietechnieken zijn geschikt?
**Onderzoeksmethoden:**
*   **Literatuuronderzoek:** informatie zoeken over verschillende communicatietechnieken die gebruikt kunnen worden om twee robotvloten met elkaar te laten communiceren.
    
*   **Vergelijkende analyse:** verschillende technieken vergelijken op basis van snelheid, betrouwbaarheid en hoe makkelijk ze te gebruiken zijn.
    
*   **Prototyping:** een eenvoudige testopstelling of simulatie maken waarin verschillende communicatietechnieken getest kunnen worden.
    
**Uitvoering:**
We onderzoeken welke communicatietechnieken geschikt zijn voor het uitwisselen van informatie tussen de twee robotvloten. Hierbij kijken we bijvoorbeeld naar het doorgeven van de status van het overdrachtspunt, transportopdrachten en bevestigingen van overdrachten. We vergelijken de technieken en kijken welke het beste past bij het transportsysteem van Viscon. Als het mogelijk is, testen we de technieken in een prototype.
**Waarom deze methoden?**
Met literatuuronderzoek krijgen we inzicht in de verschillende communicatietechnieken. Door de technieken te vergelijken, kunnen we bepalen wat de voor- en nadelen zijn. Met een prototype kunnen we testen welke techniek het beste werkt voor dit systeem.

Deelvraag 3: Hoe kan de communicatie betrouwbaar blijven bij storingen?

**Onderzoeksmethoden:**
*   **Literatuuronderzoek:** informatie zoeken over manieren om berichtenverlies, vertragingen en tijdelijke netwerkuitval op te vangen.
    
*   **Prototyping:** de communicatie testen met situaties waarin berichten te laat aankomen, niet aankomen of de verbinding tijdelijk wegvalt.
    
*   **Testresultaten analyseren:** onderzoeken of de robotvloten na een storing weer goed met elkaar kunnen communiceren en met de juiste informatie verder kunnen werken.
    
**Uitvoering:**
We testen wat er gebeurt wanneer berichten niet aankomen of pas later worden ontvangen. Ook onderzoeken we hoe het systeem hiermee om kan gaan, bijvoorbeeld door berichten opnieuw te versturen of te controleren of de ontvangen informatie nog actueel is. Daarna bekijken we of de robotvloten na een storing het transport op de juiste manier kunnen hervatten.
We leggen de resultaten vast en kijken hoe vaak berichten goed worden verwerkt en hoe snel de communicatie zich herstelt nadat de verbinding weer beschikbaar is.
**Waarom deze methoden?**
Met literatuuronderzoek krijgen we inzicht in mogelijke oplossingen voor communicatieproblemen. Met een prototype kunnen we testen hoe het systeem reageert op verschillende storingen. Door de resultaten te analyseren, kunnen we bepalen welke oplossingen de communicatie betrouwbaarder maken.
# 4. Benodigde middelen

| Middel | Waarvoor nodig? |
|---|---|
| Laptop(s) (minimaal 2) en ontwikkelsoftware | Om het prototype te bouwen en de resultaten te bekijken |
| Programmeeromgeving, C++ | Programmeren van de TCP-client en server|
| Netwerkverbinding| Uitwisselen van gegevens tussen client en server |
| TCP-testprogramma | Uitvoeren van de verschillende testsituaties |
| Literatuur en technische documentatie | Om bestaande oplossingen en technieken te onderzoeken |
|     [Bean Network Tester](https://github.com/donislawdev/BeanNetworkTester) | Vertragingen en pakketverlies simuleren |
| Spreadsheet | Meetresultaten vastleggen en analyseren |
| Technische documentatie | Onderzoeken en vergelijken van TCP, MQTT en ROS 2 |
| GitHub | Vastleggen en beheren van code/ prototype |

De exacte software, hardware en beschikbare documentatie moeten nog worden vastgesteld. Als er geen echte robots of interne Viscon-documentatie beschikbaar zijn, gebruiken we de openbare technische bronnen.

# 5. Analysecriteria

We beoordelen de resultaten met de volgende criteria:

| Criterium | Wat onderzoeken we? |
| --- | --- |
| Gemiddelde RTT | Wat is de gemiddelde tijd tussen het versturen van een bericht en het ontvangen van het antwoord? |
| Minimale RTT | Wat is de laagst gemeten rondreistijd?|
| Maximale RTT | Wat is de hoogst gemeten rondreistijd? |
| Succespercentag | Welk percentage van de verstuurde berichten krijgt een succesvol antwoord? |
| Detectietijd uitval | Hoe lang duurt het voordat het systeem een verbindingsprobleem vaststelt? |
| Hersteltijd | Hoe lang duurt het voordat communicatie na een verbindingsonderbreking weer werkt? |

We vergelijken de testresultaten tussen verschillende scenario's. We voeren de dezelfde test meerdere keren uit, zodat de resultaten minder afhankelijk zijn van één meting. De grenswaarden voor bijvoorbeeld maximale wachttijd en een maximaal aantal berichtfouten moeten nog worden vastgesteld op basis van de eisen van het systeem en de beschikbare testmogelijkheden.

# 6. Globale planning

| Fase | Activiteiten | Resultaat |
|---|---|---|
| Week 1 | Hoofdvraag en deelvragen controleren en literatuur zoeken | Definitieve onderzoeksvragen en eerste bronnen |
| Week 2 | Communicatie- en planningsoplossingen onderzoeken | Overzicht van mogelijke oplossingen |
| Week 3 | Prototype en testscenario's ontwerpen | Testopstelling en meetplan |
| Week 4 | Prototype bouwen en eerste tests uitvoeren | Eerste testresultaten |
| Week 5 | Tests uitvoeren met verschillende scenario's en resultaten analyseren | Vergelijking van de resultaten |
| Week 6 | Onderzoeksresultaten bespreken, feedback verwerken en verslag afronden | Verbeterde onderzoeksopzet en conclusies |

De planning wordt aangepast aan de deadlines van het vak en de beschikbaarheid van feedback en testmiddelen.

# Betrouwbaarheid en validiteit

Om de betrouwbaarheid percentage omhoog te krijgen, leggen we vooraf vast hoe de tests worden uitgevoerd en welke gegevens we meten. We herhalen tests waar dat mogelijk is en gebruiken dezelfde omstandigheden bij vergelijkingen.

Om de validiteit te vergroten, laten we de testscenario's aansluiten op het probleem van Viscon: twee gescheiden robotvloten, transport in beide richtingen en een overdrachtspunt dat tijdelijk niet beschikbaar is. We controleren daarnaast of de gekozen meetdata daadwerkelijk iets zegt over de hoofdvraag.

We laten de onderzoeksopzet en het prototype beoordelen door een docent of medestudent en verwerken de feedback. Omdat een simulatie niet alle omstandigheden van een echte installatie kan nabootsen, benoemen we die beperking bij het trekken van conclusies.
