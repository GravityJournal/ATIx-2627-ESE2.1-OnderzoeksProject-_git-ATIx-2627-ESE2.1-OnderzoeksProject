      
#Deelvraag 2.5
Welke encryptie veroorzaakt de kleinste overhead bij robotcommunicatie? 

Deze vraag is relevant omdat het helpt bij het kiezen van een efficiënt encryptie protocol.

---
Om deze deelvraag te beantwoorden kijken we even naar de test resultaten van deelvraag 2 en trekken we met die gegevens een conclusie op het onderzoek en beantwoorden we deelvraag 5

#Test resulaten

| Encryptie methode | overhead in ms | overhead in bytes |
| --- | --- | --- |
| AES | 34,8967 | 11 |
| ChaCha20 | 38,8586 | 12 |

#Conclusie
Uit de bovenstaande gegevens is te concluderen dat AES de Encryptie methode is met de
laagste overhead in beide tijd (
3,9619 ms sneller) en in encryptie grootte (1 byte lichter).
Het gaat hier niet om hele grote verschillen maar er is wel duidelijk te zien dat AES sneller en lichter is dan ChaCha20 en daarom voor ons de betere encryptie methode

#Verantwoording hergebruik

Deze tekst komt uit mijn onderzoeksproject van vorig jaar te vinden op: https://dev.azure.com/AvansHogeschoolAcademies/ATIxTI-2526-B2.1-OnderzoeksProject/_wiki/wikis/ATIxTI-2526-B2.1-OnderzoeksProject.wiki/19/Projectduo's