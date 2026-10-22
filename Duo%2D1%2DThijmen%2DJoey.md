# Onderzoeksproject LU2
**Studenten:** Thijmen Roozendaal & Joey Staps 
**Opleiding:** Embedded Software Engineering L2
**Onderwijsinstelling:** Avans Hogeschool Breda

## Projectomschrijving 
Tijdens Leeruitkomst 2 voeren wij twee onderzoeken uit binnen het Robot Fleet-project. In deze Wiki documenteren wij onze onderzoeksvragen, onderzoeksopzetten, meetresultaten, analyses en conclusies.

## Potentiële hoofdvragen
**TCP vs UDP**
Verschil tussen roundtrip en pakket verlies tussen verschillend netwerk protocols tussen een draadloze connectie.
Waarom relevant:
ze moeten constant kunnen communiceren en vertraging kan het systeem laten achterlopen.

**Robot locatie voorspelling**
In hoever kan positie voorspelling de nauwkeurigheid van de robotpositie verbeter bij hoge latency.

# Probleem analyse
**Probleem context:**
Binnen het project Robot Fleet word onderzocht hoe meerdere landbouwrobots kunnen samenwerken om bodemverdichting te verminderen. De robotvloot bestaat uit een rooier en twee overslagwagens die samen het oogstprocess zouden uitvoeren.

Om deze samenwerking mogenlijk te maken moeten de robots informatie met elkaar kunnen uitwisselen. denk hierbij bij actuele locatie, snelheid, bunkerinhoud en beschikbaarheid/status.

In de casus is vastgesteld dat een centrale controlunit verantwoordelijk is voor de communicatie en aansturen van de overslagwagens. Het is echter nog niet duidelijk wat voor communicatie techniek hiervoor het meest geschikt is.

Wanneer de informatie vermist of te laat aankomt. Kan dit gevolgen hebben voor de gehele samenwerking tussen de robots. een overslagwagen kan bijvoorbeeld te laat bij de rooier aankomen, waardoor de rooier mogelijk zou moeten stoppen.

Daarom is het ook zo belangrijk om te onderzoeken hoe de communicatie tussen de robots en de centrale controller betrouwbaar en efficient kan plaatsvinden.

**Belang:**
Een betrouwbare communicatie tussen de robots en de centrale controller is belangrijk om het oogstprocces betrouwbaar en effecient te laten verlopen. Als de communcatie niet goed verloopt zou er vertraging en storingen in het gehele infrastructuur kunnen optreden.

Efficiëntie:
Een betrouwbare communcatie is van belang voor de efficiëntie, Wanneer een overslagwagen te laat wordt aangestuurd, moet de rooier mogelijk wachten voordat hij verder kan gaan met oogsten. zo onstaan er vertragingen in het gehele process die uiteindelijk op kunnen gaan stapelen.

Veiligheid:
Waneer locatiegevens te laat of vertraagd bij de controlunit aan komen is er kans op verouderde locatiedata. Dat zou betekenen dat de controlunit beslissingen gaat nemen met verouderde locatiedata dit kan uiteindelijk tot gevaarlijke situaties lijden.

Bodemverdichting:
Een betrouwbare communicatie is van belang bij het onderwerp bodemverdichting. Zonder betrouwbare communicatie zouden de robotwagens over dezelfde routes kunnen gaan rijden en dat zou onnodige bodemveridichting veroorzaken

**Literatuur onderzoek**



 


# Themas & vragen?
- Robot locatie
- robot communicatie
- Proces optimalisatie
  - Rij route robots
  - Bunker legen
  - 













