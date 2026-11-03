      
# hoofdvraag 1

Hoe beïnvloeden verschillende draadloze infrastructuren (WiFi, 4G, 5G) de datadoorvoer (throughput) van de communicatie tussen robots?

## Deelvragen

1. welke verschillende standaarden zijn er voor wifi, 4g en 5g in 2025?

Deze vraag is relevant omdat een specifieke infrastructuur gekozen moet worden voor de communicatie tussen robots.

2. Hoe beïnvloed de wifi infrastructuur standaarden de datadoorvoer van de communicatie tussen robots?

Deze vraag is relevant omdat WiFi is wijdverspreid en eenvoudig inzetbaar

3. Hoe beïnvloed de 4g infrastructuur standaarden de datadoorvoer van de communicatie tussen robots?

Deze vraag is relevant omdat 4G biedt dekking over grote afstanden en ondersteunt mobiele robots

4. Hoe beïnvloed de 5g infrastructuur standaarden de datadoorvoer van de communicatie tussen robots?

Deze vraag is relevant omdat 5G een snellere optie is dan 4G en dat in real time een verschil zou kunnen maken

5. Welke draadloze infrastructuur geeft de beste datadoorvoer en welke het minst?

Deze vraag is relevant omdat de verschillende infrastructuren vergeleken worden met elkaar en zo kunnen zien wat we het beste kunnen gebruiken.

## onderzoek voor deelvraag 1.1
### Literatuur onderzoek
waarom:
de informatie om deze deelvraag te beantwoorden is redelijk toegankelijk en bestaat al.
#### betrouwbaarheid:
- meetbaarheid
               - nee, want het is een inventariserende vraag, niet iets dat je kwantitatief kunt meten.
-  reproduceerbaarheid:
               - ja, want het is een verzameling van de bestaande versies van draadloze infrastructuren van 2025.

#### validiteit:
-  ja, want ik zoek naar bekende standaarden en dit levert ook de opsomming van die standaarden op.
passen de metingen bij mijn deelvraag:
- ja, aangezien het niet echt een meting is maar het opzoeken van bestaande standaarden van draadloze netwerken.

### Middelen:
Computer/laptop/smartphone:
Voor toegang tot het internet.

Internet:
Om de al bestaande informatie van de deelvraag op te zoeken.

### Criteria:
- Eenvoudig:
  De resultaten moet eenvoudig te bemachtigen zijn.
- Snel:
  De resultaten moet binnen een half uur te vinden zijn.
- Betrouwbaar:
  De resultaten die verkregen zijn moeten correct zijn.

## onderzoek voor deelvraag 1.2

### Literatuur onderzoek
waarom:
het antwoord op deze deelvraag is al uitgebreid onderzocht en vastgelegd door anderen.

#### Betrouwbaarheid
consistent en reproduceerbaar:
Het literatuur onderzoek is gebaseerd op bestaande gedocumenteerde informatie van wifi-standaarden.
#### Validiteit
de validiteit ligt hoog omdat de bestaande kennis van dit onderzoek, standaarden en hun invloed  op datadoorvoer precies is wat ik wil meten.
### Middelen
- computer
- artikelen over wifi prestaties

### Criteria
- throughput:
  Hoeveel data er per seconden kan worden verzonden met de verschillende wifi-standaarden.
- bereik:
  Hoe groot is het effectieve bereik van de verbinding.
- Interferentie gevoeligheid:
  Hoe gevoelig is de standaard voor storingen.

## onderzoek voor deelvraag 1.3
### Literatuur onderzoek
Waarom:
De standaarden van 4G in termen van datadoorvoer, latency en betrouwbaarheid zijn al onderzocht en gepubliceerd in wetenschappelijke bronnen. Dit maakt literatuuronderzoek de meest geschikte methode.
#### Betrouwbaarheid
Consistent en reproduceerbaar:
Door meerdere betrouwbare bronnen te gebruiken kan het onderzoek consistent worden herhaald.
#### Validiteit
De methode sluit goed aan bij de vraag, omdat literatuuronderzoek inzicht geeft in de prestaties van 4G bij throughput.
### Middelen
- Computer of laptop
- Internettoegang tot  bronnen
- Artikelen over 4G-prestaties.
### Criteria
- Throughput:
  Maximale en gemiddelde snelheid van 4G in Mbps.

- Bereik:
  Dekking en prestaties over grotere afstanden.

- Latency:
  Vertraging in de communicatie tussen robots.

- Betrouwbaarheid:
  Stabiliteit van de verbinding bij beweging of obstakels.

## onderzoek voor deelvraag 1.4
### Literatuur onderzoek
waarom:
De standaarden van 5G in termen van datadoorvoer, latency en betrouwbaarheid zijn al onderzocht en gepubliceerd in wetenschappelijke bronnen. Dit maakt literatuuronderzoek de meest geschikte methode.

#### Betrouwbaarheid
Consistent en reproduceerbaar:
Door meerdere betrouwbare bronnen te gebruiken kan het onderzoek consistent worden herhaald.
#### Validiteit
De methode sluit goed aan bij de vraag, omdat literatuuronderzoek inzicht geeft in de prestaties van 5G bij throughput.
### Middelen
- Computer of laptop.
- Internettoegang tot bronnen.
- Artikelen over 5G-prestaties.
### Criteria
- **Throughput:**
  Maximale en gemiddelde datasnelheid van 5G.

