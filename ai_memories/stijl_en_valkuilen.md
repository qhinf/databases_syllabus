# Stijl, opmaak en bekende valkuilen

Conventies die in deze syllabus wérkelijk worden gebruikt (gecheckt in de
bestanden), plus de inhoudelijke gaten en fouten die je als agent moet kennen
voordat je iets "verbetert".

## Stem en taal

- **Nederlands, informeel, docent als persoon.** De tekst spreekt de leerling
  direct aan ("je", "we", "de docent"). Incidenteel "jij" (`index.md`:
  "aan de hand van wat jij inlevert") — de mix je/jij staat er bewust; maak er
  geen consistentie-project van.
- **Humor mag.** De SQL-grap *"silly question language"* met "die grap mag je van
  harte overnemen!", de Postgres-verbetering met `¯\_(ツ)_/¯` en "Vind ik.", de
  opmerking "Laat staan de AI's van nu!", "`;` ... niet zo streng gelet ;-)".
  Haal er geen "nettere" versie van.
- **Terzijde-instapverhalen**: voorbeelden uit de praktijk van de docent (vriend
  met een dubbele naam + geboortedatum, opdrachten bij de NS, "de docent heeft een
  vriend die hier daadwerkelijk last van heeft gehad").
- **Externe systeemnamen worden niet uitgelegd in de syllabus** (Squeek, q-vakken,
  app.q-vakken.nl). Verwacht dat de docent in de les vult wat hier ontbreekt.
- Woordenboom: *precies één / één of meer / nul of één / nul of meer* — exact deze
  vier formuleringen, altijd. Niet variëren met "minstens één".

## Opbouwconventies per hoofdstuk

- Eén `# Titel` per bestand; `##`-secties met een eigen ondertitel die de stof benoemt
  ("Garantie 1: iets gebeurt helemaal, of helemaal niet (atomic)").
- **Een citatenregel** `> ...` als kern van het hoofdstuk, in
  `wat_is_een_database.md` ("Een database is een systeem dat gegevens opslaat en
  doorzoekbaar maakt") en `tabellen_en_sql.md` ("Een tabel is als een
  Excel-sheet, met precieze kolommen en rijen"). Niet elk hoofdstuk doet dit.
- De vier verdiepingshoofdstukken openen met een `:::{note}` die waarschuwt dat de
  diagrammen "in een oudere stijl" zijn getekend (hoofdletters, soms
  gestippelde lijnen) maar dezelfde kraaienpoten gebruiken. Vier keer, één per
  verdiepingshoofdstuk: laat die staan als je er stof bij schrijft.
- De verdiepingshoofdstukken sluiten af met `## Opdrachten` met daarin alleen
  `:::{exercise}`-blokken. De lesstof-hoofdstukken `ontwerpen_entiteiten` en
  `ontwerpen_relaties` hebben géén oefeningen in de syllabus; die worden in de
  les gemaakt.
- Er zijn negen ```{table}``-blokken: `Gebouw`, `Gebruiker`, `Rekening`,
  `Transactie` (tabellen_en_sql), `Docent`, `Vak`, `Docent` (met
  `vak_id`) (sleutels_en_relaties), `Leerling` en "Fysiek ontwerp van tabel
  leerlingen" (verdieping_attributen). Losse voorbeeldtabellen en matrices
  (de CRUD-legenda in `verdieping_relaties`, de REIZIGER/LAND/BEZIENSWAARDIGHEID/
  BETAALMIDDEL-matrix en de rooster-tabel in `verdieping_ontwerp_verbeteren`)
  staan als gewone GFM-tabel, zónder directief.

## MyST-opmaak die hier in gebruik is

- `:::{note}` / `:::{tip}` / `:::{important}` — colon-fence admonitions.
- `:::{exercise}` en `:::{solution}` via `sphinx_exercise`. Labels:
  `:label: verd-attr-krakkemik`, `:::{solution} erdish-bestelling`,
  `:class: dropdown` (enige solution, in `meer_meer_relaties.md`). Slechts één
  uitwerking in de hele syllabus.
- Exercities hebben soms een titel (`:::{exercise} ERD lezen`) en soms niet
  (alleen een label). Beide patronen komen voor.
- ```{table} <tabeltitel> + GFM-tabel eronder — Sphinx maakt er een genummerde
  tabel van met bijschrift. De titel mag best een hele zin zijn
  ("Fysiek ontwerp van tabel leerlingen").
- ```{tableofcontents} staat alleen in `index.md`. Een `code-block`-directief
  wordt niet gebruikt; SQL-voorbeelden staan in gewone code-fences met de
  taalaanduiding `sql`. Er staat in de hele syllabus maar één query:
  ``select * from docent;`` in `tabellen_en_sql.md`. De verdieping toont alleen
  DDL (`CREATE TABLE`), plus de term `SELECT ... FROM` als uitleg van SQL-DML.
- **Substituties**: `{{ squeek }}`, `{{ deadline }}`,
  `{{ deadline_uitstel_aanvragen }}`, `{{ deadline_uitstel }}`, `{{ docent }}`,
  `{{ docent_email }}` (index only), `{{ versie }}`. `{{ squeek }}` is zélf al een
  Markdown-link (`[Squeek](url)`), dus schrijf "in {{ squeek }}" en niet
  "[in Squeek]({{ squeek }})". De letterlijke naam "Squeek" staat ook plat in
  `eindopdracht_sql.md` ("Squeek slaat je antwoorden op") — dat mag, want het is
  een systeemnaam, geen link.
- **Links tussen bestanden**: `[](sleutels_en_relaties.md)` (MyST vult de titel
  in) of `[startpagina](index.md)` als er eigen tekst bij nodig is. Altijd `.md`
  in de bron, niet de gebouwde `...html`-naam.
- **Ankers**: `(ouder-kind-relaties)=` boven de kop in `verdieping_relaties.md`,
  met erboven `[ouder-kindrelaties](#ouder-kind-relaties)`. Dit is de enige
  interne sprong (interneanker) in de syllabus; kopiëer het patroon als je meer
  interne verwijzingen nodig hebt.
- **HTML-entiteiten waar nodig**: het relationele model in
  `verdieping_erd_naar_sql.md` schrijft `&lt;ll_nr&gt;` en `&lt;vakcode&gt;`.
  Losse hoekige haken `<...>` worden als HTML geïnterpreteerd en verdwijnen stil
  uit de gebouwde pagina. Gebruik in MyST-tekst dus `&lt;`/`&gt;` (of backticks)
  voor een notatie als `<vakcode>`.
- **Backslashes**: `¯\_(ツ)_/¯` is escaped; een niet-escaped `_..._` in lopende
  tekst wordt cursief. De ERDish-voorbeelden gebruiken `_entiteit_` bewust als
  cursief (`_auto_`, `_monteur_`), en `**precies één**` als vet — houd dat
  patroon aan in nieuwe ERDish-zinnen.
- **HTML-comments voor todo's**: `<!-- todo: plaatje -->` in de lopende tekst,
  zodat het niet op de site verschijnt (in-text todo: 1 stuk, zie `todo.md`).
- **`<!-- Deze regel niet wijzigen! -->`** boven de versieregel in `index.md`:
  laat die regel en `{{ versie }}` met rust.
- **smartquotes/`replacements` staan aan**: `'` en `"` worden schuine quotes en
  `(c)` een symbool — let op met rechte quotes in brontekst-achtige stukken en in
  SQL-voorbeelden (in code-fences gebeurt dat gelukkig niet).

## Twee diagramstijlen (niet verwarren)

- **Lesstof-stijl** (nieuw, PNG, draw.io): afgeronde hoeken, entiteiten met
  kleine letters, attributen als lijst in de entiteit, kraaienpoten, de
  relatietaal op de lijn. Bestanden in `assets/<hoofdstuk>/` met een
  Engelstalige, beschrijvende bestandsnaam
  (`erd-voorbeeld-auto-monteur.png`, `kraaienpoot-notatie-legenda.png`). De namen zijn
  beschrijvend; `kraaienpoot-notatie-legenda` is de eerste Nederlandstalige.
- **Verdiepings-stijl** (oud, JPG, afkomstig uit de SLO-cursus Databasedesign):
  ENTITEITEN IN HOOFDLETTERS, UID-markeringen `#` primary UID, `(#)` secondary
  UID, `*` verplicht, `o` optioneel, en gestippelde (gewone relatie) vs
  doorgetrokken (ouder-kindrelatie) lijnen. Bestandsnamen in het Nederlands met
  underscores (`werknemer_salaris.jpg`, `opdracht_erd_lezen_3.jpg`).
- Alt-teksten zijn in het Nederlands en beschrijvend ("Plaatje van twee tabellen
  met een relatie", "Entiteit leerling met UID"). Houd die stijl aan.
- Er staan géén bewerkbare `.drawio`-bronbestanden in de repo (behalve de
  export-naam van één PNG: `db-relaties-20250918.drawio.png`). Inmiddels staat er wél
  één bewerkbare vectorbron: `assets/ontwerpen_relaties/kraaienpoot-notatie-legenda.svg`.

## Doorlopende voorbeelden (hergebruik ze, verzin geen nieuwe)

| Voorbeeldwereld | Waar het terugkomt |
|---|---|
| **reiziger / land / bezienswaardigheid / reis** | het grote doorlopende voorbeeld: de 5-entiteiten-lesfiguur in `ontwerpen_relaties` (Figuur 1 t/m 4), de CRUD-matrix + drie lees-ERD's + entrereenheid in `verdieping_relaties`, `extra_studie_land_naar_bezoeker.jpg` en de twee `SELECT`-queries in `verdieping_attributen`, het 10-tabel-rijgerecht in `verdieping_erd_naar_sql`, en drie van de zes opdrachten in `verdieping_ontwerp_verbeteren` |
| **leerling / vak / docent / les (lesdocent, leslokaal, lesdag, lestijd)** | de nieuwe lesfiguren: entiteiten + attributen in `ontwerpen_entiteiten`, kardinaliteiten en kraaienpoten in `ontwerpen_relaties`, de lesdag/lestijd-herberekening in `verdieping_relaties`, en de `Docent`-/`Vak`-tabellen in `sleutels_en_relaties` |
| **gebouw / verdieping / lokaal** | attributen en foreign key in `verdieping_attributen`, plus de `verd-verb-schoolgebouw`-opdracht |
| **klant–bestelling–product** en **recept met ingredienten** | tussenentiteiten in `verdieping_ontwerp_verbeteren` |
| **webshop: gebruiker / rekening / transactie** | SQL-DDL met `CREATE TABLE` en constraints in `tabellen_en_sql` |
| **elo (studentennummer, naam, klas) en fiets/eigenaar** | voorbeeld + opdracht in `verdieping_erd_naar_sql` |
| **paspoort / land (11 landen, 20 paspoorten)** | attributen-oefening `verd-attr-paspoort` |
| losse ERDish-paartjes | auto/monteur, film/regisseur/artiest, moeder/vader/-kind, student/vak, huis/bed, muur/schilderbehang, recept, gebouw/verdieping/lokaal |

- De sectie "Voorbeeld uit de les: een winkel" in `ontwerpen_entiteiten.md` is in
  tekst een complete **webshop** (Product, Bestelling, Klant) met drie
  subkopjes: ontwerpen → entiteit → tabel. Die brug "ontwerp → tabel" staat al
  hier en in `tabellen_en_sql`; een nieuw hoofdstuk hoeft hem niet opnieuw te
  vertellen.

## Bekende inhoudelijke fouten (gecheckt in de plaatjes zelf)

1. **`assets/ontwerpen_relaties/crows-feet-enumeration.png`** – *opgelost in november
   2026*. De bovenste kraaienpoot (rondje + ene streep = nul of één) was gelabeld
   **"nul of meer"**, en de tekst in het plaatje zei "precies 1" met een cijfer: de
   labels kwamen dus twee keer voor en de eerste was fout. De omringende tekst
   ("Een rondje of een streep voor nul of één") klopte. Het plaatje is hertekend als
   `kraaienpoot-notatie-legenda.png` (met SVG-bron), in plaats van de tekst aan het
   plaatje aan te passen. Let op: de nieuwe legenda tekent 'precies één' als twee
   streepjes, en die zin in het hoofdstuk is onbewerkt gelaten.
2. **`verdieping_attributen.md`** claimt over de `#`-markering in oud
   SQL-onderwijs: "Dit teken gebruiken we ook in de lesstof". In de huidige
   lesstof-ERD's staat nergens een `#`; daar staat de `(uid)`-notatie uit
   `ontwerpen_entiteiten.md` en de term "UID". Feitelijk klopt de claim dus niet
   helemaal — houd de zin aan (verdieping4 tekent wél met `#`) en meld het
   puntje bij het nakijken van dat hoofdstuk.
3. **`verdieping_attributen`**: `char(10)`-uitleg is recent veranderd naar
   "kortere teksten worden aangevuld met spaties". Staat als nakijkpunt in
   `todo.md`; een agent die "SQL-regels" controleert moet weten dat deze
   bewering bewust is aangepast, niet verzonnen.
4. **`verdieping_ontwerp_verbeteren`**: de redundantietabel voor Isa is
   hergenummerd van 176 naar 175, en de richting in de matrix is rechtgezet naar
   "reiziger bezoekt bezienswaardigheid" (was "wordt bezocht"). Beide staan als
   na te kijken in `todo.md`. Zie ze niet als nieuwe fouten.
5. **`verdieping_erd_naar_sql`**: de vraag "in 1e, 2e en 3e normaalvorm?" is
   bewust vervangen door "Zit er geen redundantie meer in?" — want normaalvormen
   worden nergens uitgelegd. Schrijf die term dus niet terug in de opgave.
6. **`index.md`**: de regel "Inleveren via: https://app.q-vakken.nl/" staat
   twee keer achter elkaar (typefout, geen inhoudelijk verschil).

## Gaten in de stof (niet per ongeluk "vullen")

- **`nosql.md` is een kapstok**: alleen `# NoSQL: andere soorten databases`
  (5 woorden). Lehrdoel 4 op `index.md` belooft NoSQL. Schrijf dit hoofdstuk
  alleen als de opdracht expliciet is; het staat als open punt in `todo.md`.
- **Leerdoel "databases en regels"** (bonus op `index.md`) heeft geen hoofdstuk.
  Optie in `todo.md`: schrijven óf het leerdoel schrappen. Verzin niet zelf een
  handhaving-hoofdstuk.
- **ACID wordt niet bij naam genoemd**, terwijl de vier garanties (atomic,
  consistent, isolation, durability) wél in `wat_is_een_database.md` staan. Een
  agent kan geneigd zijn "ACID" toe te voegen: doe dat niet zonder overleg, want
  de docent houdt het bewust bij de vier losse garanties.
- **SQL-DML wordt in de syllabus zelf nauwelijks onderwezen** (één
  `select * from docent;`). De SQL-queries, joins, WHERE-clausules en aggregate
  functions horen bij Squeek. Schrijf geen
  SQL-uitleg in deze syllabus om "het compleet te maken". Wel staat er in de
  verdieping al SQL die verondersteld wordt uit de Squeek-oefeningen te komen
  (`SELECT DISTINCT land_code FROM reizigers_bezoekt_bezien`,
  `SELECT * FROM docent_vak;`).
- **Normalisatie, genormaliseerde vormen, JOIN-syntax, indexen, views,
  transacties in SQL** komen niet in de stof voor. Als een oefening daarover
  gaat, is die nieuw en dus een uitbreiding van de stof (meld dat expliciet).
- **Planning per lesweek** (weeknummer, datum, fysiek/online, thema) ontbreekt;
  die tabel staat in `todo.md` en is docent-specifiek per blok: vul 'm niet in
  met verzonnen datums.
- **Slechts één uitwerking** (`erdish-bestelling`). De 16 andere opdrachten
  hebben geen solution; toevoegen kan, maar de docent wil die waarschijnlijk
  las laat in de les maken — het staat als open punt in `todo.md`.

## Squeek-link: status, hernoeming en valkuilen

`{{ squeek }}` in `_config.yml` is nu:

```yaml
squeek: "[Squeek](https://sql.merijn.xyz/)"
```

Daarboven staat in `_config.yml` nog de comment "Tijdelijk naar disney.com omdat
Squeek (https://sql.merijn.xyz) down is." — die regel is **veroudert** sinds de
placeholder in november 2026 is teruggezet; laat hem staan (het is geen
AI-bestand) en meld het puntje. Squeek — het SQL-oefensysteem van de docent, waar
leerlingen queries maken én inleveren — staat op drie plekken in de stof
(`index.md`, `tabellen_en_sql.md`, `eindopdracht_sql.md`).

- De disney-link is in het begin van blok 2026/2027 een **bewuste noodoplossing**
  geweest, geen typo om "fixen". Hij staat nog in de git-geschiedenis.
- De enige SQL-inleveropdracht van de module loopt via dat systeem: als je de
  stof aanpast alsof Squeek er niet is, verander je de beoordeling.
- **Verander de URL niet zelf.** Squeek kan verhuizen naar Q-vakken-infra, en het
  systeem is zo gebouwd dat dat kan; de docent bepaalt wanneer. Merk je dat de
  link niet werkt, meld het dan, schrijf geen alternatieve SQL-stof.
- **Hernoeming**: het systeem heette eerst **Sjaaq** (de substitutiekey in
  `_config.yml` heette toen `sjaaq`). In deze branch is alles hernoemd naar
  **Squeek**; de oude naam staat nog in de git-geschiedenis en in de verouderde
  html-resten in `syllabus/_build/`.
- Historisch: de syllabus had een hoofdstuk `bug_bounty.md` over Squeek als
  productiesysteem (ethisch hacking, "Let op! Dit is een productie-systeem!").
  Dat is verwijderd in commit `cebe457`; de tekst staat nog in de
  git-geschiedenis als je het terug wilt lezen.

## Overzicht van oefenlabels

17 opdrachten, één solution. Labels zijn cross-referencelinks: verander ze niet
zonder een verwijzing te breken.

| Prefix | Hoofdstuk | Aantal | Labelstammen |
|---|---|---|---|
| — | `meer_meer_relaties.md` | 1 | `erdish-bestelling` (+solution) |
| `verd-attr-` | `verdieping_attributen.md` | 4 | `krakkemik`, `tekenen`, `datatypes`, `paspoort` |
| `verd-rel-` | `verdieping_relaties.md` | 4 | `erdish`, `lezen`, `tekenen`, `overdraagbaar` |
| `verd-verb-` | `verdieping_ontwerp_verbeteren.md` | 6 | `matrix`, `schoolgebouw`, `bus`, `tandenborstel`, `rondewinnaar`, `tvshow` |
| `verd-sql-` | `verdieping_erd_naar_sql.md` | 2 | `elo`, `fietsen` |

Exercities worden over het hele boek doorgenummerd ("Oefening 1, 2, …" via
`numfig_format: exercise: "Oefening %s"` in `_config.yml`). Voeg je een oefening
toe, dan schuift de nummering van alle latere hoofdstukken op — per hoofdstuk
nummeren kan alleen met `numbered: true`, en dan krijgen de hoofdstuktitels
ook cijfers (daarom bewust niet gedaan; punt in `todo.md`).
