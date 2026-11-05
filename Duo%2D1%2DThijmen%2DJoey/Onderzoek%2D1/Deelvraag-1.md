
#Welke plaatsingsmogelijkheden voor een centrale controlunit (CCU) worden in bestaande onderzoeken toegepast en in hoeverre zijn deze geschikt voor onze robotvloot?**

## 1. Inleiding
Binnen ons robotvlootproject wordt gebruikgemaakt van een gecentraliseerde besturingsarchitectuur. De robotvloot bestaat uit één rooier en twee overslagwagens die samenwerken tijdens het oogstproces.

De centrale controlunit (CCU) is verantwoordelijk voor het ontvangen en verwerken van informatie van de robots. Op basis van deze gegevens kan de CCU beslissingen nemen over bijvoorbeeld de routeplanning en taakverdeling.

Een belangrijke vraag binnen deze architectuur is waar de CCU fysiek geplaatst moet worden.
Om te bepalen welke plaatsingsmogelijkheden relevant zijn voor onze robotvloot, onderzoeken we welke oplossingen in bestaande wetenschappelijke onderzoeken worden toegepast en welke overwegingen daarbij een rol spelen.

Hierbij kijken we specifiek naar centrale besturingssystemen voor landbouwrobots en andere autonome mobiele robots.

--------------------------
## 2. Literatuuronderzoek
Hieronder staan meerdere onderzoeken die potentiël relevant zijn voor onze uitwerking.

###2.1 Centrale besturing op een vaste locatie

**Onderzoek:** Intelligent Coordination of a Human-Robot Collaborative Fleet for Assistance in Manual Fruit Harvesting
**Onderzoek:** Fleets of Robots for Environmentally-Safe Pest Control in Agriculture

**Beschrijving:**

**Relevantie voor onze robotvloot**
Deze onderzoeken laat zien dat een vaste centrale besturingscomputer een toepasbare oplossing is voor het coördineren van meerdere landbouwrobots.
Voor onze robotvloot zou een vergelijkbare opstelling mogelijk zijn, waarbij de CCU zich op een vaste locatie buiten het landbouwperceel bevindt.
Een vaste locatie heeft als praktisch voordeel dat de CCU niet hoeft mee te bewegen met de landbouwmachines. Bovendien kan de apparatuur op een toegankelijke en beschermde locatie worden opgesteld.
Een aandachtspunt is dat de CCU afhankelijk blijft van de communicatieverbinding met de robots die zich over het perceel verplaatsen.
Het onderzoek toont echter niet aan dat een vaste locatie automatisch een betrouwbaardere communicatieverbinding oplevert dan een mobiele locatie.

**Bron:** González-de-Santos et al. (2017), _Precision Agriculture_.


### 2.2 Centrale besturing op een landbouwrobot
**Onderzoek: New Trends in Robotics for Agriculture: Integration and Assessment of a Real Fleet of Robots**
**Beschrijving:**



**Relevantie voor onze robotvloot**
Deze plaatsingsmogenlijkheid sluit goed aan bij onze casus.

de rooier vervult namelijk een centrale rol binnen het oogstprocess. de overslagwagens moeten hun werkzaamheden afstemmen op de positie en status van de rooier.

een mogenlijke opstelling is daarom de CCU op de rooier te plaatsen, zodat de centrale controller met het meest centrale punt meebeweegt.

Dit zou voordelen kunnen bieden voor de integratie met de systemen van de rooier. Wel ontstaat hierdoor een afhankelijkheid van de rooier als fysieke drager van de centrale besturing.

De onderzochte publicaties geven geen directe vergelijking van de communicatiebetrouwbaarheid tussen een vaste CCU en een CCU op een bewegende landbouwmachine.


**Bronnen:** [2.] Emmi et al. (2014) en González-de-Santos et al. (2017).





**Bron:** Conejero et al. (2026), _Smart Agricultural Technology_.
### 2.4 Besturing en verwerking op de robots zelf
**Onderzoek: Development of a Combined Orchard Harvesting Robot Navigation System**


**Bron:** Mao et al. (2022), _Remote Sensing_.
### 2.5 Centrale verwerking op een externe edge-server
**Onderzoek: Optimising Robotic Operation Speed with Edge Computing via 5G Network**

**Bron:** Zahidi et al. (2024), _Journal of Field Robotics_.

--------------------------

##3. Vergelijking van de plaatsingsmogelijkheden




##4. Afweging van de locaties

##5. Conclusie en selectie