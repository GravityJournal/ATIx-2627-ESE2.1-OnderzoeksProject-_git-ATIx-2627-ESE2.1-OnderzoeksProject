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

- Dubbele opdrachten herkent de AGV aan het `orderId` en het `orderUpdateId`.

- Verbindingsverlies wordt gemeld met een Last Will.

Ze kiezen dus niet voor QoS 2, maar voor een uniek ID. Daarom willen we QoS 1 + ID vergelijken met QoS 2.

###Deelvraag 2 - Wat is acceptabel?

- VDA 5050 geeft geen vaste waarden. Er staat dat time-outs en herhalingen "tijdens de integratie" bepaald moeten worden (VDA & VDMA, 2026).

Er is namelijk ook geen universeel standaard. Het hangt heel erg af van de casus. Dit moeten we dus uiteindelijk vragen aan de opdrachtgever. 


