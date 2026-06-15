(qgis_csv_eksport)=
# Eksportere punkter til CSV fra QGIS

CSV-formatet er praktisk når du skal bearbeide koordinater videre i f.eks. Python, Excel eller andre analyseverktøy. QGIS kan eksportere alle typer vektorlag til CSV og samtidig transformere koordinatene til ønsket koordinatsystem.

Typisk resultat etter eksport:

```
X,Y
600013.797,6615537.210
600013.794,6615537.215
600013.795,6615537.220
```

## Fremgangsmåte

### 1. Last inn dataene i QGIS

Importer filen din (KML, GPX, GeoPackage e.l.) som vanlig. Er dataene en linje eller flate, og du ønsker koordinatene til enkeltpunktene, må du først konvertere til punktgeometri.

```{figure} ../bilder/qgis/csv_eksport/1.png
```

### 2. Konvertere linje til punkt (ved behov)

Velg `Vektor > Geometriverktøy > Punktuttrekk` fra toppmenyen.

```{figure} ../bilder/qgis/csv_eksport/meny.png
```

Velg laget ditt som inndatalag og trykk **Kjør**. Du får et nytt midlertidig punkt-lag.

```{figure} ../bilder/qgis/csv_eksport/punktuttrekk.png
```

### 3. Eksportere til CSV

Høyreklikk på punkt-laget i lagpanelet og velg `Eksporter > Lagre objekter som ...`.

```{figure} ../bilder/qgis/csv_eksport/eksport1.png
```

I eksportvinduet konfigurerer du følgende:

| Innstilling | Verdi |
|-------------|-------|
| **Format** | Comma Separated Value [CSV] |
| **Filnavn** | Sti og filnavn, f.eks. `koordinater.csv` |
| **KRS** | Ønsket koordinatsystem, f.eks. `ETRS89 / UTM sone 32N` (EPSG:25832) |
| **GEOMETRY** | `AS_XY` – skriver X og Y som egne kolonner |
| **Bibehold lagmetadata** | Fjern haken – ikke nødvendig |

Under **Velg felt å eksportere** kan du trykke **Fravelg alle** og deretter huke av kun de feltene du trenger. De geometribaserte koordinatene legges til automatisk av `AS_XY`-innstillingen.

```{figure} ../bilder/qgis/csv_eksport/eksportvindu.png
```

:::{tip}
Velger du `ETRS89 / UTM sone 32N` som KRS, vil koordinatene være i meter – nyttig for statistiske beregninger som gjennomsnitt og standardavvik.
:::

### 4. Kjør eksporten

Trykk **OK**. Åpne den eksporterte filen i Notepad eller en tekstvisuer og kontroller at den ser riktig ut:

```
X,Y
600013.797162439,6615537.20985808
600013.793633959,6615537.21533447
600013.794641339,6615537.21981804
600013.780259357,6615537.25174379
600013.763210001,6615537.27802741
[ ... ]
```

X-verdien er øst (easting) og Y-verdien er nord (northing) i UTM-koordinater.
