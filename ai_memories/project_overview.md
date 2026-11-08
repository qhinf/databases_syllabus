# Projectoverzicht: Databases en SQL (Q-vak-module)

## Wat dit is

De syllabus (webstek) voor de module **Databases en SQL** van het
**informaticaparcours van de Q-vakken** (Quadraam). Het is een Jupyter Book:
MyST-Markdown-bron in `syllabus/`, gebouwd met `jupyter-book build syllabus`,
gepubliceerd via de gedeelde Q-vakken-syllabusomgeving (GitHub-repo `qhinf/syllabi`).

- Repo: `git@github.com:qhinf/databases_syllabus.git`
- Titel in `_config.yml`: "Databases en SQL"; auteur: "Q-Vak Informatica"
  (wordt voor de site globaal aangepast op basis van de commitgeschiedenis)
- Docent volgens de config: **Merijn Vogel** (`m.vogel@quadraam.nl`). In de
  commits en voorbeelden komen ook **Arthur Rump** en **Pieter van Engelen** voor
  (Quadraam-docenten; Pieter van Engelen doet de recente commits en correcties).

## Voor wie en wat

Doelgroep: leerlingen van het informaticaparcours. De module is kort
(één blok van ~8 lesweken) en staat op **instapniveau**: concepten, geen programmeerwerk.
Er wordt vrijwel geen SQL-syntax in de syllabus zelf onderwezen — die hoort bij
het externe oefensysteem **Squeek**.

Leerdoelen zoals die op `index.md` staan:

1. Weten wat een database is (specifiek: relationele databases)
2. Gegevens opzoeken met de vraagtaal SQL
3. Een eenvoudig datamodel ontwerpen
4. Weten dat er ook NoSQL-databases zijn
5. Bonus: "we praten ook even over databases en regels"

Let op de **afwijking tussen leerdoelen en inhoud** (bekend, vastgelegd in `todo.md`):
doel 4 heeft alleen een leeg kapstokhoofdstuk (`nosql.md`, alleen een titel) en
doel 5 heeft helemaal geen hoofdstuk.

## Opbouw van de module

Drie delen, vastgelegd in `syllabus/_toc.yml`:

| Deel | Hoofdstukken | Rol |
|------|--------------|-----|
| **Lesmateriaal** | `wat_is_een_database`, `tabellen_en_sql`, `sleutels_en_relaties`, `ontwerpen_entiteiten`, `ontwerpen_relaties`, `meer_meer_relaties`, `nosql` | "alles wat je nodig hebt voor de eindopdrachten" |
| **Verdieping** | `verdieping_attributen`, `verdieping_relaties`, `verdieping_ontwerp_verbeteren`, `verdieping_erd_naar_sql` | extra theorie + oefenopdrachten; niet verplicht |
| **Eindopdrachten** | `eindopdracht_sql`, `eindopdracht_ontwerp` | wat er wordt ingeleverd en beoordeeld |

## Beoordeling en inleveren

