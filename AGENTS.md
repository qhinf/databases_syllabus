# AGENTS.md — databases_syllabus

Aantekeningen voor AI-agents (en mensen) die aan deze repository werken.
De uitgebreide notities staan in [`ai_memories/`](ai_memories/):

- [`ai_memories/project_overview.md`](ai_memories/project_overview.md) — wat dit
  project is, voor wie, en wat de eis van de stof is
- [`ai_memories/content_map.md`](ai_memories/content_map.md) — samenvatting per
  hoofdstuk, begrippenlijst, alle oefenlabels
- [`ai_memories/stijl_en_valkuilen.md`](ai_memories/stijl_en_valkuilen.md) —
  schrijf- en opmaakconventies, bekende fouten en gaten in de stof

## Regels op een rij (lees dit eerst)

1. **Alle inhoud is Nederlandstalig**, in de informele stem van de docent
   ("je", "we", "de docent"). Taalcorrecties zijn welkom, stijlveranderingen niet.
2. **Werk op de versie-branch, niet op `main`.** De actieve branch is `2627-2`
   (schooljaar 2026/2027, blok 2). `main` is verouderd (2024) en wordt bewust
   genegeerd. Maak per blok een nieuwe branch.
3. **Alleen bestanden die in `syllabus/_toc.yml` staan horen bij het boek**
   (`only_build_toc_files: true`). Nieuw hoofdstuk = bestand + regel in `_toc.yml`
   + update van `ai_memories/content_map.md`.
4. **Gebruik substituties** uit `syllabus/_config.yml`: `{{ squeek }}`,
   `{{ deadline }}`, `{{ deadline_uitstel_aanvragen }}`, `{{ deadline_uitstel }}`,
   `{{ docent }}`, `{{ docent_email }}`. Hardcode geen deadlines, links of namen.
5. **Kom niet aan `{{ versie }}`** en niet aan de regel met
   `<!-- Deze regel niet wijzigen! -->` in `index.md`: versiebeheer loopt globaal
   via de Q-vakken-syllabusomgeving (repo `qhinf/syllabi`). De `html`-,
   `repository`- en `launch_buttons`-instellingen zijn ook globaal.
6. **`{{ squeek }}` wijst tijdelijk naar `https://www.disney.com`** omdat Squeek
   (https://sql.merijn.xyz, het SQL-oefensysteem van de docent) down is. Dit is
   een bewuste noodoplossing voor blok 2026/2027. Herstel de link zodra Squeek
   terug is, of meld het probleem expliciet. "Fix" het niet door er SQL-stof bij
   te gaan schrijven: de SQL-opdrachten zelf zijn er (nog) niet. Squeek heette
   voorheen **Sjaaq**; die oude naam staat nog in de git-geschiedenis en in de
   verouderde html-resten in `syllabus/_build/`.
7. **Houd de vaste begrippenparen aan** (zie `ai_memories/content_map.md`):
   tabel/entiteit, kolom/attribuut (nooit "rij" in een ontwerp), primary key/UID,
   foreign key/vreemde sleutel, kardinaliteit, ERDish-zinnen, redundantie,
   tussenentiteit. De vier kardinaliteiten heten exact *nul of één*, *precies
   één*, *nul of meer*, *één of meer*.
8. **Er zijn twee ERD-notatiestijlen in één boek**: de lesstof gebruikt
   `(#) * o`, verdieping4 gebruikt `1..*`, `0..*`, `1`, `0..1` en
   "totn/veelv/knvv/kntv". Behandel beide als bestaand recht, en maak een
   nieuwe oefening niet per ongeluk in nog een derde stijl.
9. **Bekende figuurfouten** (roep ze niet per ongeluk "weg te corrigeren"):
   `assets/ontwerpen_relaties/crows-feet-enumeration.png` heeft een fout label
   en `assets/sleutels_en_relaties/db-relaties-20250918.drawio.png` toont
   andere id's dan de tekst. In `todo.md` staat dat beide nakijken; er is ook een
   openstaand punt "laat alle figuren nakijken door vibos.nl".
10. **Openstaande punten staan in `todo.md`** (root, getrackt). In de markdown
    zelf staan in-text todo's als HTML-comment `<!-- todo: ... -->`, zodat ze niet
    op de site zichtbaar zijn. Nieuwe todo's: daar bijhouden, niet in de tekst.
11. **Commitberichten in het Nederlands**, kort en per onderwerp. Houd de
    `Co-Authored-By:`-trailer aan als je als agent werkt.

## Bronnen van waarheid

| Waarde | Waar |
|---|---|
| Hoofdstukvolgorde | `syllabus/_toc.yml` |
| Deadlines, links, docentnaam | `syllabus/_config.yml` (substituties) |
| Officieel vakoverzicht | <https://inhoud.qvakken.nl/vak/databases-en-sql> |
| Openstaande werkpunten | `todo.md` |
| Wat er al (niet) is gebeurd | `git log --oneline` op de versie-branch |

`syllabus/_build/` is gitignored en verouderd (html-resten van 2024 en 2025,
inclusief pagina's die niet meer bestaan). Gebruik het niet als bron van waarheid.
