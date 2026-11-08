# Contentmap: wat elk hoofdstuk docet

Vertrekpunt voor elke inhoudelijke aanpassing. Per hoofdstuk: wat erin staat,
welke termen er worden geïntroduceerd, en wat er (nog) níet in staat.
Woordaantallen zijn indicatief (stand november 2026).

## Korte index

| # | Bestand | Titel op de site | Woorden | Beeld | Oefeningen |
|---|---------|------------------|---------|-------|------------|
| – | `index.md` | Databases en SQL | 411 | 0 | 0 |
| 1 | `wat_is_een_database.md` | Wat is een (relationele) database | 603 | 0 | 0 |
| 2 | `tabellen_en_sql.md` | Hoe werkt een relationele database | 500 | 0 | 0 |
| 3 | `sleutels_en_relaties.md` | Sleutels en relaties | 549 | 1 | 0 |
| 4 | `ontwerpen_entiteiten.md` | Databases ontwerpen | 693 | 0 | 0 |
| 5 | `ontwerpen_relaties.md` | Database-ontwerp: relaties | 648 | 2 | 0 |
| 6 | `meer_meer_relaties.md` | Meer-meer: werkt in een ERD, maar niet in een relationele database | 339 | 2 | 1 |
| 7 | `nosql.md` | NoSQL: andere soorten databases | 5 | 0 | 0 |
| 8 | `verdieping_attributen.md` | Meer over entiteiten en attributen | 1019 | 2 | 4 |
| 9 | `verdieping_relaties.md` | Meer over relaties en ERD's | 1030 | 7 | 4 |
| 10 | `verdieping_ontwerp_verbeteren.md` | Een ERD verbeteren | 586 | 7 | 6 |
| 11 | `verdieping_erd_naar_sql.md` | Van ERD naar SQL | 809 | 2 | 2 |
| 12 | `eindopdracht_sql.md` | Eindopdracht 1: SQL | 58 | 0 | 0 |
| 13 | `eindopdracht_ontwerp.md` | Eindopdracht 2: Een databasemodel ontwerpen | 196 | 0 | 0 (casus) |

Totaal: ~7450 woorden, 23 afbeeldingen (alle gebruikt, geen losse resten),
17 oefenopdrachten, **1 uitwerking** (`:::{solution}` in `meer_meer_relaties.md`).

## De stof in één verhaal

De module vertelt één doorlopend verhaal in drie stappen:

1. **Wat is een database** — tabellen, rijen, kolommen, en waarom een database
   meer belooft dan een excel-sheet (garanties, constraints).
2. **Zoek en koppel** — SQL als vraagtaal (wat, niet hoe), en tabellen aan
   elkaar koppelen via primary key → foreign key.
3. **Ontwerp eerst, SQL later** — entiteiten/attributen/relaties → ERD →
   redundantie en meer-meerrelaties oplossen (koppeltabel) → SQL-DDL.

Het SQL-gedeelte zelf (oefenen, meer syntax) staat bewust **niet** in deze syllabus:
dat gebeurt in Squeek, het oefensysteem van de docent.

## Termenlijst (gebruik deze paartjes consequent)

| In de lesstof (fysiek) | In het ontwerp (logisch) | In SQL-DDL |
|---|---|---|
| tabel | entiteit | `CREATE TABLE` |
| rij, record | (geen — "rijen zijn er pas in het gebruik") | rij |
| kolom | attribuut (+ type) | kolom met datatype / `NOT NULL` |
| `id`, primary key | UID (primary of secondary) | `PRIMARY KEY` |
| foreign key, vreemde sleutel | relatie met kraaienpoten | `FOREIGN KEY(...) REFERENCES ...` |
| — | kardinaliteit (nul of één / precies één / nul of meer / één of meer) | — |
| — | ERDish-zinnen (altijd in paren) | — |
| — | redundantie | — |
| constraints, beperkingen | constraints (buiten het ERD) | `NOT NULL`, `PRIMARY KEY`, `FOREIGN KEY` |
| transaction, deadlock | — | — |
| — | tussenentiteit / koppeltabel | tabel met samengestelde PK |
| SQL-DML (`SELECT ... FROM`) | — | SQL-DDL (`CREATE TABLE`, `ALTER TABLE`) |

