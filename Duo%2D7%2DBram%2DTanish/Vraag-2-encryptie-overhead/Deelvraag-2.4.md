      
#Deelvraag 2.4

 Hoeveel overhead wordt door integriteits-controle  veroorzaakt bij robotcommunicatie? 

Deze vraag is relevant omdat door de overhead te kwantificeren voor de verschillende integriteit methodes, het je helpt een keuze te maken met de methodes.

#Test methode:
De integriteit methoden zijn getest op de volgende manier: Een iemand gebruikt zijn laptop om de server te hosten en de ander was de cliënt en toen hebben we voor elke methode 10 keer hetzelfde bericht gestuurd en daar de gegevens van genoteerd. 
Hier kwam vervolgens een gemiddelde uit wordt gehaald die wordt gebruikt om de overhead te bepalen. 
De test resultaten zijn genoteerd als de packet groottes in bytes en de Round Trip Time (RTT) in milliseconden. 
Deze metingen zijn allemaal de zelfde manier uitgevoerd (zelfde bericht, zelfde netwerk en de zelfde opzet) om duidelijke en betrouwbare metingen te verkrijgen. 
met deze metingen wordt de overhead berekend door het resultaat van de gemiddelde van elke methode af te trekken van het gemiddelde van de meting waar geen integriteit methode op wordt toegepast.

De projecten die we hebben gemaakt hebben om dit te kunnen testen staan op de [GitHub](https://github.com/Bramvdk1/Hoofdvraag-6)
 het linkje daar voor staat vanonder. Samen met de zin die we gebruikt hebben..

####Gemiddelde overhead per integriteit methode

| Integriteit methode | overhead in ms | overhead in bytes |
| --- | --- | --- |
| HMAC-SHA256 | 3,3828 | 64 |
| CMAC | 1,9071 | 32 |
| Poly1305 | 1,9541 | 32 |

#Volledige test resultaten per integriteit methode

#### Geen integriteit methode

| meting geen integriteit | RTT in ms | package size |
| --- | --- | --- |
| Meting 1 | 7,2821 | 85 |
| Meting2 | 7,4831 | 85 |
| Meting 3 | 7,5321 | 85 |
| Meting 4 | 7,056 | 85 |
| Meting 5 | 7,3785 | 85 |
| Meting 6 | 6,6893 | 85 |
| Meting 7 | 7,9743 | 85 |
| Meting 8 | 6,7749 | 85 |
| Meting 9 | 7,6206 | 85 |
| Meting 10 | 7,5823 | 85 |
| gemiddelde | 7,33732 | 85 |
####HMCAC-SHA256

| meting HMAC-SHA256 | RTT in ms | package size |
| --- | --- | --- |
| Meting 1 | 13,2368 | 149 |
| Meting2 | 7,8886 | 149 |
| Meting 3 | 10,1922 | 149 |
| Meting 4 | 11,3044 | 149 |
| Meting 5 | 11,6852 | 149 |
| Meting 6 | 9,1748 | 149 |
| Meting 7 | 14,8215 | 149 |
| Meting 8 | 9,1838 | 149 |
| Meting 9 | 10,1949 | 149 |
| Meting 10 | 9,5189 | 149 |
| gemiddelde | 10,72011 | 149 |
####CMAC

| meting CMAC | RTT in ms | package size |
| --- | --- | --- |
| Meting 1 | 9,6453 | 117 |
| Meting2 | 12,1854 | 117 |
| Meting 3 | 9,7288 | 117 |
| Meting 4 | 8,0123 | 117 |
| Meting 5 | 8,9137 | 117 |
| Meting 6 | 9,6001 | 117 |
| Meting 7 | 9,3411 | 117 |
| Meting 8 | 7,7622 | 117 |
| Meting 9 | 8,7810 | 117 |
| Meting 10 | 8,4738 | 117 |
| gemiddelde | 9,24437 | 117 |
####Poly1305

| meting Poly1305 | RTT in ms | pakket grootte |
| --- | --- | --- |
| Meting 1 | 10,1946 | 117 |
| Meting2 | 8,1761 | 117 |
| Meting 3 | 9,1353 | 117 |
| Meting 4 | 10,8968 | 117 |
| Meting 5 | 8,5033 | 117 |
| Meting 6 | 11,0026 | 117 |
| Meting 7 | 9,112 | 117 |
| Meting 8 | 9,3234 | 117 |
| Meting 9 | 7,6712 | 117 |
| Meting 10 | 8,8993 | 117 |
| gemiddelde | 9,29146 | 117 |

gebruikte zin: 
Hello, Robot! the cheese factory in Gouda is most excelent to go eat wouldnt you say?

#github pagina:
https://github.com/Bramvdk1/Hoofdvraag-6
Bij het schrijven van deze code is ChatGPT gebruikt als hulp middel

#Verantwoording hergebruik

Deze tekst komt uit mijn onderzoeksproject van vorig jaar te vinden op: https://dev.azure.com/AvansHogeschoolAcademies/ATIxTI-2526-B2.1-OnderzoeksProject/_wiki/wikis/ATIxTI-2526-B2.1-OnderzoeksProject.wiki/19/Projectduo's