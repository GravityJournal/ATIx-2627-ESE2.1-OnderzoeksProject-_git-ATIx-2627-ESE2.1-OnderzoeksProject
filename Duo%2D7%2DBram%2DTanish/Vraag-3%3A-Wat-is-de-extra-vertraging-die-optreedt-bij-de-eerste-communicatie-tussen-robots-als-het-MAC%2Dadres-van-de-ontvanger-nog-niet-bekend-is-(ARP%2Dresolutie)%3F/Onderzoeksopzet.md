Inleiding
---------

Op deze pagina kunt u de informatie vinden over de onderzoeksvraag en de bijbehorende deelvragen. Ook kun u hier de opzet van het onderzoek vinden.

1. Onderzoeksvraag
------------------

**Wat is de extra vertraging die optreedt bij de eerste communicatie tussen robots als het MAC-adres van de ontvanger nog niet bekend is (ARP-resolutie)?**
_Controle:_ De vraag is specifiek, concreet en geformuleerd als een open vraag die empirisch te meten is.

2. Deelvragen (per hoofdvraag)
------------------------------

### Deelvraag 1: ARP Mechanisme

**Wat doet het ARP-protocol wanneer het MAC-adres van de ontvanger nog niet bekend is?**
| Vraag | Toelichting |
| --- | --- |
| _Welke kleinere vragen helpen?_ | Hoe werkt ARP bij adresopslag? Wat is een ARP-request/answer? |
| _Welke kennis heb ik al?_ | Basis begrip van IP/MAC adressering. |
| _Welke inzichten ontbreken?_ | Exacte werking en timing van ARP bij eerste contact. |
| _Zijn deelvragen specifiek?_ | Ja, focust op mechanisme zonder metingen. |
| _Geven ze samen antwoord?_ | Deelvraag 1 + 2 = volledige beeld ARP vertraging. |
| _Wat ontbreekt nog?_ | Praktische meting van de timing (zie deelvraag 2). |
**Waarom relevant:** Voordat vertraging kan worden gemeten, moet het onderliggende protocol begrepen zijn om fouten te interpreteren.

### Deelvraag 2: Vertraging Vergelijking

**Wat is het verschil in tijd tussen de eerste communicatie en verdere communicatie tussen robots?**
| Vraag | Toelichting |
| --- | --- |
| _Welke kleinere vragen helpen?_ | Hoe lang duurt een ARP-request/answer? Wat is baseline latency zonder ARP? |
| _Welke kennis heb ik al?_ | Begrip netwerk timing en metingstechnieken. |
| _Welke inzichten ontbreken?_ | Exacte tijdswaarden van ARP-vertraging. |
| _Zijn deelvragen specifiek?_ | Ja, meetbare grootheid (tijdduur). |
| _Geven ze samen antwoord?_ | Deelvraag 1 + 2 = mechanisme + kwantitatieve vertraging. |
| _Wat ontbreekt nog?_ | Data verzamelen en visualisatie. |
**Waarom relevant:** Dit geeft het directe antwoord op de hoofdvraag door metingen te verrichten.

3. Onderzoek- en analysemethoden
--------------------------------

### Per Deelvraag – Methodiek

| Deelvraag | Methode | Reden geschikt | Kwaliteit waarborgen |
| --- | --- | --- | --- |
| **1: ARP Mechanisme** | **Literatuuronderzoek** | Uitgebreide documentatie online beschikbaar; meest efficiënt voor theoretische kennis. | Bronnen controleren op geloofwaardigheid (officiële protocollen, boeken). Cross-check meerdere bronnen. |
| **2: Vertraging Meting** | **Prototyping** + **Data-analyse** | Iteratief meten mogelijk; software kan automatisch testen met variabelen. | Zelfde testcondities herhaaldelijk uitvoeren; statistische uitwerking in spreadsheets. |
| **Algemeen** | **Peer review** | Controle op consistentie en duidelijkheid. | Feedback van peers verwerken voorafgaande aan definitieve versie. |

4. Benodigde Middelen
---------------------

### Per Methode – Nodige middelen

| Methode | Hardware / Infrastructuur | Software / Tools | Data & Bronnen | Tijd / Ondersteuning |
| --- | --- | --- | --- | --- |
| **Literatuuronderzoek** | - Internetverbinding  <br>- Laptop/computer | Geen speciaal  <br>Browser, notitiesoftware | Academic papers  <br>Protocol documentatie  <br>Online tutorials | 2-3 uur voor grondwerk + continue zoeken |
| **Prototyping** | 1-2 laptops  <br>Netwerk met ARP support  <br>Ping-testbaar apparaat | Metingssoftware  <br>C++ (optioneel)  <br>Google Spreadsheets | Testdata log  <br>Timing resultaten | 5+ dagen voor ontwikkeling + testen |
| **Data-analyse** | - Laptop met software  <br>- Netwerk voor data storage | Google Spreadsheets  <br>Grafiek tools | Verzamelde meetdata  <br>Statistische tabellen | 2-3 uur berekening en visualisatie |
| **Peer review** | - Communicatiemiddelen (email/chat) | Geen speciaal  <br>Wiki platform | Gereviewd onderzoeksgedeelte | 1 dag voor feedback verwerking |

5. Criteria voor Analyse
------------------------

De resultaten worden geëvalueerd aan de hand van:
1.  **Snelheid / Vertraging:** Extra tijd (ms) tussen eerste vs. verdere communicatie
2.  **Betrouwbaarheid:** Herhaalbaarheid van meetresultaten bijzelfde omstandigheden
3.  **Vereiste middelen:** Haalbaar binnen beschikbare hardware/software
4.  **Duurzaamheid:** Meetopzet werkt onder standaard netwerkcondities

6. Globale Planning
-------------------

| Fase | Activiteit | Prioriteit | Geschatte tijd |
| --- | --- | --- | --- |
| **1** | Literatuuronderzoek & theorie verzamel**en | Hoog | 3 dagen |
| **2** | Prototype ontwikkeling (software/meting) | Hoog | 5-7 dagen |
| **3** | Tests uitvoeren met verschillende scenario's | Hoge | 3-4 dagen |
| **4** | Data-analyse & visualisatie | Medium | 2 dagen |
| **5** | Peer review en feedback verwerken | Medium | 2-3 dagen |
| **6** | Eindrapportage samenstellen | - | 1 dag |