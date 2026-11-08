Probleemanalyse voor het onderzoek
==================================

Probleem
--------

Een van de klanten van ExRobotics doet ‘mission critical’ inspecties op een raffinaderij. Hierbij komen stoffen, zoals H2S(waterstofsulfide), vrij die boven een bepaalde dosis dodelijk is voor mensen. ExRobotics helpt hier al mee als een bedrijf dat robots inzet in industriële faciliteiten in de wereld waar gevaarlijke stoffen of explosiegevaar is. Uit de informatie die wij hebben doorgekregen vanuit ExRobotics blijkt ook dat de fabriek elke 8 uur moet worden geïnspecteerd en er in totaal 600 inspecties per 24 uur plaatsvinden. Dit werk wordt al verdeeld over twee robots verdeeld die elke 8 uur een inspectieronde uitvoeren en er een derde beschikbaar is als er een robot faalt.   
Er zijn dus al robots die de inspecties kunnen uitvoeren zodat mensen niet in gevaar gebracht worden. Dit brengt alsnog wel wat problemen met zich me. Een probleem hier is wanneer een van de twee robots tijdens de inspectieronde uitvalt dat de derde reserverobot niet uit zichzelf verdergaat waar de robot is uitgevallen. Ook kunnen de robots niet zomaar overal heen in de fabriek gezien de mogelijke aanwezigheid van waterstof in deze zones. 

Belang
------

Het is van belangrijk om dit probleem op te lossen zodat mensen die in de raffinaderij werken veilig over de vloer kunnen gaan zonder angst voor H2S. Zo blijven mensen gezond en veilig hun werk doen.

Doelstelling van het onderzoek
------------------------------

Het doel is vast te stellen hoeveel extra vertraging optreedt bij de eerste communicatie tussen twee robots (of een robot en het controlesysteem) wanneer het MAC-adres van de ontvanger nog niet bekend is en eerst via ARP moet worden opgevraagd. Daarnaast onderzoeken we of die vertraging een probleem is voor de communicatie tijdens een inspectieronde, bijvoorbeeld wanneer de reserverobot na een uitval voor het eerst contact legt met het systeem of met andere robots.

Literatuuronderzoek + literature gap
------------------------------------

**Wat de literatuur al zegt**
_1. Hoe ARP werkt._ IP-adressen moeten op een lokaal netwerk worden vertaald naar MAC-adressen voordat een pakket kan worden verstuurd. Dat gebeurt met een ARP-request (broadcast) en een ARP-reply (unicast) (Plummer, 1982; Kurose & Ross, 2021). Het resultaat wordt tijdelijk opgeslagen in de ARP-cache. Alleen de eerste communicatie met een onbekende ontvanger (of na het verlopen van de cache) loopt dus extra vertraging op. In IPv6 doet Neighbor Discovery hetzelfde werk (Narten et al., 2007).
_2. Wat de vertraging bepaalt._ Het eerste pakket moet wachten op de ronde ARP-request en ARP-reply. De extra vertraging hangt dus af van de round-trip-tijd van het netwerk, de verwerkingstijd van de ontvanger en eventuele verloren of herhaalde ARP-pakketten. Bij ARP-conflictdetectie, waarbij een apparaat controleert of een IP-adres al in gebruik is, kunnen extra wachttijden ontstaan (Cheshire, 2008).
_3. Meetmethoden._ Het IETF heeft een raamwerk voor het meten van netwerkprestaties (Paxson et al., 1998) en een benchmarkmethodologie (Bradner & McQuaid, 1999). Pan en Sun (2014) stellen in een Internet-Draft een metriek voor de adresresolutievertraging in SDN-netwerken voor. Zij benadrukken dat deze vertraging relevant is voor toepassingen met strikte tijdseisen, vooral wanneer de zendtijd van de data vergelijkbaar is met de resolutietijd.
_4. Draadloze netwerken._ Op draadloze verbindingen wordt een ARP-broadcast anders afgehandeld dan op bedrade netwerken (lagere datasnelheid voor broadcasts, meer kans op verlies). Hierdoor is de vertraging daar waarschijnlijk groter en variabeler. Dit moet nog worden bevestigd met bronnen over de gebruikte Wi-Fi-technologie.

