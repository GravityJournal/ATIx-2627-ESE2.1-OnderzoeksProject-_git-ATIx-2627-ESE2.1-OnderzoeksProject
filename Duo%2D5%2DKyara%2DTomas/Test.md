```mermaid
graph BT
    %% Definiëren van de technologieën met hun totale scores
    5G["5G (Totaal: 48)]
    WIFI["Wi-Fi 7 (Totaal: 43)]
    ETH["Ethernet (Totaal: 35)]
    BT["Bluetooth (Totaal: 29)]

    %% Visuele hiërarchie op basis van de rangschikking
    BT --> ETH
    ETH --> WIFI
    WIFI --> 5G

    %% Styling voor extra scannabiliteit
    style 5G fill:#1f77b4,stroke:#333,stroke-width:2px,color:#fff
    style WIFI fill:#aec7e8,stroke:#333,stroke-width:1px
    style ETH fill:#ffbb78,stroke:#333,stroke-width:1px
    style BT fill:#ff7f0e,stroke:#333,stroke-width:1px
```
