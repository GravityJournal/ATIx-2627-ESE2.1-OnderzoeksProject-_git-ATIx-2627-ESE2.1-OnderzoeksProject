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
Om bodemverdichting te beperken, moeten de overslagwagens zo efficiënt mogelijk over de akker rijden. Hierbij is het belangrijk dat ze niet meerdere keren over dezelfde plekken rijden, met uitzondering van de kopakker. Om dit mogelijk te maken, moeten de robots onderling informatie kunnen uitwisselen en hun bewegingen op elkaar afstemmen. Om dit te kunnen realiseren moeten we accurate locaties hebben van de robots, maar ook is het van belang dat de locaties niet verouderd zijn als ze aankomen aangezien machines autonoom naast en langs elkaar werken.

---

# 3. Literatuuronderzoek
Om locatie te kunnen bepalen met netwerk infrastructuur zijn meerdere technologieën beschikbaar en mogelijk zoals: Wifi, LoRa, 4G, 4G of bluetooth. Enkele van deze kunnen we al afstrepen bijvoorbeeld wifi heeft een ideale range van 50 meter (Bron 1). Wifi heeft de mogelijkheid voor grotere range doormiddel van gebruik van directional antennas, maar dat extra werk en hardware als er al een bestaand 4G/5G netwerk bestaad. Bluetooth kunnen we ook al afstrepen voor gelijke redenen en heeft maar een range van 10 meter (Bron 2). Voor de afstanden gaan we vanuit dat het alleen toegepast word in nederland met een maximale akker groote van 7.62 hectare (Bron 3) per perceel wat een akker groote geeft van 300 x 254 meter. Dus dit geeft ons de mogelijkheden tussen LoRa, 4G en 5G.

Ik ga nu onderzoeken of LoRa geschikt is voor ons hiervoor. Ik weet toevallig dat er voor radio protocollen zoals dit bepaalde wetgevingen zijn die de toepassing hiervan voor ons kan beperken. LoRa gebruikt de frequencyband van 863–870/873 MHz (Bron 5) dus heeft een duty cycle van 0.1% (Bron 6). Ik heb berekend met 3600 seconden in een uur maal 0.001 (de 0.1% duty cycle in seconden) dat geeft 3.6 seconden verzend tijd per uur. Dit kan ook nog verschillen tussen korte en lange afstanden omdat langere afstanden meer tijd kost en meer van het budget van 3.6 seconden haalt. Door dit kunnen realtime communicatie en positie bepaling niet realiseren.

Om erachter te komen welke technologie tussen 4G en 5G voor ons het best geschrikt is stellen we de volgende vragen per techniek:

*   Hoeveel data bits/s kunnen we uitwisslen tussen de robots?
    *   Hoeveel data gaan we versturen?
    *   Welke data gaan we versturen?
<br>
*   Hoeveel vertraging in ms vind er plaats tussen sturen en ontvangen?
    *   Hoeveel en wat voor impact heeft vertraging van de locatie informatie
    *   Wat is maximale vertraging die we kunnen hebben
    *   Kunnen we vertraging opvangen met behulp van locatie voorspellingen?
<br>
*   Hoeveel dekking is er in nederland?
<br>
*   Kan iemand het infrastructuur hacken en schade aanrichten?
