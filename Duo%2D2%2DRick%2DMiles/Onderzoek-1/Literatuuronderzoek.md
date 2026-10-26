# Wat is er al bekend?
Literatuur over AGV- en robotvlootbeheer beschrijft verschillende oorzaken van taakstoppages, waaronder communicatie-uitval, time-outs en fysieke blokkades rondom overdrachtspunten [1][2].

Een belangrijk aandachtspunt is de afhandeling van vertragingen binnen dynamische productieomgevingen. Onderzoek laat zien dat vaste time-outs kunnen leiden tot onnodige taakannuleringen. Daarom wordt aanbevolen om time-outs dynamisch te bepalen op basis van actuele verkeersdrukte en verwachte reistijden [2].

Wanneer een robot een kritieke vertraging oploopt, kunnen geavanceerde vlootbeheersystemen taken herverdelen naar andere beschikbare robots. Hiervoor worden onder andere de volgende methoden toegepast [2]:

- Marktgebaseerde Aanpak (MBA), waarbij robots bieden op beschikbare taken.
- Mixed-Integer Linear Programming (MILP), waarbij een optimale taakverdeling wiskundig wordt berekend.

Indien geen alternatieve robot beschikbaar is, kan de lading tijdelijk worden gebufferd zodat het overdrachtspunt beschikbaar blijft voor andere logistieke processen [2].

Daarnaast beschrijft recente literatuur het gebruik van dead zones voor lokale foutisolatie. Bij een storing of blokkade wordt alleen het getroffen gebied afgesloten, terwijl overige robots hun routes herberekenen en operationeel blijven. Hierdoor hoeft niet de volledige vloot te worden stilgelegd, wat de systeembeschikbaarheid en doorvoer verbetert [3].

# Literature gap
Hoewel verschillende strategieën voor dynamische taakherallocatie en lokale foutisolatie zijn beschreven, ontbreekt specifiek onderzoek naar de toepassing van deze mechanismen binnen gescheiden multi-zone robotvloten met vaste overdrachtspunten tussen zones. Hierdoor is nog onvoldoende bekend hoe effectief deze methoden zijn in dergelijke omgevingen.