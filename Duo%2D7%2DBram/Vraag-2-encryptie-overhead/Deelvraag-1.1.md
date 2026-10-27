      
#Deelvraag 1.1:
Welke encryptie methodes worden in 2025 gebruikt bij robotcommunicatie? 

##relevantie:
Deze vraag is relevant omdat je niet de overhead kan meten zonder te weten welke methodes je moet gebruiken.

#onderzoeksresultaten
Tijdens ons onderzoek naar encryptiemethoden zijn de volgende methoden naar voren gekomen:

##encryptie methoden:

###AES
AES is een symmetrische encryptie methode. Het is snel, efficiënt en wordt breed ondersteund in hardware, waardoor het weinig rekenkracht verbruikt.

###ChaCha20
ChaCha20 is net zoals AES symmetrisch
Het werkt snel in software en biedt sterke beveiliging met lage latency. 
ChaCha20 wordt vaak gecombineerd met Poly1305 (daarover meer in ons onderzoek over integriteit methoden).

###RSA
RSA is een asymmetrische encryptie methode.
Het is wat trager dan symmetrische methoden maar vooral sterk in authenticatie en veilige sleuteluitwisseling.
We zullen later in ons onderzoek RSA niet testen aangezien het trager en zwaarder is aangezien het meer rekenkracht gebruikt dan de symmetrische methoden.

#bronnen
ChaCha20:
https://ieeexplore.ieee.org/abstract/document/7927078

RSA:
https://ieeexplore.ieee.org/abstract/document/9336800?casa_token=sIo3euOug4YAAAAA:Z3vxY3rIk4up3EdPs6teDhbu7TfAsWxoE-IC4bjsLkRs3_u62vAamks0AC9QbzcClOOWiUxM4aw28Pg
https://ieeexplore.ieee.org/abstract/document/7927078

AES:
https://ieeexplore.ieee.org/abstract/document/9336800?casa_token=sIo3euOug4YAAAAA:Z3vxY3rIk4up3EdPs6teDhbu7TfAsWxoE-IC4bjsLkRs3_u62vAamks0AC9QbzcClOOWiUxM4aw28Pg

extra:
https://journals.sagepub.com/doi/full/10.5772/57433
https://www.prebes.be/nl/nieuws/2025/05/updates-in-de-normen-over-robots-ISO10218-1-en-2
https://www.sentinelone.com/nl/cybersecurity-101/cybersecurity/what-is-encryption/#veelvoorkomende-soorten-versleuteling