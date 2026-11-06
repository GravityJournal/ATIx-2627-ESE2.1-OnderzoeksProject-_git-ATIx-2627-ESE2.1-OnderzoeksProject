
#Welke plaatsingsmogelijkheden voor een centrale controlunit (CCU) worden in bestaande onderzoeken toegepast en in hoeverre zijn deze geschikt voor onze robotvloot?

## 1. Inleiding
op basis van de casus wordt gebruikgemaakt van een gecentraliseerde besturingsarchitectuur. De robotvloot bestaat uit één rooier en twee overslagwagens die samenwerken tijdens het oogstproces.

De centrale controlunit (CCU) is verantwoordelijk voor het ontvangen en verwerken van informatie van de robots. Op basis van deze gegevens kan de CCU beslissingen nemen over bijvoorbeeld de routeplanning en taakverdeling.

Een belangrijke vraag binnen deze architectuur is waar de CCU fysiek geplaatst moet worden.
Om te bepalen welke plaatsingsmogelijkheden relevant zijn voor onze robotvloot, onderzoeken we welke oplossingen in bestaande wetenschappelijke onderzoeken worden toegepast en welke overwegingen daarbij een rol spelen.

Hierbij word specifiek gekeken naar centrale besturingssystemen voor landbouwrobots en andere autonome mobiele robots.

--------------------------
## 2. Literatuuronderzoek
Hieronder staan meerdere onderzoeken die potentiël relevant zijn voor de uitwerking.

###2.1 Centrale besturing op een vaste locatie



**Beschrijving:**

In het onderzoek van Emmi et al. (2014) [7] wordt een gecentraliseerde besturingsarchitectuur beschreven voor het RHEA-project. Binnen dit project wordt een robotvloot van drie autonome landbouwmachines aangestuurd vanuit een centraal basisstation.
De onderzoekers hebben gekozen voor een externe computer op een vaste locatie naast het landbouwperceel. Op deze computer draait een _Mission Manager_, die verantwoordelijk is voor het plannen en coördineren van de werkzaamheden. De robots sturen gegevens, zoals hun locatie en huidige status, naar deze centrale computer. Op basis van deze informatie kan de Mission Manager de werkzaamheden bewaken en opdrachten naar de robots versturen.

Volgens Emmi et al. (2014) [7] is een centrale planner geschikt voor landbouwtoepassingen omdat het werkgebied doorgaans vooraf bekend is en de werkzaamheden van meerdere machines op elkaar moeten worden afgestemd. Daarnaast maakt een extern basisstation het mogelijk om de robotvloot vanuit één locatie te monitoren en te bedienen.

González-de-Santos et al. (2017) [1] beschrijven de verdere toepassing van deze architectuur binnen het RHEA-project. Het basisstation beschikt over een computer waarop de Mission Manager draait. Deze is verbonden met de landbouwrobots via een draadloos communicatienetwerk. De robots beschikken daarnaast over eigen besturingssystemen voor hun lokale taken.


Een andere toepassing van externe gegevensverwerking wordt beschreven door Zahidi et al. (2024) [5] in dit onderzoek word gebruikt gemaakt van edge-computing bij een autonome robotvloot. hierbij worden zware berekeningen, zoals beeldverwerking uitgevoerd op een externe server via een privaat 5G-netwerk

Hoewel dit onderzoek geen centrale vlootbesturing behandelt, laat het zien dat externe gegevensverwerking via een draadloos netwerk toepasbaar is binnen landbouwrobotica.


**Relevantie voor onze robotvloot**
Deze opstelling is meegenomen in onze robotvloot omdat ook wij gebruik willen maken van centrale coördinatie tussen meerdere landbouwmachines.
Een vaste CCU buiten het perceel zou de gegevens van de rooier en overslagwagens kunnen ontvangen en gebruiken voor de gezamenlijke routeplanning en taakverdeling.

++
- Een mogelijk voordeel van deze opstelling is dat de CCU onafhankelijk van de bewegingen van de landbouwmachines kan blijven functioneren. Daarnaast kan de centrale besturing vanaf een vaste locatie worden onderhouden en bewaakt.

- Mogelijke sterkere hardwarewaarbij je de zware taken overlaat aan de CCU/externe computer.

--
en aandachtspunt is dat de robots gedurende het oogstproces moeten kunnen blijven communiceren met de CCU, terwijl zij zich over het perceel verplaatsen.

