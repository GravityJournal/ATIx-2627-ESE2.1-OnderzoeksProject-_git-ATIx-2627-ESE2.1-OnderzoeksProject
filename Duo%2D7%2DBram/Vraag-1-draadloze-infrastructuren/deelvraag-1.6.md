#Deelvraag 1.6

Hoe verhoudt de gemeten datadoorvoer van een WiFi 4-verbinding tussen twee ESP32's zich tot de theoretische datadoorvoer van WiFi 4?
Deze vraag is relevant omdat de theoretische snelheden van WiFi niet altijd overeenkomen met de snelheden die in de praktijk worden behaald. 
Door zelf een WiFi-verbinding tussen twee ESP32's te testen die de robots zouden moeten nabootsen, kunnen we de theoretische en praktische datadoorvoer met elkaar vergelijken.
Om deze deelvraag te beantwoorden maken we een C++-programma waarmee twee ESP32's data naar elkaar kunnen versturen. We meten hoeveel data er wordt ontvangen en hoe lang dit duurt. Vervolgens berekenen we de datadoorvoer en vergelijken we deze met de theoretische snelheid van WiFi 4.

### Testopstelling

*   Eén ESP32 adafruit feather v2 wordt gebruikt als verzender.
    
*   De andere ESP32 doit devkit v1 wordt gebruikt als ontvanger.
    
*   Beide ESP32's verbinden met dezelfde WiFi-router.
    
*   De verzender verstuurt verschillende hoeveelheden data naar de ontvanger.
    

### Testresultaten

We testen verschillende hoeveelheden data om te kijken of dit invloed heeft op de behaalde datadoorvoer.

####1kb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |

####10kb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |

####100kb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |

####1mb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |


| Test | Hoeveelheid data |snelheid| verwachte snelheid| 
| --- | --- | ---| ---|
| 1 | 1 KB | x| x| 
| 2 | 10 KB | x| x| 
| 3 | 100 KB| x| x| 
| 4| 1 MB | x| x| 


Iedere test wordt meerdere keren uitgevoerd. Daarna berekenen we de gemiddelde datadoorvoer.


#github:
https://github.com/Bramvdk1/onderzoeksVraag1