ERD-notatie in de syllabus (twee stijlen, bewust):

- **Lesstof-stijl** (PNG's, draw.io): rechthoek met afgeronde hoeken,
  entiteitnamen met kleine letters, attributen in de entiteit, kraaienpoten,
  de betekenis van de relatie op de lijn.
- **Verdiepings-stijl** (JPG's, ouder SLO-materiaal): ENTITEITEN IN
  HOOFDLETTERS, plus `#` = primary UID, `(#)` = secondary UID, `*` = verplicht
  attribuut, `o` = optioneel attribuut; **doorgetrokken** lijn =
  ouder-kindrelatie, **gestippeld** = gewone relatie.
- Kraaienpoten zelf worden in beide stijlen hetzelfde gelezen.

## Hoofdstuk per hoofdstuk

### `index.md` — startpagina

Deadlines en docent via substituties, inleveren via https://app.q-vakken.nl/,
twee eindopdrachten (50/50), huiswerkregels (zelfstandig werken,
bronvermelding, netjes/leesbaar, zip bij meerdere bestanden), uitleg dat
*Verdieping* extra is en niet verplicht, en de colofon: de verdieping is
afgeleid van de SLO-cursus *Databasedesign* (Eelco Dijkstra), *van ERD naar
SQL* gebruikt materiaal van Heer deBeer, herschreven in 2023 en 2025 door
Merijn Vogel. Leerdoelen staan hier (zie `project_overview.md`).

### `wat_is_een_database.md` — why databases are trusted

- Definitie: systeem dat gegevens opslaat **en doorzoekbaar maakt**; een
  database vindt *exact* de juiste gegevens terug, in tegenstelling tot een
  "gokje" van Google of een AI.
- Intern lijkt de structuur op een excel-sheet: tabellen met kolommen en rijen.
- Herkenbare voorbeelden: chatapps en contacten in je telefoon, betaal-/bankierapp,
  school (leerlingen, klassen, cijfers, vakken, docenten).
- Side-note: SQLite (naar eigen zeggen "duizend miljard actieve databases").
- **Vier garanties** (ACID, maar de term ACID valt nergens):
  1. atomic — compleet of helemaal niet;
  2. consistent — je vertelt de database de spelregels = **constraints**/beperkingen;
  3. isolation — gelijktijdige gebruikers, wijzigingen blijven verborgen tot
     het consistent is; bundelen kan in een **transaction**;
  4. durability — klaar is pas klaar als het op de vaste opslag staat.
- Nadelen: slot op rijen/tabellen → vertraging, **deadlock**; verplicht
  wegschrijven botst met optimalisatie door het besturingssysteem.
- Termen die hier voor het eerst vallen: constraints/beperkingen, transaction,
  deadlock. Geen plaatjes.

### `tabellen_en_sql.md` — tabellen en de vraagtaal

- "Een tabel is als een Excel-sheet, met precieze kolommen en rijen"; verschil:
  Excel tolereert willekeurige inhoud, een database niet.
- Rij = **record** = vastlegging van precies 1 ding uit de "werkelijkheid"
  (product op een website, speler in een spel, rekening in een banksysteem);
  kolommen = eigenschappen van die records.
- Voorbeeldtabellen (met ```{table}``): `Gebouw` (id + naam) — met uitleg *waarom*
  een nummer: uniek kenmerk onafhankelijk van de inhoud, en computers rekenen
  sneller met getallen dan met tekst.
- Bankvoorbeeld: `Gebruiker`, `Rekening`, `Transactie` — expliciet **nog niet**
  aan elkaar gekoppeld; de koppeling wordt uitgesteld naar
  `[](sleutels_en_relaties.md)`.
- Begrippenlijstje: Tabel, Rij, Kolom.
- SQL: "silly question language"-grap van een studievriend van de docent; de
  kern is dat je alleen zegt *wat* je wilt zien, niet *hoe*; één voorbeeldquery
  `select * from docent;`; verder SQL staat in {{ squeek }} en bij de eindopdracht.
- In-text todo: `<!-- todo: plaatje -->` — er is géén plaatje van een tabel,
  terwijl dat het eerste visuele anker van de module zou moeten zijn.

### `sleutels_en_relaties.md` — primary key en foreign key

- Terreinverduidelijking in een quote: Postgres noemt een tabel een _relation_
  ("relation ... does not exist"), en de docent vindt dat incorrect gebruik van
  het woord relatie ("Vind ik.").
- Waarom een technische id: voornaam niet uniek, voor- + achternaam +
  geboortedatum ook niet altijd uniek (met persoonlijk voorbeeld van de docent).
- `primary key`: één per tabel. SQL:
  `CREATE TABLE Docent (id int PRIMARY KEY, voornaam VARCHAR, achternaam VARCHAR);`
- Tweede tabel `Parcours` (id 100 Informatica, 101 Filosofie). Met de bewuste
  vereenvoudiging "elke docent kan maar 1 parcours geven" krijgt `Docent` de kolom
  `parcours_id`, die verwijst naar de PK van de andere tabel → dat is de
  **relatie**; verwijzen naar de PK helpt de database efficiënt gegevens bij
  elkaar te halen.
- SQL: `ALTER TABLE Docent ADD COLUMN parcours_id int REFERENCES Parcours(id);`
  en de definitie van **foreign key**: de primaire sleutel van een andere tabel.
- Box-quote-kern: "De relatie tussen twee tabellen loopt via de primaire
  sleutel van een van de twee tabellen."
- Afsluiting: de database dwingt de relatie af (geen nieuwe rijen die niet
  voldoen; je kunt rijen niet weghalen als er naar verwezen wordt). Dit is
  referentiële integriteit, maar die term wordt expliciet niet gebruikt.
- Bekende fout: het plaatje `db-relaties-20250918.drawio.png` toont tabellen
  `Docent`↔`Vak` met id's 1–3, terwijl de tekst `Parcours` 100/101 gebruikt
  (in-text todo + punt in `todo.md`).

### `ontwerpen_entiteiten.md` — ontwerpen: werkwijze en terminologie

- Ontwerpproces in vijf stappen: **Analyse** (vragen stellen aan opdrachtgevers,
  uitwerkingen in diagrammen, soms proof-of-concept) → **Ontwerpen** (technisch
  uitwerken; bij onmogelijkheid terug naar analyse) → **Realisatie** (echt systeem
  + hosting) → **Demonstreren** (demo's, klant laat testen) → **bijstellen op
  basis van terugkoppeling**, iteratief tot een eerste livegang; daarna
  constante updates of op zijn minst onderhoud.
- Beperkingen van een relationele database: je werkt met tabellen, en een kolom
  kan alleen verwijzen naar één andere tabel; `docenten` die meerdere `vakken`
  geven en `vakken` die door meerdere docenten gegeven worden kan niet direct.
- Terminologie-overgang: *entiteit* ≈ tabel, *attribuut* ≈ kolom, *type* =
  beperking in de waarden (getal, tekst, datum, meer). "Rij" komt in het
  ontwerp niet terug: rijen bestaan pas in het gebruik.
- Voorbeeld uit de les **NS**: kandidaat-entiteiten trein, station, kaartje,
  ov-chipkaart, paaltjes/poortjes. Leuk detail: NS probeert in zijn IT-systemen
  het woord "trein" te vermijden omdat het veel betekent (fysiek apparaat op
  rails / gepland vertrek vanaf Utrecht spoor 12 om 17:32 richting Amsterdam /
  goederentrein die de passagiersdienstverlening dreigt te verstoren); fysieke
  trein = "materieel", plus personeel (machinisten, conducteurs) en zelfs
  "bak-samenstellingseenheid"; een treinnummer is onmiskenbaar een attribuut.
- Voorbeeld uit de les **webshop**: bedenk entiteiten, met de `:::{tip}` om het
  eerst zonder een webshop te bekijken te doen.
- Let op: deze hoofdstukken hebben géén `:::{exercise}`-blokken — de oefeningen
  worden in de les mondeling gedaan. Ook geen plaatjes, terwijl hier net de
  ontwerp-taal wordt geïntroduceerd.

### `ontwerpen_relaties.md` — kardinaliteit en ERDish-zinnen

- Relaties werken twee kanten op (voorbeeldrelaties: klant koopt product, auto
  wordt onderhouden door monteur, docent doceert vakken).
- **Kardinaliteit**: "hoeveel van de ene entiteit hoort bij de andere", vast te
  leggen in precies vier mogelijkheden: nul of één, precies één, nul of meer,
  één of meer; met voorbeelden (e-mailadres van klant nul of één; bestelregel
  hoort bij precies één bestelling; product wordt gekocht door nul of meer
  klanten; bestelling omvat één of meer producten).
- "Dit is maar de helft van het verhaal": ook de andere kant moet beschreven
  worden.
- **ERDish-zinnen**: vaste structuur *Iedere* **entiteit A** __werkwoord__
  ..aantal.. **entiteit B**, altijd in paren. Voorbeeldparen: auto/monteur,
  product/klant, plus nog vier paren (leerling/vak, medewerker/afdeling,
  klant/bestelling, gebruiker/account).
- Kraaienpoten (crow's feet) als tekenwijze voor de kardinaliteit, met plaatje.
- Van ERDish-zinnen naar ERD: auto/monteur-voorbeeld met plaatje; in dat plaatje
  zie je rechthoeken met afgeronde hoeken, attributen, kraaienpoten en de
  betekenis van de relatie op de lijn.
- Bekende fout: `crows-feet-enumeration.png` noemt de bovenste kraaienpoot
  (rondje + ene streep = nul of één) "nul of meer", en de tekst in dat plaatje
  zegt "precies 1". Er is geen bewerkbare bron bij het plaatje.
- Termen hier voor het eerst: kardinaliteit, ERDish-zinnen, kraaienpoten. De
  afkorting ERD wordt hier al volop gebruikt, maar pas in
  `verdieping_relaties.md` uitgelegd als *Entity Relationship Diagram*.

### `meer_meer_relaties.md` — de enige échte Solution in de lesstof

- Meer-meerrelatie = ERDish-zinnen die in beide richtingen "meer" bevatten.
- Voorbeeld klant/product (product wordt gekocht door nul of meer klanten, klant
  koopt één of meer producten) → twee-tabellen-oplossing faalt: in `klant` kan
  maar één product, in `product` maar één klant.
- Nuance die de stof bewust maakt: met "product" wordt bedoeld *een zwart T-shirt
  in maat M*, waarvan de winkel er honderd heeft. Een rij per individueel item
  is mogelijk "maar dat voelt raar" — je herhaalt dan steeds hetzelfde.
- Oplossing: een entiteit `bestelling` erbij, en "nog handiger" een vierde
  entiteit `bestelregel` (wat als ik vier zwarte T-shirts wil?). De "klassieke"
  structuur klant → bestelling → bestelregel → product, met plaatje, is daarna
  vrij van meer-meerrelaties.
- Oefening `erdish-bestelling`: zes ERDish-zinnen bij dit ERD maken, met de enige
  `:::{solution}` van de syllabus (6 zinnen, `:class: dropdown`).

### `nosql.md` — leeg

Alleen `# NoSQL: andere soorten databases`. De pagina staat wél in de
inhoudsopgave (tussen `meer_meer_relaties` en de verdieping), dus leerlingen
zien een lege hoofdstukpagina terwijl leerdoel 4 ("weet dat er meer soorten
databases zijn") ernaar verwijst. Openstaand in `todo.md`.

### `verdieping_attributen.md` — types, waarden, soorten attributen

- Open met de waarschuwing dat verdiepingsdiagrammen in oudere stijl zijn
  (hoofdletters), maar dezelfde kraaienpoten gebruiken.
- **Logisch vs fysiek ontwerp**: entiteit/attribuut (logisch) wordt in het
  fysieke ontwerp tabel/kolom. Voorbeeld-entiteit `leerling` met plaatje en
  tabel (Piet Konijn, Jan Haas, Sylvia Slak; telefoonnummer van Jan leeg).
- **`null`** = geen waarde, letterlijk de verwijzing naar niets, en dus niet
  hetzelfde als `0` (dat is wél een waarde).
- Fysiek-ontwerptabel met kolommen `datatype`, `lengte`, `standaardwaarde`
  (`varchar` 20/30, `date`, `char` 10).
- Datatypesoorten: getal (`integer`, `real`), tekst (`varchar`, `char`), datum
  (`date`), plaatje/geluid (`blob`). `varchar(50)` mag kortere tekst; een
  `char`-veld van lengte 10 bevat altijd precies 10 tekens (kortere teksten
  worden aangevuld met spaties) — dit is de *aangepaste* tekst; de oude tekst
  beweerde dat kortere tekst niet mag (nakijkpunt in `todo.md`).
- `standaardwaarde`-voorbeeld: kolom "nationaliteit" met "NL".
- **Soorten attributen**: *vluchtig* (leeftijd i.p.v. geboortedatum — je moet
  elke verjaardag bijwerken), *verplicht* (achternaam) vs *optioneel*
  (telefoonnummer), en **UID**: kan één attribuut zijn, een combinatie van
  attributen, of zelfs een relatie; voor- en achternaam, en zelfs die
  combinaties met geboortedatum, leveren op een grote school nog risico's op;
  voeg daarom liever een extra attribuut `leerlingnummer` toe. In het fysieke model heet een UID een *primary key*
  (verwijzing naar `sleutels_en_relaties.md`).
- ERD-tekens: `#` primary UID, `(#)` secondary UID (reserve/controle, hier de
  combinatie naam + geboortedatum), `*` verplicht, `o` optioneel.
- Opdrachten: `verd-attr-krakkemik` (autodealer-tekst: wat is entiteit,
  eigenschap, waarde; noem ook eigenschappen die niet in de tekst staan terwijl
  er waarden van genoemd zijn), `verd-attr-tekenen` (entiteit tekenen met
  UID/verplicht/optioneel), `verd-attr-datatypes` (datatype + lengte per
  attribuut, met link naar de SQL-datatypes van w3schools), `verd-attr-paspoort`
  (waarom staat haarlengte niet in een paspoort — antwoord: vluchtig attribuut).

### `verdieping_relaties.md` — ERD-eigenschappen buiten de basis

- Waarschuwing over de oude stijl plus het enige plaats waar **gestippelde vs
  doorgetrokken** lijnen worden uitgelegd; nadrukkelijk "in de lesstof en de
  eindopdracht hoef je dat onderscheid niet te maken".
- **Checklist voor ERDish-zinnen**: begint met _iedere_/elke, komen in paren,
  bevatten een werkwoord, kardinaliteit in de vier formuleringen,
  onderwerp/lijdend voorwerp zijn entiteiten, en vaak moet je met de
  opdrachtgever bespreken hoe het zit (meerdere banen per werknemer?).
- Anker `(ouder-kind-relaties)=` → **ouder-kindrelatie**: de kind-entiteit heeft
  geen eigen UID en erft die van de ouder; in de oude diagrammen te zien aan de
  doorgetrokken lijn. Voorbeeld `WERKNEMER` → `SALARISGESCHIEDENIS`: de UID van
  het kind is `werknemer_id`, dus de UID komt uit een relatie; in het fysieke
  model een extra kolom in die tabel.
- **Doel van een ERD**: een voorstel documenteren om met de opdrachtgever over
  te discussiëren. **Regels**: informatie slechts één keer tonen, en geen
  informatie die je kunt afleiden (geboortedatum → geen leeftijd opslaan).
- **Constraints**: bedrijfsregels die níet in het ERD horen (25 jaar dienstverband
  → seintje; geen toekomstige geboortedata; begindatum vóór einddatum; afdeling
  uit minimaal drie werknemers); realiseren met programmeerwerk of in het DBMS.
  Constraints over UID-lidmaatschap kun je wél in het ERD opnemen.
- **Overdraagbaarheid** (transferable): een koppeling die achteraf niet verzet
  mag worden → in het fysieke model "not updatable". Gedicht→dichter is niet
  overdraagbaar; leerling→klas wél (overplaatsen).
- **CRUD-analyse**: per onderdeel van een applicatie (bijv. "Adreswijziging
  leerling") noteren welke data wordt **C**reated/**R**etrieved/**U**pdated/**D**eleted.
- Opdrachten: `verd-rel-erdish` (4 paren), `verd-rel-lezen` (4 ERD-plaatjes;
  tevens "er staan relaties tussen die in werkelijkheid niet kloppen"),
  `verd-rel-tekenen` (8 paren, waaronder bewust een meer-meerrelatie
  leerling/docent), `verd-rel-overdraagbaar` (welke van die relaties zijn niet
  overdraagbaar, met onderbouwing).

### `verdieping_ontwerp_verbeteren.md` — matrix, redundantie, meer-meer

- **Matrix van relaties** als hulpmiddel om relaties tussen vele entiteiten te
  vinden (REIZIGER / LAND / BEZIENSWAARDIGHEID / BETAALMIDDEL; richtingen zijn
  rechtgezet naar "reiziger bezoekt bezienswaardigheid" — nakijkpunt in `todo.md`).
- De theorie heet **normalisatie**, "een heel technische term"; die wordt hier
  bewust *niet* uitgelegd, in plaats daarvan twee concrete problemen en hun
  oplossingen.
- **Probleem 1 redundantie**: een rooster-tabel (leerlingnummer, voornaam, vak,
  dag, tijd, lokaal, docent; rijen voor leerling 174 Robin / 175 Isa / 176 Jamie)
  waarin veel dubbele informatie staat en onduidelijk is wat de entiteit is
  ("het zijn er feitelijk meerdere door elkaar"). Oplossing: opbreken in
  Leerling, Vak, Docent en Rooster als koppelaar.
- **Probleem 2 meer-meerrelaties**: verwijst naar `meer_meer_relaties.md`;
  oplossing = tussenentiteit die in de database een koppeltabel wordt.
  BEDRIJF ↔ EVENEMENT wordt BEDRIJF_EVENEMENT, met UID = combinatie van
  `bedrijf_id` en `evenement_id`; metafoor: "je moet de tussenentiteit zien als
  een soort kaartje". Soms krijgt de tussenentiteit zelf attributen.
- Opdrachten: `verd-verb-matrix` (garagebedrijf/auto/persoon),
  `verd-verb-schoolgebouw`, `verd-verb-bus` (langeafstandsbus vooraf boeken),
  `verd-verb-tandenborstel`, `verd-verb-rondewinnaar`, `verd-verb-tvshow`
  (meer-meer oplossen). Vijf ERD-verbeteropdrachten op plaatjes.

### `verdieping_erd_naar_sql.md` — het fysieke ontwerp in SQL-DDL

- Na de ontwerpfase: realisatie. Twee controles vooraf: **geen redundantie
  meer?** en **zijn alle meer-meerrelaties opgelost?** (verving de vraag over
  1e/2e/3e normaalvorm, want normaalvormen worden nergens uitgelegd —
  nakijkpunt in `todo.md`).
- Vijf stappen: elke entiteit wordt een tabel; primaire sleutels (UID) worden
  dikgedrukt; vreemde sleutels tussen `<` en `>`; dat geeft een *relationeel
  model*; dat model zet je om in SQL-DDL.
- Relationeel model van het ELO-ERD: `leerling(**ll_nr**, naam, geboorte_datum,
  foto, klas)`, `volgt(**<ll_nr>, <vakcode>**)`, `vak(**vakcode**, naam)`,
  `opdracht(**opdrachtcode**, titel, opdrachttekst, deadline, <vakcode>)`,
  `maakt(**<opdrachtcode>, <ll_nr>**, URL, inleverdatum, inlevertijd, punt)`.
  Aandachtspunten die de tekst zelf aanstipt: `maakt` heeft een PK van twee
  vreemde sleutels, en optioneel/verplicht staat nog niet aangegeven.
- **SQL-DML** (gegevens opvragen/veranderen/invoeren/verwijderen; `SELECT ...
  FROM`) versus **SQL-DDL** (tabelstructuren definiëren en aanpassen).
- Twee volledige `CREATE TABLE`-voorbeelden (`leerling`, `maakt`) met `NOT NULL`,
  `CHAR(6)`/`VARCHAR(20)`/`BLOB`/`DATE`/`TIME`/`NUMERIC(3,1)`, samengestelde
  `PRIMARY KEY(opdrachtcode, ll_nr)` en `FOREIGN KEY(...) REFERENCES ...`.
  De `NOT NULL`-keuzes haal je uit het ERD.
- `:::{important}`: een vreemde sleutel moet exact hetzelfde type hebben als de
  PK waarnaar hij verwijst. Extra regels: botsende kolomnamen hernoemen, en elk
  SQL-statement sluit je af met `;` (bij DML wordt minder streng gekeken).
- Opdrachten: `verd-sql-elo` (definities voor `volgt`, `vak`, `opdracht`),
  `verd-sql-fietsen` (ERD van een fietsenwinkel: meer-meer verwijderen,
  relationeel model, SQL-DDL; met type-hints — merken/typen als "Gazelle",
  staat goed/redelijk/slecht, prijs met twee decimalen, `nieuw` voor
  nieuw/tweedehands).

### `eindopdracht_sql.md` en `eindopdracht_ontwerp.md`

- SQL-opdracht: in Squeek, waar ook de meeste SQL-uitleg staat; Squeek slaat
  antwoorden op, dus dat is meteen de inlevering. Score is lineair.
- Ontwerp-opdracht: casus "fantasierijke tuintjes" in een fantasiewereld, met
  2 punten voor 4–6 entiteiten + attributen, 6 punten voor ERDish-zinnen,
  7 punten voor een ERD zonder meer-meerrelaties (koppeltabellen waar nodig),
  5 punten voor voorbeeldtabellen per entiteit, +1 bonus voor originaliteit
  (cyberpunk, fantasy, Discworld, ...). 20 punten = een 10, minimum een 1.

## Oefenopdrachten: alle labels

17 `:::{exercise}`-blokken. Labels zijn cross-referencelinks, dus verander ze
niet zonder de verwijzingen aan te passen.

| Bestand | Labels |
|---|---|
| `meer_meer_relaties.md` | `erdish-bestelling` (+ `:::{solution}`) |
| `verdieping_attributen.md` | `verd-attr-krakkemik`, `verd-attr-tekenen`, `verd-attr-datatypes`, `verd-attr-paspoort` |
| `verdieping_relaties.md` | `verd-rel-erdish`, `verd-rel-lezen`, `verd-rel-tekenen`, `verd-rel-overdraagbaar` |
| `verdieping_ontwerp_verbeteren.md` | `verd-verb-matrix`, `verd-verb-schoolgebouw`, `verd-verb-bus`, `verd-verb-tandenborstel`, `verd-verb-rondewinnaar`, `verd-verb-tvshow` |
| `verdieping_erd_naar_sql.md` | `verd-sql-elo`, `verd-sql-fietsen` |

Over de nummering: oefeningen worden over het hele boek doorgenummerd
("Oefening 1, 2, ..."), per `numfig_format: exercise: "Oefening %s"` in
`_config.yml`. Per hoofdstuk nummeren kan alleen met `numbered: true`, en dan
krijgen ook de hoofdstuktitels cijfers — daarom bewusst niet gedaan
(nakijkpunt in `todo.md`).

## Verwijzingen tussen hoofdstukken

De stof is een keten; verplaats of hernoem je een hoofdstuk, breek dan deze
links:

- `tabellen_en_sql.md` → `sleutels_en_relaties.md` (koppelen van tabellen) en
  → `eindopdracht_sql.md`
- `verdieping_attributen.md` → `ontwerpen_entiteiten.md`, `sleutels_en_relaties.md`
- `verdieping_relaties.md` → `ontwerpen_relaties.md` (+ interne anker-link naar
  `(ouder-kind-relaties)=`)
- `verdieping_ontwerp_verbeteren.md` → `meer_meer_relaties.md`
- `verdieping_erd_naar_sql.md` → `verdieping_attributen.md` (notatie `*`/`o`)
- `index.md` → `eindopdracht_sql.md`, `eindopdracht_ontwerp.md`;
  `eindopdracht_ontwerp.md` → `index.md` (cijververdeling, deadline, inleverregels)
- Externe links: de SQL-datatypeslijst op w3schools (twee keer:
  `verd-attr-datatypes`, `van ERD naar SQL`), en https://app.q-vakken.nl/ (inleveren).

## Wat er níét in de stof zit (gaten om rekening mee te houden)

- **NoSQL**: alleen een titel (`nosql.md`), terwijl leerdoel 4 ernaar verwijst.
- **"Databases en regels"**: als bonus-leerdoel aangekondigd, geen hoofdstuk
  (staat in `todo.md` als "hoofdstuk schrijven of leerdoel schrappen").
- **Normalisatie** (1e/2e/3e normaalvorm) wordt genoemd maar niet uitgelegd;
  de stof lost het op met "geen redundantie" en "geen meer-meerrelaties".
- **ACID** als term niet genoemd, terwijl de vier garanties er wél staan.
- **JOIN's / samengestelde queries**: `SELECT` verschijnt één keer, er wordt
  niet mee geoefend in de syllabus (dat gebeurt in Squeek).
- **Joins uit een ERD halen** (waar gaan vreemde sleutels fysiek zitten bij het
  omzetten van ouder-kind of meer-meer) wordt in verdieping wél benoemd
  (extra kolom, koppeltabel) maar niet systematisch behandeld.
- **Transacties, deadlock, constraints in SQL** (`CHECK`, `UNIQUE`) komen in de
  stof voor als begrip maar niet als iets dat je zelf schrijft.
- **Uitwerkingen**: alleen `erdish-bestelling` heeft een solution; van de 16
  verdiepingsopdrachten heeft er geen enkele een uitwerking.
- **Weekplanning**: er is geen tabel met weeknummer, datum, fysiek/online en thema.
- **Plaatjes ontbreken** bij `tabellen_en_sql.md` (eerste tabel-voorbeeld) en
  bij `ontwerpen_entiteiten.md` (entiteit/attribuut/UID), terwijl juist de
  verdieping die plaatjes wél heeft (in een oudere stijl).
