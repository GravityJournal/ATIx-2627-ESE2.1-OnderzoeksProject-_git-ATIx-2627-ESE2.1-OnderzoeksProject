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
voor het bepalen wat het meest geschikte communicatie en besturings-architectuur voor onze robotvloot zijn twee wetenschappelijke onderzoeken bekeken. hierin worden de verschillen tussen gecentraliseerde, gedecentraliseerde en hybride systemen besproken.


**Onderzoek 1: Gecentraliseerde en gedecentraliseerde communicatie**
In het onderzoek van Katikaridis et al. (2025) worden twee verschillende communicatiearchitecturen voor landbouwrobots met elkaar vergeleken: een gecentraliseerd en een gedecentraliseerd systeem.

Bij een gedecentraliseerd systeem communiceren robots rechtstreeks met elkaar, zonder tussenkomst van een centrale controlunit. Bij een gecentraliseerd systeem verloopt de communicatie via een centraal systeem.

De onderzoekers hebben 120 praktijktesten uitgevoerd met een drone en een kleine autonome landbouwrobot. Hierbij werd gekeken naar de betrouwbaarheid en snelheid van de communicatie in een open veld en een boomgaard.

**Resultaten:**
uit het onderzoek bleek dat het gecentraliseerde systeem betrouwbaarder was in het afleveren van berichten. Dit systeem behaalde een succespercentage van maar liefst 97%. het gedecentraliseerde systeem behaalde 83% in het open veld en 70% in de boomgaard.

Het gedecentraliseerde systeem had bij het terugsturen van positiegegevens wel een lagere communicatie vertraging, daarin tegen ontstond er bij hun setup veel packet-loss en latency.

**Toepasbaarheid**
Dit onderzoek laat zien dat de gekozen communicatiearchitectuur invloed kan hebben op de betrouwbaarheid en vertraging van de communicatie.

voor onze robotvloot is betrouwbare communicatie belangrijk, omdat de rooier en overslagwagens voortdurend informatie moeten uitwissel over hun locatie,status en werkzaamheden.

Hoewel het onderzoek interessante resultaten oplevert, sluit de testopstelling niet volledig aan op onze casus. In het onderzoek werd gebruikgemaakt van een drone en een relatief kleine landbouwrobot. Onze robotvloot bestaat daarentegen uit een grote rooier en twee overslagwagens.
Door het verschil in afmetingen kunnen de antennes van onze landbouwmachines mogelijk hoger worden geplaatst, waardoor gewassen het radiosignaal minder snel blokkeren. Dit kan invloed hebben op de betrouwbaarheid van de communicatie.

De resultaten zijn daarom niet rechtstreeks toepasbaar op onze situatie, Daarom hebben we nog even verder gezocht!

**Onderzoek 2: Besturingsarchitecturen voor landbouwmachines**
In het onderzoek van Xia et al. (2026) worden drie verschillende besturingsarchitecturen voor landbouwmachines besproken: gecentraliseerd, gedecentraliseerd en hybride.

De onderzoekers vergelijken de eigenschappen en toepassingsmogelijkheden van de architectuur

**Resultaten:**
Volgens Xia et al. (2026) zijn gecentraliseerde architecturen vooral geschikt voor kleinere robotvloten met stabiele communicatieverbindingen.

**Gecentraliseerd**
Bij een gecentraliseerd systeem worden de taakverdeling  en globale routeplanning vanuit een centrale controller geregeld en gecommuniceerd. hierdoor beschikt het systeem een gezamelijk overzicht van de werkzaamheden en routes van de voertuigen.

Een nadeel is dat het systeem dan echt afhankelijk is van de centrale controller, wanneer deze uitvalt kan dat gevolgen hebben voor de gehele robotvloot. Zonder betrouwbare communcicatie en verbindingen zou een gecentraliseerde architectuur geen voordelen meer hebben.

**Gedecentraliseerd**
bij een gedecentraliseerd systeem nemen de robots zelfstandig beslissingen en stemmen ze hun werkzaamheden onderling af. hierdoor zijn ze minder afhankelijk van een centraal systeem, maar is het wel lastiger om de werkzaamheden van de gehele robotvloot te optimaliseren en af te stemmen.

Een hybride architectuur combineert centrale coördinatie met lokale zelfstandigheid van de voertuigen.

**Toepasbaarheid**
Uit dit onderzoek blijkt dat de ophang van de robotvloot en de behoefte aan een gezamelijke planning belangrijke factoren zijn bij het kiezen van de besturingsarchitectuur.

