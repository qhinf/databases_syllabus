# Hoe werkt een relationele database

> Een tabel is als een Excel-sheet, met precieze kolommen en rijen

Een tabel <!-- todo: plaatje --> ziet er uit als een Excel-sheet. Er is wel een
belangrijk verschil. Excel laat je toe om willekeurig wat in de vakjes te
zetten. Een database laat dat niet toe.

Elke **rij** in een tabel is een **record**, een 'vastlegging'. Deze rij
vertegenwoordigt precies 1 ding in de "werkelijkheid" van het systeem.
Bijvoorbeeld een product op een website. Of een speler in een spel. Of een
rekening in een banksysteem.

Elke tabel heeft vaste **kolommen**. Deze kolommen zijn de eigenschappen van
de records in de tabel.

## Voorbeelden

### Een gebouw heeft een nummer en een naam

```{table} Gebouw
| id | naam                 |
|----|----------------------|
| 1  | Kasteel op de heuvel |
| 2  | Ziekenhuis           |
```

De reden om een nummer toe te voegen is om, onafhankelijk van de inhoud, altijd een uniek kenmerk te hebben per rij.
Daar zijn technische redenen voor, onder andere omdat computers sneller kunnen rekenen met getallen dan met tekst.

### Een bank met gebruiker, rekening, transacties

Een bank houdt bij wie haar klanten zijn, welke rekeningen er zijn en welke
transacties (overboekingen, pinbetalingen) er op die rekeningen gebeuren. Elk
van deze dingen krijgt een eigen tabel:

```{table} Gebruiker
| id | voornaam | achternaam |
|----|----------|------------|
| 1  | Sanne    | de Vries   |
| 2  | Ahmed    | Benali     |
```

```{table} Rekening
| id | iban               | soort    |
|----|--------------------|----------|
| 1  | NL01QBNK0123456789 | betaal   |
| 2  | NL02QBNK9876543210 | spaar    |
| 3  | NL03QBNK1122334455 | betaal   |
```

```{table} Transactie
| id | datum      | bedrag  | omschrijving     |
|----|------------|---------|------------------|
| 1  | 2026-11-02 | -4.50   | Kantine          |
| 2  | 2026-11-03 | 250.00  | Salaris bijbaan  |
| 3  | 2026-11-03 | -100.00 | Naar spaarrekening |
```

Je ziet dat in deze tabellen nog niet staat *welke* rekening van *welke*
gebruiker is, of bij welke rekening een transactie hoort. Hoe je tabellen aan
elkaar koppelt, leer je in [](sleutels_en_relaties.md).

## Begrippen

- Tabel
- Rij
- Kolom

## De vraagtaal SQL

> SQL: Een studievriend van de docent noemde het ooit *silly question
> language*, die grap mag je van harte overnemen!

### SQL: structured query language

Al sinds het begin van de informatica is er een zoektocht naar programmeertalen
die 'makkelijk' zijn. Dit zodat meer mensen met computers kunnen werken. Zeker
in de tijd dat er nog geen touchscreens en zelfs nog geen computermuis bestond
was dit erg lastig. Laat staan de AI's van nu!

De essentie van SQL is dat je de database laat weten *wat* je wilt zien, maar niet *hoe* die dat moet gaan vinden.

Alle kolommen laten zien van de tabel `docent`:

```sql
select * from docent;
```

Alle verdere uitleg over SQL vind je in {{ squeek }}, het systeem waar je
queries kunt uitvoeren en maken. Daar maak je ook
[](eindopdracht_sql.md).
