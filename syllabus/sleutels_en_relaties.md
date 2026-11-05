# Sleutels en relaties

Deze module gaat over _relationele_ databases. Dat betekent dat tabellen in een database een relatie kunnen hebben met andere tabellen.

> `¯\_(ツ)_/¯` Het database systeem _postgres_ noemt een _tabel_ een _relation_, dus als je een fout maakt zie je soms 'relation ... does not exist' of zoiets; dan bedoelt postgres een tabel. Naar _mijn_ mening is dat incorrect gebruik van de term relatie; dat is iets tussen twee tabellen. Vind ik.


## Sleutels

Elke rij in een tabel is de vastlegging (een record) van een feit, ding, gebeurtnis etc. Dat zou een 'uniek' iets moeten zijn.
Zouden we leerlingen alleen met voornaam opslaan dan krijgen we al gauw een probleem. Zelfs de combinatie van voor- en achternaam *en* geboortedatum is niet altijd uniek. (De docent heeft een vriend die hier daadwerkelijk last van heeft gehad!). Om die reden is het handig een _technische_ unieke identificatie-kolom te maken. Die noemen we vaak `id`:


| Docent | | |
|----|--------|------------|
| *id* | *voornaam*   | *achternaam* |
|----|--------|------------|
| 1  | Merijn | Vogel      |
| 2  | Arthur | Rump       |
| 3  | Pieter | van Engelen|
| 4  | Karen  | van Wichen |


Zo'n kolom heet `primary key`, de belangrijkste sleutel, van de tabel. Een tabel kan maximaal 1 primary key hebben.

Bij het aanmaken van een tabel met SQL, vertellen we dit ook aan de database:

```sql
CREATE table Vrienden ( id int PRIMARY KEY, naam VARCHAR, Geboortedatum DATETIME);
```


Stel we maken een tweede tabel met parcoursen:

| Parcours |  |
|----|--------|
| *id* | *naam*   |
|----|--------|
| 100  | Informatica | 
| 101  | Filosofie | 


Deze heeft ook een primary key.

## Relatie

Nu willen we graag docenten en parcoursen aan elkaar koppelen.
Voor het gemak gaan we ervanuit dat elke docent maar 1 module kan geven. We kunnen dan de tabel van docenten uitbreiden:

| Docent |    |            |     |
|----|--------|------------|-----|
| *id* | *voornaam*   | *achternaam* | *parcours_id* |
|----|--------|------------|--------|
| 1  | Merijn | Vogel      | 101 |
| 2  | Arthur | Rump       | 101 |
| 3  | Pieter | van Engelen| 101 |
| 4  | Karen  | van Wichen | 102 |

We noemen hier niet de naam van de module, maar we verwijzen naar de _primary key_ van de tabel _parcours_. Dit legt de _relatie_ vast tussen de twee tabellen.
Door te wijzen naar de _primary key_ van de andere tabel helpen we de database: deze kan efficient de gegevens bij elkaar halen.


Dit kunnen we aan SQL vertellen op bijvoorbeeld de volgende manier:

```sql
alter table Docent add column parcours_id int references Parcours(id);
```

De kolom *parcours_id* heet een _foreign key_: de primaire sleutel van een _andere_ (foreign) tabel.

> De relatie tussen twee tabellen loopt via de _primaire sleutel_ van een van de twee tabellen. Een rij in een tabel verwijst naar de _id_-kolom van de tabel waar die een relatie mee heeft.


In een plaatje:

![Plaatje van twee tabellen met een relatie](assets/sleutels_en_relaties/db-relaties-20250918.drawio.png)

Databases zullen een relatie afdwingen: je kunt alleen nieuwe rijen toevoegen die aan de relatie voldoen; en je kunt rijen niet weghalen als er een verwijzing naartoe is. Die bescherming is een belangrijke eigenschap van relationele databases.
