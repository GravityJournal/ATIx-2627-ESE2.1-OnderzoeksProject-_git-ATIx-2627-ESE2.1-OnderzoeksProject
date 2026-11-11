Nu we het vooronderzoek hebben afgerond, kunnen we doorgaan naar wat we inmiddels weten en wat we nog niet weten. Vragen die weinig met communicatie te maken hebben (zoals: _"Welke specifieke rooier en overslagwagens simuleren we, en wat zijn hun specificaties?"_) worden in deze conclusie niet meegenomen.
Dit heeft geleid tot een aantal vragen waarop we het antwoord nog niet weten:

# Hoofdonderzoeksvragen Selectie

**De eerste vraag komt voort uit 'Communicatieaspecten', hoofdstukken 'Hoe ver moeten berichten worden verzonden?' en 'Wanneer moet het systeem actief zijn?'** Het onderzoek geeft een inschatting van de afstand die de communicatie waarschijnlijk moet overbruggen en de snelheid waarmee de machines zich verplaatsen. Het beschrijft echter niet wat het effect van deze afstanden en snelheden is op de draadloze communicatie.

Dit leidt tot vraag 1: **Hoe beïnvloeden de afstand en de beweging van de robots de betrouwbaarheid van draadloze communicatie?**

**De tweede vraag komt voort uit 'Communicatieaspecten', hoofdstuk 'Wat is de maximale latency?'** Het onderzoek stelt hoge eisen aan de frequentie waarmee positie-updates van de voertuigen moeten worden verstuurd. Een hoge frequentie kan het communicatiesysteem onnodig belasten. Daarom is het zinvol om te onderzoeken hoe deze belasting kan worden verminderd.

Dit leidt tot vraag 2: **Hoe kan de frequentie van positie-updates worden geoptimaliseerd om de netwerkbelasting binnen de robotvloot te beperken?**

**De derde vraag komt voort uit 'Communicatieprotocol', hoofdstuk 'Welk applicatieprotocol moet worden gebruikt?'** Uit het onderzoek blijkt dat MQTT van de bestaande protocollen de beste optie lijkt. Er is echter nog een duidelijk kennishiaat, omdat ook een zelfontwikkeld protocol tot de mogelijkheden behoort. Over zelfontwikkelde protocollen zijn geen algemene literatuurgegevens beschikbaar, omdat de eigenschappen sterk afhankelijk zijn van de manier waarop ze worden ontworpen en geïmplementeerd.

Dit leidt tot vraag 3: **Welk communicatieprotocol is geschikter voor de communicatie binnen de robotvloot uit deze casus: MQTT of een zelfontwikkeld protocol?**

**De vierde vraag komt voort uit 'Communicatiearchitectuur', hoofdstuk 'Welke netwerkarchitectuur moet worden gebruikt?'** Uit het vooronderzoek blijkt dat een client-serverarchitectuur het beste aansluit bij de wens voor centrale aansturing en centraal gegevensbeheer. Er is echter nog niet vastgesteld hoe de verschillende apparaten binnen deze architectuur fysiek en logisch met elkaar moeten worden verbonden.

Dit leidt tot vraag 4: **Welke netwerktopologie is het meest geschikt voor de communicatie tussen de rooier, overslagwagens en server?**

**De vijfde vraag komt voort uit een kennishiaat in het vooronderzoek.** Tijdens 'Communicatieaspecten', hoofdstuk 'Hoeveel berichten moeten tegelijkertijd worden verzonden?', zijn verschillende berichtlijnen gedefinieerd. Deze berichtlijnen zijn in het verdere onderzoek gebruikt om de verschillende communicatiestromen binnen het systeem aan te duiden. Ze hebben invloed op meerdere onderdelen van het verdere onderzoek, omdat iedere berichtlijn andere communicatiebehoeften en eisen heeft. Dit is in het vooronderzoek niet verder onderzocht, omdat daarbij werd uitgegaan van één algemene communicatieoplossing. Hierdoor viel het buiten de scope van het vooronderzoek. In het vervolgonderzoek kan dit onderwerp echter wel worden meegenomen.

