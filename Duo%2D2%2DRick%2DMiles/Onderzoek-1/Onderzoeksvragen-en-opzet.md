# Hoofdvraag
Wat is het meest efficiënte ontwerp van een afhandelingsmechanisme met gebruik van dynamische time-outs en herallocatie van taken voor het verminderen van overdrachtspunt blokkades?

# Doelstelling onderzoek
Het ontwerpen en testen van een C++ afhandelingsmechanisme met dynamische time-outs en herallocatie om te voorkomen dat een overdrachtspunt geblokkeerd blijft wanneer een robot vertraagd is of faalt.

# Scope
 - C++ console-simulatie die het logistieke proces bij een overdrachtspunt en de wachtrij van opdrachten simuleert.
 - Focus op de logica rondom time-outs, taakannulering en het toewijzen van een vervangende robot.
 - Buiten scope: Echte navigatie, fysieke obstakeldetectie en sensoren.

# Onderzoeksopzet
Een C++ programma simuleert de aankomst van robots uit Zone A en Zone B bij een overdrachtspunt. Via code worden kunstmatige vertragingen en uitval van robots gesimuleerd. We vergelijken twee algoritmen in C++: (1) een statische time-out (vast X seconden wachten) en (2) een dynamische time-out met automatische taakherallocatie naar een andere robot of tijdelijke buffer. Gemeten wordt hoeveel seconden het overdrachtspunt onnodig geblokkeerd blijft en hoeveel opdrachten per minuut verwerkt kunnen worden.

# Deelvraag 1
Welke invloed heeft het instellen van een dynamische time-out ten opzichte van een statische time-out op de gemiddelde blokkade-tijd van het overdrachtspunt in C++ wanneer een robot vertraging oploopt?

# Deelvraag 2
Hoe reageert de C++ vlootsimulatie op het wegvallen van een toegewezen robot, en welk effect heeft een automatische herallocatieregel op de totale doorvoer van de zone-overdracht?