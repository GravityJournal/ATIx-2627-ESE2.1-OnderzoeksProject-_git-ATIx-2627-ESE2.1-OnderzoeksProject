## 1. Probleem analyse
### 1.1 Probleemcontext
Binnen de casus moeten producten tussen 2 zones worden verplaatst. Elke zone heeft een eigen robotvloot, en robots mogen de zonegrens nooit passeren. Goederen (bijv. pallets, kratten) gaan via een overdrachtspunt/ sluis van zone A naar zone B, en lege ladingdragers gaan weer terug.

Daarvoor moeten de beide zones met elkaar kunnen praten. Denk aan opdrachten zoals: "Robot A moet naar de sluis voor overdracht met Robot B". In de randvoorwaarde van de casus staat dat tijdens een storing of communicatie-uitval het systeem in een veilige toestand moet terechtkomen, zonder dat opdrachten verloren gaan of dubbel worden uitgevoerd.

Voor de veilige communicatie is nog niet bepaald met welk communicatiemechanisme gewerkt moet worden. Dit onderzoek werkt dit stukje van de infrastructuur uit.

### 1.2 Belang
- Productie: een verloren overdrachtsbericht kan een overdrachtspunt blokkeren of een productielijn stil laten vallen.

- Hygiëne en veiligheid: een dubbel uitgevoerde opdracht kan betekenen dat twee robots tegelijk naar het overdrachtspunt rijden, of dat een pallet wordt opgehaald die er niet staat.

- Traceerbaarheid: de opdrachtgever wil per overdracht kunnen aantonen wanneer die plaatsvond en met welke robots. Dat lukt alleen als berichten betrouwbaar en uniek identificeerbaar zijn.

- Ontwerp robotvloot: de uitkomst bepaalt direct welk protocol en welke foutafhandeling wij in ons groepsproject kunnen gaan gebruiken.

### 1.3 Literatuuronderzoek (samenvatting)

Het volledige literatuuronderzoek staat op de pagina [Literatuuronderzoek](/Duo%2D6%2DMatthijs%2DWessel/Onderzoek-1-\(Matthijs\)/Literatuuronderzoek). Hieronder staan de belangrijkste punten.

- Een zender weet nooit zeker of een bericht is aangekomen. Daarom zijn er drie soorten garanties: at-most-once, at-least-once en exactly-once. Echt exactly-once bestaat in de praktijk niet. Je kunt het wel benaderen door berichten te herhalen tot er een bevestiging komt en elk bericht een uniek ID te geven, zodat de ontvanger dubbele berichten kan negeren (Kleppmann, 2017).

- TCP zorgt alleen voor betrouwbare aflevering zolang de verbinding blijft bestaan. Valt de verbinding weg, dan weet de zender niet wat de andere kant al verwerkt heeft (Eddy, 2022). TCP alleen is dus niet genoeg.

- MQTT heeft drie QoS-niveaus (0, 1 en 2), een keep alive en een Last Will (OASIS, 2019). De QoS geldt tussen client en broker, en niet tussen de twee applicaties.

- De standaard VDA 5050 gebruikt voor opdrachten QoS 0 en herkent dubbele opdrachten aan een uniek orderId. Vaste waarden voor time-outs geeft de standaard niet; die moeten "tijdens de integratie" bepaald worden. De standaard gaat ook alleen over een fleet manager met zijn eigen robots (VDA & VDMA, 2026).

- Lee et al. (2013) hebben vertraging en berichtverlies per QoS-niveau gemeten, maar niet gekeken of opdrachten ook echt één keer worden uitgevoerd.

- Chandra en Toueg (1996) laten zien dat je nooit zeker weet of een systeem uitgevallen is of alleen traag is. Een korte time-out ziet uitval sneller, maar geeft meer valse alarmen.

### 1.4 Literature gap

Er is veel bekend over hoe je berichten betrouwbaar verstuurt, maar niet voor de situatie in deze casus. Wat nog ontbreekt:

1. Hoe de communicatie werkt tussen twee aparte vloten (zone A en zone B) die samen een sluis gebruiken. VDA 5050 gaat alleen over één fleet manager met zijn eigen robots. → Deelvraag 1

2. Wat een acceptabele vertraging is voor een overdracht via een sluis. Hier bestaat geen vaste waarde voor, het hangt af van de casus. → Deelvraag 2

3. Hoeveel opdrachten bij storingen echt verloren gaan of dubbel worden uitgevoerd. Bestaande metingen kijken alleen of berichten aankomen. → Deelvraag 3 en 4

4. Welke time-out en heartbeat passen bij een overdracht, zodat een sluis niet onnodig lang geblokkeerd blijft. → Deelvraag 5

Kort gezegd is niet bekend welk mechanisme (TCP met ACK, MQTT QoS 1 met ID of MQTT QoS 2) bij storingen geen opdrachten kwijtraakt en niets dubbel uitvoert, met een vertraging die acceptabel is. Dat ga ik in dit onderzoek uitzoeken.

### 1.5 Doelstelling
Het doel van dit onderzoek is uitzoeken welk communicatiemechanisme tussen zone A en zone B het beste werkt voor overdrachtsopdrachten. Het mechanisme moet bij storingen geen opdrachten kwijtraken en niets dubbel uitvoeren, met een vertraging die acceptabel is.

Hiervoor bouw ik een testopstelling in C++ met twee programma's: 1 voor zone A en 1 voor zone B. Daarmee test ik de vier varianten (TCP, TCP met ACK en ID, MQTT QoS 1 met ID en MQTT QoS 2) onder verschillende storingen. Wat acceptabel is, bepaal ik eerst in deelvraag 2.

Met de uitkomst kan ik een advies geven over welk mechanisme en welke instellingen (time-out en heartbeat) we in het groepsproject kunnen gebruiken.

Het onderzoek is geslaagd als:

- ik per variant heb gemeten hoeveel opdrachten verloren gaan of dubbel worden uitgevoerd, en hoeveel vertraging er is;
- de metingen herhaalbaar zijn;
- ik op basis van een multicriteria-analyse één variant kan aanraden.

### 1.6 Afbakening
Binnen scope

- Berichtenverkeer tussen de coördinatiesoftware van zone A en zone B over overdrachten (verzoek, gereed, overname, voltooid).

- Vier varianten: ruwe TCP-sockets, TCP met applicatie-ACK en idempotentie, MQTT QoS 1 met idempotentie, MQTT QoS 2.

- Gesimuleerde storingen: pakketverlies, vertraging, korte en lange verbindingsonderbreking, crash en herstart van een proces.

Buiten scope

- Navigatie en locatiebepaling van robots, en padplanning.

- Keuze tussen centrale en decentrale architectuur.

- Beveiliging/encryptie (TLS) en WiFi-dekking.

- Prioritering bij drukte (de "extra uitdaging" uit de casus).