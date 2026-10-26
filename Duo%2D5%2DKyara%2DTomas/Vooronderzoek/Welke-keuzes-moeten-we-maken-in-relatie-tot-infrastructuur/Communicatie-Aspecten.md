# Hoe ver moeten berichten worden verzonden?

Het bericht dat de grootste afstand moet overbruggen, wordt verzonden van de operator aan de zijkant van het veld naar een overslagwagen aan het uiteinde van het veld. Om deze afstand te bepalen, moeten we een schatting maken van de afmetingen van het perceel.
We wilden achterhalen wat het grootste perceel was, maar helaas hebben we hierover geen informatie gevonden. Daarom moeten we voor dit onderdeel enkele aannames doen. Volgens het CBR bedroeg de gemiddelde perceelgrootte voor zetmeelaardappelvelden in 2021 maximaal 5,34 hectare [1]. Omdat we geen informatie hebben over de spreiding van de perceelgroottes en eventuele uitschieters, gebruiken we deze waarde als uitgangspunt voor onze berekening.
Vervolgens moeten we de lengte en breedte van het perceel bepalen. Omdat we rekening willen houden met relatief langwerpige percelen, hanteren we een lengte-breedteverhouding van 5:1. Dit levert een perceel op van ongeveer $103,3 m × 516,5 m$. We ronden dit af naar $100 m × 535 m$. De oppervlakte blijft hiermee ongeveer 5,35 hectare.
Afhankelijk van de zijde van het perceel waar de operator zich bevindt, moet een bericht maximaal ongeveer 100 of 535 meter overbruggen. Om rekening te houden met beide situaties, gaan we voor de verdere berekeningen uit van een maximale afstand van ongeveer 535 meter.

## Conclusie

Op basis van de beschikbare literatuur en de gemaakte aannames schatten we dat de **maximale communicatieafstand ongeveer 535 meter** overbrugt. Dit is een globale schatting, omdat er geen informatie beschikbaar is over de werkelijke afmetingen van het perceel in de casus. De werkelijke communicatieafstand kan daarom afwijken van deze waarde.

# Wanneer moet het systeem actief zijn?

Dit proces vindt plaats tijdens het oogsten van een perceel. Het oogsten van een gewasperceel vindt doorgaans ongeveer één keer per jaar plaats [2]. Hoe lang het oogsten duurt, hangt af van de grootte van het perceel, de snelheid van de rooier en de werkbreedte ervan.
Voor de perceelgrootte gebruiken we de aannames uit de paragraaf _‘Hoe ver moeten berichten worden verzonden?’_.
De snelheid hebben we bepaald door verschillende online artikelen met elkaar te vergelijken [3][4][5][6]. Op basis hiervan gaan we ervan uit dat de rooier een snelheid van ongeveer 2 kilometer per uur heeft.
Ook voor de werkbreedte hebben we verschillende bronnen met elkaar vergeleken [3][7][8]. Op basis hiervan hanteren we een naar boven afgeronde werkbreedte van 3,5 meter.
**Hoe lang moet het systeem dan ongeveer actief zijn?**
*   **Aantal stroken:** $100 / 3,5 ≈ 29 stroken$.
*   **Totale rijafstand:** $29 × 535 = 15.515 meter ≈ 15,5 kilometer$.
*   **Totale tijd:** $15,5 / 2 ≈ 7,76 uur$.
Als we rekening houden met draaien en andere onderbrekingen, schatten we dat het systeem ongeveer 8 tot 9 uur per jaar per gewasperceel actief moet zijn.

## Conclusie

Op basis van literatuuronderzoek naar de gemiddelde perceelgrootte, de snelheid van de machines en de benodigde oogsttijd schatten we dat het systeem **ongeveer 8 tot 9 uur per jaar per gewasperceel actief moet zijn**. Dit is een globale schatting, omdat er geen informatie beschikbaar is over de werkelijke perceelgrootte, machinesnelheid en werkbreedte in de casus. De werkelijke benodigde actieve tijd kan daarom afwijken van deze schatting.

