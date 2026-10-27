# Infrastructuuronderzoek – Casusanalyse

## 1. Beschrijving van de casus

Het doel van het project is om bodemverdichting op landbouwakkers te verminderen door middel van robotisering. Hiervoor wordt een autonome robotvloot ontwikkeld die het oogstproces zo efficiënt mogelijk moet uitvoeren.

### De robotvloot bestaat uit twee verschillende voertuigen en in totaal drie voertuigen:
* **Eén rooier:** oogst de gewassen en rijdt hiervoor heen en weer over de akker. Aan het einde van iedere rij keert de rooier op de kopakker.
* **Twee overslagwagens:** vervoeren de geoogste gewassen van de rooier naar het lospunt en rijden vervolgens terug naar de rooier.

### Ook maakt de robot vloot gebruik van twee operators:
* **Rooier operator:** bepaalt de snelheid van de overslagwagen en rooier tijdens de momenten dat ze naast elkaar rijden. De operator keert ook de rooier op keerpunten van de akker.
* **Overslagwagen operator:** De operator krijgt controle over de overslagwagen tijdens het ontladen van aardappels. Hiervoor kan hij de snelheid en richting van de wagen aanpassen.


Om bodemverdichting te beperken, moeten de overslagwagens zo efficiënt mogelijk over de akker rijden. Hierbij is het belangrijk dat ze niet meerdere keren over dezelfde plekken rijden, met uitzondering van de kopakker.

Om dit mogelijk te maken, moeten de robots onderling informatie kunnen uitwisselen en hun bewegingen op elkaar afstemmen. Hiervoor is een betrouwbare netwerkinfrastructuur nodig.

Binnen dit onderzoek wordt gekeken naar de communicatiebehoeften van de robotvloot en welke eisen dit stelt aan de netwerkinfrastructuur.

## 2. Analyse van de communicatiebehoeften

Om te bepalen welke infrastructuur geschikt is voor de robotvloot, moet eerst duidelijk worden hoe de robots met elkaar communiceren en welke informatie ze nodig hebben.

### 2.1 Communicatie tussen robots

**Hoe communiceren de robots met elkaar?**

Communiceren de robots rechtstreeks met elkaar of verloopt alle communicatie via een centrale controller?
Kan de centrale control unit op de rooier?:
voordelen:
- Je hebt geen aparte server nodig. Niks extras te verplaatsen?
- Communicatie met rooier heeft weinig latency.
- geen aparte computer installatie op het veld. zit namelijk op de rooier zelf
Nadeel:
- Rooier beweegt. onvoorspelbaar latency?.
- De rooier 

### Gecentraliseerde en gedecentraliseerde communicatie

In het onderzoek van Katikaridis et al. (2025) worden twee verschillende communicatiearchitecturen voor landbouwrobots met elkaar vergeleken: een gecentraliseerd en een gedecentraliseerd systeem. Bij een gedecentraliseerd systeem communiceren robots rechtstreeks met elkaar, terwijl bij een gecentraliseerd systeem de communicatie via een centrale controlunit verloopt.
De onderzoekers hebben 120 praktijktesten uitgevoerd met een drone en een kleine autonome landbouwrobot. Hierbij werd gekeken naar de betrouwbaarheid en snelheid van de communicatie in een open veld en een boomgaard.
**Resultaten**
Uit het onderzoek bleek dat het gecentraliseerde systeem betrouwbaarder was in het afleveren van berichten. Dit systeem behaalde in beide omgevingen een succespercentage van 97%. Het gedecentraliseerde systeem behaalde 83% in het open veld en 70% in de boomgaard.
Het gedecentraliseerde systeem had bij het terugsturen van positiegegevens wel een lagere communicatievertraging. De onderzoekers concludeerden dat beide systemen voordelen hebben, afhankelijk van de toepassing en de omgeving.
**Toepasbaarheid op onze robotvloot**
Hoewel dit onderzoek interessante resultaten oplevert, sluit de testopstelling niet volledig aan op onze casus. In het onderzoek werd gebruikgemaakt van een drone en een relatief kleine landbouwrobot. Onze robotvloot bestaat daarentegen uit een grote rooier en twee overslagwagens.
Door het verschil in afmetingen kunnen de antennes van onze landbouwmachines mogelijk hoger worden geplaatst, waardoor gewassen het radiosignaal minder snel blokkeren. Dit kan invloed hebben op de betrouwbaarheid van de communicatie.
Daarnaast bestaat onze robotvloot uit drie grondvoertuigen, terwijl in het onderzoek de communicatie tussen een drone en een grondvoertuig werd getest.
De resultaten zijn daarom niet rechtstreeks toepasbaar op onze situatie. Wel laat het onderzoek zien dat de keuze voor een communicatiearchitectuur invloed kan hebben op de betrouwbaarheid en vertraging van de communicatie.

**Bronvermelding (APA 7)**
Katikaridis, D., Benos, L., Busato, P., Kateris, D., Papageorgiou, E., Karras, G., & Bochtis, D. (2025). Experimental comparative analysis of centralized vs. decentralized coordination of aerial–ground robotic teams for agricultural operations. _Robotics, 14_(9), Article 119. [https://doi.org/10.3390/robotics14090119](https://doi.org/10.3390/robotics14090119)



**Welke informatie moeten de robots uitwisselen?**

Denk hierbij aan locatiegegevens, snelheid, rijrichting, bunkerinhoud, geplande routes en de status van de voertuigen.

**Hoe vaak moet deze informatie worden uitgewisseld?**

Is het bijvoorbeeld noodzakelijk dat een robot iedere 100 milliseconden zijn locatie doorstuurt, of is een lagere updatefrequentie voldoende?

**Welke beslissingen nemen de robots zelfstandig?**

Moet een robot bij het detecteren van een obstakel wachten op instructies van de centrale controller, of kan deze zelfstandig reageren?

## 3. Analyse van de netwerkinfrastructuur

Naast de communicatiebehoeften moet worden onderzocht welke technische eisen aan het netwerk worden gesteld.

### 3.1 Netwerktechnologie

**Welke netwerktechnologie is geschikt voor de robotvloot?**

Kan de communicatie plaatsvinden via WiFi, 4G of 5G? En welke technologie sluit het beste aan bij de eisen van het project?

### 3.2 Netwerkbereik

**Hoe groot moet het bereik van het netwerk zijn?**

Moet de netwerkinfrastructuur het volledige landbouwperceel dekken, inclusief het lospunt, of is gedeeltelijke dekking voldoende?

### 3.3 Betrouwbaarheid

**Hoe betrouwbaar moet de netwerkverbinding zijn?**

Blijft de verbinding stabiel wanneer de robots over de akker bewegen? En wat gebeurt er wanneer een robot tijdelijk de verbinding verliest?

### 3.4 Netwerkcapaciteit

**Hoeveel netwerkcapaciteit heeft de robotvloot nodig?**

Hoeveel gegevens worden er tussen de robots en de controller uitgewisseld? Kan het netwerk deze gegevens gelijktijdig verwerken zonder dat er te veel vertraging ontstaat?
