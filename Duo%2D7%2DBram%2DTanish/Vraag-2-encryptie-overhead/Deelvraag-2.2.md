      
#Deelvraag 2.2
Hoeveel overhead wordt door encryptie veroorzaakt bij robotcommunicatie? 
Deze vraag is relevant omdat door de overhead te kwantificeren voor de verschillende encryptie methodes, het je helpt een keuze te maken met de methodes.

#Test methode:
De encryptie methoden zijn getest op de volgende manier: Een iemand gebruikt zijn laptop om de server te hosten en de ander was de cliënt en toen hebben we voor elke methode 10 keer hetzelfde bericht gestuurd en daar de gegevens van genoteerd.
Hier kwam vervolgens een gemiddelde uit wordt gehaald die wordt gebruikt om de overhead te bepalen.
De test resultaten zijn genoteerd als de packet groottes in bytes en de Round Trip Time (RTT) in milliseconden.
Deze metingen zijn allemaal de zelfde manier uitgevoerd (zelfde bericht, zelfde netwerk en de zelfde opzet) om duidelijke en betrouwbare metingen te verkrijgen.
met deze metingen wordt de overhead berekend door het resultaat van de gemiddelde van elke methode af te trekken van het gemiddelde van de meting waar geen encryptie methode op wordt toegepast.

De projecten die we hebben gemaakt hebben om dit te kunnen testen staan op de [GitHub](https://github.com/Bramvdk1/Hoofdvraag-6) het linkje daar voor staat vanonder. Samen met de zin die we gebruikt hebben.

####Gemiddelde overhead per encryptie methode

| Encryptie methode | overhead in ms | overhead in bytes |
| --- | --- | --- |
| AES | 34,8967 | 11 |
| ChaCha20 | 38,8586 | 12 |

#Volledige test resultaten per encryptie methode
#### Geen encryptie

| meting geen encryptie | RTT in ms | pakket grootte |
| --- | --- | --- |
| Meting 1 | 10,2221 | 85 |
| Meting2 | 34,9144 | 85 |
| Meting 3 | 30,6949 | 85 |
| Meting 4 | 13,3383 | 85 |
| Meting 5 | 8,9716 | 85 |
| Meting 6 | 41,1092 | 85 |
| Meting 7 | 21,9195 | 85 |
| Meting 8 | 31,6971 | 85 |
| Meting 9 | 37,2515 | 85 |
| Meting 10 | 12,5504 | 85 |
| gemiddelde | 24,2669 | 85 |

####AES

| meting AES  | RTT in ms | pakket grootte |
| --- | --- | --- |
| Meting 1 | 36,5333 | 96 |
| Meting2 | 85,1633 | 96 |
| Meting 3 | 81,1287 | 96 |
| Meting 4 | 70,9399 | 96 |
| Meting 5 | 35,9805 | 96 |
| Meting 6 | 10,4761 | 96 |
| Meting 7 | 25,0019 | 96 |
| Meting 8 | 34,3109 | 96 |
| Meting 9 | 100,2979 | 96 |
| Meting 10 | 111,803 | 96 |
| gemiddelde | 59,16355 | 96 |

####ChaCha20

| meting ChaCha20 | RTT in ms | pakket grootte |
| --- | --- | --- |
| Meting 1 | 41,2923 | 97 |
| Meting2 | 32,7234 | 97 |
| Meting 3 | 30,7247 | 97 |
| Meting 4 | 115,9784 | 97 |
| Meting 5 | 37,0586 | 97 |
| Meting 6 | 79,3333 | 97 |
| Meting 7 | 75,9856 | 97 |
| Meting 8 | 84,0138 | 97 |
| Meting 9 | 53,8700 | 97 |
| Meting 10 | 80,2748 | 97 |
| gemmidelde | 63,12549 | 97 |

gebruikte zin:
Hello, Robot! the cheese factory in Gouda is most excelent to go eat wouldnt you say?

GitHub:
https://github.com/Bramvdk1/Hoofdvraag-6
Bij het schrijven van deze code is ChatGPT gebruikt als hulp middel

#Verantwoording hergebruik

Deze tekst komt uit mijn onderzoeksproject van vorig jaar te vinden op: https://dev.azure.com/AvansHogeschoolAcademies/ATIxTI-2526-B2.1-OnderzoeksProject/_wiki/wikis/ATIxTI-2526-B2.1-OnderzoeksProject.wiki/19/Projectduo's
Op de figuur na waar het gemiddelde van de drie methoden naast elkaar te zien zijn. 