# Wat is de maximale latency

| Bericht | Reactie Type | Formule |
| --- | --- | --- |
| Overslagwagen roepen | Machine Event | $t_{\text{lat,max}} = \frac{100-p_{\text{notif}}}{s_{\text{vul}}} - \frac{a_{\max}}{s_{\text{wagen}}}$ |
| Rooier aanroepen | Machine Event | 100 milliseconden |
| Rooier afroepen | Machine Event | $t_{\text{lat,max}} = \frac{100-p_{\text{notif}}}{s_{\text{vul}}} - t_{\text{stop}}$ |
| Overslagwagen versnellen/vertragen | Mens Event | 100 milliseconden |
| Positie van de overslagwagen melden | Machine Continu | $t_{\text{update,max}} = \frac{a_{\text{update,max}}}{s_{\text{wagen}}}$ |
| Status tonen op de operatorinterface | Mens Continu | 100 milliseconden |

*De formules zijn onderaan te vinden.  
*De reactietijd van 100 milliseconden is gebaseerd op de richtlijnen voor responstijden in UX [9].  
*Voor het aanroepen van de rooier is geen formule opgenomen, omdat op het moment van de aanroep aan alle voorwaarden is voldaan.

## Conclusie

Op basis van het literatuuronderzoek kan deze vraag **nog niet worden beantwoord**. Er is informatie nodig over de daadwerkelijke werking van de machines om te kunnen bepalen welke vertraging maximaal toelaatbaar is en wat daarmee de maximale latency mag zijn.

# Hoe vaak moeten berichten worden verzonden?

| Bericht | Reactie Type | Vaakheid Type | Interval |
| --- | --- | --- | --- |
| Overslagwagen roepen | Machine Event | 1x per ronde | NA |
| Rooier aanroepen | Machine Event | 1x per ronde | NA |
| Rooier afroepen | Machine Event | 1x per ronde | NA |
| Overslagwagen afroepen | Machine Event | 1x per ronde | NA |
| Overslagwagen versnellen/vertragen | Mens Event | 1x per event | NA |
| Positie van de overslagwagen melden | Machine Continu | tijdsinterval | $t_{\text{update,max}} = \frac{a_{\text{update,max}}}{s_{\text{wagen}}}$ |
| Status tonen op de operatorinterface | Mens Continu | tijdsinterval | 100 milliseconden |

*De formules zijn onderaan te vinden.  
*De reactietijd van 100 milliseconden is gebaseerd op de richtlijnen voor responstijden in UX [9].

## Conclusie

Op basis van het literatuuronderzoek en de eisen uit de casus hebben we inzicht gekregen in de vereiste verzendfrequentie van berichten. Een uitzondering hierop is het doorgeven van de positie van de overslagwagen. Om de verzendfrequentie van dit bericht te kunnen bepalen, moeten we weten wat de maximaal toegestane verplaatsing tussen positie-updates (in meters) is. Omdat deze waarde nog niet bekend is, kan de **vereiste verzendfrequentie voor dit bericht nog niet worden vastgesteld**.

# Hoeveel berichten moeten tegelijkertijd worden verzonden?
*   **Cyclusberichtlijn:** de communicatie over de cyclus van het ophalen en afladen van de rooier.
*   **Besturingsberichtlijn:** de communicatie voor het versnellen en vertragen van de overslagwagen.
*   **Interfaceberichtlijn:** de communicatie voor het bijwerken van de interface met voertuiggegevens.

## Conclusie

Op basis van het literatuuronderzoek en de eisen uit de casus kunnen er **maximaal drie berichten, afkomstig uit verschillende berichtlijnen, tegelijkertijd worden verzonden**.

# Hoeveel bandbreedte is er nodig?

$$ B_{\text{vereist}} = D_{\text{bericht}} \times f_{\text{berichten}} \times 8 \times M_{\text{veiligheid}}$$

