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
| 4 | Prototyping, data-analyse | Vertraging en overhead hangen af van de opstelling, dus die meet ik zelf. Met Wireshark tel ik de pakketten. |
| 5 | Prototyping, data-analyse | Ik test verschillende time-outs en kijk per instelling hoe snel uitval gezien wordt en hoeveel valse alarmen er zijn. |
| Hoofdvraag | Multicriteria-analyse, peer review | Met de MCA vergelijk ik de varianten op meerdere criteria. Met de peer review laat ik mijn opzet en resultaten controleren voordat ik conclusies trek. |

### 3.4 Testopstelling (prototype)

Ik maak twee C++-programma's: coördinator A (zone A) en coördinator B (zone B). Coördinator A stuurt overdrachtsopdrachten naar B. Elke opdracht heeft een uniek ID. B voert de opdracht "uit" (schrijft hem in een logbestand) en stuurt een bevestiging terug. Tussen de twee zit een tool die storingen veroorzaakt.

::: mermaid

graph LR

    A[Coördinator A - C++] -->|opdracht met ID| F[Storingstool - clumsy / tc netem]

    F --> M[MQTT-broker - alleen bij V3 en V4]

    M --> B[Coördinator B - C++]

    B -->|bevestiging| F

    A -.-> L[(Logbestanden)]

    B -.-> L

:::

*Figuur 1. Testopstelling met twee coördinatoren en een storingstool ertussen. (Gemaakt met Claude)*

#### Varianten

| Variant | Mechanisme | Wat verwacht ik? |
|--|--|--|
| V1 | Alleen TCP, geen bevestiging vanuit de applicatie | Opdrachten kunnen verloren gaan bij een onderbreking |
| V2 | TCP + bevestiging + opnieuw versturen + uniek ID | Geen verlies, geen dubbele uitvoering |
| V3 | MQTT QoS 1 + uniek ID | Geen verlies, geen dubbele uitvoering |
| V4 | MQTT QoS 2 | Geen dubbele berichten, maar mogelijk verlies bij een crash van B |
  
#### Testscenario's

Elk scenario draai ik met 1000 opdrachten en 5 keer per variant.

| Scenario | Storing |
|--|--|
| S0 | Geen storing (referentie) |
| S1 | 5% pakketverlies |
| S2 | 20% pakketverlies |
| S3 | Verbinding valt 2 seconden weg, elke 30 seconden |
| S4 | Verbinding valt 10 seconden weg |
| S5 | Coördinator B crasht en start opnieuw op |

#### Wat meet ik?

- A logt per opdracht: ID, tijd verstuurd, tijd bevestiging ontvangen.
- B logt per opdracht: ID, tijd ontvangen, uitgevoerd ja/nee.
- Een script vergelijkt de logs:
  - verloren = verstuurd maar nooit uitgevoerd
  - dubbel = vaker dan 1 keer uitgevoerd
  - vertraging = tijd tussen versturen en bevestiging (gemeten op computer A, zodat de klokken van twee computers niet uitmaken)

### 3.5 Benodigde middelen

| Middel | Waarvoor |
|--|--|
| laptop en Raspberry Pi + router/switch | Twee aparte zones op een echt netwerk |
| C++, GitHub | Prototype en versiebeheer |
| Sockets (Winsock of POSIX) | Variant V1 en V2 |
| Mosquitto (broker) + Eclipse Paho MQTT C++ | Variant V3 en V4 |
| clumsy (Windows) of tc netem (Raspberry Pi) | Storingen op een herhaalbare manier veroorzaken |
| Wireshark | Pakketten tellen (overhead) en controleren wat er gebeurt |
| Python of Excel | Logs analyseren en grafieken maken |
| Andere studenten en de docent | Peer review en feedback |

### 3.6 Criteria voor analyse (MCA)

| Criterium | Hoe meet ik het? | Gewicht |
|--|--|--|
| Verloren opdrachten | aantal per 1000 | Moet 0 zijn (anders valt de variant af) |
| Dubbel uitgevoerde opdrachten | aantal per 1000 | Moet 0 zijn (anders valt de variant af) |
| Vertraging | milliseconden (gemiddeld en de langzaamste 5%) | 20% |
| Hersteltijd na een onderbreking | seconden tot alle opdrachten weer verwerkt zijn | 20% |
| Overhead | aantal pakketten en bytes per opdracht | 20% |
| Detectie van uitval | seconden en aantal valse alarmen | 20% |
| Complexiteit | hoeveel code en extra software nodig is | 20% |

De gewichten zijn voorlopig. Ik pas ze aan als ik het antwoord van de product owner heb (deelvraag 2). Varianten die opdrachten verliezen of dubbel uitvoeren, laat ik wel in de resultaten zien, maar ze kunnen niet winnen in de MCA.

### 3.7 Globale planning

| Stap | Wat | Oplevering |
|--|--|--|
| 1 | Onderzoeksopzet afmaken en feedback vragen | Onderzoeksopzet v1 + feedback |
| 2 | Prototype bouwen: eerst V1 en V2 (TCP), daarna V3 en V4 (MQTT) | Code op GitHub |
| 3 | Metingen S0 t/m S5 en de time-outtest | Logbestanden + resultaten in de wiki |
| 4 | Data-analyse en grafieken | Resultatenpagina |
| 5 | Peer review | Feedback + verwerking |
| 6 | MCA en conclusie | Conclusiepagina |
| 7 | Evaluatie, AI-verantwoording, code als zip | Wiki compleet |  
| ASYNC | Mail naar de product owner (deelvraag 2) | Grenswaarden |

### 3.8 Betrouwbaarheid en validiteit

#### Betrouwbaarheid

- Elk scenario draai ik 5 keer met 1000 opdrachten.
- Storingen maak ik met een tool, niet door met de hand een kabel eruit te trekken.
- Alle testscenario's staan vast op deze pagina en als script in de repository.
- Bij elke meting noteer ik de datum, de versie van de code en de opstelling.

#### Validiteit

- Ik kijk of een opdracht echt is uitgevoerd bij B, en niet alleen of het bericht is aangekomen.
- De vertraging meet ik op één computer, zodat verschillen tussen klokken geen rol spelen.
- Met Wireshark controleer ik of de opstelling doet wat ik denk.
- Beperking: ik test in een eigen netwerk en niet in een echte fabriek met WiFi. Dit wordt meegenomen in de evaluatie.