      
#Deelvraag 1.3
Hoe beïnvloed de 4g infrastructuur standaarden de datadoorvoer van de communicatie tussen robots?

Deze vraag is relevant omdat 4G biedt dekking over grote afstanden en ondersteunt mobiele robots

Het gebruik van draadloze netwerken tussen robot communicatie is een belangrijke keuze dat de prestaties van de robots en de data die ervan daan komen en naar toe worden gestuurd kan worden beïnvloedt. Robots sturen veel data, voldoende datadoorvoer is nodig om dit zonder vetraging te verwerken. dit is vooral van belang bij het inzetten van meerdere robots. dit moet ook niet ten koste gaan van lage latency, wat belangrijk is bij real-time communicatie. stevige packet loss tijdens het overbrengen van data kan leiden tot ongewenste situaties, consistentie in throughput belangrijk maakt (Gielis, Shankar, & Prorok, 2022).

#### LTE (Release 8)
LTE Release 8 voerde OFDMA en MIMO in wat een datadoorvoer tot ongeveer 300 Mbps mogelijk maakt. Voor de robot communicatie betekend dit dat communicatie met een lage latency nog te doen is. Dit vormt een probleem bij grote robot aantallen wat de datadoorvoer nogal verminderd (Holma & Toskala, 2009).

#### LTE-Advanced (released 10-11)
LTE-Advanced maakt gebruikt van carrier aggregation en MIMO, dit zorgt voor een datadoorvoer van 1 Gbps. Voor robotcommunicatie betekende dit dat parallelle datastromen betrouwbaarder konden worden verwerkt, bijvoorbeeld voor de coördinatie van meerdere robots in dezelfde omgeving (Ahmadi, 2013).

#### LTE-Advanced Pro(release 13-14)
LTE-Advanced Pro maakt gebruik van technieken zoals Licensed Assisted Access (LAA) en verbeterde IoT-ondersteuning. Hierdoor word de datadoorvoer efficiënter gebruikt en latency verder verlaagd. Voor robot communicatie betekend dit dat real-time communicatie in industriële omgevingen betrouwbaarder word, ook bij een hoog aantal robots (Dahlman, Parkvall, & Sköld, 2016).

#Bronnen

Gielis, J., Shankar, A., & Prorok, A. (2022). A Critical Review of Communications in Multi-robot Systems. _Current Robotics Reports_, _3_(4), 213–225. Geraadpleegd op 26 november 2025, van https://doi.org/10.1007/s43154-022-00090-9

Holma, H., & Toskala, A. (2009). _LTE for UMTS_. Google Books. Geraadpleegd op 26 november 2025, van https://books.google.com/books?hl=nl&lr=&id=uhr3KwSww2kC&oi=fnd&pg=PR13&ots=qiGDz2337F&sig=8rezyFosXMbH2GE9J9FWKW-Hm94

Ahmadi, S. (2013b). _LTE-Advanced_. Google Books. Geraadpleegd op 26 november 2025, van https://books.google.com/books?hl=nl&lr=&id=DTsTAAAAQBAJ&oi=fnd&pg=PP1&ots=zU5O1ECjky&sig=RDli30PQhMQzbboZOhQP5I5rV-s

Dahlman, E., Parkvall, S., & Sköld, J. (2019). _4G, LTE-Advanced Pro and The Road to 5G_. Google Books. Geraadpleegd op 26 november 2025, van [https://books.google.nl/books?hl=nl&lr=&id=6J1FCgAAQBAJ&oi=fnd&pg=PP1&ots=OqEVXV4jEU&sig=96vaZYlvsiYwWBtM_dSbet0Vyfw&redir_esc=y#v=onepage&q&f=false](https://books.google.nl/books?hl=nl&lr=&id=6J1FCgAAQBAJ&oi=fnd&pg=PP1&ots=OqEVXV4jEU&sig=96vaZYlvsiYwWBtM_dSbet0Vyfw&redir_esc=y#v=onepage&q&f=false)