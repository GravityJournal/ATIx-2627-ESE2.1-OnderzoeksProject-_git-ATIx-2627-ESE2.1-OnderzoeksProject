# Wat is het effect van een multi-communicatie-infrastructuur op de betrouwbaarheid van de transportlaag?

* * *
* * *

# Deelvragen

## Welke transportprotocollen zijn geschikt voor de verschillende berichtlijnen?

Voor dit onderzoek gaan we analyseren wat de juiste berichtlijnen zijn en welke transportprotocollen geschikt zijn voor deze berichtlijnen.
Dit is relevant omdat dit nodig is om een logische en betrouwbare multi-communicatie-infrastructuur binnen dit project te creëren. De verschillende berichtlijnen kunnen namelijk verschillende eisen stellen aan de betrouwbaarheid van de gegevensoverdracht.

### Onderzoeksmethode: Literatuuronderzoek + Data-analyse

| Benodigdheden |
| --- |
| Laptop |
| Voorgaand onderzoek |
| Voorgaande gebruikte literatuur |
| Documentatie van transportprotocollen |
| Criteria | Definitie |
| --- | --- |
| Betrouwbaarheid | De mate waarin een bericht volledig en correct bij de ontvanger aankomt. |
| Overhead | De hoeveelheid extra data die een transportprotocol toevoegt aan een bericht. |

**Hoe verzamelen we data?** Door informatie uit het voorgaande onderzoek, de bijbehorende literatuur en technische documentatie van transportprotocollen te verzamelen.

**Hoe analyseren we het resultaat?** Door de eigenschappen van de verschillende protocollen te vergelijken met de communicatiebehoeften van de berichtlijnen. Op basis hiervan bepalen we welk protocol het beste aansluit bij iedere berichtlijn.

**Waarom doen we het op deze manier?** Omdat het individueel testen van ieder beschikbaar communicatieprotocol buiten de scope van het project valt. In het vooronderzoek is bovendien al vastgesteld dat er voldoende literatuur beschikbaar is om een onderbouwde keuze te maken.

**Is dit haalbaar?** Ja, omdat de benodigde informatie grotendeels beschikbaar is in bestaande literatuur en technische documentatie.


* * *

## Wat is het ontwerp voor de multi- en single- communicatie programma's ?

Voor dit onderzoek gaan we twee klassendiagrammen maken: één voor de single-communicatie-infrastructuur en één voor de multi-communicatie-infrastructuur. Deze diagrammen worden vervolgens uitgewerkt tot code.

Dit is relevant omdat beide communicatiesituaties nodig zijn om een eerlijke vergelijking te kunnen maken. Door beide situaties op dezelfde manier te implementeren, kunnen we onderzoeken welk effect het gebruik van meerdere communicatie-infrastructuren heeft op de betrouwbaarheid van de gegevensoverdracht.

### Onderzoeksmethode: Prototyping + Peer Review

| Benodigdheden |
| --- |
| Laptop |
| Visual Studio |
| PowerPoint of Lucidchart |

**Hoe verzamelen we data?** Door de twee mogelijke communicatiesituaties eerst uit te werken in klassendiagrammen en deze vervolgens te implementeren in code. Hierbij zorgen we ervoor dat beide implementaties dezelfde functionaliteit en berichtinhoud ondersteunen.
**Hoe analyseren we het resultaat?** Door de klassendiagrammen en de uiteindelijke implementaties door een tweede persoon te laten controleren. Hierbij beoordelen we of de implementaties realistisch zijn en of er fouten aanwezig zijn.

| Criteria | Meetmethode | Definitie |
| --- | --- | --- |
| Realisme | Peer review | Hoe realistisch is de situatie in vergelijking met een werkelijke situatie? |
| Fouten | Codecontrole | Zijn er fouten aanwezig in de implementatie? |

**Waarom doen we het op deze manier?** Zodat de kwaliteit van de code door een tweede partij wordt gecontroleerd en niet uitsluitend afhankelijk is van de kennis of mogelijke vooringenomenheid van de maker.
**Is dit haalbaar?** Ja, zolang de implementatie niet zo uitgebreid wordt dat volledige simulaties van werkelijke systemen nodig zijn.

* * *

## Wat is het verschil in berichtverlies tussen de multi-communicatiemethode en de single-communicatiemethode?