- **Latency:**
  Vertraging tussen zenden en ontvangen van data.

- **Bereik:**
  Prestaties over korte en langere afstanden.

- **Betrouwbaarheid:**
  Stabiliteit van verbindingen bij hoge snelheid en mobiliteit.

## onderzoek voor deelvraag 1.5
### Multicriteria analyse
waarom: met de resultaten van onderzoekdeelvragen 1.2 t/m 1.4 kunnen de infrastructuren tegen elkaar worden vergeleken.
#### Betrouwbaarheid
De vergelijking is reproduceerbaar omdat de analyse gebaseerd is op dezelfde, vastgestelde meetcriteria uit de eerdere deelvragen (1.2 t/m 1.4).
#### Validiteit
De methode meet precies wat relevant is voor de hoofdvraag, de vergelijking van datadoorvoer van de verschillende infrastructuren.
### Middelen
- Resultaten en data uit deelvragen 1.2 t/m 1.4

- Tabellen en overzichtsrapporten over prestaties van WiFi, 4G en 5G

- Computer/laptop voor analyse en vergelijking
### Criteria
- Throughput:
  Gemiddelde en maximale snelheid per infrastructuur.

- Latency:
  Reactietijd van dataoverdracht.

- Betrouwbaarheid:
  Stabiliteit van de verbinding onder verschillende omstandigheden.

- Bereik:
  Invloed van afstand op prestaties.

##Onderzoek voor deelvraag 1.6

Hoe verhoudt de gemeten datadoorvoer van een WiFi 4-verbinding tussen twee ESP32's zich tot de theoretische datadoorvoer van WiFi 4?

### Prototype light

###Waarom:
De datadoorvoer van een WiFi-verbinding kan duidelijk worden gemeten door twee ESP32's met elkaar te laten communiceren. Met een C++-programma wordt data verstuurd en de benodigde tijd gemeten. Hierdoor kunnen we de praktische datadoorvoer vergelijken met de theoretische datadoorvoer van WiFi 4.

###Betrouwbaarheid

- Meetbaarheid: Hoog, omdat de hoeveelheid ontvangen data en de benodigde tijd exact gemeten kunnen worden.
    
- Reproduceerbaarheid: Hoog, als dezelfde ESP32's, WiFi-router en testopstelling worden gebruikt. Door meerdere metingen uit te voeren, kunnen we een gemiddelde berekenen.
    

### Validiteit

Ja, omdat we de daadwerkelijke datadoorvoer meten van een WiFi 4-verbinding tussen twee ESP32's. Dit sluit aan bij de deelvraag, omdat we de praktische snelheid vergelijken met de theoretische snelheid.

### Middelen

*   Twee ESP32's (DOIT ESP32 DevKit V1 en Adafruit ESP32 Feather V2).
    
*   C++-programma voor het versturen en ontvangen van data.
    
*   Computer met Arduino IDE voor het programmeren van de ESP32's en uitlezen van serial monitor.
    
*   WiFi-router voor de verbinding tussen de ESP32's.
    .
    

### Criteria

*   **Throughput:** De hoeveelheid data die per seconde wordt ontvangen, gemeten in Mbps.
    
*   **Tijd:** Hoe lang het duurt om een bepaalde hoeveelheid data volledig te ontvangen.
    
*   **Consistentie:** Dezelfde test meerdere keren uitvoeren om een gemiddelde datadoorvoer te berekenen.
    
*   **Vergelijkbaarheid:** De gemeten datadoorvoer vergelijken met de theoretische datadoorvoer van WiFi 4.


## Globale planning:
Hieronder staat de planning die gebruikt is tijdens het onderzoek vorig jaat:

| Dag           | Activiteit                                                              |
| ------------- | ----------------------------------------------------------------------- |
| Maandag w12   | Literatuur verzamelen over WiFi-, 4G- en 5G-standaarden (deelvraag 1.1) |
| Dinsdag w12   | Onderzoeken van WiFi-standaarden en datadoorvoer (deelvraag 1.2)        |
| Woensdag w12  | Onderzoeken van 4G-standaarden en datadoorvoer (deelvraag 1.3)          |
| Donderdag w12 | Onderzoeken van 5G-standaarden en datadoorvoer (deelvraag 1.4)          |
| Vrijdag w12   | Multicriteria-analyse van de infrastructuren (deelvraag 1.5)            |
| Zondag w12    | Resultaten samenvoegen, conclusies formuleren en hoofdstuk afronden     |
| week 13       | hoofdvraag 2                                                            |
| week 14       | hoofdvraag 3                                                            |

#Verantwoording hergebruik

Deze tekst komt uit mijn onderzoeksproject van vorig jaar te vinden op: https://dev.azure.com/AvansHogeschoolAcademies/ATIxTI-2526-B2.1-OnderzoeksProject/_wiki/wikis/ATIxTI-2526-B2.1-OnderzoeksProject.wiki/19/Projectduo's