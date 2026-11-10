## Inleiding
Om te kunnen bepalen hoe de afstand en snelheid van de robot moeten worden afgesteld voor een zo betrouwbaar mogelijke verbinding, moet eerst duidelijk zijn wat een betrouwbare verbinding inhoudt. Een betrouwbare verbinding zorgt ervoor dat gegevens tussen de robot en het besturingssysteem correct, volledig en op tijd worden verzonden en ontvangen.

Bij dit project wordt gebruikgemaakt van een 5G-netwerk om de communicatie tussen de robot en het besturingssysteem mogelijk te maken. Het is daarom belangrijk om te onderzoeken welke factoren invloed hebben op de betrouwbaarheid van een draadloze verbinding.

Voor dit onderzoek worden vier factoren meegenomen:
- Latency
- Packet loss
- Jitter
- Signaalsterkte

Deze factoren geven samen inzicht in de betrouwbaarheid van de verbinding.

## Wat wordt verstaan onder een betrouwbare verbinding?

Een betrouwbare verbinding is een verbinding waarbij gegevens zo snel en volledig mogelijk bij de ontvanger aankomen. In het geval van de robot betekent dit dat de data vanuit en naar het centrale controller correct en zonder onnodige vertraging verzonden en ontvangen worden.
Wanneer een verbinding niet betrouwbaar is, kunnen verschillende problemen ontstaan. 
bijvoorbeeld bij het geval dat de operator een opdracht geeft aan de robot:
- De robot reageert vertraagd op commando's.
- Commando's komen niet aan bij de robot.
- Commando's komen met wisselende vertraging aan.
- De verbinding wordt instabiel of valt tijdelijk weg.
    
Dit kan gevolgen hebben voor de besturing van de robot. Wanneer bijvoorbeeld een stopcommando vertraagd of helemaal niet aankomt, kan de robot langer blijven bewegen dan de operator dat bedoelt bedoeld.
Om deze problemen te voorkomen, moeten de verschillende factoren die invloed hebben op de verbinding zo goed 
mogelijk worden gecontroleerd.

## factoren betrouwbaarheid

### Latency

Latency is de tijd die nodig is om gegevens van de zender naar de ontvanger te versturen. Bij dit onderzoek wordt gekeken naar de tijd tussen het versturen van een bericht door het besturingssysteem en het ontvangen van dit bericht door de robot.
Latency wordt uitgedrukt in milliseconden (ms). Hoe lager de latency, hoe sneller de robot kan reageren op de verstuurde berichten.
Een hoge latency kan dus ervoor zorgen dat de robot vertraagd reageert op de besturing. Dit kan vooral problemen opleveren wanneer de robot snel moet reageren op veranderingen of een noodstop.
Voor een goede verbinding is het daarom belangrijk om de latency zo laag mogelijk te houden.

### Packet loss

Packet loss betekent dataverlies tijdens het verzenden van gegevens. Bij digitale communicatie worden gegevens opgedeeld in packets. Deze packets worden via het netwerk naar de ontvanger verstuurd.
Wanneer een packets niet bij de ontvanger aankomt, spreken we van packet loss.
Packet loss wordt uitgedrukt in procenten. Dit percentage geeft aan hoeveel van de verzonden packets verloren zijn gegaan. Bijvoorbeeld wanneer er 1000 packets worden verstuurd en 10 packets niet aankomen, is dat een packet loss van 1%

Voor een goede verbinding is het belangrijk dat packet loss zo dicht mogelijk bij 0% ligt. Wanneer berichten verloren gaan, kan de robot deze niet ontvangen en dus ook niet uitvoeren.

### Jitter

Jitter is de variatie in de vertraging waarmee verschillende packets bij de ontvanger aankomen. Dit betekent dat de tijd tussen het versturen en ontvangen van packets niet altijd hetzelfde is.
Bijvoorbeeld packet 1 komt na 10 ms aan, packet 2 komt na 15 ms aan en packet 3 komt na 40 ms aan. De verschillen tussen deze vertragingen laten zien dat de verbinding niet altijd even snel reageert. Dit verschil in vertraging wordt jitter genoemd.
Jitter wordt uitgedrukt in milliseconden (ms). Hoe lager de jitter, hoe gelijkmatiger de packets aankomen.
Bij het besturen van een robot kan een hoge jitter ervoor zorgen dat berichten niet met een gelijkmatige vertraging aankomen. Hierdoor kan de robot onregelmatig reageren op de besturing.
Voor een goede verbinding is het dus ook belangrijk om de jitter zo laag mogelijk te houden.

### Signaalsterkte

Signaalsterkte geeft aan hoe sterk het radiosignaal is dat door de ontvanger wordt ontvangen. Bij dit onderzoek gaat het om de sterkte van het 5G-signaal dat de robot ontvangt.
De signaalsterkte kan worden beïnvloed door bijvoorbeeld de afstand tussen de robot en het communicatiepunt, Obstakels zoals muren en voorwerpen, storingen van andere radiosignalen en de positie en richting van de antenne.
Wanneer de afstand tussen de robot en het communicatiepunt groter wordt, kan het ontvangen signaal zwakker worden. Hierdoor kan de verbinding minder stabiel worden en kunnen latency en packet loss toenemen.
De signaalsterkte van een 5G-verbinding kan onder andere worden weergegeven met SS-RSRP. Dit is een meetwaarde die de ontvangen sterkte 5G signalen aangeeft en wordt gemeten in dBm.
Bij het meten in dBm geldt dat een waarde dichter bij nul een sterker signaal aangeeff en dus beter voor de betrouwbaarheid van de verbinding.

## conclusie
Een verbinding kan als betrouwbaar worden gezien wanneer de latency zo laag mogelijk is, het percentage packet loss zo dicht mogelijk bij 0% ligt, de jitter zo klein mogelijk is en de verbinding stabiel blijft tijdens het bewegen van de robot.
Naar deze vier criteria zal worden gekeken in deelvraag 2
   