Onze robotbloot bestaat uit slechts drie voertuigen. hierdoor verwachten wij dat de beperking van een gecentraliseerd systeem op het gebied van schaalbaarheid minimale invloed zou hebben.

Daarnaast is gazemelijke routeplanning en afstemming belangerijk om onnodige bodemverdichting te vermijden. Met een centrale controller kunnen de posities en routes gezamelijk bijgehouden worden, waardoor je de routeplanning makkelijker en effecienter kan afstemmen. 

Dit onderzoek geeft ons daarom een belangrijke onderbouwing voor de keuze van een gecentraliseerde architectuur.























**Bronvermelding (APA 7)**
Katikaridis, D., Benos, L., Busato, P., Kateris, D., Papageorgiou, E., Karras, G., & Bochtis, D. (2025). Experimental comparative analysis of centralized vs. decentralized coordination of aerial–ground robotic teams for agricultural operations. _Robotics, 14_(9), Article 119. [https://doi.org/10.3390/robotics14090119](https://doi.org/10.3390/robotics14090119)



**Welke informatie moeten de robots uitwisselen?**
Denk hierbij aan locatiegegevens, snelheid, rijrichting, bunkerinhoud, geplande routes, taak informatie en de status van de voertuigen.

**Hoe vaak moet deze informatie worden uitgewisseld?**

Is het bijvoorbeeld noodzakelijk dat een robot iedere 100 milliseconden zijn locatie doorstuurt, of is een lagere updatefrequentie voldoende?

**Welke beslissingen nemen de robots zelfstandig?**

Moet een robot bij het detecteren van een obstakel wachten op instructies van de centrale controller, of kan deze zelfstandig reageren?

### 3. Analyse van de netwerkinfrastructuur

Naast de communicatiebehoeften moet worden onderzocht welke technische eisen nodig zijn voor het netwerk. Hiervoor zijn meerdere technologieen beschrikbaar en mogelijk zoals: Wifi, LoRa, 4G, 4G of bluetooth. Enkele van deze kunnen we al afstrepen bijvoorbeeld wifi heeft een ideale range van 50 meter (Bron 1). Wifi heeft de mogelijkheid voor grotere range doormiddel van gebruik van directional antennas, maar dat extra werk en hardware als er al een bestaand 4G/5G netwerk bestaad. Bluetooth kunnen we ook al afstrepen voor gelijke redenen en heeft maar een range van 10 meter (Bron 2). Voor de afstanden gaan we vanuit dat het alleen toegepast word in nederland met een maximale akker groote van 7.62 hectare (Bron 3) per perceel wat een akker groote geeft van 300 x 254 meter. Dus dit geeft ons de mogelijkheden tussen LoRa, 4G en 5G. Om erachter te komen welke technologie voor ons het best geschrikt is stellen we de volgende vragen per techniek:
*   Hoeveel data bits/s kunnen sturen tussen de robots
    *   Hoeveel data gaan we versturen
    *   Welke data gaan we versturen
*   Hoeveel vertraging in ms vind er plaats tussen sturen en ontvangen?
    *   Hoeveel en welke impact heeft vertraging
    *   Wat is maximale vetraging die we kunnen hebben
*   Hoeveel dekking is er in nederland voor 4g en 5g? (bron 4) 

    ![chrome_EQQPt3lWTo.png](/.attachments/chrome_EQQPt3lWTo-ffa0f293-8b8c-4502-a907-01968328959c.png)

### Bronnen:
* Bron 1: [https://en.wikipedia.org/wiki/Long-range_Wi-Fi](https://en.wikipedia.org/wiki/Long-range_Wi-Fi)  
"Wi-Fi networks have a range that's limited by the frequency, transmission power, antenna type, the location they're used in, and the environment.[1] A typical wireless router in an indoor point-to-multipoint arrangement using 802.11n and a stock antenna might have a range of 50 metres (160 ft) or less"
* Bron 2: [https://en.wikipedia.org/wiki/Bluetooth](https://en.wikipedia.org/wiki/Bluetooth)  
"In the most widely used mode, transmission power is limited to 2.5 milliwatts, giving it a very short range of up to 10 metres"
* Bron 3: [https://www.cbs.nl/nl-nl/maatwerk/2022/08/gemiddelde-oppervlakte-percelen-akkerbouwgewassen-2017-2021](https://www.cbs.nl/nl-nl/maatwerk/2022/08/gemiddelde-oppervlakte-percelen-akkerbouwgewassen-2017-2021)
* Bron 4: [https://www.kpn.com/netwerk/dekkingskaart](https://www.kpn.com/netwerk/dekkingskaart)

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
