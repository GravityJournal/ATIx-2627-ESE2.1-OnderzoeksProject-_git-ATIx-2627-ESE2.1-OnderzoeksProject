### Wat is er veranderd ten opzichte van v1?

| Wat | In v1 | In v2 | Waarom |
|--|--|--|--|
| Storingstool | clumsy of tc netem | Eigen programma storing.cpp | Windows Defender zette een onderdeel van clumsy in quarantaine. Met een eigen programma kan ik de storingen ook precies herhalen. |
| Pakketverlies (S1, S2) | Echt pakketverlies | Bericht wordt soms 300 ms vastgehouden | TCP stuurt een verloren pakket zelf opnieuw. Ik doe dat effect na. Het is dus geen echt pakketverlies. |
| S3 | Elke 30 seconden 2 s weg | Elke 5 seconden 2 s weg | Een run duurt ongeveer 12 seconden. Bij 30 seconden zou er geen storing in vallen. |
| MQTT | Alleen A loopt door de storingstool | A en B lopen allebei door de storingstool | Anders meet ik bij MQTT maar de helft van de weg en is de vergelijking met TCP niet eerlijk. |
| Pakketten tellen | Wireshark | storing.cpp telt bytes en stukjes | Dit kon ik zo in de testscripts meenemen. TCP/IP-headers tel ik dus niet mee. |