De onderzoeken tonen aan dat een vaste centrale besturing praktisch toepasbaar is binnen een landbouwrobotvloot. Er wordt echter niet aangetoond dat deze plaatsing een betrouwbaardere communicatieverbinding oplevert dan een CCU op een bewegende landbouwmachine.
Daarom blijft het relevant om de invloed van de fysieke locatie van de CCU binnen onze eigen robotvloot verder te onderzoeken.


**Gebruikte bronnen:**

[2] Emmi et al. (2014)
[1] González-de-Santos et al. (2017)
[5] Zahidi et al. (2024)

-----------


### 2.2 Centrale besturing op een landbouwrobot
**Beschrijving:**

In het onderzoek van Emmi et al. (2014)[7] wordt naast een vaste centrale besturing ook een master-slaveconfiguratie beschreven. Bij deze architectuur wordt de centrale besturing ondergebracht op één van de landbouwrobots, die vervolgens verantwoordelijk is voor het aansturen van de overige robots.

De onderzoekers hebben deze architectuur toegepast binnen het RHEA-project, dat bestaat uit drie autonome landbouwmachines. Eén van deze machines fungeert als master en voert de centrale taken uit, zoals het plannen van de werkzaamheden, het versturen van opdrachten en het controleren van de voortgang. De overige machines functioneren als slaves en ontvangen opdrachten van de masterrobot.

--
Een nadeel van deze architectuur is de afhankelijkheid van de masterrobot. Wanneer de centrale besturing op deze robot uitvalt, kan dit ervoor zorgen dat de werkzaamheden van de volledige robotvloot worden onderbroken.

++
Volgens Emmi et al. (2014) heeft deze configuratie verschillende voordelen. Zo is er geen afzonderlijke centrale computer in een basisstation nodig, waardoor de hoeveelheid benodigde hardware wordt verminderd. Daarnaast kan het werkgebied mogelijk worden vergroot doordat de centrale besturing met de robotvloot meebeweegt.





**Relevantie voor onze robotvloot**
Deze architectuur sluit aan op onze robotvloot, omdat deze eveneens bestaat uit drie landbouwmachines die gezamenlijk werkzaamheden uitvoeren.

Een mogelijke toepassing is om de CCU op de rooier te plaatsen. De rooier speelt een centrale rol tijdens het oogstproces, omdat de overslagwagens hun werkzaamheden moeten afstemmen op de locatie en status van de rooier.


Het is echter nog niet duidelijk of deze opstelling daadwerkelijk voordelen oplevert voor de betrouwbaarheid van de communicatie. Het onderzoek van Emmi et al. (2014) richt zich voornamelijk op de besturingsarchitectuur en het functioneren van de robotvloot.

Daarom is deze plaatsingsmogelijkheid relevant om binnen ons eigen onderzoek verder te vergelijken met een vaste centrale besturing.

**Gebruikte bronnen:**
[2] Emmi et al. (2014)
[7] Casus van het project (2026)




-------


##3. Vergelijking van de plaatsingsmogelijkheden

Uit het literatuuronderzoek zijn verschillende mogelijkheden voor de centrale besturing naar voren gekomen. Hoewel er meerdere technische oplossingen mogelijk zijn, kunnen deze op basis van hun fysieke locatie worden onderverdeeld in twee categorieën: een vaste en een mobiele CCU.


|  Eigneschap|Vaste CCU  |Mobiele CCU  |
|--|--|--|
|Fysieke eigenschappen  |  Vaste locatie binnen of buiten het perceel| Beweegt mee met robot vloot |
| Hardware|  Externe server of afzonderlijke computer nodig| Externe server word op de robot geplaatst |
|Netwerkverbinding| Kan bedraad of draadloos worden aangesloten|Vereist tijdens het rijden draadloze connectie|
|Rekenkracht|Mogenlijk om een krachtige externe server te gebruiken| Bepert door de beschikbaare ruimte, koeling maar vooral energievoorziening|


##4. Afweging van de locaties

Uit de onderzochte literatuur blijkt dat beide plaatsingsmogelijkheden binnen landbouwrobotvloten toepasbaar zijn. Er wordt echter niet aangetoond welke opstelling de betrouwbaarste communicatie oplevert.
Daarom kunnen we op basis van deze onderzoeken nog geen conclusie trekken over betrouwbaarheid van de architectuur.

##5. Conclusie en selectie
Uit deze analyse kunnen we nog geen verdere conclusie trekken en zullen we door moeten onderzoeken dmv een POC.