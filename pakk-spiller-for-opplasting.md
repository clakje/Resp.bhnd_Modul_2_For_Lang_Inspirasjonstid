# Oppgave for KI-agent: Pakk «player»-mappen som frittstående opplasting

Bruk denne filen som instruks til KI-verktøyet i IDE-en din hver gang et scenario
er klart og du skal publisere det. Instruksen er generell — den gjelder uansett
hvilket scenario-prosjekt du står i, så lenge mappestrukturen er den samme som
beskrevet under.

## Bakgrunn / mappestruktur

Hvert scenario-prosjekt består av to deler:

- **Rotmappen** — «verktøyet»: scenario-generatoren og alt som hører til å bygge
  og teste scenariet (bl.a. `style.css`, `simulator.js`, `renderer.js`, samt
  test- og kladdefiler). Dette skal **aldri** slettes eller flyttes — det brukes
  til neste scenario.
- **`player/`-mappen** — «produktet»: den ferdige, avspillbare simuleringen
  (`index.html`, `app.js`, `player.css`, `scenario.json`, `scenario-data.js`,
  `bygg-scenario-data.js`, `README.md`).

`player/index.html` refererer i utgangspunktet til tre filer i rotmappen via
relative lenker (`../style.css`, `../simulator.js`, `../renderer.js`). Det
fungerer fint lokalt, men gjør at `player/`-mappen ikke virker alene når den
lastes opp et annet sted.

## Mål

Lag en **ny, frittstående kopi** av `player/`-mappen som kan zippes og lastes
opp direkte, uten avhengigheter utenfor mappen.

## Steg KI-agenten skal utføre

1. **Rør ikke originalprosjektet.** Lag output i en ny mappe, f.eks.
   `<scenario-navn>-player/`, ved siden av eller i en egen outputs-mappe.
2. Kopiér alt innholdet i `player/` til output-mappen.
3. Kopiér disse tre filene fra rotmappen til output-mappen:
   `style.css`, `simulator.js`, `renderer.js`.
4. Åpne `index.html` i output-mappen og erstatt de tre relative lenkene:
   - `../style.css` → `./style.css`
   - `../simulator.js` → `./simulator.js`
   - `../renderer.js` → `./renderer.js`
5. **Verifiser**: søk gjennom alle filer i output-mappen etter strengen
   `../`. Den skal ikke finnes igjen noe sted (heller ikke i kommentarer —
   oppdater eventuelle kommentarer som beskriver den gamle strukturen).
6. Fjern — **kun fra output-kopien**, aldri fra originalprosjektet — filer som
   ikke er nødvendige for at spilleren skal kjøre i nettleseren, hvis de
   finnes: kladde-/testmapper (f.eks. `scratch/`), testskript
   (`test_*.js`), eksportverktøy (`scenario-export.js/.css`),
   plandokumenter (`*_V1.txt` e.l.), duplikate scenario-json/md-filer som
   ligger utenfor `player/`, samt `.git` og `.gitignore`.
7. Gi output-mappen et filsystemvennlig navn: kun `a-z`, `0-9` og bindestrek —
   ingen mellomrom, æ/ø/å eller andre spesialtegn
   (f.eks. `asynkroni-hoy-triggersensitivitet-player`).
8. Komprimer output-mappen til en `.zip`-fil med samme navn.
9. List innholdet i zip-filen og bekreft at den inneholder nøyaktig:
   `index.html`, `app.js`, `player.css`, `scenario.json`, `scenario-data.js`,
   `style.css`, `simulator.js`, `renderer.js`
   (`bygg-scenario-data.js` og `README.md` kan valgfritt følge med — de er
   ikke nødvendige for nettleseren, men skader ikke).

## Definisjon av «ferdig»

- Zip-filen kan pakkes ut, og `index.html` kan åpnes direkte i en nettleser
  (også med dobbeltklikk / `file://`) uten at noe mangler eller feiler.
- Ingen filer utenfor selve output-mappen er nødvendige for at siden skal
  virke.
- Originalprosjektet (rotmappen og `player/`) er fullstendig urørt.

## Ikke gjør

- Slett **aldri** `.git`, testfiler, `scratch/` eller andre verktøyfiler fra
  selve arbeidsprosjektet — kun fra output-kopien.
- Slett **aldri** `style.css`, `simulator.js` eller `renderer.js` fra
  rotmappen — de skal fortsatt ligge der til neste scenario.
