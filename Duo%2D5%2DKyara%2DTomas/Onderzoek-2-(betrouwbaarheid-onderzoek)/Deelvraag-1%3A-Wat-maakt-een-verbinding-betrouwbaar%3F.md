## Inleiding
Om te kunnen bepalen hoe de afstand en snelheid van de robot moeten worden afgesteld voor een zo betrouwbaar mogelijke verbinding, moet eerst duidelijk zijn wat een betrouwbare verbinding inhoudt. Een betrouwbare verbinding zorgt ervoor dat gegevens tussen de robot en het besturingssysteem correct, volledig en op tijd worden verzonden en ontvangen.

Bij dit project wordt gebruikgemaakt van een 5G-netwerk om de communicatie tussen de robot en het besturingssysteem mogelijk te maken. Het is daarom belangrijk om te onderzoeken welke factoren invloed hebben op de betrouwbaarheid van een draadloze verbinding.

Bij dit project wordt gebruikgemaakt van een 5G-netwerk om draadloos te communiceren tussen de robot en het besturingssysteem. Tijdens deze communicatie kunnen verschillende factoren invloed hebben op de betrouwbaarheid van de verbinding. Daarom is het belangrijk om te onderzoeken welke factoren hierbij een rol spelen en hoe deze gemeten kunnen worden.

Voor dit onderzoek worden vier factoren meegenomen:
- Latency
- Packet loss
- Jitter
- Signaalsterkte

Deze factoren geven samen inzicht in de snelheid, stabiliteit en kwaliteit van de verbinding.
## Wat wordt verstaan onder een betrouwbare verbinding?

Een betrouwbare verbinding is een verbinding waarbij gegevens zo snel en volledig mogelijk bij de ontvanger aankomen. In het geval van de robot betekent dit dat de data vanuit en naar het centrale controller correct en zonder onnodige vertraging verzonden en ontvangen worden.
Wanneer een verbinding niet betrouwbaar is, kunnen verschillende problemen ontstaan. 
bijvoorbeeld bij het geval dat de operator een opdracht geeft aan de robot:
- De robot reageert vertraagd op commando's.
- Commando's komen niet aan bij de robot.
- Commando's komen met wisselende vertraging aan.
- De draadloze verbinding wordt instabiel of valt tijdelijk weg.
    
Dit kan gevolgen hebben voor de besturing van de robot. Wanneer bijvoorbeeld een stopcommando vertraagd of helemaal niet aankomt, kan de robot langer blijven bewegen dan bedoeld.
Om deze problemen te voorkomen, moeten de verschillende factoren die invloed hebben op de verbinding zo goed mogelijk worden gecontroleerd.