Voor dit onderzoek gaan we het berichtverlies van de single-communicatiemethode en de multi-communicatiemethode met elkaar vergelijken. Hiervoor versturen we dezelfde berichten via beide methoden en meten we hoeveel berichten succesvol bij de ontvanger aankomen.
Dit is relevant omdat berichtverlies direct invloed heeft op de betrouwbaarheid van de gegevensoverdracht. Wanneer berichten niet aankomen, kunnen machines mogelijk niet correct reageren op de ontvangen informatie.

### Onderzoeksmethode: Prototyping + Data-analyse

| Benodigdheden |
| --- |
| 2x Laptop |
| Visual Studio |
| Geïmplementeerde single-communicatiecode met berichtverliesmeting |
| Geïmplementeerde multi-communicatiecode met berichtverliesmeting |
| Google Sheets |
| Excel |

| Criteria | Eenheid | Definitie |
| --- | --- | --- |
| Berichtverlies | Percentage (%) | Het percentage verzonden berichten dat niet bij de ontvanger aankomt. |
| Ontvangstpercentage | Percentage (%) | Het percentage verzonden berichten dat succesvol bij de ontvanger aankomt. |

**Hoe verzamelen we data?** Door beide implementaties meerdere keren te laten uitvoeren. Hierbij registreren we hoeveel berichten worden verzonden en hoeveel berichten daadwerkelijk bij de ontvanger aankomen. De metingen worden uitgevoerd voor de verschillende berichtlijnen en vastgelegd in een txt-bestand. Hiervoor krijgt ieder bericht een uniek identificatienummer, zodat verzonden en ontvangen berichten met elkaar vergeleken kunnen worden.

**Hoe analyseren we het resultaat?** Door het berichtverlies en ontvangstpercentage van beide methoden met elkaar te vergelijken.

| Criteria | Eenheid | Meetmethode |
| --- | --- | --- |
| Aantal verzonden berichten | Berichten | Het totale aantal verzonden berichten tellen. |
| Aantal ontvangen berichten | Berichten | Het totale aantal succesvol ontvangen berichten tellen. |
| Berichtverlies | % | Het aantal verloren berichten delen door het aantal verzonden berichten en vermenigvuldigen met 100. |
| Verschil in berichtverlies | Procentpunten | Het berichtverlies van beide methoden met elkaar vergelijken. |

**Waarom doen we het op deze manier?** Omdat we hiermee rechtstreeks kunnen meten hoeveel berichten verloren gaan bij beide communicatiemethoden. Hierdoor kunnen we vaststellen welke methode de betrouwbaarste gegevensoverdracht biedt.

**Is dit haalbaar?** Ja, omdat het aantal verzonden en ontvangen berichten met behulp van code kan worden bijgehouden.

* * *

## Wat is het verschil in latency tussen de multi-communicatiemethode en de single-communicatiemethode?

Voor dit onderzoek gaan we de latency van de single-communicatiemethode en de multi-communicatiemethode met elkaar vergelijken. Hiervoor versturen we dezelfde berichten via beide methoden en meten we hoeveel tijd er verstrijkt tussen het verzenden en ontvangen van een bericht.

Dit is relevant omdat latency invloed heeft op de snelheid waarmee machines op elkaar kunnen reageren. Een hoge latency kan ervoor zorgen dat informatie te laat aankomt, wat gevolgen kan hebben voor de betrouwbaarheid van de communicatie.

### Onderzoeksmethode: Prototyping + Data-analyse

| Benodigdheden |
| --- |
| 2x Laptop |
| Visual Studio |
| Geïmplementeerde single-communicatiecode met latency-meetfunctie |
| Geïmplementeerde multi-communicatiecode met latency-meetfunctie |
| Google Sheets |
| Excel |
| Criteria | Eenheid | Definitie |
| --- | --- | --- |
| Latency | ms | De tijd tussen het verzenden en ontvangen van een bericht. |

**Hoe verzamelen we data?** Door beide implementaties meerdere keren te laten uitvoeren en de verzend- en ontvangsttijd van ieder bericht vast te leggen. De metingen worden uitgevoerd voor de verschillende berichtlijnen en vastgelegd in een txt-bestand.

