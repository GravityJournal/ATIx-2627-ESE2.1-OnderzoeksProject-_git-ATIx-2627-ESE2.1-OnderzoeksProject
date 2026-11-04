## Inleiding
Om te kunnen bepalen hoe de afstand en snelheid van de robot moeten worden afgesteld voor een zo betrouwbaar mogelijke verbinding, moet eerst duidelijk zijn wat een betrouwbare verbinding inhoudt. Een betrouwbare verbinding zorgt ervoor dat gegevens tussen de robot en het besturingssysteem correct, volledig en op tijd worden verzonden en ontvangen.

Bij dit project wordt gebruikgemaakt van een 5G-netwerk om de communicatie tussen de robot en het besturingssysteem mogelijk te maken. Het is daarom belangrijk om te onderzoeken welke factoren invloed hebben op de betrouwbaarheid van een draadloze verbinding.

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
- De verbinding wordt instabiel of valt tijdelijk weg.
    
Dit kan gevolgen hebben voor de besturing van de robot. Wanneer bijvoorbeeld een stopcommando vertraagd of helemaal niet aankomt, kan de robot langer blijven bewegen dan de operator dat bedoelt bedoeld.
Om deze problemen te voorkomen, moeten de verschillende factoren die invloed hebben op de verbinding zo goed 
mogelijk worden gecontroleerd.

## factoren betrouwbaarheid
### Latency
Latency is de tijd die nodig is om gegevens van de zender naar de ontvanger te versturen. Bij dit onderzoek wordt gekeken naar de tijd tussen het versturen van een bericht door het besturingssysteem en het ontvangen van dit bericht door de robot.
Latency wordt uitgedrukt in milliseconden (ms). Hoe lager de latency, hoe sneller de robot kan reageren op de verstuurde berichten.
Een hoge latency kan dus ervoor zorgen dat de robot vertraagd reageert op de besturing. Dit kan vooral problemen opleveren wanneer de robot snel moet reageren op veranderingen of een noodstop.
De ITU beschrijft in [recommendation G.114](https://www.itu.int/rec/T-REC-G.114/) de invloed van vertraging op communicatie. Hierin wordt onder andere aangegeven dat interactieve toepassingen gevoelig kunnen zijn voor vertragingen. De benodigde latency is afhankelijk van de toepassing.
Voor dit onderzoek is het daarom belangrijk om de latency zo laag mogelijk te houden.