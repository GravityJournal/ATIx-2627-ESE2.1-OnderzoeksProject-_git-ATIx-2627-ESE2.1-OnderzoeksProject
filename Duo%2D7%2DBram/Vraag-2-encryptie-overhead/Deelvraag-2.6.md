      
#Deelvraag 2.6
Welke integriteits-controle veroorzaakt de kleinste overhead bij robot communicatie? 

Deze vraag is relevant omdat het helpt bij het kiezen van een efficiënt integriteit protocol.
---
Om deze deelvraag te beantwoorden kijken we even naar de test resultaten van deelvraag 4 en trekken we met die gegevens een conclusie op het onderzoek en daarmee beantwoorden we deelvraag 6

####Gemiddelde overhead per integriteit methode

| Integriteit methode | overhead in ms | overhead in bytes |
| --- | --- | --- |
| HMAC-SHA256 | 3,3828 | 64 |
| CMAC | 1,9071 | 32 |
| Poly1305 | 1,9541 | 32 |

#Conclusie
Uit de bovenstaande gegevens is te concluderen dat CMAC de snelste integriteit methode is aangezien het 0.0470ms sneller dan poly1305 en 1.4757 ms sneller dan HMAC-SHA256. qua overhead in bytes is het 32 bytes lichter dan HMAC-SHA256 en even zwaar als Poly1305.
Het gaat tussen Poly1305 en CMAC om een erg klein verschil in snelheid maar omdat er toch een verschil is denken wij dat CMAC de beste integriteit methode is.

#Verantwoording hergebruik

Deze tekst komt uit mijn onderzoeksproject van vorig jaar te vinden op: https://dev.azure.com/AvansHogeschoolAcademies/ATIxTI-2526-B2.1-OnderzoeksProject/_wiki/wikis/ATIxTI-2526-B2.1-OnderzoeksProject.wiki/19/Projectduo's