(qgis_csv_import)=
# Importere punkter fra CSV til QGIS

CSV (Comma Separated Values) er et enkelt tekstformat for tabelldata der verdier er skilt med komma. Det er et godt egnet format for å flytte koordinatlister inn i QGIS fordi det er leselig, kompakt og støttet av nesten alle programmer.

Et typisk eksempel på en CSV-fil med punktkoordinater:

```
name,easting,northing,elevation
AASC,600389.138,6614931.498,94.575
FLO3,600153.479,6615523.159,103.808
G010,599667.953,6615798.982,98.851
```

Filen må ha en header-linje (kolonnenavn i første rad) og koordinatene må stå i egne kolonner.

## Fremgangsmåte

### 1. Åpne importdialogen

Velg `Lag > Legg til lag > Legg til tegnseparert tekstlag ...` fra toppmenyen.

```{figure} ../bilder/qgis/csv/meny.png
```

Du kan også åpne **Datakildebehandler** med `Ctrl+L` og velge fanen _Tegnseparert tekst_.

### 2. Konfigurer importinnstillingene

I dialogvinduet som åpnes:

**Filnavn og lagnavn**

- **Filnavn** – bla frem til CSV-filen din
- **Lagnavn** – QGIS foreslår et navn basert på filnavnet; endre om ønskelig

**Filformat**

- Velg _CSV_ for kommaseparerte filer (standard)
- Velg _Egendefinerte skilletegn_ for andre skilletegn som semikolon eller tabulator (`\t`)
- Velg _Regulæruttrykk som skilletegn_ for mer avanserte mønstre

**Poster og felt**

- **Antall header-linjer som skal forkastes** – hopp over eventuelle innledende linjer som ikke er data
- Aktiver _Første post har feltnavn_ hvis første rad inneholder kolonnenavn (vanligvis standard)
- Aktiver _Detekter felttyper_ for at QGIS automatisk skal gjenkjenne tall, datoer osv.
- Aktiver _Fjern mellomrom fra felt_ for å rydde bort ledende/etterfølgende mellomrom
- Aktiver _Desimalskilletegn er komma_ ved europeisk tallformat

**Geometridefinisjon**

Velg hvordan QGIS skal tolke de romlige dataene:

- _Punktkoordinater_ – velg riktig kolonne for X (øst) og Y (nord). Har filen høydeverdi, sett også Z-felt. Kryss av _DMS-koordinater_ dersom koordinatene er i grader/minutter/sekunder.
- _Well known text (WKT)_ – velg kolonnen som inneholder WKT-geometri
- _Ingen geometri (kun attributtabell)_ – for ikke-romlige tabeller

**KRS** – velg riktig koordinatsystem. For Sør-Norge er dette som regel `ETRS89 / UTM sone 32N` (EPSG:25832).

**Lagsinnstillinger**

- _Bruk romlig indeks_ – anbefales; forbedrer ytelsen ved visning og utvalg
- _Bruk delmengdeindeks_ – nyttig dersom du skal filtrere laget
- _Overvåk fil_ – oppdaterer laget automatisk hvis filen endres eksternt

```{figure} ../bilder/qgis/csv/import.png
```

:::{tip}
Kontroller forhåndsvisningen nederst i vinduet – der ser du at kolonner og datatyper er tolket riktig før du trykker _Legg til_.
:::

### 3. Legg til laget

Trykk **Legg til**. Punktene vises nå som et eget lag i kartet.

```{figure} ../bilder/qgis/csv/kart.png
```

### 4. Endre utseende

Høyreklikk på laget i lagpanelet og velg **Egenskaper**.

```{figure} ../bilder/qgis/csv/egenskaper.png
```

Under **Symbologi** kan du endre farge, form og størrelse på punktene.

```{figure} ../bilder/qgis/csv/symbologi.png
```

### 5. Legg til punktnavn i kartet

Under fanen **Påskrift** kan du aktivere navnevisning. Velg riktig kolonne (f.eks. `name`) i verdifeltet for å vise punktnavn direkte i kartvisningen.

```{figure} ../bilder/qgis/csv/paskrift.png
```

:::{note}
Et CSV-lag i QGIS er kun et midlertidig visningslag. Vil du lagre det som en permanent geografisk fil, høyreklikk på laget og velg `Eksporter > Lagre objekter som ...` og velg f.eks. GeoPackage eller Shapefile.
:::
