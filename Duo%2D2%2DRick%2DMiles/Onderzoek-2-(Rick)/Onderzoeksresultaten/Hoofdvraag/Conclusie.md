# Multicriteria-analyse
Ter onderbouwing van de uiteindelijke keuze is een gewogen multicriteria-analyse opgesteld op basis van de vantevoren vastgestelde analysecriteria (lager is beter voor RTT, Jitter en Overhead). Deze is ingevuld op basis van de harde waardes uit de tabel in figuur 1.

| **Criterium** | **Weging** | **TCP + JSON** | **TCP + Struct** | **UDP + JSON** | **UDP + Struct** |
| --- | --- | --- | --- | --- | --- |
| **Gemiddelde RTT** | 30% | Laag (0.0393 ms) | Matig (0.0285 ms) | Hoog (0.0126 ms) | **Hoog (0.0125 ms)** |
| **Jitter / Stabiliteit** | 25% | Laag (hoge uitschieters) | Matig | Hoog | **Zeer Hoog (minimale jitter)** |
| **Data-overhead** | 25% | Laag (56 bytes) | Hoog (36 bytes) | Laag (56 bytes) | **Hoog (36 bytes)** |
| **Betrouwbaarheid / Verlies** | 20% | Hoog (gegarandeerd) | Hoog (gegarandeerd) | Matig (geen ACK in basis UDP) | **Hoog (geoptimaliseerd)** |
| **Gewogen Eindoordeel** | **100%** | Onvoldoende | Matig | Goed | **Optimaal** |

# Beantwoording hoofdvraag
Het meest efficiënte communicatieprotocol voor realtime data-uitwisseling en overdrachtsstatussen tussen vlootbeheerders en robots is een **UDP-socketverbinding in combinatie met een binaire C++ `struct`**.
Uit de systematische metingen blijkt dat UDP de vertraging (RTT) en jitter minimaliseert ten opzichte van TCP, terwijl de binaire struct de data-overhead met 35% reduceert ten opzichte van JSON. Hiermee wordt voldaan aan de strenge eisen voor realtime vlootbeheer, waarbij voorspelbaarheid en lage responstijden prioriteit hebben boven transportgaranties op socketniveau.