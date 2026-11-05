# Bug bounty 2025-2026

Je mag Sjaaq proberen te hacken, onder voorwaarden.

Als je het volgende bereikt, krijg je eeuwige roem (en ik verzin nog een
prijs). Eeuwige roem betekent dat ik op deze pagina een hall-of-fame
maak, en daarop meldt wat je hebt gevonden. Je naam mag erbij, hoeft niet.


> Main quest: Als je in Sjaaq queries van een andere student kunt zien of bewerken, of als je de tabellen van de opgaven kunt zien of bewerken, dan heb je Sjaaq gehackt voor de hoofdprijs. 

(Mogelijk komen hier side-quests)

## Let op! Dit is een productie-systeem!

Dit is een systeem dat 'productie' draait, dat wil zeggen dat als je overlast veroorzaakt, je mensen in problemen brengt. Gebruik daarom een beetje je gezonde verstand bij het hacken.

Daarom mag je in de laatste weken van een blok het systeem niet proberen te hacken.

PS: Wil je echt met grof geschut aan de gang en doe je bijvoorbeeld een module over security, neem contact op met de docent (die van security of Merijn Vogel, die Sjaaq heeft gemaakt).

Wellicht kan ik een extra versie voor je klaarzetten, of krijg je gewoon de hele broncode en mag je 'glass-box' security testen!
Let wel, dit is geen capture the flag, er zit niet gegarandeerd een veiligheidslek in. En de maker heeft verrassend veel vertrouwen in de security (en wil toch graag dat Sjaaq gehackt wordt, dan heeft-ie een verhaal voor een java-conferentie!)

## Wat je mag doen als ethisch hacker

Je mag queries uitvoeren via het query-interface, of op andere manieren proberen het backend dingen te laten doen die de maker niet heeft bedoeld.

## Wat je NIET mag doen als ethisch hacker

- Gaat door je experiment het systeem 'down' (het werkt voor niemand meer goed), meldt het dan onmiddelijk.
- Doe geen denial of service-aanvallen. Dus niet onnodig veel queries spammen, hele grote queries of onzin opslaan.
- Ga niet superveel accounts registreren, dat is niet hacken.

## Wat moet je doen als je een hack vindt

De prijs claimen bij de docent! Dat doe je via een direct bericht in teams en eventueel een mailtje.
Je legt uit wat je hebt gedaan en wat je zien, en waarom je denkt dat je daarmee het systeem hebt gehackt.

Je naam kan op de hall of fame komen te staan. En samenwerken is uiteraard toegestaan.


## Hoe Sjaaq werkt

Sjaaq bestaat uit een javascript front-end met een java programma als backend.
Het gebruikt geen 'frameworks', het is zoveel mogelijk native Java. De enige
echte afhankelijkheden zijn een eenvoudige json library (nanojson) en de
postgres database driver zodat JDBC werkt.

De database wordt benaderd via JDBC. Alle databases zijn postgres.

Er is een hoofd-database waar de opgaves in staan en waarin het werk leerlingen in wordt opgeslagen.
Dat is een gescheiden database ten opzichte van de databases waar de queries van studenten op
worden uitgevoerd.

Elke leerling heeft een eigen database. Dat is een kopie van een template database. Als een leerling zich registreert wordt die database gekopieerd.
Ook worden alle rechten zo gezet dat leerlingen niet per ongeluk in elkaars database zouden kunnen werken (ook al zijn ze identiek).

Data wordt nooit blijvend gewijzigd.
