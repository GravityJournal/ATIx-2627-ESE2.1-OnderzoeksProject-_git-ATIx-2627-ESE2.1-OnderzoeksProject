      
# hoofdvraag 2

Hoe groot is de overhead van encryptie en integriteits-controle op de netwerkprestaties bij robotcommunicatie?

## Deelvragen
1. Welke encryptie methodes worden in 2025 gebruikt bij robotcommunicatie?
Deze vraag is relevant omdat je niet de overhead kan meten zonder te weten welke methodes je moet gebruiken.
2. Hoeveel overhead wordt door encryptie veroorzaakt bij robotcommunicatie?
Deze vraag is relevant omdat door de overhead te kwantificeren voor de verschillende encryptie methodes, het je helpt een keuze te maken met de methodes.
3. Welke integriteit methodes worden in 2025 gebruikt bij robot communicatie?
Deze vraag is relevant omdat je niet de overhead kan meten zonder te weten welke methodes je moet gebruiken.
4. Hoeveel overhead wordt door integriteits-controle  veroorzaakt bij robotcommunicatie?
Deze vraag is relevant omdat door de overhead te kwantificeren voor de verschillende integriteit methodes, het je helpt een keuze te maken met de methodes.
5. Welke encryptie veroorzaakt de kleinste overhead bij robotcommunicatie?
Deze vraag is relevant omdat het helpt bij het kiezen van een efficiënt  encryptie protocol.
6. Welke integriteits-controle veroorzaakt de kleinste overhead bij robot communicatie?
Deze vraag is relevant omdat het helpt bij het kiezen van een efficiënt  integriteit protocol.

## Onderzoek voor deelvraag 2.1
Welke encryptie methodes worden in 2025 gebruikt bij robotcommunicatie?
### Literatuur onderzoek
Waarom:
De informatie over welke encryptie methodes in robotcommunicatie gebruikt worden is redelijk toegankelijk en bestaat al in wetenschappelijke artikelen.
#### Betrouwbaarheid
- Meetbaarheid:
               - laag, het is een inventariserende vraag, niet kwantitatief.
- Reproduceerbaarheid:
               - hoog, voor het jaar 2025. Als dezelfde bronnen worden geraadpleegd, levert dit dezelfde lijst met methodes op.
#### Validiteit
Ja, omdat het onderzoek direct inzicht geeft in de methodes die in gebruik zijn in 2025.
### Middelen
- computer/laptop/smartphone: voor toegang tot het internet
- wetenschappelijke bronnen: voor raadpleging van betrouwbare bronnen
### Criteria
- Eenvoudig: De resultaten moeten overzichtelijk en toegankelijk zijn.
- Snel: Binnen een uur de methodes kunnen vinden.
- Betrouwbaar: Alleen methodes die daadwerkelijk worden gebruikt in 2025.

## Onderzoek voor deelvraag 2.2
Hoeveel overhead wordt door encryptie veroorzaakt bij robotcommunicatie?
### Prototype
waarom: het gebruik van encryptie op netwerkprestaties kan duidelijk worden gemeten door robotcommunicatie na te bootsen en daarmee pakketverkeer vast te leggen en te analyseren.
#### Betrouwbaarheid
- Meetbaarheid: Hoog; pakketgroottes en timestamps zijn exact meetbaar.

- Reproduceerbaarheid: Hoog; als dezelfde methodes, netwerkopstelling en  tools gebruikt worden, levert dit vergelijkbare resultaten.

#### Validiteit
ja, omdat het metingen zijn van het effect van encryptie op netwerkpakketten.
### Middelen
- Simpele server & client programma opstelling.
- laptops als hardware voor het gebruik van de server & client opstelling
- Wireshark als tool voor het meten van de pakket overhead
### Criteria
- overhead in bytes: het verschil in pakketgrootte tussen data en encrypted data.
- Latency overhead: vertraging in milliseconden veroorzaakt door encryptie.
- consistentie: een standaard grootte bericht gebruiken voor beide data en encrypted data.

