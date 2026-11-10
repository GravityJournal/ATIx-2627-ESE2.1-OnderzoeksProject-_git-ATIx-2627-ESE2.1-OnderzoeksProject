# Welke meetmethode en prestatie-indactoren zijn geschikt om de betrouwbaarheid van de commincatie te beoordelen?

##1. Inleiding
------------
Binnen onze robotvloot is betrouwbare communicatie tussen de centrale controlunit (CCU) en de robots belangrijk. De CCU ontvangt gegevens zoals de locatie en status van de robots en gebruikt deze informatie voor de centrale routeplanning en taakverdeling.

Om te kunnen onderzoeken welke invloed de fysieke locatie van de CCU heeft op de communicatiebetrouwbaarheid, moeten we eerst bepalen hoe deze betrouwbaarheid gemeten kan worden.

Hiervoor onderzoeken we bestaande wetenschappelijke onderzoeken waarin de communicatieprestaties van landbouwrobots en andere autonome mobiele systemen worden gemeten.
Daarnaast onderzoeken we welke meetmethode het beste aansluit op de communicatiearchitectuur van onze robotvloot

##2. Literatuuronderzoek
----------------------
### 2.1 Wat is een betrouwbare communicatie.
Om de betrouwbaarheid van de communicatie tussen de centrale controlunit (CCU) en de robots te kunnen beoordelen, moet eerst worden vastgesteld wat betrouwbare communicatie inhoudt.

Volgens de internationale standaard [8]ITU-T Y.1540 (2019) kunnen de prestaties van communicatie binnen IP-netwerken worden beoordeeld aan de hand van vier eigenschappen:
- **Snelheid**: Hoe snel gegevens van de verzender naar de ontvanger worden overgedragen.
- **Nauwkeurigheid:** hoe corrent de gegevns worden overgedragen (zonder fouten).
- **Betrouwbaarheid:** de mate waarin de gegevensoverdracht corrent en volgens verwachting verloopt.
- **Beschikbaarheid:** de mate waarin de communicatiedienst beschikbaar is om gegevens uit te wisselen

deze eigenschappen vormen volgens [8]ITU-T Y.1540 (2019) een basis voor het veoordelen van prestaties van IP-communicatie

#### Relevantie tot de gekozen netwerk-architectuur
Binnen het systeem communiceren een rooier en twee overslagwagens via een centrale control unite. De CCU ontvangt informatie van de robots en gebruikt voor deze voor onder andre de routeplanning en taakverdeling.

voor deze toepassing is het be;angrijk dat informatie tijdig en correct wordt ontvangen en dat de communicatie voldoende beschikbaar blijft.

Wanneer berichten vertraagd aankomen gaat de CCU beslissingen nemen op verouderde informatie. wanneer berichten verloren gaan of de communicatie is tijdelijk niet beschikbaar, kan dit gevolgen hebben en leiden tot vertraging in het gehele oogst process.

op basis van  [8]ITU-T Y.1540 (2019) kan communicatie betrouwbaarheid voor de robotvloot worden beschowud als de mate waarin gegevens tijdig, correct en met volgoende continuiteit tussen de CCU en de robots kunnen worden uitgewisseld.

Om deze eigenschappen objectief te beoordelen, moet worden onderzocht welke meetpare indicatoren hiervoor geschikt zijn en wat de communicatie mogelijk kan beinvloeden.

### 2.2 Welke factoren beinvloeden de kwaliteit van de communicatie
De kwaliteit van een draadlooze connectie wordt beinvloed door verschillende factoren. Om te onderzoeken welke invloed de fysieke locatie van de CCU heeft op de communicatie betrouwbaarheid, is het belangrijk om te weten welke factoren de communicatie prestatie kan beinvloeden.


### 2.3 Welke meet-methode/indicatoren worden in bestaande onderzoeken en standaarden gebruikt


##3. Relevante meetmethoden voor communicatie betrouwbaarheid

##4. meetmethode selectie 

##5. Conclusie