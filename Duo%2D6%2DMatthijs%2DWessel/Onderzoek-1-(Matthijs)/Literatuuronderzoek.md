Op deze pagina staat wat we in de literatuur hebben gevonden over betrouwbare communicatie tussen twee zones. We hebben het ingedeeld per deelvraag. Onderaan staat de literature gap en welke deelvraag daarbij hoort.

###Zoekstrategie
Er is vooral gezocht via Google Scholar, IEEE Xplore (via Xplora) en arXiv. Daarnaast zijn de standaarden zelf opgezocht (MQTT, TCP en VDA 5050).

###Deelvraag 1 - Welke mechanismen zijn er?
  
####Afleveringsgaranties

Volgens Kleppmann (2017) weet een zender nooit zeker of een bericht is aangekomen. Het bericht kan kwijt zijn, maar de bevestiging ook. Daarom zijn er drie soorten garanties:

- at-most-once (QoS 0): maximaal één keer, maar het bericht kan kwijtraken

- at-least-once (QoS 1): de zender blijft herhalen tot er een bevestiging komt, maar het bericht kan dubbel aankomen

- exactly-once (QoS 2): precies één keer

Exactly-once kun je in de praktijk alleen benaderen door at-least-once te combineren met een uniek ID per bericht. De ontvanger negeert dan berichten die hij al gehad heeft (Kleppmann, 2017).

####MQTT

MQTT heeft drie QoS-niveaus (OASIS, 2019):

- QoS 0: at most once

- QoS 1: at least once

- QoS 2: exactly once, via een handshake van vier berichten


Daarnaast heeft MQTT een keep alive (een soort heartbeat) en een Last Will. De Last Will is een bericht dat de broker verstuurt als een client wegvalt. Wat opviel: de QoS geldt tussen client en broker, niet van de ene applicatie tot de andere. Als coördinator B crasht nadat hij het bericht heeft ontvangen, maar voordat hij het uitvoert, kan de opdracht toch kwijtraken. Dat wil ik testen.

####TCP

TCP zorgt dat data goed en op volgorde aankomt, maar alleen zolang de verbinding blijft bestaan (Eddy, 2022). Valt de verbinding weg, dan weet de zender niet wat de andere kant al verwerkt heeft. TCP alleen is dus niet genoeg voor onze opdrachten. Er moet ook een bevestiging vanuit de applicatie komen.

####VDA 5050

VDA 5050 is een Duitse standaard voor communicatie tussen een fleet manager en AGV's via MQTT (VDA & VDMA, 2026). Wat hier interessant is:

- Voor opdrachten (order) gebruiken ze QoS 0, om de overhead laag te houden. Alleen het connection-topic gebruikt QoS 1.

- Dubbele opdrachten herkent de AGV aan het orderId en het orderUpdateId.

- Verbindingsverlies wordt gemeld met een Last Will.

Ze kiezen dus niet voor QoS 2, maar voor een uniek ID. Daarom willen we QoS 1 + ID vergelijken met QoS 2.

###Deelvraag 2 - Wat is acceptabel?

- VDA 5050 geeft geen vaste waarden. Er staat dat time-outs en herhalingen "tijdens de integratie" bepaald moeten worden (VDA & VDMA, 2026).

Er is namelijk ook geen universeel standaard. Het hangt heel erg af van de casus. Dit moeten we dus uiteindelijk vragen aan de opdrachtgever. 

###Deelvragen 3 en 4 - Verlies, dubbele opdrachten en vertraging

Lee et al. (2013) hebben gemeten hoeveel vertraging en berichtverlies er is bij de verschillende QoS-niveaus van MQTT. Zij keken alleen of berichten aankomen. Of een opdracht ook echt één keer wordt uitgevoerd, hebben ze niet onderzocht.

###Deelvraag 5 - Time-out en heartbeat

Chandra en Toueg (1996) laten zien dat je nooit zeker weet of een ander systeem echt uitgevallen is of alleen traag is. Een korte time-out ziet uitval snel, maar geeft ook meer valse alarmen.

Ik ga een paar vaste time-outs testen (bijvoorbeeld 0.5, 1, 2 en 5 seconden) en kijken hoe snel uitval wordt gezien en hoeveel valse alarmen er zijn.

###Literature gap

Er is veel bekend over hoe je berichten betrouwbaar verstuurt. Met VDA 5050 is er ook een standaard voor één fleet manager met zijn eigen robots. Communicatie met andere systemen valt buiten die standaard (VDA & VDMA, 2026). Voor onze casus ontbreken nog een paar dingen. Die zijn gekoppeld aan de deelvragen:

| Gap | Wat is al bekend | Wat ontbreekt | Deelvraag |
|--|--|--|--|
| 1| Afleveringsgaranties, unieke ID's, VDA 5050 | Hoe dit werkt tussen twee aparte vloten (zone A en zone B) | Deelvraag 1|
| 2 | Niks | Wat acceptabel is voor een overdracht via een sluis | Deelvraag 2|
| 3 | Metingen van MQTT-verlies en -vertraging | Metingen van verloren en dubbel uitgevoerde opdrachten bij storingen | Deelvragen 3 en 4 |
| 4 | Afweging tussen snel detecteren en valse alarmen | Welke time-out past bij onze overdracht | Deelvraag 5 |

Wat er nog niet bekend is: welk mechanisme (TCP met ACK, MQTT QoS 1 met ID of MQTT QoS 2) bij storingen geen opdrachten kwijtraakt en niets dubbel uitvoert, met een vertraging die acceptabel is. Dat moet allemaal worden onderzocht.

### 7. Bronnen
Chandra, T. D., & Toueg, S. (1996). Unreliable failure detectors for reliable distributed systems. *Journal of the ACM, 43*(2), 225–267. https://doi.org/10.1145/226643.226647

Eddy, W. (Red.). (2022). *Transmission Control Protocol (TCP)* (RFC 9293). IETF. https://doi.org/10.17487/RFC9293

Kleppmann, M. (2017). *Designing data-intensive applications*. O'Reilly Media. 

Lee, S., Kim, H., Hong, D., & Ju, H. (2013). Correlation analysis of MQTT loss and delay according to QoS level. In *The International Conference on Information Networking 2013 (ICOIN)* (pp. 714–717). IEEE. https://doi.org/10.1109/ICOIN.2013.6496715

OASIS. (2019). *MQTT version 5.0* (OASIS Standard). https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html

VDA & VDMA. (2026). *VDA 5050: Interface for the communication between mobile robots and a fleet control* (Versie 3.0.0). https://github.com/VDA5050/VDA5050