## Onderzoek voor deelvraag 2.3
Welke integriteit methodes worden in 2025 gebruikt bij robot communicatie?
### Literatuur onderzoek
Waarom:
De informatie over welke integriteit methodes in robotcommunicatie gebruikt worden is redelijk toegankelijk en bestaat al in wetenschappelijke artikelen.
#### Betrouwbaarheid
- Meetbaarheid: laag, het is een inventarisatie.
- Reproduceerbaarheid: hoog, voor het jaar 2025. Als dezelfde bronnen worden  geraadpleegd, levert dit dezelfde lijst met methodes op.
#### Validiteit
Ja, omdat het onderzoek inzicht geeft in de methodes die daadwerkelijk toegepast worden in 2025.
### Middelen
- computer/laptop/smartphone: voor toegang tot het internet
- wetenschappelijke bronnen: voor raadpleging van betrouwbare bronnen
### Criteria
- Eenvoudig: De resultaten moeten overzichtelijk en toegankelijk zijn.
- Snel: Binnen een uur de methodes kunnen vinden.
- Betrouwbaar: Alleen methodes die daadwerkelijk worden gebruikt in 2025.

## Onderzoek voor deelvraag 2.4
Hoeveel overhead wordt door integriteits-controle  veroorzaakt bij robotcommunicatie?
### Prototype light
Waarom:
Het gebruik van integriteitscontroles op netwerkprestaties kan duidelijk worden gemeten door robotcommunicatie na te bootsen en daarmee pakketverkeer vast te leggen en te analyseren.
#### Betrouwbaarheid
Meetbaarheid: hoog,  header groottes zijn exact meetbaar.
Reproduceerbaarheid: hoog, als dezelfde testopstelling wordt gebruikt.
#### Validiteit
Ja, omdat het metingen zijn van het effect van integriteitscontroles op netwerkpakketten.
### Middelen
- Simpele server & client programma opstelling.
- laptops als hardware voor het gebruik van de server & client opstelling
- Wireshark als tool voor het meten van de pakket overhead
### Criteria
- Overhead in bytes: het verschil in pakketgrootte tussen data en data met integriteits-controle.
- Latency overhead: vertraging in milliseconden veroorzaakt door integriteit.
- Consistentie: een standaard grootte bericht gebruiken voor beide data en data met integriteit methodes .

## Onderzoek voor deelvraag 2.5
Welke encryptie veroorzaakt de kleinste overhead bij robotcommunicatie?
### Multi-criteria analyse
Waarom:
door verschillende encryptie methodes te meten kan worden vastgesteld welke protocol de minste impact heeft op de netwerkprestaties.
#### Betrouwbaarheid
- Meetbaarheid: hoog, door gebruik te maken van Wireshark kan zowel de byte-grootte  als latency van de overhead, die ontstaan door het gebruik van de verschillende encryptie methodes , gebruikt worden om te vergelijken tegen de andere resultaten.
- Reproduceerbaarheid: hoog, als dezelfde methodes en testopstellingen worden gebruikt.

#### Validiteit
Ja, omdat de vergelijking direct de relevantie voor de hoofdvraag, overhead, meet.
### Middelen
- Data van het resultaat van het onderzoek uit deelvraag 2.
- laptop, voor het invoeren van de data in een multi-criteria analyse.
### Criteria
- Overhead in bytes: absolute extra bytes toegevoegd door de encryptie methodes per pakket.
- Latency overhead: vertraging in milliseconden veroorzaakt door de  encryptie methodes.

## Onderzoek voor deelvraag 2.6
Welke integriteitscontrole veroorzaakt de kleinste overhead bij robotcommunicatie?
### Multi-criteria analyse
Waarom:
Door verschillende integriteit methodes te meten kan worden vastgesteld welk protocol de minste impact heeft op de netwerkprestaties.
#### Betrouwbaarheid
- Meetbaarheid: hoog, door gebruik te maken van Wireshark kan zowel de byte-grootte  als latency van de overhead, die ontstaan door het gebruik van de verschillende integriteit methodes, gebruikt worden om te vergelijken tegen de andere resultaten.
- Reproduceerbaarheid: hoog, als dezelfde methodes en testopstellingen worden gebruikt.
#### Validiteit
Ja, omdat de vergelijking direct de relevantie voor de hoofdvraag, overhead, meet.
### Middelen
- Data van het resultaat van het onderzoek uit deelvraag 4.
- Laptop, voor het invoeren van de data in een multicriteria-analyse.
### Criteria
- Overhead in bytes: Absolute extra bytes toegevoegd door de integriteit methodes per pakket.
- Latency overhead: Vertraging in milliseconden veroorzaakt door de integriteit methodes.

#Verantwoording hergebruik

Deze tekst komt uit mijn onderzoeksproject van vorig jaar te vinden op: https://dev.azure.com/AvansHogeschoolAcademies/ATIxTI-2526-B2.1-OnderzoeksProject/_wiki/wikis/ATIxTI-2526-B2.1-OnderzoeksProject.wiki/19/Projectduo's