### Literature gap

1.  **Geen metingen in een robotcontext.** De ARP-vertraging wordt in de literatuur beschreven als protocolmechanisme of gemeten in algemene of SDN-netwerken. Ik vond geen onderzoek naar de vertraging bij de eerste communicatie tussen mobiele inspectierobots.
2.  **Geen aandacht voor het uitvalscenario.** Bij de overdracht van een uitgevallen robot naar de reserverobot moet die reserverobot voor het eerst communiceren met het netwerk en mogelijk met andere robots. Het is niet onderzocht hoeveel tijd die eerste communicatie kost en of dat acceptabel is.
3.  **Geen cijfers voor een industriële draadloze omgeving.** Een raffinaderij heeft veel metaal en storing, en robots roamen tussen access points. Het is niet bekend hoe groot de extra ARP-vertraging daar in de praktijk is, en of die voor een veiligheidskritisch bericht zoals een H2S-alarm een risico vormt.
4.  **De norm voor “acceptabel” ontbreekt.** Er is geen bruikbare eis voor de maximale toegestane vertraging bij de eerste communicatie in deze toepassing. Zonder zo’n norm is een gemeten vertraging niet te beoordelen.
**Binnen de scope**
*   Het meten van de ARP-resolutievertraging op een lokaal netwerk (laag 2/3): de tijd tussen de ARP-request en de ontvangst van de ARP-reply, en de extra vertraging van het eerste pakket.
*   Een vergelijking tussen de eerste communicatie (lege ARP-cache) en daaropvolgende communicatie (gevulde cache).
*   Invloed van netwerkomstandigheden, zoals pakketverlies en netwerkbelasting, op de vertraging.
*   Het scenario waarin de reserverobot voor het eerst communiceert na een uitval.
*   Metingen in een laboratorium- of testopstelling die de situatie bij ExRobotics nabootst.
**Buiten de scope**
*   Vergelijking van transportprotocollen (TCP en UDP) en applicatieprotocollen zoals MQTT, OPC UA en ROS 2/DDS.
*   Routering over meerdere netwerken (laag 3 en hoger) en WAN-verbindingen.
*   Optimalisatie of vervanging van ARP, bijvoorbeeld door statische ARP-tabellen. Dit kan wel in de aanbevelingen terugkomen.
*   IPv6 en Neighbor Discovery, tenzij de klant IPv6 gebruikt.
*   Cybersecurity, zoals ARP-spoofing.
*   Robothardware, sensoren, navigatie en de besluitvorming bij uitval.
*   Metingen op de echte raffinaderij, ATEX-certificering en kosten.
**Randvoorwaarden en aannames**
*   De robots en het controlesysteem zitten in hetzelfde lokale netwerk (subnet).
*   Het netwerk bestaat uit gangbare hardware zoals access points en switches.
*   De uitkomst is een advies voor ExRobotics.

### Bronnen

*   Bradner, S., & McQuaid, J. (1999). _Benchmarking Methodology for Network Interconnect Devices_ (RFC 2544). IETF.
*   Cheshire, S. (2008). _IPv4 Address Conflict Detection_ (RFC 5227). IETF.
*   Kurose, J. F., & Ross, K. W. (2021). _Computer Networking: A Top-Down Approach_ (8e druk). Pearson.
*   Narten, T., Nordmark, E., Simpson, W., & Soliman, H. (2007). _Neighbor Discovery for IP version 6 (IPv6)_ (RFC 4861). IETF.
*   Pan, X., & Sun, J. (2014). _Address Resolution Delay Metric in Software-Defined Networking (SDN)_ (Internet-Draft, draft-pan-ippm-sdn-addr-resolv-perf-00). IETF. [https://datatracker.ietf.org/doc/draft-pan-ippm-sdn-addr-resolv-perf/](https://datatracker.ietf.org/doc/draft-pan-ippm-sdn-addr-resolv-perf/)
*   Paxson, V., Almes, G., Mahdavi, J., & Mathis, M. (1998). _Framework for IP Performance Metrics_ (RFC 2330). IETF.
*   Plummer, D. C. (1982). _An Ethernet Address Resolution Protocol_ (RFC 826). IETF.