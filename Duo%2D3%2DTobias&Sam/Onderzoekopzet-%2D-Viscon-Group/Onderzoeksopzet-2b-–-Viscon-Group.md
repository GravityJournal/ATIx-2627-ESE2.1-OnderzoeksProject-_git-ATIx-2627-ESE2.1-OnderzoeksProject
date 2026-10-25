# 1 Onderzoeksvraag

**Hoofdvraag:**
Hoe kan het geautomatiseerde transportsysteem van Viscon Group het tweerichtingsvervoer tussen hygiënezones efficiënt en betrouwbaar organiseren wanneer het gedeelde overdrachtspunt tijdelijk niet beschikbaar is door reiniging of onderhoud?

# 2 Deelvragen

Deelvraag 1
**Welke informatie moeten de twee robotvloten met elkaar uitwisselen om het transport via het gedeelde overdrachtspunt goed te laten verlopen?**

Deze deelvraag is nodig om vast te stellen welke gegevens de robotvloten nodig hebben om het transport goed op elkaar af te stemmen. Hierbij kijken we bijvoorbeeld naar de beschikbaarheid van het overdrachtspunt, transportopdrachten en bevestigingen van overdrachten.

Deelvraag 2
**Hoe kan het systeem de transportplanning aanpassen wanneer het overdrachtspunt tijdelijk niet beschikbaar is?**

Deze deelvraag onderzoekt hoe het systeem reageert op een tijdelijke sluiting van het overdrachtspunt. Het doel is om onnodige wachttijden te beperken en te voorkomen dat robots naar een gesloten overdrachtspunt blijven rijden.

Deelvraag 3
**Hoe kan de communicatie tussen de robotvloten betrouwbaar blijven bij vertragingen of tijdelijke netwerkuitval?**

Deze deelvraag richt zich op de betrouwbaarheid van de communicatie. We onderzoeken hoe het systeem omgaat met berichten die vertraagd zijn of niet aankomen en hoe wordt voorkomen dat robots op basis van verouderde informatie werken.


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

Deelvraag 2: Transportplanning bij een gesloten overdrachtspunt

**Onderzoeksmethoden:**
- **Literatuuronderzoek:** onderzoeken welke planningsmethoden worden gebruikt bij meerdere robots en gedeelde middelen.
- **Data-analyse:** indien gegevens beschikbaar zijn, wachttijden en vertragingen analyseren.
- **Prototyping:** een transportsituatie simuleren waarin het overdrachtspunt tijdelijk gesloten wordt.

**Uitvoering:**
We testen verschillende situaties, bijvoorbeeld een overdrachtspunt dat normaal beschikbaar is en een overdrachtspunt dat tijdelijk gesloten wordt. We vergelijken hoe het systeem reageert en of de planning wordt aangepast. Daarbij kijken we onder andere naar wachttijd, vertraging en het aantal transporten dat succesvol wordt uitgevoerd.

**Waarom deze methoden?**
Met literatuuronderzoek vinden we mogelijke planningsoplossingen. Met data-analyse kunnen we bestaande prestaties beoordelen. Het prototype maakt het mogelijk om verschillende situaties onder dezelfde omstandigheden te vergelijken.

Deelvraag 3: Betrouwbaarheid van de communicatie

**Onderzoeksmethoden:**
- **Literatuuronderzoek:** informatie zoeken over betrouwbare netwerkcommunicatie, foutafhandeling en het opnieuw versturen van berichten.
- **Prototyping:** berichtenverkeer testen met bijvoorbeeld vertraging, een gemist bericht of tijdelijke netwerkuitval.
- **Peer review:** de gekozen communicatieoplossing en testresultaten laten beoordelen door een medestudent of docent.

**Uitvoering:**
We voeren herhaalde tests uit en controleren of statuswijzigingen correct worden verwerkt. Ook testen we wat er gebeurt wanneer een bericht niet aankomt of pas later wordt ontvangen. We leggen de resultaten vast en vergelijken deze met de vooraf vastgestelde criteria.

**Waarom deze methoden?**
Literatuuronderzoek geeft inzicht in mogelijke oplossingen. Met prototyping kunnen we de communicatie onder verschillende omstandigheden testen. Peer review helpt om fouten of zwakke punten in de aanpak te ontdekken.

# 4. Benodigde middelen

| Middel | Waarvoor nodig? |
|---|---|
| Laptop en ontwikkelsoftware | Om het prototype te bouwen en de resultaten te bekijken |
| Programmeeromgeving, C++ | Om de communicatie- en planningslogica te maken|
| testopstelling | Om twee robotvloten en een gedeeld overdrachtspunt na te maken |
| Netwerk- of communicatie-instellingen | Om berichtenuitwisseling, vertraging en uitval te testen |
| Literatuur en technische documentatie | Om bestaande oplossingen en technieken te onderzoeken |
| Testscenario's en meetgegevens | Om de resultaten vast te leggen en te vergelijken |
| Feedback van docent of medestudent | Om het onderzoeksontwerp en prototype te controleren |

De exacte software, hardware en beschikbare documentatie moeten nog worden vastgesteld. Als er geen echte robots of interne Viscon-documentatie beschikbaar zijn, gebruiken we de openbare technische bronnen.

# 5. Analysecriteria

We beoordelen de resultaten met de volgende criteria:

| Criterium | Wat onderzoeken we? |
|---|---|
| Betrouwbaarheid van berichten | Komen berichten correct aan en worden ze correct verwerkt? |
| Toestand van informatie | Werken de robotvloten met de meest recente status van het overdrachtspunt? |
| Wachttijd | Hoe lang moeten robots wachten wanneer het overdrachtspunt gesloten is? |
| Hersteltijd | Hoe snel hervat het systeem het transport nadat het overdrachtspunt weer beschikbaar is? |
| Succesvolle transporten | Hoeveel transportopdrachten worden correct afgerond? |
| Omgaan met netwerkuitval | Blijft het systeem veilig en herstelt het correct wanneer communicatie tijdelijk wegvalt? |

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

Om de validiteit te vergroten, laten we de testscenario's aansluiten op het probleem van Viscon: twee gescheiden robotvloten, transport in beide richtingen en een overdrachtspunt dat tijdelijk niet beschikbaar is. We controleren daarnaast of de gekozen meetcriteria daadwerkelijk iets zeggen over de hoofdvraag.

We laten de onderzoeksopzet en het prototype beoordelen door een docent of medestudent en verwerken de feedback. Omdat een simulatie niet alle omstandigheden van een echte installatie kan nabootsen, benoemen we die beperking bij het trekken van conclusies.
