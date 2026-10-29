# Hoofdvraag
Wat is het meest efficiënte ontwerp van een afhandelingsmechanisme met gebruik van dynamische time-outs en herallocatie van taken voor het verminderen van overdrachtspunt blokkades?

# Deelvraag 1
Welke invloed heeft het instellen van een dynamische time-out ten opzichte van een statische time-out op de gemiddelde blokkade-tijd van het overdrachtspunt in C++ wanneer een robot vertraging oploopt?

# Deelvraag 2
Hoe reageert de C++ vlootsimulatie op het wegvallen van een toegewezen robot, en welk effect heeft een automatische herallocatieregel op de totale doorvoer van de zone-overdracht?

*** 
# Onderzoeks- en analysemethoden

## deelvraag 1:
**Simulatie:** 
hierin worden de twee time-out methodes vergeleken met elkaar:
- Scenario 1: statische time-out (vaste timeoutwaarde).
- Scenario 2: dynamische time-out (afhankelijk van verwachte reistijd en verkeersdrukte).

In beide scenario's worden identieke vertragingen geïntroduceerd bij robots die naar het overdrachtspunt rijden.
Voor beide scenario's worden meerdere simulatieruns uitgevoerd. Vervolgens worden de volgende waarden berekend:

- Gemiddelde blokkade-tijd van het overdrachtspunt.
- Aantal onnodig afgebroken taken.
- Aantal succesvolle overdrachten.

De resultaten worden vergeleken met behulp van gemiddelden en procentuele verschillen.
Het literatuuronderzoek laat zien dat dynamische time-outs onnodige taakannuleringen kunnen voorkomen. Door uitsluitend de timeoutstrategie te wijzigen en alle andere factoren gelijk te houden, kan het effect van de dynamische time-out direct worden gemeten.


## deelvraag 2:
 
**Simulatie:** 
Hierin wordt gekeken naar de werking van het systeem wanneer robots uitvallen:
- Scenario 1: bij uitval vindt geen herallocatie plaats.
- Scenario 2: bij uitval vindt automatische taakherallocatie naar een alternatieve robot plaats.

De uitval vindt op vooraf vastgestelde momenten plaats zodat de situaties vergelijkbaar blijven.
Per scenario worden de volgende gegevens verzameld:
- Totale doorvoer (aantal succesvol afgehandelde overdrachten).
- Gemiddelde wachttijd van vracht.
- Aantal mislukte taken.
- Hersteltijd na de uitval.


De verschillen tussen beide scenario's worden kwantitatief vergeleken.
De literatuur beschrijft herallocatie als een methode om verstoringen op te vangen. Door een robot bewust te laten uitvallen kan worden vastgesteld of herallocatie daadwerkelijk leidt tot een hogere doorvoer en minder verstoring van het systeem.

***

# Benodigde middelen

## Software

- C++ ontwikkelomgeving.
- Eigen vlootsimulatie.
- Git voor versiebeheer.
- Spreadsheetsoftware voor analyse van meetresultaten.

## Hardware

- Ontwikkelcomputer.
- Testomgeving voor het uitvoeren van simulaties.

## Data

- Simulatielogs.
  - Tijdmetingen van blokkades.
  - Doorvoercijfers.
  - 
- Timeout- en herallocatieparameters.

*** 
# analysecriteria


*** 
# globale planning



# Doelstelling onderzoek
Het ontwerpen en testen van een C++ afhandelingsmechanisme met dynamische time-outs en herallocatie om te voorkomen dat een overdrachtspunt geblokkeerd blijft wanneer een robot vertraagd is of faalt.

# Scope
 - C++ console-simulatie die het logistieke proces bij een overdrachtspunt en de wachtrij van opdrachten simuleert.
 - Focus op de logica rondom time-outs, taakannulering en het toewijzen van een vervangende robot.
 - Buiten scope: Echte navigatie, fysieke obstakeldetectie en sensoren.

# Onderzoeksopzet
Een C++ programma simuleert de aankomst van robots uit Zone A en Zone B bij een overdrachtspunt. Via code worden kunstmatige vertragingen en uitval van robots gesimuleerd. We vergelijken twee algoritmen in C++: (1) een statische time-out (vast X seconden wachten) en (2) een dynamische time-out met automatische taakherallocatie naar een andere robot of tijdelijke buffer. Gemeten wordt hoeveel seconden het overdrachtspunt onnodig geblokkeerd blijft en hoeveel opdrachten per minuut verwerkt kunnen worden.

