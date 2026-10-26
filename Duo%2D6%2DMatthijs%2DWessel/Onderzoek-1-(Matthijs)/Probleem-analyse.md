## 1. Probleem analyse
### 1.1 Probleemcontext
Binnen de casus moeten producten tussen 2 zones worden verplaatst. Elke zone heeft een eigen robotvloot, en robots mogen de zonegrens nooit passeren. Goederen (bijv. pallets, kratten) gaan via een overdrachtspunt/ sluis van zone A naar zone B, en lege ladingdragers gaan weer terug.

Daarvoor moeten de beide zones met elkaar kunnen praten. Denk aan opdrachten zoals: "Robot A moet naar de sluis voor overdracht met Robot B". In de randvoorwaarde van de casus staat dat tijdens een storing of communicatie-uitval het systeem in een veilige toestand moet terechtkomen, zonder dat opdrachten verloren gaan of dubbel worden uitgevoerd.

Voor de veilige communicatie is nog niet bepaald met welk communicatiemechanisme gewerkt moet worden. Dit onderzoek werkt dit stukje van de infrastructuur uit.