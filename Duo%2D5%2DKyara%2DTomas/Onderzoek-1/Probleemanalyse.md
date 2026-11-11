# Probleem Context

Binnen de robotvloot project "[Robotzwermen tegen bodemverdichting](https://brightspace.avans.nl/d2l/le/lessons/308932/topics/2204945)" werken meerdere machines samen om een oogstproces uit te voeren. De vloot bestaat uit een rooier, twee overslagwagens; twee operatorinterfaces en een centrale controller en. Deze systemen moeten onderling communiceren om het oogstproces veilig en efficiënt te laten verlopen.

Het project vereist verschillende soorten communicatiestromen die moeten worden ondersteund. Deze informatiestromen stellen verschillende eisen aan de manier waarop de communicatie wordt afgehandeld. Het voorgaande onderzoek ging uit van één enkele communicatiemethode. Dit kan echter leiden tot compromissen bij het maken van een keuze voor de communicatiemethode. Een manier om te voorkomen dat de ene communicatiestroom wordt beperkt door de eisen van een andere, is om elke communicatiestroom een eigen communicatie-infrastructuur te geven.

# Belang

De ontwikkeling van een project vereist een zo betrouwbaar mogelijke werking van het systeem. De communicatie tussen de verschillende onderdelen van de robotvloot speelt hierin een belangrijke rol. Wanneer berichten verloren gaan, vertraging oplopen of een communicatie-infrastructuur tijdelijk niet beschikbaar is, kan dit gevolgen hebben voor de werking van het systeem.
Wanneer er mogelijkheden bestaan om de betrouwbaarheid van de communicatie te verbeteren, moeten deze worden onderzocht en waar mogelijk worden benut.

# Literatuuronderzoek

Uit voorgaand onderzoek is gebleken dat het systeem op verschillende manieren communiceert. Tijdens dit onderzoek werden zogenaamde 'berichtlijnen' voorgesteld. In deze context werd met een 'berichtlijn' een logisch gegroepeerde stroom van berichten tussen twee of meerdere systemen bedoeld, die gezamenlijk een specifiek communicatiedoel binnen het systeem ondersteunen.
De berichtlijnen die voor het onderzoek werden gebruikt, kwamen voort uit het hoofdstuk 'Communicatieaspecten', met name uit de paragraaf 'Hoeveel berichten moeten tegelijkertijd worden verzonden?'. Deze berichtlijnen werden vervolgens gebruikt voor alle andere onderdelen waarin dit relevant was. De destijds gekozen berichtlijnen waren als volgt:
*   **Cyclusberichtlijn**: de communicatie over de cyclus van het ophalen en afladen van de rooier.
*   **Besturingsberichtlijn**: de communicatie voor het versnellen en vertragen van de overslagwagen.
*   **Interfaceberichtlijn**: de communicatie voor het bijwerken van de interface met voertuiggegevens.

Voor een gedegen onderzoek is het echter beter om berichtlijnen op een meer algemene manier te definiëren, zonder deze definitie uitsluitend te baseren op het aantal berichten dat tegelijkertijd wordt verzonden. Om de verschillende berichtlijnen binnen een project te identificeren, zijn de volgende gegevens nodig: het doel van de communicatie, de betrokken verzenders en ontvangers, de inhoud van de berichten en de manier waarop de berichten worden verzonden. Deze aspecten worden in dit onderzoek behandeld om tot een duidelijke definitie van de verschillende berichtlijnen te komen.

Het vooronderzoek heeft inzicht gegeven in de eigenschappen van verschillende communicatiemethoden. Er is echter nog geen onderzoek gedaan naar welke communicatiemethode het meest geschikt is voor elke afzonderlijke berichtlijn. Daarnaast is nog niet vastgesteld welk effect het verdelen van de berichtlijnen over meerdere communicatie-infrastructuren heeft op de betrouwbaarheid van de gegevensoverdracht binnen de transportlaag.

**Literature gap:** Er ontbreekt specifiek onderzoek naar het effect van een multi-communicatie-infrastructuur op de betrouwbaarheid van de transportlaag binnen de beschreven robotvloot. Hierbij ligt de nadruk op berichtverlies, latency, benodigde bandbreedte en beschikbaarheid.

# Doelstelling

Het doel van dit onderzoek is om inzicht te krijgen in het effect van een multi-communicatie-infrastructuur op de betrouwbaarheid van de transportlaag binnen de robotvloot.

Dit wordt bereikt door een multi-communicatie-infrastructuur te vergelijken met een single-communicatie-infrastructuur. Hierbij worden de verschillen onderzocht op het gebied van berichtverlies, latency, benodigde bandbreedte en beschikbaarheid.

Het onderzoek is geslaagd wanneer duidelijk is welke verschillen optreden tussen beide infrastructuren en in hoeverre het toepassen van meerdere communicatie-infrastructuren voordelen oplevert voor de betrouwbaarheid van de gegevensoverdracht binnen de robotvloot.

# Afbakening

Dit onderzoek richt zich op de communicatie tussen de rooier, overslagwagens, centrale controller en operatorinterfaces. Hierbij wordt specifiek gekeken naar het effect van een single- en multi-communicatie-infrastructuur op de betrouwbaarheid van de transportlaag.

De volgende aspecten worden onderzocht:
*   **Berichtverlies**: het percentage verzonden berichten dat niet bij de ontvanger aankomt.
*   **Latency**: de tijd die verstrijkt tussen het verzenden en ontvangen van een bericht.
*   **Benodigde bandbreedte**: de hoeveelheid netwerkcapaciteit die nodig is om de verschillende berichtstromen te verwerken.
*   **Beschikbaarheid**: de mate waarin de communicatie-infrastructuur operationeel en bruikbaar blijft wanneer deze nodig is.

Buiten de scope van dit onderzoek vallen de volledige implementatie van de communicatie-infrastructuur, andere keuzes met betrekking tot de transport laag, zelfgemaakte protocollen, overige betrouwbaarheidscriteria en informatie die voortkomt uit voorgaand onderzoek.