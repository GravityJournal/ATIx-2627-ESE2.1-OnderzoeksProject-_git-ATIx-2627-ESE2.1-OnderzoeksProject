3.1 Inleiding[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.1-inleiding)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

In deze fase van ons faseplan wordt onderzocht hoe twee robotvloten (/ robots) informatie met elkaar kunnen uitwisselen en hoe het transportsysteem betrouwbaar kan blijven werken wanneer het gedeelde overdrachtspunt tijdelijk niet beschikbaar is (door bijvoorbeeld: onderhoud of schoonmaak).
Voor het beantwoorden van de deelvragen is gebruikgemaakt van technische documentatie en wetenschappelijk onderzoek. Hierbij is gekeken naar communicatie tussen automatische voertuigen, verschillende communicatietechnieken en manieren om berichtenverlies, vertragingen en netwerkuitval op te vangen.
De verzamelde informatie wordt per deelvraag besproken. Vervolgens worden de mogelijke oplossingen vergeleken om te bepalen welke technieken het beste aansluiten bij de situatie van Viscon Group.

3.2 Deelvraag 1: Welke informatie moeten de twee robotvloten(/ robots) met elkaar uitwisselen om het transport via het gedeelde overdrachtspunt goed te laten verlopen?[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.2-deelvraag-1%3A-welke-informatie-moeten-de-twee-robotvloten(/-robots)-met-elkaar-uitwisselen-om-het-transport-via-het-gedeelde-overdrachtspunt-goed-te-laten-verlopen%3F)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Om transport tussen twee gescheiden robotvloten(/robots) goed te laten verlopen, moet het systeem niet alleen weten welke goederen moeten worden vervoerd, maar ook wat de actuele status van het overdrachtspunt en de betrokken transportopdrachten is.
Chen et al. (2020) beschrijven hoe automatische voertuigen en andere geautomatiseerde systemen hun werkzaamheden moeten afstemmen om transporttaken efficiënt uit te voeren. Hun onderzoek laat zien dat de planning van verschillende voertuigen onderling afhankelijk is. Dit is ook relevant voor Viscon Group, omdat beide robotvloten(/robots) hetzelfde overdrachtspunt gebruiken en transportopdrachten in beide richtingen moeten uitvoeren.
Op basis hiervan zijn vijf categorieën informatie belangrijk.

### 3.2.1 Status van het overdrachtspunt[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.2.1-status-van-het-overdrachtspunt)

De robotvloten(/ robots) moeten kunnen vaststellen of het overdrachtspunt beschikbaar is voor een nieuwe overdracht.
De status moet minimaal onderscheid maken tussen beschikbaar, bezet, gesloten voor reiniging of onderhoud, en buiten gebruik door een storing. Daarnaast is het belangrijk dat bekend is wanneer de status voor het laatst is bijgewerkt.
Wanneer het overdrachtspunt tijdelijk gesloten is, moeten beide robotvloten(/ robots) deze wijziging ontvangen. Zo wordt voorkomen dat een robot met een nieuwe overdracht begint terwijl het overdrachtspunt niet beschikbaar is.
Alleen een melding dat het overdrachtspunt beschikbaar is, is niet voldoende. Het systeem moet ook voorkomen dat beide robotvloten(/ robots) tegelijkertijd aanspraak maken op dezelfde overdrachtsmogelijkheid. Hiervoor moet een overdracht kunnen worden gereserveerd en bevestigd.

### 3.2.2 Transportopdrachten[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.2.2-transportopdrachten)

