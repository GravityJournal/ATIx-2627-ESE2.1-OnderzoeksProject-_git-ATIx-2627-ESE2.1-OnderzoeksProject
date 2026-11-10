# 1. Validiteit
Ons prototype is zeer valide in het testen. Dit komt doordat de commando's die hij gebruikt om de tijd van het versturen van het datapakket op te halen, commando's zijn die al in het operating system van de computer zitten verwerkt en zowel voor linux als windows bijna exact hetzelfde functioneren. Het enige verschil daar is mogelijk verschillende syntax.
Hierdoor zijn de metingen de we doen op dat vlak iniedergeval valide.

Een minpunt voor de validiteit van het onderzoek zit in twee dingen.
Allereerst is netwerkverkeer nooit consistent en zal er altijd verschil zitten in de waardes en soms ook immense uitschieters.
Ten tweede hebben we niet veel duidelijk betrouwbare bronnen gevonden om ons literatuuronderzoek op te baseren en kan ook dat niet volledig valide zijn.

Om deze minpunten dan ook te midneren of mogelijk zelfs te vorkomen zouden we dan ook sowieso vele malen meer metingen doen zodat de buitenliggende uitschieters van metingen minder invloed hebben op het gemiddelde.
Ook zouden we extensiever onderzoek en dieper onderzoek doen om meer bronnen te vinden die niet alleen informatie geven maar ook bevestigen wat andere bronnen zeggen.

# 2. Betrouwbaarheid
Onze metingen waren so consistent als mogelijk door het gebruiken van een programma voor her prototype. Hierin hebben we namelijk tijdens het testen zo gemaakt dat het enige wat een variabele invloed heeft op het resultaat het internetverkeer is en op welk netwerk je zit en wiens IP je pingde.
Hierdoor werden alle berekeningen en metingen consistent uitgevoert.

Maar de variabelen die er waren kunnen wel een drastisch verschil brengen. We hebben ook zelf namelijk een keer ondervonden dat de school wifi een stuk langzamer was dan gewoon en dat dat de resultaten toen flink beinvloedde. Deze hebben we dan ook niet meegenomen in onze resultaten omdat deze vele malen hoger waren dan alle andere meningen die we hadden.

# 3. Reproduceerbaarheid
Met de gebruikte code en kennis van hoe je het IP van een apparaat kan vinden is het onderzoek zeer makkelijk te reproduceren sinds de code het grootste deel van het werk van het testen doet.

Het grote minpunt hier is wel doordat we op Linux hebben gewerkt verschillen de commando's voor arp of ping een beetje hier en daar en kan het dus zijn dat iemand op windows hier wat kleine aanpassingen aan moet maken en dus de code iets diepgaander moet kunne begrijpen.

Om hiermee te helpen hebben we dus ook commentaar in de code toegevoegd om wat dingen uit te leggen maar daarmee kom je lang niet ver genoeg om de code helemaal duidelijk te maken.

# 4. Procesreflectie

Wat we zouden veranderen aan het process is ook wat voortkwam uit de peer-review. Om niet handmatig de resultaten to copy-pasten naar een apart bestandje of dergelijks maar om het programma deze al automatisch naar een .csv bestand laten schrijven zodat we daarna dat heel gemakkelijk met behulp van python konden analyseren zoals we dat vorig jaar in periode 1.4 ook hebben moeten doen voor het vak data-analyse.