**Hoe analyseren we het resultaat?**

| Criteria | Eenheid | Meetmethode |
| --- | --- | --- |
| Gemiddelde latency | ms | Het gemiddelde berekenen van alle gemeten berichten. |
| Maximale latency | ms | De hoogste gemeten latency bepalen. |
| 95e percentiel latency | ms | De latency bepalen waaronder 95% van de berichten valt. |
| Verschil in latency | ms en % | De resultaten van beide methoden met elkaar vergelijken. |

Door de gemiddelde, maximale en 95e percentiel latency van beide methoden te vergelijken, kunnen we vaststellen welke communicatiemethode de meest consistente gegevensoverdracht biedt.

**Waarom doen we het op deze manier?** Omdat we hiermee zowel de gemiddelde vertraging als uitschieters in de latency kunnen vaststellen. Dit geeft een beter beeld van de betrouwbaarheid van de communicatie dan alleen het gemiddelde.

**Is dit haalbaar?** Ja, omdat de verzend- en ontvangsttijd met behulp van code kan worden vastgelegd.

* * *

## Wat is het verschil in benodigde bandbreedte tussen de multi-communicatiemethode en de single-communicatiemethode?

Voor dit onderzoek gaan we de benodigde bandbreedte van de single-communicatiemethode en de multi-communicatiemethode met elkaar vergelijken. Hiervoor versturen we dezelfde berichten via beide methoden en meten we hoeveel data er per seconde wordt verzonden.

Dit is relevant omdat de beschikbare bandbreedte invloed kan hebben op de betrouwbaarheid van de gegevensoverdracht. Wanneer de benodigde bandbreedte groter is dan de beschikbare capaciteit, kunnen vertragingen of berichtverlies ontstaan.

### Onderzoeksmethode: Prototyping + Data-analyse

| Benodigdheden |
| --- |
| 2x Laptop |
| Visual Studio |
| Geïmplementeerde single-communicatiecode met bandbreedtemeetfunctie |
| Geïmplementeerde multi-communicatiecode met bandbreedtemeetfunctie |
| Google Sheets |
| Excel |

| Criteria | Eenheid | Definitie |
| --- | --- | --- |
| Benodigde bandbreedte | kbit/s | De hoeveelheid data die per seconde via de communicatie-infrastructuur wordt verstuurd. |

**Hoe verzamelen we data?** Door beide implementaties meerdere keren te laten uitvoeren en de hoeveelheid verzonden data gedurende een bepaalde tijd vast te leggen. De metingen worden uitgevoerd voor de verschillende berichtlijnen en vastgelegd in een txt-bestand.

**Hoe analyseren we het resultaat?** Door de totale datagrootte, gemiddelde bandbreedte, maximale bandbreedte en 95e percentiel bandbreedte van beide methoden met elkaar te vergelijken.

| Criteria | Eenheid | Meetmethode |
| --- | --- | --- |
| Totale datagrootte | Bytes (B) | Het totale aantal verzonden bytes meten. |
| Gemiddelde bandbreedte | kbit/s | De totale hoeveelheid verzonden bits delen door de meetduur in seconden. |
| Maximale bandbreedte | kbit/s | De hoogste gemeten hoeveelheid verzonden bits per seconde bepalen. |
| 95e percentiel bandbreedte | kbit/s | De bandbreedte bepalen waaronder 95% van de gemeten waarden valt. |
| Verschil in bandbreedte | kbit/s en % | De resultaten van beide methoden met elkaar vergelijken. |

**Waarom doen we het op deze manier?** Omdat we hiermee kunnen onderzoeken hoeveel netwerkcapaciteit beide communicatiemethoden nodig hebben. Hierdoor kunnen we vaststellen of het verdelen van berichtlijnen over meerdere communicatie-infrastructuren invloed heeft op het totale bandbreedtegebruik.

**Is dit haalbaar?** Ja, omdat de hoeveelheid verzonden data en de meetduur met behulp van code kunnen worden vastgelegd.

* * *

## Wat is het verschil in beschikbaarheid tussen de multi-communicatie-infrastructuur en de single-communicatie-infrastructuur?

