Databases en SQL
================

*Versie {{ versie }}. Jouw docent: {{ docent }} ({{ docent_email }})*

- Deadline voor het inleveren van de eindopdracht: **{{ deadline }}**
- Deadline voor het aanvragen van uitstel: **{{ deadline_uitstel_aanvragen }}**
  - Uitgestelde deadline: **{{ deadline_uitstel }}**


Oudere versie: [[databases-en-sql-old.md]]


Inhoudsopgave:

```{tableofcontents}
```

# Inleveropdrachten

Welkom bij een informaticamodule van de Q-highschool!

Deze module werkt met TWEE inleveropdrachten, die voor 10 oktober 16.00uur
moeten zijn ingeleverd.

## Deadline
- Laatste week van het "blok" (bij een vier-blokken-per-jaar rooster). De
docent vertelt je de deadline voor het blok bij elke les. Eerder inleveren mag.
- Inleveren via: https://app.q-highschool.nl/

## Zelfstandig werken en bronnen vermelden
De volgende uitgangspunten gelden voor deze module:

- Je maakt de opdracht zelf
- Als je iets overneemt van een boek of internet, doe je dat met bronvermelding
- Je werk is overzichtelijk en netjes

## Opdrachten met broncode
Informatica heeft vaak opdrachten met broncode, vormen van programmeerwerk.

- Je levert een bestand dat in voor computers en voor mensen leesbaar is
	- Let daarom goed op de instructies bij de opdracht
	
## Meerdere bestanden inleveren

- Maak een mapje met daarin de bestanden
- Maak van dat mapje een zip-bestand
- Lever het zip-bestand in via: https://app.q-highschool.nl/ 

# Inhoud van deze module, wat ga je leren

Aan het eind van deze module:

- Weet je wat een databases is, specifiek richten we ons op zogenaamde relationele databases
- Kun je gegevens opzoeken in een database met de vraag-taal SQL
- Kun je een eenvoudig datamodel ontwerpen
- Weet je dat er meer soorten database zijn dan alleen relationele databases (NoSQL)
- En bonus: we praten ook even over databases en regels

# De eindopdrachten

Er zijn bij deze module twee zaken die je moet inleveren:

1. Werken met queries in het systeem dat de docent heeft gemaakt, zie [de query-taal SQL]
2. Het maken van een database-ontwerp, meer informatie vind je ....

# Wat is een (relationele) database

> Een database is een systeem dat gegevens opslaat en doorzoekbaar maakt

Een database is een computersysteem dat gegevens opslaat op een gestructureerde
manier. Een goed ontworpen database maakt het mogelijk gegevens weer snel en
efficient terug te kunnen vinden. En niet 'een gokje' te doen naar die gegevens
(zoals google of een AI), maar *exact* de juiste gegevens terugvindt.

Een database heeft daarom intern een structuur die lijkt op een excel-sheet:
het heeft *tabellen* met daarin kolommen en rijen.


Waar bestaan databases? Overal waar computers zijn. Bijna elke app in je
telefoon heeft waarschijnljk een database. Chat apps bijvoorbeeld voor al je
chats en contacten. Je telefoon voor al je contacten met een telefoonnummer.

Een betaal-en-bankieren-app heeft contact met een centrale database van de bank
om te weten wat het saldo is en wat er met je geld is gebeurd.

Een school heeft databases voor het bijhouden van leerlingen, klassen, cijfers,
    vakken, docenten etc.

Niet elk van deze tabellen is een relationele database waarmee we kennis maken
in deze module, al zal het je verbazen hoeveel dat er wel zijn.

> Voor wie dieper wil duiken: zoek SQLite op. De website is underwhelming maar
> er zijn letterlijk duizend miljard (een miljoen keer een miljoen) sqlite
> databases actief op de wereld

## Garanties van (relationele) databases

