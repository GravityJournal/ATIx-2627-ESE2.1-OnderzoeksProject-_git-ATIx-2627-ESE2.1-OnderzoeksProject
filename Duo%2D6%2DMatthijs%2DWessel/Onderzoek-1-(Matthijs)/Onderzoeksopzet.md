## 3. Onderzoeksopzet

Op deze pagina staat hoe ik mijn onderzoek ga uitvoeren: welke methode ik per deelvraag gebruik, hoe de testopstelling eruitziet, wat ik nodig heb en hoe ik de resultaten ga vergelijken.

### 3.1 Onderzoeksvraag

Welk communicatiemechanisme tussen de systemen van zone A en zone B zorgt ervoor dat overdrachtsopdrachten bij communicatie-uitval niet verloren gaan en niet dubbel worden uitgevoerd, tegen een acceptabele vertraging en overhead?
  
### 3.2 Deelvragen

| Deelvraag | Waarom nodig? |
|--|--|
| 1. Welke mechanismen voor betrouwbare berichtaflevering bestaan er, en welke worden toegepast in bestaande AGV-systemen (bijv. VDA 5050)? | Hieruit volgen de varianten die ik ga testen. |
| 2. Welke maximale vertraging, hersteltijd en berichtenoverhead zijn voor een overdracht tussen twee zones nog acceptabel? | Zonder grenswaarden kan ik niet zeggen of een variant goed genoeg is. |
| 3. Hoeveel overdrachtsopdrachten gaan per variant verloren of worden dubbel uitgevoerd bij pakketverlies, verbindingsonderbreking en een crash van de ontvanger? | Dit test de eis uit de casus: geen verloren en geen dubbele opdrachten. |
| 4. Hoe groot is de extra vertraging en de berichtenoverhead per variant onder normale omstandigheden en onder storing? | Betrouwbaarder kost meestal meer tijd. Ik wil weten of dat binnen de grens van deelvraag 2 blijft. |
| 5. Welke instelling van time-out en heartbeat detecteert uitval van de andere zone het snelst zonder valse alarmen? | De casus zegt dat een sluis niet onnodig lang geblokkeerd mag blijven. Dit levert waarden op die ik in het ontwerp kan gebruiken. |

Deelvraag 1 levert de varianten op, deelvraag 2 de grenswaarden en deelvragen 3 t/m 5 de meetresultaten. Met een multicriteria-analyse kan ik daarna de hoofdvraag beantwoorden.

### 3.3 Onderzoeks- en analysemethoden
  
| Deelvraag | Methode | Waarom deze methode? |
|--|--|--|
| 1 | Literatuuronderzoek, Available Product Analysis (VDA 5050) | Het antwoord staat al in bestaande bronnen en standaarden, dus ik hoef het niet zelf te meten. |
| 2 | Expert interview (vragen per mail aan de product owner van Viscon), literatuuronderzoek | In de literatuur staat geen vaste waarde. Wat acceptabel is, hangt van de casus af, en dat weet de opdrachtgever het beste. |
| 3 | Prototyping, data-analyse | Hoeveel opdrachten verloren gaan of dubbel worden uitgevoerd, kan ik alleen weten door het zelf te testen. |
| 4 | Prototyping, data-analyse | Vertraging en overhead hangen af van de opstelling, dus die meet ik zelf. Het storingsprogramma telt de bytes en stukjes. |
| 5 | Prototyping, data-analyse | Ik test verschillende time-outs en kijk per instelling hoe snel uitval gezien wordt en hoeveel valse alarmen er zijn. |
| Hoofdvraag | Multicriteria-analyse, peer review | Met de MCA vergelijk ik de varianten op meerdere criteria. Met de peer review laat ik mijn opzet en resultaten controleren voordat ik conclusies trek. |
  
### 3.4 Testopstelling (prototype)

Ik heb C++-programma's gemaakt voor coördinator A (zone A) en coördinator B (zone B). A stuurt 1000 overdrachtsopdrachten naar B. Elke opdracht is een uniek nummer. B voert de opdracht "uit" (schrijft het nummer in een logbestand) en stuurt daarna "klaar" terug. Tussen A en B zit het storingsprogramma.

::: mermaid

graph LR

    A[Coördinator A - C++] --> F[Storingsprogramma - C++]

    B[Coördinator B - C++] --> F

    F --> M[MQTT-broker - alleen bij V3 en V4]

    A -.-> L[(Logbestanden)]

    B -.-> L

:::

*Figuur 1. Testopstelling bij MQTT: A en B lopen allebei door het storingsprogramma. Bij TCP gaat A via het storingsprogramma rechtstreeks naar B.*

#### Varianten

| Variant | Mechanisme | Wat verwacht ik? |
|--|--|--|
| V1 | Alleen TCP, A stuurt niets opnieuw | Opdrachten kunnen verloren gaan bij een onderbreking |
| V2 | TCP + bevestiging + opnieuw versturen + uniek nummer | Geen verlies, geen dubbele uitvoering |
| V3 | MQTT QoS 1 + uniek nummer | Geen verlies, geen dubbele uitvoering |
| V4 | MQTT QoS 2 | Geen dubbele berichten, maar mogelijk verlies bij een crash van B |

