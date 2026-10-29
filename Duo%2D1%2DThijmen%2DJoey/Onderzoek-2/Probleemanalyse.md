# 1. Casus probleemcontext
Het doel van het project is om bodemverdichting op landbouwakkers te verminderen door middel van robotisering. Hiervoor wordt een autonome robotvloot ontwikkeld die het oogstproces zo efficiënt mogelijk moet uitvoeren. Hieronder zie je de rollen van de voertuigen en operators.

## De robotvloot bestaat uit twee verschillende voertuigen en in totaal drie voertuigen:
*   **Eén rooier:** oogst de gewassen en rijdt hiervoor heen en weer over de akker. En heeft een buffer in de wagen zitten. En aan het einde van iedere rij keert de rooier op de kopakker.
*   **Twee overslagwagens:** vervoeren de geoogste gewassen van de rooier naar het lospunt en rijden vervolgens terug naar de rooier.

## Ook maakt de robot vloot gebruik van twee operators:
*   **Rooier operator:** bepaalt de snelheid van de overslagwagen en rooier tijdens de momenten dat ze naast elkaar rijden. De operator keert ook de rooier op keerpunten van de akker.
*   **Overslagwagen operator:** De operator krijgt controle over de overslagwagen tijdens het ontladen van aardappels. Hiervoor kan hij de snelheid en richting van de wagen aanpassen.

Het probleem wat we met dit onderzoek willen oplossen is hoe de robots hun locaties kunnen achterhalen door middel van het netwerk infrastructuur. Het is momenteel onduidelijk welke infrastructuur technologieën geschikt zijn voor onze situatie.

---

# 2. Belang
Om bodemverdichting te beperken, moeten de overslagwagens zo efficiënt mogelijk over de akker rijden. Hierbij is het belangrijk dat ze niet meerdere keren over dezelfde plekken rijden, met uitzondering van de kopakker.
Om dit mogelijk te maken, moeten de robots onderling informatie kunnen uitwisselen en hun bewegingen op elkaar afstemmen. Om dit te kunnen realiseren moeten we accurate locaties hebben van de robots, maar ook is het van belang dat de locaties niet verouderd zijn als ze aankomen aangezien machines autonoom naast en langs elkaar werken.

---

# 3. Literatuuronderzoek
Voor dit probleem zijn de volgende technologi