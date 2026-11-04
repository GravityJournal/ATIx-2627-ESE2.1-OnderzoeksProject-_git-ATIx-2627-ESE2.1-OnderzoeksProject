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
    
De esp32 gebruiken wifi 4 en een frequentie van 2.4GHz de maximale snelheid hiervoor is 150mbps
### Testresultaten

We testen verschillende hoeveelheden data om te kijken of dit invloed heeft op de behaalde datadoorvoer en pakken van elke meting het gemiddelde.

####1kb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |
|gem||
####10kb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |
|gem||
####100kb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |
|gem||
####1mb:
| Test | snelheid |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 | |
| 4| |
| 5| |
|gem||

| Test | Hoeveelheid data |snelheid|
| --- | --- | ---|
| 1 | 1 KB | x|
| 2 | 10 KB | x|
| 3 | 100 KB| x|
| 4| 1 MB | x|



#bronnen
datasheet espressif:
https://documentation.espressif.com/esp32_datasheet_en.html

#github:
https://github.com/Bramvdk1/onderzoeksVraag1