# 1. Probleemcontext
Het doel van het project is om bodemverdichting op landbouwakkers te verminderen door middel van robotisering. Hiervoor wordt een autonome robotvloot ontwikkeld die het oogstproces zo efficiënt mogelijk moet uitvoeren. Hieronder zie je de rollen van de voertuigen en operators. Om te zorgen dat deze grote landbouw machines veilig te gebruiken zijn is het van belang dat het draadloze noodstop systeem snel en betrouwbaar is.

Om het draadloze noodstop systeem te kunnen implementeren moet er eerst duidelijk ontstaan met welke draadloze netwerk protocollen geschrikt zijn hiervoor zijn de volgende belangen:


# Belangen
**Voorkomen van schade:** Landbouw robots zijn grote zware machines die makkelijk schade aan kan brengen aan levende of niet levende dingen. Het is van belang dat de noodstop altijd werkt als de landbouw machines in beweging zijn.

**Bereikbaarheid:** Het netwerk moet bereikbaar zijn over het hele akker voor de boer.

**Vertraging:** Do noodstop moet zo snel mogelijk reageren voor de veiligheid

# Doelstelling
Uit het literatuur onderzoek kwam de literatuur gap antwoord "De theoretische vertraging waarde tussen 4G en 5G zijn bekend, maar het is nog niet duidelijk wat de minimale vertraging eisen voor een draadloze noodstop voor landbouw machines." Het doel van de onderzoek gaat worden om er achter te komen wat de minimale vertraging eisen zijn voor een draadloze noodstop voor de landbouw machines, zodat het systeem veilig blijft.

Het direct testen met 4G en 5G netwerken ligt buiten bereik, daarom is er gekozen om deze doelstelling te beantwoorden door middel van een simulatie tussen twee computers met een c++ test programma waarin het theoretische stopafstand berekend word en nep vertraging word toegepast met de waardes vanuit het literatuur onderzoek. 

**Het onderzoek is geslaagd als de volgende statements waar zijn:**
1. Je kunt antwoord geven op de vraag: wat is de minimale en maximale vertraging in milliseconden voor een veilige draadloze noodstop?
2. De testen zijn herhaalbaar met gelijke resultaten

# Afbaking
**Binnen scope**
- De stopafstand simuleren met variabele massa en snelheid
- Infrastructuur nep vertraging toepassen 
- Toepassen van reactiesnelheid van een mens

**Buiten scope**
- De stopafstand simulatie met wrijving ongelijke vloer en luchtweerstand
- Direct met 4G en 5G netwerken werken
- fizieke robot testen