Waarbij:
*   $B_{\text{vereist}}$ = de benodigde bandbreedte (bit/s).
*   $D_{\text{bericht}}$ = de gegevensgrootte per bericht (bytes).
*   $f_{\text{berichten}}$ = het aantal berichten per seconde (1/s).
*   $8$ = de omrekenfactor van bytes naar bits.
*   $M_{\text{veiligheid}}$ = de veiligheidsfactor (bijvoorbeeld 1{,}5 voor 50% extra capaciteit).

## Conclusie

Op basis van het literatuuronderzoek kan de benodigde bandbreedte **nog niet worden vastgesteld**. Hiervoor zijn de gegevensgrootte per bericht, het aantal berichten per seconde en de veiligheidsfactor nodig. Omdat deze waarden momenteel nog niet bekend zijn, kan de vereiste bandbreedte nog niet worden berekend.

_Voor dit onderzoek is gebruikgemaakt van de bronnen [10] en [11]._

<br>

---
# Formules

## Overslagwagen roepen:

*   $s_{\text{vul}}$ = vulsnelheid van de rooier (% per seconde)
*   $p_{\text{notif}}$ = vulpercentage waarbij de notificatie wordt verstuurd (%)
*   $a_{max}$ = maximale afstand tot de rooier (m)
*   $s_{\text{wagen}}$ = snelheid van de overslagwagen (m/s)
*   $t_{\text{rij}}$ = benodigde rijtijd van de overslagwagen (s)
*   $t_{\text{vul}}$ = resterende vultijd tot de bunker vol is (s)
*   $t_{\text{lat,max}}$ = maximale reactietijd (s)

**1.  Bereken resterende vultijd: $t_{\text{vul}} = \frac{100-p_{\text{notif}}}{s_{\text{vul}}}$
2.  Bereken benodigde rijtijd: $t_{\text{rij}} = \frac{a_{max}}{s_{\text{wagen}}}$
3.  Bereken reactietijd: $t_{\text{lat,max}} = t_{\text{vul}} - t_{\text{rij}}$**

## Rooier afroepen:

*   $s_{\text{vul}}$ = vulsnelheid van de overslagwagen (% per seconde)
*   $p_{\text{notif}}$ = vulpercentage waarbij de notificatie wordt verstuurd (%)
*   $t_{\text{stop}}$ = benodigde tijd om de vulling te stoppen (s)
*   $t_{\text{vul}}$ = resterende vultijd tot de bunker vol is (s)
*   $t_{\text{lat,max}}$ = maximale reactietijd (s)

**1.  Bereken resterende: $t_{\text{vul}} = \frac{100-p_{\text{notif}}}{s_{\text{vul}}}$
2.  Berken maximale reactietijd: $t_{\text{lat,max}} = t_{\text{vul}} - t_{\text{stop}}$**

## Positie van de overslagwagen doorgeven:

*   $s_{\text{wagen}}$ = snelheid van de overslagwagen (m/s)
*   $a_{\text{update,max}}$ = maximaal toegestane verplaatsing tussen positie-updates (m)
*   $t_{\text{update,max}}$ = maximale tijd tussen positie-updates (s)

**1.  Bereken maximale tijd tussen positie-updates: $t_{\text{update,max}} = \frac{a_{\text{update,max}}}{s_{\text{wagen}}}$**

