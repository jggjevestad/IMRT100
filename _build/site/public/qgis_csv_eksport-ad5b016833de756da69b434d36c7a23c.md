(qgis_csv_eksport)=
# Eksportere csv fil fra QGIS

```
X               , Y
600013.797162439, 6615537.20985808
600013.793633959, 6615537.21533447
600013.794641339, 6615537.21981804
600013.780259357, 6615537.25174379
[ ... ]
```

Ofte ønsker man å gjøre utregninger på koordinater i f.eks Python. KML, GPX og andre filformat kan være veldig knotete å lese inn i python så ofte er det lurt å konvertere disse til csv (comma seperated values). I tillegg kan QGIS transformere geografiske koordinater til f.eks UTM, noe som også er mer innvikla å gjøre i python.

## Fremgangsmåte:

### 1. Konvertere linje til punkt

Last inn fila deres i QGIS. Er det en kml fil vil man ofte bare få en linje. Da må vi konvertere den til punkt for å kunne lage csv fila.

```{figure} ../bilder/qgis/csv_eksport/1.png
```

For å konvertere linje til punkt velger dere `Vektor -> Geometriverktøy -> Punktuttrekk` fra toppmenyen

```{figure} ../bilder/qgis/csv_eksport/meny.png
```

I vinduet velger dere laget dere importerte og trykker kjør

```{figure} ../bilder/qgis/csv_eksport/punktuttrekk.png
```

### 2. Eksportere punkt til en csv fil
Nå kan dere eksportere punktene. Høyreklikk på laget og velg `Eksporter -> Lagre objekter som ...`
```{figure} ../bilder/qgis/csv_eksport/eksport1.png
```

Nå får dere opp et vindu med mange valg. Her er det dere må endre:

- **Format: Comma Seperated Value [CSV]**
- **Filnavn: ditt_filnavn.csv** Husk å lagre fila på en lur plass
- **KRS: ETRS89 UTM32** Hvilket koordinatsystem du vill eksportere til. Skal man regne på gjennomsnitt og annen statistikk er UTM fint fordi enhetene er i meter
- **Hvilke felt skal eksporteres...** Utvid menyen og trykk på `Fravelg alle`. Hvis dere vill kan dere eksportere de feltene dere synes er interresante, men mesteparten er bare støy
- **Bibehold lagmetadata: [ ]** Denne lager en ekstra fil som inneholder forklaringer til kolonnene. Det er som regel ikke nødvendig.

- **GEOMETRY: AS_XY** hvilket format det blir på koordinatene. I eksemplene i dette emnet bruker vi X,Y (øst, nord)
```{figure} ../bilder/qgis/csv_eksport/eksportvindu.png
```

Når alt er klart trykker dere kjør og koordinater lagres forhåpentligvis som dere ønska. Åpne fila i f.eks notepad og sjekk at den ser riktig ut:

```
X,Y
600013.797162439,6615537.20985808
600013.793633959,6615537.21533447
600013.794641339,6615537.21981804
600013.780259357,6615537.25174379
600013.763210001,6615537.27802741
600013.749096082,6615537.29993294
600013.624070957,6615538.09655177
600013.722789364,6615539.75816998
600013.718462,6615539.75136928
600013.709893976,6615539.75559669
600013.704172031,6615539.75878608
600013.694715767,6615539.75407648
600013.683954276,6615539.7560169
600013.663706736,6615539.75436108
600013.653597858,6615539.75297649
600013.646364845,6615539.74944053
600013.654783946,6615539.75077991
600013.655704621,6615539.73743467
600013.637352701,6615539.74919943
600013.185514383,6615540.09921231
[ ... ]
```