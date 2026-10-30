# 2b. Onderzoeksaanpak

## Onderzoeksdoel

Het doel van dit onderzoek is om te bepalen welke communicatiemethode het meest geschikt is voor het betrouwbaar uitwisselen van overdrachtsinformatie tussen twee afzonderlijke robotvloten. Hiervoor worden TCP en MQTT onderzocht en met elkaar vergeleken. De resultaten moeten helpen bij het maken van een onderbouwde keuze voor de communicatie tussen de twee hygiënezones van Viscon Group.

## Deelvraag 1 – Eigenschappen en verschillen van TCP en MQTT

**Onderzoeksmethode:** Literatuuronderzoek.

**Aanpak:**

Voor deze deelvraag wordt informatie verzameld over de werking en eigenschappen van TCP en MQTT. Hiervoor worden technische documentatie, officiële documentatie en relevante artikelen geraadpleegd.

De informatie wordt gebruikt om de belangrijkste verschillen tussen beide communicatiemethoden inzichtelijk te maken. Hierbij wordt onder andere gekeken naar de betrouwbaarheid, berichtbevestiging, foutafhandeling en de complexiteit van de implementatie.

**Benodigde middelen:**
- Computer met internetverbinding.
- Officiële documentatie van TCP en MQTT.
- Technische artikelen en onderzoeksbronnen.
- Azure DevOps Wiki voor het vastleggen van informatie.

**Onderbouwing:**

Literatuuronderzoek is geschikt om eerst inzicht te krijgen in de werking en eigenschappen van beide communicatiemethoden. Deze kennis vormt de basis voor de verdere vergelijking.

## Deelvraag 2 – Omgaan met netwerkproblemen en systeemuitval

**Onderzoeksmethode:** Literatuuronderzoek en praktijkgericht onderzoek.

**Aanpak:**

Voor deze deelvraag wordt onderzocht hoe TCP en MQTT reageren op problemen tijdens de communicatie. Hiervoor wordt eerst bestaande documentatie geraadpleegd. Vervolgens worden de mogelijkheden om met netwerkproblemen en systeemuitval om te gaan meegenomen in het ontwerp van het prototype.

Er wordt gekeken naar situaties zoals een tijdelijke verbindingsonderbreking, netwerkvertraging en het opnieuw opstarten van een systeem. Hierbij ligt de nadruk op het herstellen van de communicatie en het betrouwbaar verwerken van overdrachtsberichten.

**Benodigde middelen:**
- Computer.
- Technische documentatie van TCP en MQTT.
- C++ ontwikkelomgeving.
- TCP- en MQTT-softwarebibliotheken.
- Software voor het ontwikkelen van het prototype.

**Onderbouwing:**

Door literatuuronderzoek te combineren met praktijkgericht onderzoek kan worden onderzocht hoe de communicatiemethoden zich gedragen bij problemen. Hierdoor wordt niet alleen gekeken naar de theoretische werking, maar ook naar de toepassing binnen de casus.

## Deelvraag 3 – Vergelijken van TCP en MQTT

**Onderzoeksmethode:** Prototypeonderzoek en vergelijkend onderzoek.

**Aanpak:**

Voor deze deelvraag wordt een prototype ontwikkeld waarin twee afzonderlijke systemen met elkaar communiceren. Deze systemen stellen de twee robotvloten in de verschillende hygiënezones voor.

Het prototype wordt gebruikt om overdrachtsberichten tussen beide systemen uit te wisselen. Hierbij worden TCP en MQTT toegepast, zodat beide communicatiemethoden met elkaar kunnen worden vergeleken.

De vergelijking richt zich op de betrouwbaarheid van de communicatie, de snelheid waarmee berichten worden uitgewisseld en de manier waarop beide methoden omgaan met verbindingsproblemen. Ook wordt gekeken naar de complexiteit van de implementatie.

De bevindingen uit het prototype worden gebruikt om te bepalen welke communicatiemethode het beste aansluit bij de eisen van de casus.

**Benodigde middelen:**
- Computer.
- C++ ontwikkelomgeving.
- TCP sockets.
- MQTT-broker en MQTT-clientbibliotheek.
- Prototype met twee afzonderlijke systemen.
- Software voor het vastleggen en bekijken van testgegevens.

**Onderbouwing:**

Prototypeonderzoek is geschikt omdat de communicatiemethoden binnen een nagebootste situatie kunnen worden toegepast. Door beide methoden op dezelfde manier te onderzoeken, kunnen de verschillen inzichtelijk worden gemaakt. Dit helpt bij het maken van een onderbouwde keuze.

## Prototype

Voor het onderzoek wordt een prototype ontwikkeld dat de communicatie tussen twee robotvloten nabootst. Het prototype bestaat uit twee afzonderlijke systemen die de hygiënezones A en B voorstellen.

Het eerste systeem kan een overdrachtsverzoek versturen naar het tweede systeem. Het tweede systeem ontvangt het verzoek en kan hierop reageren met een bevestiging. Vervolgens kan de status van de overdracht worden teruggekoppeld.

Het prototype richt zich uitsluitend op de communicatie tussen de systemen. De fysieke robots, navigatie en het mechanische overdrachtspunt vallen buiten de scope van het onderzoek.

Binnen het prototype worden zowel TCP als MQTT toegepast. Hierdoor kunnen beide communicatiemethoden binnen dezelfde onderzoeksomgeving worden vergeleken.

## Betrouwbaarheid en validiteit

Om de betrouwbaarheid van het onderzoek te ondersteunen, worden beide communicatiemethoden onder vergelijkbare omstandigheden onderzocht. De gebruikte instellingen en onderzoeksmethoden worden vastgelegd, zodat de vergelijking zo eerlijk mogelijk verloopt.

De validiteit wordt ondersteund door de onderzoeksmethoden af te stemmen op de hoofdvraag en de praktijksituatie van Viscon Group. Het prototype richt zich specifiek op de communicatie tussen twee afzonderlijke robotvloten en de overdracht van berichten tussen deze systemen.

## Planning

| Onderdeel | Activiteit |
|---|---|
| 1 | Literatuuronderzoek naar TCP en MQTT |
| 2 | Onderzoeks- en prototypeontwerp |
| 3 | Ontwikkelen van het prototype |
| 4 | Onderzoeken van beide communicatiemethoden |
| 5 | Vergelijken en analyseren van de bevindingen |
| 6 | Beantwoorden van de deelvragen |
| 7 | Beantwoorden van de hoofdvraag en afronden van het onderzoeksverslag |

## Bronnen

- MQTT – Officiële website: https://mqtt.org/
- OASIS – MQTT Version 5.0: https://docs.oasis-open.org/mqtt/mqtt/v5.0/
- IETF – RFC 793 (Transmission Control Protocol): https://www.rfc-editor.org/rfc/rfc793
- IETF – RFC 9293 (Transmission Control Protocol): https://www.rfc-editor.org/rfc/rfc9293
- VDA – VDA 5050: https://www.vda.de/en/topics/automotive-industry/vda-5050

## Gebruik van AI

Tijdens het opstellen van de onderzoeksvragen en onderzoeksaanpak is AI gebruikt als hulpmiddel. Het is ingezet om de hoofdvraag, deelvragen en mogelijke onderzoeksmethoden te formuleren niet te genereren. De voorgestelde inhoud is aangepast aan de casus van Viscon Group en wordt door de onderzoekers gecontroleerd.