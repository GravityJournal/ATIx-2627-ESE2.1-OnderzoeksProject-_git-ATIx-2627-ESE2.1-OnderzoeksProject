# Hoofdvraag:
Wat de minimale vertraging eisen voor een draadloze noodstop?

# Deelvragen:
1. Wat is het stop afstand van de landbouw machine?
2. Wat is de remkracht van landbouw machines?
3. Welke massa hebben verschillende een landbouw machine?
4. Hoeveel heeft vertraging effect op stopafstand?

# Onderzoek opzet
Hieronder zie je het opzet van het onderzoek om aan te geven hoe ik een antwoord ga krijgen op de hoofdvraag en welke rollen de deel vragen daarin spelen.

## Deelvraag 1: Wat is het stop afstand van de landbouw machine?
De stopafstand is van belang om te weten of het landbouw voertuig op tijd stil staat. het stopafstand is een van de metingen die we gaan opslaan als meters voor de data analyse. De stopafstand word berekend door middel van de volgende formules:

- gemiddelde remkracht = 2.4 m/s^2
- stopafstand (meter) = remafstand (meter) + reactieafstand (meter)
- remafstand (meter) = massa (kg) * (snelheid (m/s) * snelheid (m/s)) / 2 * remkracht (m/s^2)
- reactieafstand (meter) = snelheid (m/s) * reactiesnelheid (seconden)

Met behulp van deze formules kunnen we in C++ de stopafstand berekenen

## Deelvraag 2: Wat is de remkracht van landbouw machines?
Om de deelvraag 1 te beantwoorden hebben we de remkracht nodig voor landbouw machines. Aangezien veel er veel soorten machines met verschillende remkrachten is er een medium gekozen voor de remkracht van verschillende landbouw machines. Vanuit het RDW apk-handboek krijgen we de remkracht van 2.4 m/s^2 voor voertuigen onder de 30km/h (bron: https://apk-handboek.rdw.nl/landbouwvoertuigen/reminrichting/remvertraging-bedrijfsrem)

## Deelvraag 3: Welke massa hebben verschillende een landbouw machine?
Het massa van landbouw voertuigen verschild per voertuig voor het onderzoek word het maximum massa gebruikt voor voertuigen met 4 assen. Dat is 50.000 kg (bron https://www.land-bouwverkeer.nl/wp-content/uploads/2021/11/Maximale-afmetingen-massas-en-aslasten-van-landbouwvoertuigen-vanaf-1-januari-2021_0.pdf)

## Deelvraag 4: Hoeveel heeft vertraging effect op stopafstand?
Dit is wat we gaan onderzoek om de hoofdvraag te beantwoorden. Dit is getest door middel van een simulatie met behulp van nep vertraging.

Er is een  c++ test programma instantie lopend op een computer. Het test programma voert een lijst uit met schillende nep vertraging waardes, massa's en snelheden. Deze waardes worden gebruikt om de stopafstand te berekenen.



# Welke data gaan we gebruiken?

# Welke data gaan we verzamelen?

# Testopstelling

# Code

# resultaten




