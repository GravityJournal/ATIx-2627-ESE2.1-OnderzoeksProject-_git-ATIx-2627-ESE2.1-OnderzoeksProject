      
#Hoofdvraag:
**Hoe groot is de overhead van encryptie en integriteitscontrole op de netwerkprestaties bij robotcommunicatie?**

---
om de hoofdvraag te beantwoorden moeten we eerst kijken naar de deelvragen het begint met onderzoek doen naar verschillende encryptie en integriteit methoden en deze vervolgens te testen en deze testen te concluderen.

Voor de hoofdvraag te beantwoorden is er geen vast antwoord aangezien metingen en encryptie en integriteitscontrole afhangen van de daarvoor gebruikte methoden.

De lichtst mogelijke overhead volgens ons onderzoek is het gebruik van
AES voor de encryptie
CMAC Voor de integriteits controle

Hieronder zie je een tabel met daar in de gegevens van AES en CMAC en wat de overhead zou zijn als je ze samen zou gebruiken.

| Methode | overhead in ms | overhead in bytes |
| --- | --- | --- |
| AES | 34,8967 | 11 |
| CMAC | 1,9071 | 32 |
| AES-CMAC |36,8038 | 43 bytes|

Dus de totale overhead bij robot communicatie bij AES-CMAC zou in tijd 36,8038 milliseconden en in pakket grootte 43 bytes.