- **50%** SQL-opdrachten in **Squeek** (het eigen SQL-oefensysteem van de docent,
  https://sql.merijn.xyz). Squeek slaant antwoorden op = automatisch ingeleverd.
  Lineaire score: meer goede vragen = hoger deelcijfer.
- **50%** database-ontwerp (casus "fantasierijke tuintjes"), 20 punten:
  2 pt entiteiten (4–6 stuks), 6 pt ERDish-zinnen, 7 pt ERD (zonder meer-meerrelaties,
  koppeltabellen waar nodig), 5 pt voorbeeldtabellen, +1 pt bonus originaliteit.
  20 pt = cijfer 10, minimum cijfer 1.
- Inleveren via https://app.q-vakken.nl/ (zip als er meerdere bestanden zijn),
  behalve de SQL-opdracht die in Squeek zelf "terechtkomt".
- Deadlines per branch (substituties in `_config.yml`). Op `2627-2`:
  inleveren **donderdag 28 januari 16:00**, uitstel aanvragen **maandag 4 januari 16:00**,
  uitgestelde deadline **dinsdag 16 februari 16:00**.
- Huiswerkregels: zelfstandig werken, bronvermelding, netjes en leesbaar werk.

## Versie- en branchmodel (belangrijk!)

Branchnamen zijn jaar+blok: `JJYY-B`. Bijvoorbeeld `2324-4`, `2425-1`, `2526-1`,
`2526-2`, **`2627-2` (huidige checkout)**. Per blok wordt een branch afgetakt en
daarop de deadlines (en eventueel docentnamen) gezet; inhoudelijke verbeteringen
kunnen op de actuele branch.

- `main` is een oude snapshot (laatste commit 2024-10-03) en wordt door de
  publicatieworkflow explicaat **buiten beschouwing** gehouden
  (`branches-ignore: main`). De actuele stek komt dus van een versie-branch.
- De actieve branch staat 33 commits boven `origin/main`.
- De recente historie op `2627-2` is in "fases" gewerkt (opruimen → opsplitsten per
  hoofdstuk → inhoud rechttrekken/verdieping), grotendeels door AI-agents met
  `Co-Authored-By`-trailers. Hou commits klein, onderwerpgericht en Nederlandstalig.

## Publicatieproces

`.github/workflows/update.yml` vuurt bij elke push op een niet-`main`-branch een
`workflow_dispatch` naar `qhinf/syllabi` → `update.yml`, met inputs
`name: <syllabusnaam>/<branch>` (naam afgeleid uit de repoinnaam door `_syllabus`
weg te strippen), `ref`, `url`, `branch`, `add: true`. Daarvoor is een
`PAT_SYLLABI_UPDATE`-secret nodig.

Gevolgen:

- De eigenlijke build/publish draait centraal, niet in deze repo (geen CI-build hier).
- `html`-, `repository`- en `launch_buttons`-instellingen én de `versie`-substitutie
  worden **globaal** voor alle Q-vak-syllabi geregeld. Die commentaarregel helemaal
  onder in `_config.yml` is de herinnering daaraan.
- Zelf lokaal bouwen is wél handig om opmaakfouten te vangen (zie
  `project_structure.md`).

## Externe afhankelijkheden en context

- **Squeek** (https://sql.merijn.xyz/), voorheen **Sjaaq**: SQL-oefensysteem van de
  docent, de facto de plek waar SQL wordt aangeleerd én ingeleverd. De substitutie
  `{{ squeek }}` in `_config.yml` wees in blok 2026/2027 tijdelijk naar
  `https://www.disney.com` (Squeek was toen down); die placeholder is in november
  2026 teruggezet op de echte URL. Het domein kan nog verhuizen: Squeek is zo
  gebouwd dat dat kan, en de bedoeling is dat het op Q-vakken-infra gaat draaien.
  Vroeger bevatte de syllabus ook een
  "Bug bounty"-hoofdstuk over Squeek (ethisch hacking op een productiesysteem); dat
  is in 2026 verwijderd (commit `cebe457`), de tekst staat nog in de git-geschiedenis.
- **Colofon**: de verdiepingshoofdstukken zijn afgeleid van de cursus
  *Databasedesign* van het SLO (Eelco Dijkstra); *van ERD naar SQL* gebruikt
  materiaal van Heer deBeer. Herschreven door Merijn Vogel in 2023 en 2025.
- **Zuster-repo's** (zelfde template, lokaal ernaast):
  `../javascript_syllabus`, `../linux_servers_syllabus`. `javascript_syllabus`
  heeft een `.venv` met jupyter-book (handig om te lenen of als voorbeeld) en een
  eigen `ai_memories/`-map — dezelfde conventie die hier wordt gevolgd.

## Huidige staat (stand november 2026, branch 2627-2)

- 15 markdown-bestanden in `syllabus/`, ~7450 woorden, 17 oefenopdrachten (alle in
  de verdieping + 1 in `meer_meer_relaties.md`), 23 afbeeldingen in `syllabus/assets/`.
- Structuur is net opgesplitst van één big file (`databases-and-sql.md`, 632 regels)
  naar hoofdstuk-per-bestand; de inhoud is daarna "rechtgetrokken".
- Openstaand werk staat in `todo.md` (root): NoSQL-hoofdstuk schrijven,
  weekplanning-tabel, twee plaatjes die fout/verkeerd gelabeld zijn, verdieping-
  diagrammen in oude stijl opnieuw tekenen, en uitwerkingen bij oefenopdrachten.
- De Squeek-link is hersteld: `{{ squeek }}` wijst weer op
  https://sql.merijn.xyz/ (de disney.com-placeholder van begin blok 2026/2027 is
  weg). Zie `stijl_en_valkuilen.md`.
