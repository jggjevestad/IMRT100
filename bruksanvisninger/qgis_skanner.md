# Visualisering av skannerdata i QGIS

Her er en steg-for-steg bruksanvisning for hvordan du kan visualisere de polare koordinatene (retning og avstand) fra skanneren/Maqueen-roboten som punkter (X, Y) i QGIS. 

Siden skanneren din lagrer data som en vinkel og en avstand fra skanneren, må vi bruke et spesialverktøy i QGIS for å regne dette om til kartkoordinater før vi kan se det.

## Steg 1: Importer filen til QGIS som en tabell
Først må vi laste inn dataene inn i QGIS uten geometri, ettersom filen bare inneholder tallverdier.

1. Åpne **QGIS**.
2. Gå til toppmenyen og velg **Lag** > **Legg til lag** > **Legg til avgrenset tekstlag...** (Layer > Add Layer > Add Delimited Text Layer...).
3. Klikk på de tre prikkene **[...]** ved *Filnavn* og velg filen din `skanning.csv`.
4. Under seksjonen *Filformat*, velg **Egendefinerte skilletegn** (Custom delimiters). Ut fra dataene dine ser det ut som du må krysse av for **Tabulator** (Tab) og/eller **Komma** for at kolonnene skal dele seg riktig.
5. Sjekk forhåndsvisningen nederst i vinduet. Kolonnene `tid`, `retning` og `avstand` skal stå i hver sin egen kolonne.
6. Under seksjonen *Geometridefinisjon* (Geometry Definition), velg **Ingen geometri (kun attributtabell)** (No geometry).
7. Klikk **Legg til** (Add) og deretter **Lukk** (Close). Du vil nå se `skanning`-tabellen din i lagpanelet (Layers) til venstre.

## Steg 2: Tegn punktene ved hjelp av matematikk
Nå skal vi bruke litt enkel trigonometri for å fortelle QGIS hvordan retning og avstand kan tegnes som et vanlig koordinat. (Formelen forvandler skannerens plassering til X=0 og Y=0).

1. Gå til toppmenyen og velg **Prosessering** > **Verktøykasse** (Processing > Toolbox) for å åpne verktøypanelet til høyre.
2. I søkefeltet i verktøykassen, skriv inn **Geometri via uttrykk** (Geometry by expression) og dobbeltklikk på verktøyet.
3. Fyll inn følgende i vinduet som spretter opp:
   * **Inndatalag (Input layer):** Velg `skanning`-tabellen.
   * **Resultatgeometritype (Output geometry type):** Velg **Punkt** (Point).
   * **Geometriuttrykk (Geometry expression):** Kopier og lim inn denne eksakte koden i tekstboksen:
     ```sql
     make_point("avstand" * sin(radians("retning")), "avstand" * cos(radians("retning")))
     ```
     *(Dette regner om vinkelen fra grader til radianer, og beregner deretter X- og Y-posisjonen i rommet)*.
4. Klikk på **Kjør** (Run) og deretter **Lukk**.

## Steg 3: Se på og tilpass visualiseringen
1. QGIS har nå laget et nytt lag i lagpanelet ditt, ofte kalt *Endret geometri* eller *Modified geometry*.
2. Høyreklikk på dette nye laget og velg **Zoom til lag** (Zoom to layer).
3. Du skal nå se en 2D-punktsky som viser alle hindringene roboten din skannet, der midten av skjermen representerer selve roboten.

> [!TIP]
> **Fargekode etter tid eller avstand**
> For å se skanningen tydeligere, dobbeltklikk på det nye punktslaget for å åpne *Egenskaper*. Gå til fanen **Symbologi**. Endre øverste rullgardinmeny fra *Enkelt symbol* til **Gradert** (Graduated). Sett *Verdi* (Value) til `tid`, velg en fin fargeskala og trykk på *Klassifiser*. Nå vil punktene skifte farge i samme rekkefølge som roboten snudde seg, noe som kan gi en stilig radareffekt!