Databases worden door software ontwikkelaars gezien als "betrouwbaar". Dat
betekent dat ze de database zien als een systeem dat als het ware altijd gelijk
heeft. Dit komt door de manier waarop we databases ontwerpen, maar ook door wat
database systemen bieden: garanties.


### Garantie 1: iets gebeurt helemaal, of helemaal niet (atomic)

Als je vraagt aan een database om iets toe te voegen, verwijderen of bij te
werken, dan gebeurt dat ofwel compleet, ofwel helemaal niet. Hierdoor weet je
zeker dat de inhoud van de database altijd 'sense' maakt.

### Garantie 2: consistent

Bij het ontwerpen en inrichten van een database vertellen we zoveel mogelijk
aan de database wat de spelregels zijn. Dit noemen we **constraints**, in het
Nederlands **beperkingen**. De database zal die constraints bewaken en alleen
een actie afmaken als de constraints dat toelaten.

### Garantie 3: isolation

Grotere systemen hebben vaak meerdere gebruikers tegelijk. En voor die
gebruikers worden onafhankelijk van elkaar acties uitgevoerd op de database. De
database houdt wijzigingen onzichtbaar voor de ander, totdat die zeker is dat
alles consistent is en veilig kan worden doorgevoerd.

Je kunt in een database meerdere acties bundelen in een **transaction**, die allemaal als 'atomair' (zie boven) worden gezien en dus allemaal samen doorgaan, of niet doorgaan.

### Garantie 4: durability (duurzaamheid)

Een database geeft pas aan dat een actie klaar is, als die er zeker van is dat
de actie onherroepelijk is uitgevoerd. Dus als direct daarna de stroom uitvalt,
dan heeft de database het resultaat opgeslagen op de vaste opslag. Komt de
database weer terug, dan kun je er zeker van zijn dat de data er is.


### Gevolgen van garanties

Een voordeel kan nadelen met zich meebrengen.

Een database kan rijen of soms zelfs hele tabellen op slot zetten, totdat een actie
klaar is. Dit kan betekenen dat andere processen moeten wachten tot dat slot
eraf is. Dit kan zorgen voor vertraging. Sterker nog: soms wachten processen op zo'n manier op elkaar
dat ze geen ban allen meer vooruit komen. Dat heet een **deadlock**.

En de laatste garantie heeft ook een nadeel. Een database *moet* gegevens
wegschrijven naar de vaste opslag. Dat is niet altijd efficient.
Besturingssytemen van computer willen dat graag optimaliseren en soms even
wachten met gegevens wegschrijven. 

# Hoe werkt een **relationele** database

> Een tabel is als een excelsheet, met precieze kolommen en rijen

Een tabel (todo: plaatje) ziet er uit als een excel-sheet. Er is wel een
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

(todo: maak voorbeeld-tabellen)

## Begrippen

- Tabel
- Rij
- Kolom



# De vraag-taal SQL

> SQL: Een studievriend van de docent noemde het ooit *silly question
> language*, die grap mag je van harte overnemen!

## SQL: structured query language

Al sinds het begin van de informatica is er een zoektocht naar programmeertalen
die 'makkelijk' zijn. Dit zodat meer mensen met computers kunnen werken. Zeker
in de tijd dat er nog geen touch-screens en zelfs nog geen computermuis bestond
was dit erg lastig. Laat staan de AI's van nu!

De essentie van SQL is dat je de database laat weten *wat* je wil zien, maar niet *hoe* die dat moet gaan vinden. 

Alle kolommen laten zien van de tabel `docent`:
```sql
select * from docent;

```
Veel meer uitleg en de eerste inleveropdracht vind je op de website: [Sjaaq][https://sql.merijn.xyz]
het systeem waar je queries kunt uitvoeren en maken.

# Eindopdracht 1: SQL

Veel meer uitleg over SQL en de eerste inleveropdracht vind je op de website: [Sjaaq][https://sql.merijn.xyz]
Dit is door de docent gemaakt. De score is lineair: hoe meer vragen je goed hebt, hoe hoger je cijfer!