Voor dit onderzoek gaan we de beschikbaarheid van de single-communicatie-infrastructuur en de multi-communicatie-infrastructuur met elkaar vergelijken. Hiervoor onderzoeken we hoe vaak de communicatie-infrastructuren beschikbaar zijn en of de communicatie blijft functioneren wanneer een communicatieverbinding uitvalt.

Dit is relevant omdat de beschikbaarheid bepaalt in hoeverre de communicatie-infrastructuur bruikbaar blijft wanneer deze nodig is. Een multi-communicatie-infrastructuur kan mogelijk voordelen bieden doordat verschillende berichtlijnen over afzonderlijke communicatieverbindingen worden verdeeld. Hierdoor hoeft een storing in één verbinding niet automatisch gevolgen te hebben voor alle berichtlijnen.

### Onderzoeksmethode: Prototyping + Data-analyse

| Benodigdheden |
| --- |
| 2x Laptop |
| Visual Studio |
| Geïmplementeerde single-communicatiecode |
| Geïmplementeerde multi-communicatiecode |
| Mogelijkheid om communicatieverbindingen te onderbreken |
| Google Sheets |
| Excel |

| Criteria | Eenheid | Definitie |
| --- | --- | --- |
| Beschikbaarheid | Percentage (%) | Het percentage van de totale meetperiode waarin de communicatie succesvol beschikbaar is. |
| Hersteltijd | ms of s | De tijd die nodig is voordat de communicatie na een storing weer functioneert. |
| Uitvalfrequentie | Aantal | Het aantal keren dat de communicatie tijdens de meetperiode uitvalt. |

**Hoe verzamelen we data?** Door beide implementaties gedurende een gelijke periode te laten uitvoeren. Hierbij registreren we wanneer de communicatie beschikbaar is en wanneer er sprake is van een storing. Daarnaast onderbreken we gecontroleerd een communicatieverbinding om te onderzoeken wat het effect hiervan is op de verschillende berichtlijnen. De resultaten worden vastgelegd in een txt-bestand.

**Hoe analyseren we het resultaat?** Door de beschikbaarheid, hersteltijd en uitvalfrequentie van beide methoden met elkaar te vergelijken.

| Criteria | Eenheid | Meetmethode |
| --- | --- | --- |
| Totale meetduur | Seconden (s) | De totale duur van de meting vastleggen. |
| Beschikbare communicatieduur | Seconden (s) | De tijd meten waarin de communicatie succesvol functioneert. |
| Beschikbaarheid | % | De beschikbare communicatieduur delen door de totale meetduur en vermenigvuldigen met 100. |
| Hersteltijd | ms of s | De tijd tussen het optreden van een storing en het succesvol hervatten van de communicatie meten. |
| Uitvalfrequentie | Aantal | Het aantal storingen gedurende de meetperiode tellen. |

**Waarom doen we het op deze manier?** Omdat we hiermee kunnen onderzoeken hoe goed beide communicatie-infrastructuren blijven functioneren wanneer er storingen optreden. Vooral het gecontroleerd onderbreken van verbindingen maakt het mogelijk om te onderzoeken of een multi-communicatie-infrastructuur voordelen biedt bij verbindingsuitval.

**Is dit haalbaar?** Ja, omdat de beschikbaarheid en hersteltijd met behulp van code kunnen worden bijgehouden. Het onderbreken van communicatieverbindingen kan bovendien gecontroleerd worden uitgevoerd.

* * *

# Planning

| Deadline | Activiteit | Onderzoeker | C | Reviewer | C |
| --- | --- | --- | :-: | --- | :-: |
| Week 8 | Literatuur Onderzoek Deelvraag 1 | K. Mennens | X | T. Ramerman |  |
| Week 9 | Programmadesign Deelvraag 2-6 | K. Mennens | T | T. Ramerman |  |
| Week 9 | Programmabouwing Deelvraag 2 | K. Mennens | T | T. Ramerman |  |
| Week 10 | Documentatieprogramma 2 | K. Mennens | T | T. Ramerman |  |
| Week 10 | Programmabouwing Deelvraag 3-6 | K. Mennens |  | T. Ramerman |  |
| Week 10 | Documentatieprogramma 3-6 | K. Mennens |  | T. Ramerman |  |
| Week 11 | Programma bevindingen | K. Mennens |  | T. Ramerman |  |

X = Gedaan  
T = Gedaan, maar te laat