Dit leidt tot vraag 5: **Wat is het effect van een multi communicatie-infrastructuur?**
<br>
# Feedback op Hoofdonderzoeksvragen
Voor de selectie en verbetering van de vragen heeft dit onderzoek feedback gevraagd van A. Broeders Docent in 'Infrastructuur en Computernetwerken' en begeleidingsdocent op Avans Breda voor de studie 'Jaar 2, Embedded Software Engineering, Robot Fleet, 2026' [1]. De observaties van deze feedback is opgenomen in het onderstaande tabel:
| Vraag | Goedkeuring | Probleem | Aanpassingen |
| --- | --- | --- | --- |
| Vraag 1 | Goed | Geen | Geen |
| Vraag 2 | Middelmatig | Geen prototyping nodig | Niet Gekozen |
| Vraag 3 | Redelijk | Matig gebruik prototyping | Niet Gekozen |
| Vraag 4 | Fout | Geen prototyping + Te voor de hand liggend | Niet Gekozen |
| Vraag 5 | Goed | Niet speciek genoeg  <br>- Welke Laag?  <br>- Welke Criteria? | Afbakenen  <br>- Laag  <br>- Criteria |

<br>

# Selectie Hoofdonderzoeksvragen

De keuze in hoofdvragen is gedaan aan de hand van de welke het hoogste goedkeuringsniveau hadden.

## Hoofdonderzoeksvraag 1

**Wat is het effect van een multi-communicatie-infrastructuur op de betrouwbaarheid van de transport laag? – Twee aanpassingen**
1.  **Criteria:** Hierbij wordt gekeken naar berichtverlies (geeft aan welk percentage van de verzonden berichten niet bij de ontvanger aankomt), latency (geeft aan hoeveel tijd er verstrijkt tussen het verzenden en ontvangen van een bericht), benodigde bandbreedte (geeft aan hoeveel netwerkcapaciteit nodig is om de verschillende berichtstromen te kunnen verwerken) en beschikbaarheid (geeft aan in hoeverre de communicatie-infrastructuur beschikbaar blijft wanneer deze nodig is). Door deze criteria te onderzoeken, kan worden vastgesteld of het verdelen van verschillende berichtstromen over meerdere communicatie-infrastructuren voordelen oplevert voor de betrouwbaarheid van de gegevensoverdracht.
2.  **Laag:** Transport laag, gekozen vanwege de duidelijke twee opties die er zijn.
De selectie van deelvragen hiervoor is als volgt:
*   **DV 1: Welke transportprotocollen zijn geschikt voor de verschillende berichtlijnen?**
*   **DV 2: Wat is het ontwerp voor de multi- en single- communicatie programma's ?**
*   **DV 3: Wat is het verschil in berichtverlies tussen de multi-communicatiemethode en de single-communicatiemethode?**
*   **DV 4: Wat is het verschil in latency tussen de multi-communicatiemethode en de single-communicatiemethode?**
*   **DV 5: Wat is het verschil in benodigde bandbreedte tussen de multi-communicatiemethode en de single-communicatiemethode?**
*   **DV 6: Wat is het verschil in beschikbaarheid tussen de multi-communicatie-infrastructuur en de single-communicatie-infrastructuur?**
Om dit onderzoek correct te kunnen verwerken moeten we eerst opstellen hoe we de multi communicatie correct overbrengen voor het project en daarna stellen we vragen die het meet.

## Hoofdonderzoeksvraag 2

**Hoe beïnvloeden de verplaatsing van de robots de betrouwbaarheid van draadloze communicatie? - Geen aanpassing**
De selectie van deelvragen hiervoor zijn als volgt:
*   **DV 1: Hoe beïnvloeden de afstand van de robots de betrouwbaarheid van draadloze communicatie?**
*   **DV 2: Hoe beïnvloeden de beweging van de robots de betrouwbaarheid van draadloze communicatie?**
Deze onderdelen zijn de verschillende aspecten van verplaatsing.


---

[1] A. Broeders, begeleidingssessie