# Hoe werkt een **relationele** database

> Een tabel is als een excelsheet, met precieze kolommen en rijen

Een tabel <!-- todo: plaatje --> ziet er uit als een excel-sheet. Er is wel een
belangrijk verschil. Excel laat je toe om willekeurig wat in de vakjes te
zetten. Een database laat dat niet toe.

Elk **rij** in een tabel is een een **record**, een 'vastlegging'. Deze rij
vertegenwoordigt precies 1 ding in de "werkelijkheid" van het systeem.
Bijvoorbeeld een product op een website. Of een speler in een spel. Of een
rekening in een banksysteem.

Elke tabel heeft vaste, **kolommen**. Deze kolommen zijn de eigenschappen van
de records in de tabel.


Enkele voorbeelden:

### Een gebouw heeft een nummer en een naam

| Gebouw | |
|----|---------------------|
| **id** | **naam**        |
| 1 | Kasteel op de heuvel |
| 2 | Ziekenhuis           |

De reden om een nummer toe te voegen is om, onafhankelijk van de inhoud, altijd een uniek kenmerk te hebben per rij.
Daar zijn technische redenen voor, onder andere omdat computers sneller kunnen rekenen met getallen dan met tekst.


### Een bank met gebruiker, rekening, transacties

<!-- todo: maak voorbeeld-tabellen -->

## Begrippen

- Tabel
- Rij
- Kolom


## De vraag-taal SQL

> SQL: Een studievriend van de docent noemde het ooit *silly question
> language*, die grap mag je van harte overnemen!

### SQL: structured query language

Al sinds het begin van de informatica is er een zoektocht naar programmeertalen
die 'makkelijk' zijn. Dit zodat meer mensen met computers kunnen werken. Zeker
in de tijd dat er nog geen touch-screens en zelfs nog geen computermuis bestond
was dit erg lastig. Laat staan de AI's van nu!

De essentie van SQL is dat je de database laat weten *wat* je wil zien, maar niet *hoe* die dat moet gaan vinden. 

Alle kolommen laten zien van de tabel `docent`:
```sql
select * from docent;

```
Al mijn uitleg en de eerste inleveropdracht vind je op de website: {{ sjaaq }}
het systeem waar je queries kunt uitvoeren en maken. Dat systeem slaat je antwoorden op en op die manier zijn ze ook meteen ingeleverd, handig!
