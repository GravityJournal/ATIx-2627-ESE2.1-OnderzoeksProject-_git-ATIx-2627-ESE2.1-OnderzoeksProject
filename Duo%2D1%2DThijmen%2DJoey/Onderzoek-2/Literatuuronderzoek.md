# **Wat is er al bekend?**
Voor verschillende communicatie protocollen is er al heel wat informatie bekend en te vinden op het internet. Daarom word hieronder al deel van de technologieën afgestreept en komen de vragen naar boven die we niet makkelijk kunnen beantwoorden voor het juiste communicatie protocol voor de casus en voor de veiligheid van de robot vloot.

# **Bluetooth & Wifi**
Om locatie te kunnen bepalen met netwerk infrastructuur zijn meerdere technologieën beschikbaar en mogelijk zoals: Wifi, LoRa, 4G, 4G of Bluetooth. Enkele van deze al worden afgestreept bijvoorbeeld wifi heeft een ideale range van 50 meter **(Bron 1)**. Wifi heeft de mogelijkheid voor grotere range door middel van gebruik van directional antennes, maar dat extra werk en hardware als er al een bestaand 4G/5G netwerk bestaand. Bluetooth kan ook al worden afgestreept voor gelijke redenen en heeft, maar een range van 10 meter **(Bron 2)**. Voor de afstanden voor deze casus worden toegepast in Nederland met een maximale akker grootte van 7.62 hectare **(Bron 3)** per perceel wat een akker grootte geeft van 300 x 254 meter. Dus dit geeft ons de mogelijkheden tussen LoRa, 4G en 5G.

# **LoRa**
Er is onderzochten of LoRa geschikt is voor de casus. Vanuit de gastles van Ericson is er bekend gemaakt dat er voor radio protocollen zoals dit bepaalde wetgevingen zijn die de toepassing hiervan voor ons kan beperken. LoRa gebruikt de frequency band van 863–870/873 MHz **(Bron 4)** dus heeft een duty cycle van 0.1% **(Bron 5)**. Ik heb berekend met 3600 seconden in een uur maal 0.001 (de 0.1% duty cycle in seconden) dat geeft 3.6 seconden verzend tijd per uur. Dit kan ook nog verschillen tussen korte en lange afstanden omdat langere afstanden meer tijd kost en meer van het budget van 3.6 seconden haalt. Door dit kunnen realtime communicatie en positie bepaling niet realiseren.

# **4G & 5G**
Om erachter te komen welke technologie tussen 4G en 5G voor ons het best geschrikt is stellen we de volgende vragen per techniek:

## **Hoeveel dekking is er in Nederland**  
Het is van belang dat het netwerk genoeg bereik heeft zodat er zekerheid is dat er verbinding gemaakt kan worden. Hieronder zie je twee kaarten met de dekking van 4G en 5G in nederland **(Bron 6)**  
![4and5gmap.png](https://dev.azure.com/AvansHogeschoolAcademies/d85453f3-b6ef-409b-9e59-5824066f8fdc/_apis/git/repositories/8216dca4-8185-4fb8-96f9-e5cb3be4eb9f/Items?path=/.attachments/4and5gmap-574541b0-e2ee-46d1-8afb-a40e296bc73f.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=wikiMaster)  
Hieruit zien we dat 5G iets minder dekking heeft en dat in Apeldoorn voor beide minder dekking is, Maar dat gebied is een natuurgebied.
    
## **Hoeveel vertraging in ms vind er plaats tussen sturen en ontvangen?**  
Het verschil van vertraging van 4G is tussen de 30-50 ms en die van 5G is 10 ms **(Bron 7)** Dit helpt nog niet om duidelijkheid te geven op de vraag welke beter is voor de veiligheid van de noodstop, omdat er nog duidelijkheid is van het impact van vertraging is voor onze robotfleet voor de veiligheid van de noodstop. Vanuit deze paper **(Bron 8)** komen ze tot de conclusie dat lagere vertraging in communicatie cruciaal is voor een veiliger en efficiënter systeem.

# **Literatuurgap**
Wat zijn de minimale vertraging eisen voor een draadloze noodstop voor landbouw machines?

    