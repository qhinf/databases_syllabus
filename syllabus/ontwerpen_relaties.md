# Database-ontwerp: relaties

Een relationele database draait om de relaties die _entiteiten_ met elkaar kunnen hebben:

- _klant_ koopt _product_ 
- _auto_ wordt onderhouden door een _monteur_
- _docent_ doceert één of meer _vakken_


We willen in een ontwerp deze relaties zo precies mogelijk vastleggen.

> Een relatie werkt twee kanten op; dat werkt ook zo bij entiteiten in een database-ontwerp

## Nul, een, meer? 'kardinaliteit'

Voor een database-ontwerp is het van belang te weten 'hoeveel' van de ene entiteit hoort bij de andere entiteit.
Bij de analyse stellen we vragen, zoals: "Klopt het dat een klant meerdere producten in een winkelmandje kan leggen?"
en "Klopt het dat een winkelmandje bij precies 1 klant hoort?".

>Dit lijken eenvoudige vragen; dit klopt voor zo'n beetje elke online winkel! Soms weten we het antwoord niet meteen zoals de vraag: Klopt het dat een patiënt maximaal 1 infuuspomp tegelijk gebruikt? (Nee, soms zijn er meer medicijnen die onafhankelijk worden toegediend...)

Om deze aantallen vast te leggen zijn er in een database-ontwerp precies vier mogelijkheden voor de relaties:

- Nul of één
- Precies één
- Nul of meer
- Eén of meer


Voorbeelden:

- Van een klant weten we nul of één e-mailadres
- Elke regel in een bestelling hoort bij precies één bestelling
- Een product wordt gekocht door nul of meer klanten
- Elke bestelling omvat één of meer producten

*Maar* dit is maar de helft van het verhaal! Van al deze zaken willen we ook de andere kant van de relatie weten. Bijvoorbeeld:

- Iedere bestelling bestaat uit één of meer regels, en
- Iedere klant koopt één of meer producten.

### ERDish-zinnen

We willen ervoor zorgen dat we structureel alle relaties in de database goed beschrijven.
Dit doen we door relaties tussen entiteiten te beschrijven in een precieze structuur. Voorbeelden:

- _auto_ en _monteur_:
    - *Iedere* _auto_ wordt onderhouden door **precies één** _monteur_.
    - *Iedere* _monteur_ onderhoudt **één of meer** _auto's_.

- _product_ en _klant_
    - *Ieder* _product_ wordt gekocht door **nul of meer** _klanten_.
    - *Iedere* _klant_ koopt **één of meer** _producten_.

Aan de voorbeelden kun je zien dat die zinnen altijd dezelfde structuur hebben:

_Iedere_ **entiteit A** __werkwoord__ ..aantal.. **entiteit B**


En dat de zinnen altijd in paren voorkomen. Als er een relatie is tussen twee entiteiten, dan moet je beide kanten van de relatie beschrijven.

### Voorbeelden van ERDish-zinparen

- Iedere leerling volgt één of meer vakken. Ieder vak wordt gevolgd door nul of meer leerlingen.
- Elke medewerker werkt voor precies één afdeling. Voor iedere afdeling werken één of meer medewerkers.
- Elke klant plaatst nul of meer bestellingen. Iedere bestelling is voor precies één klant.
- Elke gebruiker heeft één of meer accounts. Elk account hoort bij precies één gebruiker.


## Entiteit-relatie-diagrammen, een plaatje zegt meer

De 'kardinaliteit' die we hierboven beschreven met woorden als 'precies één', 'één of meer' tekenen we als zogenaamde kraaienpoten (de Engelse term
hiervoor is crow's feet). Dit is een veelgebruikte manier om in een diagram de hoeveelheid (kardinaliteit) van een relatie te beschrijven.

Deze kraaienpoten zien er zo uit:


![Plaatje van de vier kraaienpoten](assets/ontwerpen_relaties/kraaienpoot-notatie-legenda.png)

Een rondje of een streep voor nul of één. Een enkele streep of drie streepjes in de vorm van een 
vogelpootje voor de 'meer'-variant.


## Van ERDish-zinnen naar een ERD

We hebben ERDish-zinnen gemaakt om de relaties tussen entiteiten te beschrijven. Dit zetten
we om in een diagram op de volgende manier.

- _auto_ en _monteur_:
    - *Iedere* _auto_ wordt onderhouden door **precies één** _monteur_.
    - *Iedere* _monteur_ onderhoudt **één of meer** _auto's_.

![Plaatje van auto monteur ERD](assets/ontwerpen_relaties/erd-voorbeeld-auto-monteur.png)

In dit plaatje:
- Wordt iedere entiteit getoond als rechthoek met afgeronde hoeken.
- Zijn attributen opgenomen
- Staan kraaienpoten
- Staat de betekenis van de relatie beschreven op de lijn


Als er meer entiteiten zijn, dan worden die allemaal ondergebracht in een grote plaat.
In het volgende hoofdstuk zien we daarvan een voorbeeld.
