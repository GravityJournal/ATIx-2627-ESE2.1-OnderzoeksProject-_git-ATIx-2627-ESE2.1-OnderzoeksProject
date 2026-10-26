# Wat moet er worden verstuurd?

Voor deze samenwerking moet duidelijk zijn welke gegevens de systemen onderling uitwisselen. Dit onderdeel beschrijft de inhoud van de berichten die nodig zijn voor de communicatie tussen de robots, de centrale controller en de operatorinterfaces.
Het doel van dit onderdeel is om te bepalen welke gegevens moeten worden verstuurd om aan de eisen van het project te voldoen.

## Communicatielijnen

### Cyclusberichtlijn

Deze berichtlijn beschrijft de cyclus van het ophalen en afladen van gewassen door de rooier en de overslagwagens.

| Bericht | Verstuurder | Ontvanger | Benodigde gegevens |
| --- | --- | --- | --- |
| Overslagwagen oproepen | Rooier | Overslagwagen | ID, taakstatus rooier |
| Rooier aanroepen | Overslagwagen | Rooier | ID, taakstatus overslagwagen |
| Rooier afmelden | Overslagwagen | Rooier | ID, taakstatus overslagwagen |
| Overslagwagen afmelden | Rooier | Overslagwagen | ID, taakstatus rooier |
| Lospunt bereikt melden | Overslagwagen | Centrale controller | ID, taakstatus overslagwagen |

*Verstuurder = het systeem dat het bericht verstuurt.  
*Ontvanger = het systeem dat het bericht ontvangt.
Het vullingspercentage is niet opgenomen, omdat de logica voor het bepalen van de benodigde acties intern wordt afgehandeld.

### Besturingsberichtlijn

Deze berichtlijn beschrijft de communicatie voor het versnellen, vertragen en besturen van de overslagwagens.
| Bericht | Verstuurder | Ontvanger | Benodigde gegevens |
| --- | --- | --- | --- |
| Snelheid wijzigen | Rooieroperatorinterface | Overslagwagen | ID, lineaire snelheid |
| Snelheid wijzigen | Randoperatorinterface | Overslagwagen | ID, lineaire snelheid, angulaire snelheid |
| Besturing wijzigen | Operatorinterface | Overslagwagen | ID, besturingsstatus |

*Verstuurder = het systeem dat het bericht verstuurt.  
*Ontvanger = het systeem dat het bericht ontvangt.

### Interfaceberichtlijn

Deze berichtlijn beschrijft de communicatie waarmee de operatorinterface informatie over de voertuigen ontvangt.
De casus vereist dat de status van de robots inzichtelijk is, maar specificeert niet welke informatie precies moet worden weergegeven. Daarom zijn op basis van de beschikbare informatie enkele aannames gedaan over de benodigde berichten.
| Bericht | Verstuurder | Ontvanger | Benodigde gegevens |
| --- | --- | --- | --- |
| Machinestatus melden | Rooier | Operatorinterface | ID, taak, besturingsstatus, lineaire snelheid, angulaire snelheid, locatie |
| Machinestatus melden | Overslagwagen | Operatorinterface | ID, taak, besturingsstatus, lineaire snelheid, angulaire snelheid, locatie |
| Waarschuwing melden | Robot | Operatorinterface | ID, waarschuwing, ernst |

*Verstuurder = het systeem dat het bericht verstuurt.  
*Ontvanger = het systeem dat het bericht ontvangt.
Daarnaast zijn er enkele mogelijke berichten die de functionaliteit van de operatorinterface kunnen uitbreiden.

| Bericht | Verstuurder | Ontvanger | Benodigde gegevens |
| --- | --- | --- | --- |
| Perceelstatus melden | Centrale controller | Operatorinterface | Voltooiingsstatus |
| Communicatiestatus melden | Robot | Operatorinterface | ID, verbindingsstatus, tijdstip van laatste update |
| Taakstatus melden | Robot | Operatorinterface | ID, huidige status, taakvoortgang |

*Verstuurder = het systeem dat het bericht verstuurt.  
*Ontvanger = het systeem dat het bericht ontvangt.

## Conclusie

Op basis van de casus zijn twee mogelijke voorstellen opgesteld voor de gegevensstructuur. Deze voorstellen beschrijven welke variabelen nodig kunnen zijn om de berichten tussen de systemen uit te wisselen.

### Voorstel 1: Gecombineerde gegevensstructuur

| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Rooier-ID | GUID | - |
| Overslagwagen-ID | GUID | - |
| Taak | ENUM | - |
| Besturingsstatus | BOOL | - |
| Lineaire snelheid | FLOAT | Meter per seconde (m/s) |
| Angulaire snelheid | FLOAT | Radiaal per seconde (rad/s) |
| Locatie | STRUCT | X-positie (FLOAT), Y-positie (FLOAT), oriëntatie (FLOAT) |
| Waarschuwing | ENUM | - |
| Ernst | ENUM | - |


### Voorstel 2: Gescheiden gegevensstructuren per berichttype

In dit voorstel krijgt elk berichttype een eigen gegevensstructuur. Hierdoor bevat elk bericht alleen de gegevens die nodig zijn voor de betreffende functie. Dit voorkomt dat bij ieder bericht onnodige gegevens worden meegestuurd en maakt de berichtstructuren specifieker.

<br>

**Structuur A: Taakbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Rooier-ID | GUID | - |
| Overslagwagen-ID | GUID | - |
| Taak | ENUM | - |

<br>

**Structuur B: Besturingsbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Overslagwagen-ID | GUID | - |
| Lineaire snelheid | FLOAT | Meter per seconde (m/s) |
| Angulaire snelheid | FLOAT | Radialen per seconde (rad/s) |
| Besturingsstatus | BOOL | - |

<br>

**Structuur C: Locatie bericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Overslagwagen-ID | GUID | - |
| Locatie | STRUCT | X-positie (FLOAT), Y-positie (FLOAT), oriëntatie (FLOAT) |

<br>

**Structuur D: Waarschuwingsbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Robot-ID | GUID | - |
| Waarschuwing | ENUM | - |
| Ernst | ENUM | - |

<br>

**Structuur E: Statusbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Robot-ID | GUID | - |
| Taak | ENUM | - |
| Besturingsstatus | BOOL | - |
| Lineaire snelheid | FLOAT | Meter per seconde (m/s) |
| Angulaire snelheid | FLOAT | Radialen per seconde (rad/s) |
| Locatie | STRUCT | X-positie (FLOAT), Y-positie (FLOAT), oriëntatie (FLOAT) |

<br>

**Structuur F: Communicatiestatusbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Robot-ID | GUID | - |
| Verbindingsstatus | ENUM | - |
| Tijdstip van laatste update | TIMESTAMP | - |

<br>

**Structuur G: Perceelstatusbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Voltooiingsstatus | FLOAT | Percentage (%) |

<br>

**Structuur H: Taakvoortgangsbericht**
| Variabele | Datatype | Eenheid of structuur |
| --- | --- | --- |
| Robot-ID | GUID | - |
| Huidige status | ENUM | - |
| Taakvoortgang | FLOAT | Percentage (%) |