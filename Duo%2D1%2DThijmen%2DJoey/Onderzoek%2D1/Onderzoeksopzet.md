#Onderzoeksopzet
##Onderzoeksvraag:
Welke invloed heeft de fysieke locatie van de centrale controlunit (CCU) op de latency, het pakketverlies en de beschikbaarheid van de communicatie tussen de CCU en de robots binnen onze robotvloot?

##Deelvragen
**1. Welke fysieke locaties voor de CCU zijn binnen onze robotvloot geschikt om te onderzoeken?**

_Toelichting:_
Om de invloed van de plaatsing te kunnen onderzoeken, moeten we eerst bepalen welke locaties relevant en praktisch haalbaar zijn. Hierbij kijken we naar de eigenschappen van onze robotvloot en de mogelijke locaties van de CCU.

_Onderzoeks methode_:


Casusanalyse en literatuuronderzoek

**2. Welke verschillen in latency, packet loss en beschikbaarheid ontstaan bij verschillende fysieke locaties van de CCU?**
_Toelichting:_
Met behulp van een PoC willen we de communicatieprestaties bij verschillende CCU-locaties meten.
Door de resultaten met elkaar te vergelijken, kunnen we vaststellen of de locatie van de CCU invloed heeft op de betrouwbaarheid van de communicatie en hoe groot eventuele verschillen zijn.

_Onderzoeks methode:_ 
Experimenteel onderzoek met een Proof of Concept (PoC)

### Beschrijving testopstelling (PoC)

Voor het uitvoeren van de metingen maken we gebruik van een testopstelling met meerdere computers. Eén computer fungeert als centrale controlunit (CCU), terwijl de andere computers de robots simuleren.
De computers communiceren via een draadloos netwerk met elkaar. Met behulp van een TCP-client en server worden berichten uitgewisseld om de round-trip time (RTT), het pakketverlies en de bereikbaarheid te meten.
Tijdens het experiment wordt de CCU op verschillende fysieke locaties geplaatst, terwijl de overige computers op vaste posities blijven. De netwerkconfiguratie en meetinstellingen blijven hierbij zo veel mogelijk gelijk.
De verzamelde meetgegevens worden opgeslagen en geanalyseerd om eventuele verschillen in communicatiebetrouwbaarheid tussen de CCU-locaties vast te stellen.



**3.Hoe kunnen we de betrouwbaarheid van de communicatie tussen de CCU en de robots meten?**
_Toelichting:_
Om verschillende locaties objectief te kunnen vergelijken, moeten we eerst bepalen hoe we communicatiebetrouwbaarheid meten.
Hiervoor onderzoeken we hoe latency, packet loss en de beschikbaarheid van de verbinding gemeten kunnen worden. Ook bepalen we hoe we deze metingen onder vergelijkbare omstandigheden kunnen uitvoeren.

_Onderzoeks methode:_ 

We onderzoeken welke bestaande meetmethoden geschikt zijn om de communicatiebetrouwbaarheid te bepalen.

Hierbij richten we ons op drie meetwaarden:
*   Latency
*   Packet loss
*   Beschikbaarheid van de verbinding
