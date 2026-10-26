# Context
Binnen de geautomatiseerde intralogistiek van Viscon Group moeten vloten van autonome robots in gescheiden hygiënezones nauw met elkaar en met de centrale vlootbesturing communiceren om goederen via overdrachtspunten (sluizen) te verplaatsen. Om te zorgen dat een robot uit Zone A feilloos op elkaar afgestemd is met een robot uit Zone B, is continue data-uitwisseling over statussen noodzakelijk.

Op dit moment is het binnen de infrastructuur nog onduidelijk hoe deze communicatie optimaal moet worden ingericht. Verschillende keuzes in netwerkprotocollen (zoals het betrouwbare TCP versus het snellere UDP) en berichtformaten (zoals compacte binaire C++ `structs` versus zwaardere tekstgebaseerde JSON-strings) hebben een directe invloed op de prestaties. Zonder een goed onderzoek is het risico aanwezig dat er gekozen wordt voor een inefficiënte configuratie, wat leidt tot onnodige vertraging en een overbelaste datastroom.

# Belang
- **Realtime besturing & snelheid:** Hoe lager de vertraging, hoe sneller de robots op elkaar kunnen inspelen bij de sluis, wat de totale doorvoer van de fabriek vergroot.
- **Netwerkefficiëntie & bandbreedte:** Door te kiezen voor een formaat met een lage data-overhead (bytes per bericht) wordt voorkomen dat het netwerk volloopt met overbodige data, wat goed is voor de stabiliteit van de vloot.
- **Betrouwbaarheid:** De communicatie moet robuust genoeg zijn zodat statuswijzigingen nooit verloren gaan, wat cruciaal is om opstoppingen en miscommunicatie tussen de zones te voorkomen.