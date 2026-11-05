# Databases ontwerpen

Een database is gemaakt door mensen en voor mensen (en voor machines... die werken voor mensen). Dus een database
moet worden ontworpen. In deze sectie leer je hoe we komen tot een 'zinnig' database ontwerp. Een database die werkt,
zowel voor de beperkingen van een relationeel database systeem, als voor het uitdrukken van de beperkingen van de 'echte' wereld.


## Hoe gaan we te werk

Om een computersysteem, zoals een database, te maken zodat het gebruikt kan worden, hebben we meestal ongeveer deze stappen:

1. Analyse: wat moet er in de database
    - Vragen stellen aan de opdrachtgevers
    - Uitwerkingen maken in diagrammen en terugkoppelen
    - Soms zelfs een proof-of-concept maken

2. Ontwerpen
    - Technisch uitwerken wat alle details zijn van het systeem
    - Bij problemen (iets in de analyse is onmogelijk in techniek), terug naar stap 1

3. Realisatie
    - Het uitwerken van het ontwerp tot een echt systeem
    - Het ergens plaatsen van het systeem zodat het bereikbaar is (hosting)

4. Demonstreren
    - Demo's geven van dit systeem en de klant laten testen

5. Op basis van terugkoppeling bij de demonstratie terug naar stap 2 en het ontwerp bijstellen

En dit proces herhaalt zich tot we een punt bereiken waarop we tevreden zijn voor een eerste live-gang.
De meeste applicaties die we zo maken worden daarna constant bijgewerkt met nieuwe features, en anders op zijn
minst onderhouden.

## Beperkingen van een relationele database

Zoals we ontdekt hebben bij onze avonturen met SQL, werken relationele databases met tabellen.
In de tabel leggen rijen een 'opname' vast: een weergave van 'iets' in de werkelijkheid. De kolommen van een tabel
zijn de eigenschappen van een opname (of je noemt dat een rij, of in het Engels een record).

Ook weten we van onze lessen met SQL dat er relaties bestaan tussen tabellen. Een kolom in een tabel kan verwijzen
naar een andere tabel. Dit beperkt ons: het is niet mogelijk om direct twee tabellen te koppelen waarbij `docenten` meerdere `vakken` kunnen geven als vakken ook moeten worden gegeven door meerdere docenten.

## Datamodel-ontwerp: terminologie

We zijn nu gewend geraakt aan de termen `tabel`, `kolom` en `rij`. In de database-ontwerp wereld spreken we van:

- *Entiteit*: een 'dinges', een entiteit komt min of meer overeen met een *tabel*
- *Attribuut*: een eigenschap van een entiteit, een attribuut komt min of meer overeen met een *kolom*
- *Type*: een attribuut heeft een type, dat wil zeggen, een beperking in wat voor waarden erin kunnen. Bij onze SQL lessen hebben we gezien dat kolommen een type hebben: getal, tekst, datum; en zo zijn er meer.

Het begrip 'rij' komt niet terug in het ontwerp: de rijen zijn er pas in het gebruik!

## Datamodel-ontwerp: oefeningen

In de lessen bespreek ik wat oefeningen die we doen om tot een database ontwerp
te komen. Gegeven wat tekst of simpelweg een denkbeeldige omgeving: wat zouden
de entiteiten zijn en wat zijn de eigenschappen van zulke entiteiten.


### Voorbeeld uit de les: NS

Jullie docent, Merijn, heeft een paar keer opdrachten bij de NS, de Nederlandse Spoorwegen, gehad.
Wat zouden `entiteiten` kunnen zijn in de wereld van de NS? 

Antwoorden die zoal voorbij komen zijn:

- trein
- station
- kaartje
- ov-chipkaart
- paaltjes / poortjes

Een aardig verhaal bij de NS is dat ze in hun IT-systemen proberen het woord 'trein' te vermijden. Het kan veel verschillende dingen betekenen! 

- een fysiek apparaat dat op rails rijdt,
- een gepland vertrek van station Utrecht, spoor 12, om 17:32 uur in de richting van Amsterdam,
- een goederentrein (die de passagiers dienstverlening dreigt te verstoren)

Een fysieke trein wordt ook wel 'materieel' genoemd; en dan is er nog 'personeel' nodig, machinisten, conducteurs.
En zelfs de term 'bak-samenstellingseenheid' of zoiets is wel ergens gespot; een fysieke trein die uit delen kan bestaan:
je ziet in de trein een 'treinnummer'. Zo'n nummer is zonder twijfel een attribuut van een entiteit in een database!


### Voorbeeld uit de les: een winkel

Webshops zijn er te over. Bedenk entiteiten waar je aan denkt bij een webshop.

:::{tip}
Doe dit eerst zonder er een te bekijken. Daarna bekijk er eens een; komen er meer naar boven?
:::
