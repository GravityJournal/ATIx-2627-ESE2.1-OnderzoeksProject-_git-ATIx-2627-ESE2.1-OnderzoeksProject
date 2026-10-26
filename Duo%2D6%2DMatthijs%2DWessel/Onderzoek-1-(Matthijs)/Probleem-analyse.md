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

### 1.4 Literature gap

### 1.5 Doelstelling

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