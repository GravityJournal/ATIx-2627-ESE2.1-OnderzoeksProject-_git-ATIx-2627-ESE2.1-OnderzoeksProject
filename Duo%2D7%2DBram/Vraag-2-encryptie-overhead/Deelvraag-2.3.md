      
#Deelvraag 2.3:
Welke integriteit methodes worden in 2025 gebruikt bij robot communicatie?

##relevantie:
Deze vraag is relevant omdat je niet de overhead kan meten zonder te weten welke methodes je moet gebruiken.

#onderzoeksresultaten
Tijdens ons onderzoek naar eintegriteit methoden zijn de volgende methoden naar voren gekomen:

##integriteit methoden

Het is belangrijk dat integriteit methodes lichtgewicht en efficïent zijn zodat robots met beperkte rekenkracht en energie ze kunnen gebruiken, zoals een robot met een raspberry pi single board computer. Deze methodes moeten real-time prestaties kunnen leveren met weinig tot geen vertraging, sterke integriteitgaranties bieden, sterk beveiligd zijn tegen aanvallen en schaalbaarheid hebben in een multi-robot netwerk (Range‑Based Multi‑Robot Integrity Monitoring, 2025).

### HMAC‑SHA256
HMAC‑SHA256 wordt meegenomen om te testen omdat het berichten sterke integriteitsgaranties geeft, het sneller is in software te implementeren dan oudere methodes zoals DES, de library code breed inzetbaar is en het gebruik ervan laat zien dat netwerkprestaties verbeteren, met een hogere throughput en een betere packet delivery ratio (Implementation of HMAC‑SHA256 algorithm for hybrid routing protocols in MANETs, 2015).

Dit is een integriteit‑ en authenticiteitsmethode die een bericht samen met een secret key hashed met de hashfunctie SHA‑256. Dit creëert een vaste 256‑bit hash. Dit resultaat wordt vervolgens nog een keer gehashed met dezelfde secret key. Zo krijg je een inner hash met de inner padding (ipad) en een outer hash met de outer padding (opad). Dit vormt een HMAC die de integriteit en authenticiteit garandeert (Implementation of HMAC‑SHA256 algorithm for hybrid routing protocols in MANETs, 2015).

### CMAC
CMAC, wat staat voor Cipher‑based Message Authentication Code, wordt meegenomen om te testen omdat het berichten voorziet van sterke integriteits‑ en authenticiteitsgaranties (Dworkin, 2015; Poovendran, Lee, & Iwata, 2006). Het algoritme is gebaseerd op de AES‑blokcipher waardoor het efficiënt werkt in zowel software als hardware omgevingen. CMAC is gestandaardiseerd door NIST en IETF, waardoor het geschikt is voor allerlei soorten toepassingen (Dworkin, 2015). Door de vaste lengte van de gegenereerde MAC, meestal rond de 128 bits, daardoor blijft de overhead laag en werkt het goed in systemen waar compacte en betrouwbare communicatie belangrijk is (Poovendran et al., 2006).

CMAC behoudt de integriteit en authenticiteit van berichten door het bericht samen met een geheime sleutel te verwerken via AES in CBC-mode. Hierbij is het belangrijk te vermelden dat AES wordt gebruikt voor encryptie en in CMAC alleen dient als rekencomponent om de Message Authentication Code te genereren. Het bericht wordt blok voor blok verwerkt en gecombineerd, waarna het resultaat een vaste 128‑bit code vormt. Elke wijziging in het bericht of sleutel leidt tot een totaal andere MAC, waardoor de integriteit en authenticiteit van berichten gegarandeerd wordt (Dworkin, 2015; Poovendran et al., 2006).

### Poly1305
Poly1305 is gekozen voor de test omdat het een snelle en efficiënte manier is om berichten te beveiligen tegen wijzigingen. De methode werkt snel, vraagt weinig van de processor en geheugen en houdt de integriteit van data goed in stand. Daardoor is het geschikt voor kleine systemen met beperkte rekenkracht, zoals robots die draaien op een Raspberry Pi (Bernstein, 2005).
Omdat de code altijd 16 bytes lang is, blijft de extra belasting klein en is de methode geschikt voor compacte en betrouwbare communicatie (Bernstein, 2005).

Om de integriteit toe te passen met Poly1305 wordt een bericht met een 32‑byte sleutel verwerkt en wordt een vaste 16‑byte tag gegenereerd. Die tag werkt als een digitale handtekening. Zodra er iets in het bericht verandert, klopt de tag niet meer. Een sleutel mag maar één keer gebruikt worden. Als dezelfde sleutel opnieuw wordt ingezet, verliest de tag zijn betrouwbaarheid en kan de integriteit niet meer gegarandeerd worden.

#bronnen

_Range-Based Multi-Robot Integrity Monitoring For Cyberattacks and Faults: An Anchor-Free Approach_. (2025, 1 maart). IEEE Journals & Magazine | IEEE Xplore. Geraadpleegd op 24 november 2025, van https://ieeexplore.ieee.org/document/10854616

HMAC-SHA256:
_Implementation of HMAC-SHA256 algorithm for hybrid routing protocols in MANETs_. (2015, januari 1). IEEE Conference Publication | IEEE Xplore. Geraadpleegd op 24 november 2025, van https://ieeexplore.ieee.org/abstract/document/7060558?casa_token=tmq_E04WwnIAAAAA:uMkHd-lQHwgl5uPGtedfntaVaaTb2HezR8s5W6fYSU3B_fr0mcdcClAKi2AYbZUGbYzL5eL50edacg

CMAC:
Dworkin, M., Computer Security Division, Information Technology Laboratory, U.S. Department of Commerce, & National Institute of Standards and Technology. (2005). _NIST Special Publication 800-38B Recommendation for Block Cipher Modes of Operation: The CMAC Mode for Authentication_. Geraadpleegd op 25 november 2025, van https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-38b.pdf

Poovendran, R., Lee, J., & Iwata, T. (2006d). _The AES-CMAC algorithm_.  https://doi.org/10.17487/rfc4493

Poly1305:
Bernstein, D. J. (2005b). The Poly1305-AES Message-Authentication Code. In _Lecture notes in computer science_ (pp. 32–49). Geraadpleegd op 24 november 2025, van https://doi.org/10.1007/11502760_3