---
# Bronnen
[1] Centraal Bureau voor de Statistiek, “Gemiddelde oppervlakte percelen akkerbouwgewassen, 2017-2021,” _Centraal Bureau Voor De Statistiek_, Feb. 25, 2022. [https://www.cbs.nl/nl-nl/maatwerk/2022/08/gemiddelde-oppervlakte-percelen-akkerbouwgewassen-2017-2021](https://www.cbs.nl/nl-nl/maatwerk/2022/08/gemiddelde-oppervlakte-percelen-akkerbouwgewassen-2017-2021)  
[2] “Akkerbouwkalender - Akkerbouw van nu,” _Akkerbouw Van Nu_. [https://www.akkerbouw-van-nu.nl/akkerbouwkalender/](https://www.akkerbouw-van-nu.nl/akkerbouwkalender/)  
[3] Janinevit, “Eerste autonome aardappelrooier draait op Groninger akkers,” _akkerbouwbedrijf.nl_, Nov. 30, 2021. [https://www.akkerbouwbedrijf.nl/akkerbouwmachines/rooimachine/harvey-one-eerste-autonome-aardappelrooier-draait-op-groninger-akkers/](https://www.akkerbouwbedrijf.nl/akkerbouwmachines/rooimachine/harvey-one-eerste-autonome-aardappelrooier-draait-op-groninger-akkers/)  
[4] H. Schreuder and H. Schreuder, “Aardappels rooien,” _Harrysfarm_, Oct. 29, 2020. [https://www.harrysfarm.nl/2020/10/24/aardappels-rooien-2/](https://www.harrysfarm.nl/2020/10/24/aardappels-rooien-2/)  
[5] Nieuwe Oogst, [https://www.nieuweoogst.nl](https://www.nieuweoogst.nl), “Agra Warrior-rooier van Graafstra is praktijkrijp,” _Nieuwe Oogst_, Jan. 02, 2026. [https://www.nieuweoogst.nl/nieuws/2026/01/02/agra-warrior-rooier-van-graafstra-is-praktijkrijp](https://www.nieuweoogst.nl/nieuws/2026/01/02/agra-warrior-rooier-van-graafstra-is-praktijkrijp)  
[6] “8.3 Oogst wat gegroeid is | IRS | Kennis- en onderzoekscentrum.” [https://www.irs.nl/interessegebieden/alle-interessegebieden/teelthandleiding/8-3-oogst-wat-gegroeid-is/#rijsnelheid](https://www.irs.nl/interessegebieden/alle-interessegebieden/teelthandleiding/8-3-oogst-wat-gegroeid-is/#rijsnelheid)  
[7] akkerbouwbedrijf.nl, “Grimme Rooster: Eenvoudige en lichte rooier met goede capaciteit,” _akkerbouwbedrijf.nl_, Jul. 30, 2020. [https://www.akkerbouwbedrijf.nl/trekkers-en-mechanisatie/trekkers/grimme-rooster-eenvoudige-en-lichte-rooier-met-goede-capaciteit/](https://www.akkerbouwbedrijf.nl/trekkers-en-mechanisatie/trekkers/grimme-rooster-eenvoudige-en-lichte-rooier-met-goede-capaciteit/)  
[8] J. Wevers, “Bieten rooien als aardappelen,” _Cosun Magazine_, vol. 18, no. 12, pp. 18–19, Dec. 2003, [Online]. Available: [https://www.irs.nl/wp-content/uploads/2020/12/Bieten-rooien-als-aardappelen.pdf](https://www.irs.nl/wp-content/uploads/2020/12/Bieten-rooien-als-aardappelen.pdf)  
[9] J. Nielsen, “Response times: The 3 important limits,” _Nielsen Norman Group_, Jan. 31, 2024. [https://www.nngroup.com/articles/response-times-3-important-limits/](https://www.nngroup.com/articles/response-times-3-important-limits/)  
[10] Marketing Team, “Network bandwidth - How to calculate WiFi bandwidth need?,” _Tanaza - Cloud Management Platform for WiFi Access Points_, Nov. 09, 2020. [https://www.tanaza.com/blog/how-to-calculate-network-bandwidth-requirements/](https://www.tanaza.com/blog/how-to-calculate-network-bandwidth-requirements/)  
[11] R. D. Hernandez en Medium, “5 steps to estimating network bandwidth requirements”, 28 juni 2025. [https://medium.com/@robhernandez5/a-5-step-guide-to-estimating-network-bandwidth-requirements-75219367642a](https://medium.com/@robhernandez5/a-5-step-guide-to-estimating-network-bandwidth-requirements-75219367642a)