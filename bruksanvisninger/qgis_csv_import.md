(qgis_csv_import)=
# Legge inn punkt fra csv filer i QGIS

CSV står for comma seperated values og er den enkleste måten å lagre data i tabellform. Det er rett og slett data seperert med komma, f.eks en liste med koordinater:
```
name,     easting,    northing,    elevation
AASC,     600389.138, 6614931.498,  94.575
FLO3,     600153.479, 6615523.159, 103.808
G010,     599667.953, 6615798.982,  98.851
```

Har dere koordinater dere vill putte inn i qgis er den aller enkleste metoden å lage en csv fil i dette formatet og importere den

## Fremgangsmåte

Trykk på `lag > Legg til Lag > Legg til tegnseparert tekstlag ...`
```{figure} ../bilder/qgis/csv/meny.png
```

I vinduet dere får opp må dere under fanen _Geometridefinisjon_ velge riktig x og y kolonne og riktig KRS. Det er som regel ETRS89 UTM 32
```{figure} ../bilder/qgis/csv/import.png
```

Trykk legg til så skal punktene dukke opp som et lag:
```{figure} ../bilder/qgis/csv/kart.png
```

For å endre på utseende til punktene kan dere høyreklikke på laget og velge egenskaper:
```{figure} ../bilder/qgis/csv/egenskaper.png
```

Under symbologi kan dere velge farge og tegn:
```{figure} ../bilder/qgis/csv/symbologi.png
```

Under påskrift kan dere få navnet på punktet til å dukke opp i kartet. Husk å velg riktig kolonne i verdifeltet

```{figure} ../bilder/qgis/csv/paskrift.png
```