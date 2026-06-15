(qgis_csv_import)=
# Legge inn punkter fra CSV-fil i QGIS

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

- **Filnavn** – bla frem til CSV-filen din
- **Filformat** – velg _CSV_ (komma som skilletegn er standard)
- **Geometridefinisjon** – velg _Punktkoordinater_ og angi riktig kolonne for X (øst) og Y (nord). Har filen høydeverdi kan du også sette Z-felt.
- **KRS** – velg riktig koordinatsystem. For Sør-Norge er dette som regel `ETRS89 / UTM sone 32N` (EPSG:25832)

```{figure} ../bilder/qgis/csv/import.png
```

:::{tip}
Kontroller forhåndsvisningen nederst i vinduet – der ser du at kolonner er tolket riktig før du trykker _Legg til_.
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
