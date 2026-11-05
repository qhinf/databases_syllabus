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