Voor iedere transportopdracht moet duidelijk zijn wat er moet worden vervoerd en tussen welke zones de overdracht plaatsvindt.
De volgende gegevens zijn hiervoor nodig:
*   Een uniek identificatienummer van de transportopdracht.
*   De identificatie van het goed, de krat of de pallet.
*   De brongebied en de bestemmingsgebied.
*   De prioriteit van de opdracht en eventueel de gewenste uitvoeringstijd.
*   De actuele status van de opdracht, bijvoorbeeld aangemaakt, toegewezen, wachtend op overdracht, overgedragen of afgerond.
Met een uniek identificatienummer kan het systeem herkennen of een ontvangen bericht bij een bestaande opdracht hoort. Dit helpt voorkomen dat dezelfde transportopdracht meerdere keren wordt aangemaakt of uitgevoerd.
De opdracht moet bovendien altijd de juiste bron- en bestemmingszone bevatten. Een robotvloot mag uitsluitend opdrachten uitvoeren die binnen de eigen hygiënezone vallen. De overdracht tussen zones moet via het daarvoor aangewezen overdrachtspunt plaatsvinden.

### 3.2.3 Status en beschikbaarheid van robots[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.2.3-status-en-beschikbaarheid-van-robots)

De robotvloten(/ robots) moeten voldoende informatie uitwisselen om te bepalen of een transportopdracht kan worden uitgevoerd.
Daarvoor zijn met name de beschikbaarheid van een robot, de actuele opdrachtstatus en eventuele storingen relevant. Een indicatie van de verwachte aankomsttijd kan daarnaast helpen om transportopdrachten beter op elkaar af te stemmen.
Wanneer een robot vertraagd is of een storing heeft, kan het systeem daarmee rekening houden. Het kan bijvoorbeeld een opdracht uitstellen, een andere geschikte robot inzetten of voorkomen dat het overdrachtspunt onnodig lang bezet blijft.
Niet alle interne robotgegevens hoeven hiervoor te worden uitgewisseld. Alleen informatie die nodig is voor de transportcoördinatie hoeft tussen de robotvloten(/ robots) beschikbaar te zijn.

### 3.2.4 Bevestigingen van overdrachten[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.2.4-bevestigingen-van-overdrachten)

Het systeem moet kunnen vaststellen of een transportopdracht daadwerkelijk is uitgevoerd.
Daarvoor zijn bevestigingen nodig bij belangrijke momenten in het overdrachtsproces. Denk aan het accepteren van een opdracht, het gereedzetten van een goed, het overnemen van het goed door de ontvangende robotvloot en het afronden van de overdracht.
Een ontvangen bericht betekent namelijk niet automatisch dat de fysieke overdracht is uitgevoerd. De status van de transportopdracht moet daarom pas worden gewijzigd wanneer de bijbehorende stap daadwerkelijk is bevestigd.
Iedere overdracht moet daarnaast worden geregistreerd met het tijdstip, de betrokken robots en het gebruikte overdrachtspunt. Dit sluit aan bij de randvoorwaarden van Viscon Group, waarin achteraf aantoonbaar moet zijn hoe een overdracht heeft plaatsgevonden.

### 3.2.5 Actualiteit van informatie en verbindingsstatus[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=3.2.5-actualiteit-van-informatie-en-verbindingsstatus)

Ten slotte moet het systeem kunnen vaststellen of de ontvangen informatie nog actueel is.
Bij belangrijke berichten zijn daarom een tijdstip, een uniek bericht- of opdrachtnummer en eventueel een versienummer van de status nuttig. Hierdoor kan het systeem herkennen dat een ontvangen bericht ouder is dan de informatie die al beschikbaar is.
Ook moet duidelijk zijn wanneer een robotvloot of communicatiesysteem niet meer bereikbaar is. Hiervoor kunnen periodieke statusberichten of heartbeats worden gebruikt.
Als de verbinding uitvalt en de actuele status van het overdrachtspunt niet meer kan worden vastgesteld, mag het systeem niet zonder meer aannemen dat het overdrachtspunt nog beschikbaar is.

### Antwoord op deelvraag 1[](https://dev.azure.com/AvansHogeschoolAcademies/ATIx-2627-ESE2.1-OnderzoeksProject/_wiki/wikis/ATIx-2627-ESE2.1-OnderzoeksProject.wiki/1262/Onderzoekresultaten?anchor=antwoord-op-deelvraag-1)

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