# TODO

Openstaande punten uit de syllabus. In de markdown staan ze als HTML-comment
(`<!-- todo: ... -->`), zodat ze niet zichtbaar zijn op de site.

## syllabus/index.md

- [x] Planning per lesweek toevoegen (tabel met weeknummer, datum, fysiek/online, thema)
      (Merijn: ...niet helemaal mee eens, dat staat in app.q-vakken.nl en zou redundant zijn...)
- [x] Leerdoel "databases en regels": hoofdstuk schrijven of leerdoel schrappen
  *Merijn*: nop, ik ga dat noemen in een les en hoef er geen hoofdstuk van te maken ook al vind opus vanalles.

- [x] Nakijken: colofon noemt Merijn Vogel als herschrijver in 2025 (afgeleid uit de commits van "merry" in die periode)
      *Merijn*: dat klopt, Merijn heeft het ge-de-wiskundiseerd, moeilijke
       worden zoals 'normaalvorm' leiden af van het doel 'problemen vermijden'
       maar de hoofdlijn van de module is nog min or meer intact en gebaseerd
       op wat er al was

## syllabus/_toc.yml

- [x] Nakijken: oefeningen worden over het hele boek doorgenummerd (Oefening 1, 2, …). Per hoofdstuk nummeren kan met `numbered: true`, maar dan krijgen ook de hoofdstuktitels nummers
      *Merijn*: Deze opdrachten zijn meer een handreiking in de syllabus voor
      leerlingen die dit zelfstandig willen doen en als hint voor mij als
      docent bij het maken van de lessen.

## syllabus/tabellen_en_sql.md

- [x] Plaatje van een tabel toevoegen bij "Een tabel ziet er uit als een excel-sheet" (`todo: plaatje`)
  *Merijn*: gaan we gewoon niet doen elke leerling weet wat een excelsheet is is een goede aanname)

- [x] Voorbeeld-tabellen maken bij "Een bank met gebruiker, rekening, transacties" (`todo: maak voorbeeld-tabellen`)

## syllabus/sleutels_en_relaties.md

- [x] Plaatje `db-relaties-20250918.drawio.png` gebruikt de tabel Vak (id 1-3) terwijl de tekst Parcours (id 100/101) gebruikt; plaatje aanpassen (`todo: plaatje gebruikt de tabel Vak ...`)
      *Opgelost door de tekst aan te passen in plaats van het plaatje*: Parcours is verdwenen
      uit het Q-vakken lexicon, dus de tekst gebruikt nu tabel `Vak` en kolom `vak_id`
      (commit in de werkboom, nog te reviewen). Het verschil in id's (tekst 100/101,
      plaatje 1 Filosofie / 2 Informatica / 3 Wiskunde D) blijft bewust open staan; de
      in-text todo in dat hoofdstuk staat er nog.

## syllabus/ontwerpen_relaties.md

- [x] Plaatje `crows-feet-enumeration.png`: bovenste kraaienpoot heet "nul of meer", moet "nul of een" zijn (geen bewerkbare bron aanwezig, opnieuw tekenen)
  *Merijn*: dat hebben we al 6 jaar overleefd...
  *Opgelost nov 2026*: hertekend als `kraaienpoot-notatie-legenda.png`, met bewerkbare
  SVG-bron `kraaienpoot-notatie-legenda.svg`. Vier kardinaliteiten, elk op eigen rij,
  Nederlandse termen rechts van het pootpunt. Het foute plaatje is verwijderd. maar ok we gaan hem vervangen

## syllabus/nosql.md

- [x] Hoofdstuk over NoSQL-databases schrijven
  *Verplaatst nov 2026*: op verzoek van de docent staat `nosql.md` in
  `_toc.yml` nu als laatste hoofdstuk bij het onderdeel Verdieping (was eerst
  Lesmateriaal). Open punt: leerdoel 4 op `index.md` belooft NoSQL nog als
  gewone leerstof.
  

## syllabus/verdieping_*.md

- [x] Diagrammen in de oude stijl (hoofdletters, gestippelde lijnen) opnieuw tekenen in de huisstijl van de lesstof, met bewerkbare draw.io-bron
  *Merijn*: als je weer eens met opus gaat vlooien door deze syllabus mag je hier even preciezer aangeven wat je zou willen.
  En nieuwe diagrammen willen we waarschijnlijk liever als `svg` laten maken met AI, zodat AI er dan weer vergelijkbare diagrammen van kan maken.
  Als je nog tokens hebt... kunnen we dat vast een keer doen.

- [x] Uitwerkingen toevoegen bij de oefenopdrachten (`:::{solution}`)
  *Merijn*: de oefenopdrachten hebben geen uitwerkingen; al is het maar omdat ze meer als denk-oefening zijn bedoeld en/of tot inspiratie kunnen dienen voor de les.

## syllabus/verdieping_attributen.md

- [x] Nakijken: tekst over `char(10)` aangepast. De oude tekst zei dat kortere tekst niet mag; in SQL wordt die aangevuld met spaties
  *Merijn*: strikt genomen is dat aanvullen met spaties een implementatiedetail maar dat is wel wat waarschijnlijk de standaard is.

## syllabus/verdieping_ontwerp_verbeteren.md

- [x] Nakijken: in de redundantie-tabel stond Isa één keer met leerlingnummer 176, nu overal 175
  *Merijn*: dit klopt, en wordt juist verplichte kost denk ik, tenzij ik het al uitleg in de eedere hoofdstukken

- [x] Nakijken: in de matrix is de richting rechtgezet naar "reiziger bezoekt bezienswaardigheid" (stond "wordt bezocht")
  *Merijn*: lgtm opus... lgtm

## syllabus/verdieping_erd_naar_sql.md

- [x] Nakijken: de vraag "Is deze ERD in 1e, 2e en 3e normaalvorm?" is vervangen door "Zit er geen redundantie meer in?", omdat normaalvormen nergens worden uitgelegd
  *Merijn* dat lijkt me correct, ik *vermijd* de term 'normaalvorm' en dat heeft dan ook nog eens levels... net alsof dit een moeilijk vak is...
   Het is simpelweg 'zijn er geen problemen voor een echte database'. Zie het als de-wiskundificatie. Ja, ik heb naar Felienne geluisterd.
