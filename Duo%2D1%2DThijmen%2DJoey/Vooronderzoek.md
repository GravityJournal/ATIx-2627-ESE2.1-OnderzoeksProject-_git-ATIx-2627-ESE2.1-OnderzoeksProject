# Infrastructuuronderzoek – Casusanalyse

## 1. Beschrijving van de casus

Het doel van het project is om bodemverdichting op landbouwakkers te verminderen door middel van robotisering. Hiervoor wordt een autonome robotvloot ontwikkeld die het oogstproces zo efficiënt mogelijk moet uitvoeren.

De robotvloot bestaat uit drie voertuigen:

* **Eén rooier:** oogst de gewassen en rijdt hiervoor heen en weer over de akker. Aan het einde van iedere rij keert de rooier op de kopakker.
* **Twee overslagwagens:** vervoeren de geoogste gewassen van de rooier naar het lospunt en rijden vervolgens terug naar de rooier.

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
