# Op welke manier moet de communicatie veilig zijn?

Bij communicatiebeveiliging worden drie vaste beveiligingsdoelen onderscheiden: confidentiality (vertrouwelijkheid), integrity (integriteit) en availability (beschikbaarheid). Voor dit project bekijken we per categorie wat belangrijk is, aan de hand van de mogelijke gevolgen wanneer de betreffende beveiligingseigenschap niet wordt gewaarborgd.
| Categorie | Consequentie | Schade | Prioriteit |
| --- | --- | --- | --- |
| **Vertrouwelijkheid** | - Mensen kunnen zien waar een machine zich bevindt.  <br>- Mensen kunnen zien wat een machine doet. | NA | Laag |
| **Integriteit** | - De overslagwagen kan een verkeerde locatie ontvangen.  <br>- De overslagwagen kan een verkeerde snelheidsinstructie ontvangen.  <br>- De operatorinterface kan onjuiste informatie weergeven. | - De overslagwagen komt niet op de juiste locatie aan.  <br>- De overslagwagen botst tegen de rooier.  <br>- De overslagwagen rijdt van de rooier weg.  <br>- De operator heeft weinig tot geen inzicht in de situatie. | Zeer hoog |
| **Beschikbaarheid** | - De overslagwagen reageert niet.  <br>- De operatorinterface reageert niet. | - De overslagwagen komt niet op de juiste locatie aan.  <br>- De operator heeft weinig tot geen inzicht in de situatie. | Hoog |

<br>

## Conclusie

Op basis van het literatuuronderzoek moet de nadruk bij de communicatiebeveiliging liggen op **integriteit en beschikbaarheid**. Deze eigenschappen zijn van groot belang om ervoor te zorgen dat de machines de juiste instructies ontvangen en dat de operator over actuele informatie beschikt.

_Voor dit onderzoek is gebruikgemaakt van de bronnen [1] en [2]._


# Op welke manier beveilig je de communicatie van het systeem?

Vertrouwelijkheid, integriteit en beschikbaarheid kunnen op verschillende manieren worden toegepast op bestaande systemen [1][2][3]. Vertrouwelijkheid wordt in dit onderzoek buiten beschouwing gelaten vanwege de lage impact ervan binnen dit project.

## Integriteit

Volgens de workshop "Encryption - Hashing - Certificates" is het gebruik van een Message Authentication Code (MAC) een geschikte methode om de integriteit van berichten te waarborgen.
**Benodigdheden:**
*   $s$ = een gedeelde geheime sleutel
*   $b_{\text{origineel}}$ = het oorspronkelijke bericht
*   $M$ = een MAC-functie
*   $v_{\text{MAC}}$ = de berekende MAC-waarde
*   $v'_{\text{MAC}}$ = de verwachte MAC-waarde

**Verzenden:**
1.  Stel het bericht samen: 
`b_original`.
    
2.  Bereken de MAC-waarde: 
$v_{\text{MAC}} = M(s, b_{\text{origineel}})$
    
3.  Verstuur het oorspronkelijke bericht samen met de MAC-waarde: 
`(b_original, v_mac)`.
    
<br>

**Ontvangen:**
1.  Ontvang het oorspronkelijke bericht en de bijbehorende MAC-waarde.
    
2.  Bereken de verwachte MAC-waarde met dezelfde geheime sleutel:
    $v'_{\text{MAC}} = M(s, b_{\text{origineel}})$
    
3.  Vergelijk de ontvangen MAC-waarde met de berekende waarde. Als beide waarden overeenkomen, wordt het bericht geaccepteerd. Als de waarden niet overeenkomen, wordt het bericht afgewezen.
    
De MAC maakt het mogelijk om te controleren of een bericht is gewijzigd en of het afkomstig is van een partij die over de juiste geheime sleutel beschikt. Een aanvaller zonder deze sleutel kan niet zomaar een geldige MAC-waarde voor een aangepast bericht genereren.

## Beschikbaarheid

De aanbevelingen uit de literatuur over beschikbaarheid zijn minder specifiek en bestaan voornamelijk uit algemene maatregelen, zoals hardwareonderhoud, het bijwerken van systemen, het opstellen van een faalplan en het vermijden van knelpunten (_bottlenecks_) [2].
Voor de communicatie-infrastructuur zijn vooral het vermijden van knelpunten en het opstellen van een faalplan relevant. Door knelpunten te vermijden, wordt het risico verkleind dat een onderdeel van het systeem de communicatie vertraagt of blokkeert. Een faalplan helpt daarnaast om storingen tijdig te signaleren en passende maatregelen te nemen wanneer de communicatie uitvalt.

## Conclusie

Op basis van het literatuuronderzoek concluderen we dat **MAC's geschikt zijn om de integriteit van de communicatie te waarborgen**. Voor de beschikbaarheid zijn **goed onderhoud, het vermijden van knelpunten en het opstellen van een faalplan** belangrijke aandachtspunten.
Bij de verdere keuzes voor de communicatie-infrastructuur moet ook rekening worden gehouden met zowel integriteit als beschikbaarheid, aangezien deze beveiligingseigenschappen een hoge prioriteit hebben binnen het project.

_Voor dit onderzoek is gebruikgemaakt van de bronnen [1], [2] en [3]._

<br>

* * *

# Bronnen

[1] “Encryption - Hashing - Certificates - ICT-B ESE2.1 Robot Fleet 2026-27 P1-P2 Breda.” [https://brightspace.avans.nl/d2l/le/lessons/308932/topics/2074678\](https://brightspace.avans.nl/d2l/le/lessons/308932/topics/2074678%5C)  
[2] "GeeksforGeeks, “Understanding CIA triad,” _GeeksforGeeks_, Jun. 29, 2026. [https://www.geeksforgeeks.org/cybersecurity/the-cia-triad-in-cryptography/"](https://www.geeksforgeeks.org/cybersecurity/the-cia-triad-in-cryptography/%22)  
[3] GeeksforGeeks, “Working of message authentication code,” _GeeksforGeeks_, Apr. 08, 2026. [https://www.geeksforgeeks.org/computer-networks/how-message-authentication-code-works/](https://www.geeksforgeeks.org/computer-networks/how-message-authentication-code-works/)