#### Testscenario's
  
Elk scenario draai ik met 1000 opdrachten en 5 keer per variant.
  
| Scenario | Storing |
|--|--|
| S0 | Geen storing (referentie) |
| S1 | 5% van de berichten wordt 300 ms vastgehouden |
| S2 | 20% van de berichten wordt 300 ms vastgehouden |
| S3 | Vanaf 3 s: elke 5 s is de verbinding 2 s kapot |
| S4 | Na 3 s is de verbinding 1 keer 10 s kapot |
| S5 | B crasht na 4 s en start 1 s later opnieuw |

Voor deelvraag 5 stuurt B hartslagen naar A. Ik test een interval van 100, 250, 500 en 1000 ms, met een time-out van 2 en 3 keer het interval. Elke instelling test ik 5 keer op valse alarmen (20 s lang, 20% vastgehouden) en op hoe snel A een uitval ziet.

#### Wat meet ik?
 
- A logt per opdracht: nummer, gelukt of mislukt, wachttijd en tijdstip.
- B logt per opdracht: het nummer.
- Een script vergelijkt de logs:
  - verloren = A heeft het verstuurd, maar B heeft het nooit uitgevoerd
  - dubbel = B heeft het vaker dan 1 keer uitgevoerd
  - mislukt = A kreeg geen "klaar" en gaf het op
  - niet gemeld = A denkt dat het mislukt is, maar B heeft het wel uitgevoerd
  - vertraging = tijd tussen versturen en "klaar" (gemeten op computer A, zodat de klokken van twee computers niet uitmaken)
  - hersteltijd = het langste gat tussen twee gelukte opdrachten
  
### 3.5 Benodigde middelen
  
| Middel | Waarvoor |
|--|--|
| 2 Windows-laptops + router/switch | Twee aparte zones op een echt netwerk |
| C++, CMake, Visual Studio | Prototype |
| Winsock | Variant V1 en V2 |
| Mosquitto (broker) + Eclipse Paho MQTT C++ | Variant V3 en V4 |
| Eigen storingsprogramma | Storingen op een herhaalbare manier veroorzaken en bytes tellen |
| Python | Tests draaien en logs analyseren |
| Python | Grafieken maken |
| Mail aan de product owner | Deelvraag 2 |
| Andere studenten en de docent | Peer review en feedback |
  
### 3.6 Criteria voor analyse (MCA)
  
| Criterium | Hoe meet ik het? | Gewicht |
|--|--|--|
| Verloren opdrachten | aantal per 1000 | Moet 0 zijn (anders valt de variant af) 
| Dubbel uitgevoerde opdrachten | aantal per 1000 | Moet 0 zijn (anders valt de variant af) |
| Vertraging | milliseconden (gemiddeld en de langzaamste 5%) | 20% |
| Hersteltijd na een onderbreking | langste gat tussen twee gelukte opdrachten | 20% |
| Overhead | aantal stukjes en bytes per opdracht | 20% |
| Detectie van uitval | seconden en aantal valse alarmen | 20% |
| Complexiteit | hoeveel code en extra software nodig is | 20% |
  
De gewichten zijn voorlopig. Ik pas ze aan als ik deelvraag 2 heb. Varianten die opdrachten verliezen of dubbel uitvoeren, laat ik wel in de resultaten zien, maar ze kunnen niet winnen in de MCA.
  
### 3.7 Globale planning
  
| Stap | Wat | Oplevering |
|--|--|--|
| 1 | Metingen S0 t/m S5 en de time-outtest | Logbestanden + resultaten in de wiki |
| 2 | Data-analyse en grafieken | Resultatenpagina |
| 3 | Peer review | Feedback + verwerking |
| 4 | MCA en conclusie | Conclusiepagina |
| 5 | Evaluatie, AI-verantwoording, code als zip | Wiki compleet |
  
### 3.8 Betrouwbaarheid en validiteit
  
#### Betrouwbaarheid
  
- Elk scenario draai ik 5 keer met 1000 opdrachten.
- Storingen maak ik met een programma, niet door met de hand een kabel eruit te trekken.
- Alle testscenario's staan vast op deze pagina en in het testscript.
- Bij elke meting noteer ik de datum en de opstelling. De logs van elke run bewaar ik.

  
#### Validiteit
  
- Ik kijk of een opdracht echt is uitgevoerd bij B, en niet alleen of het bericht is aangekomen.
- De vertraging meet ik op één computer, zodat verschillen tussen klokken geen rol spelen.
- Beperking: pakketverlies is nagedaan met 300 ms vasthouden. De vertraging bij S1 en S2 laat vooral zien hoeveel berichten een variant nodig heeft, niet hoe een echt netwerk reageert.
- Beperking: bij een verbreking merken A en B meteen dat de verbinding weg is. Bij een echte storing blijft het soms stil.
- Beperking: ik test in een eigen netwerk en niet in een echte fabriek met WiFi.