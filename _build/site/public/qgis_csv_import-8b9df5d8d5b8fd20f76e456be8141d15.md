(qgis_csv_import)=
# Importere punkter fra CSV til QGIS

CSV (Comma Separated Values) er et enkelt, universelt tekstformat for lagring av tabelldata. Denne brukerveiledningen viser hvordan du importerer lister med koordinater (f.eks. måledata fra GNSS/GPS) fra en CSV-fil til geografiske punkter i QGIS.

---

## 📋 Oversikt
For at QGIS skal kunne importere en CSV-fil med punkter, må filen ha følgende struktur:
* **Feltnavn (header)**: Første rad må definere kolonnenavn (f.eks. `name,easting,northing,elevation`).
* **Koordinater**: Øst (X) og Nord (Y) må ligge i egne kolonner.
* **Separering**: Verdiene må være skilt med et definert tegn (komma, semikolon eller tabulator).

Eksempel på korrekt format:
```text
name,easting,northing,elevation
P102,600043.410,6615542.322,97.511
P103,600011.199,6615540.593,98.128
```

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Åpne importdialogen
1. Gå til toppmenyen i QGIS: **Lag (Layer)** -> **Legg til lag (Add Layer)** -> **Legg til tegnseparert tekstlag (Add Delimited Text Layer)**.
   ```{figure} ../bilder/qgis/csv/meny.png
   :align: center
   ```
2. Du kan også bruke snarveien `Ctrl+L` (åpner datakildebehandleren) og velge fanen **Tegnseparert tekst (Delimited Text)**.

### 2. Konfigurere importinnstillinger
Gjør følgende valg i dialogboksen:
   ```{figure} ../bilder/qgis/csv/import.png
   :align: center
   ```
* **Filnavn**: Klikk på knappen til høyre (`...`) og bla frem til CSV-filen din.
* **Filformat**: 
  * Velg **CSV (kommaseparert)** dersom filen bruker engelsk format (komma).
  * Velg **Egendefinerte skilletegn** og kryss av for *Semikolon* dersom filen er laget i en norsk versjon av Excel.
* **Poster og felt**: 
  * Kryss av for **Første post har feltnavn (First record has field names)**.
  * Kryss av for **Desimalskilletegn er komma (Decimal separator is comma)** dersom tallene dine bruker komma som desimaltegn (f.eks. `97,511` i stedet for `97.511`).
* **Geometridefinisjon**: 
  * Velg **Punktkoordinater**.
  * **X-felt (Easting)**: Velg kolonnen som inneholder øst-koordinaten (f.eks. `easting` eller `E`).
  * **Y-felt (Northing)**: Velg kolonnen som inneholder nord-koordinaten (f.eks. `northing` or `N`).
  * **Z-felt**: Hvis filen har høyder, sett denne til høydekolonnen (f.eks. `elevation` eller `H`).
* **Komp-KRS**: Velg koordinatsystemet tallene er målt i (f.eks. `EPSG:25832 - ETRS89 / UTM zone 32N`).
* *Forhåndsvisning*: Sjekk tabellen nederst i vinduet for å se at kolonnene er skilt riktig før du trykker **Legg til**. Klikk deretter **Lukk**.

### 3. Visualisere og merke punktene
Etter importen dukker punktene opp i kartvisningen:
   ```{figure} ../bilder/qgis/csv/kart.png
   :align: center
   ```
For å tilpasse utseendet:
1. Høyreklikk på CSV-laget i lagpanelet og velg **Egenskaper (Properties)**.
2. Gå til fanen **Symbologi**: Her kan du endre farge, symbol, form og størrelse på punktene.
   ```{figure} ../bilder/qgis/csv/symbologi.png
   :align: center
   ```
3. Gå til fanen **Påskrift (Labels)**: Endre fra *Ingen påskrifter* til **Enkeltpåskrifter (Single Labels)**. Sett *Verdi* til kolonnen som inneholder navnet (f.eks. `name`) for å vise punktnavn på kartet.
   ```{figure} ../bilder/qgis/csv/paskrift.png
   :align: center
   ```

---

## 💡 Tips & feilsøking

* **🚨 Desimaltegn-krøll (Tom tabell eller feilplasserte punkter)**: Dette er den vanligste feilen i Norge. Hvis CSV-filen har tall som `600043,41` (med komma), og QGIS tror desimalskilletegnet er et punkt, vil koordinatene bli tolket helt feil (eller bli tomme). Husk å huke av for *Desimalskilletegn er komma* i import-innstillingene dersom dataene dine har komma.
* **X- og Y-felt byttet om**: Hvis punktene dine havner på helt feil sted (f.eks. i havet sør for Ekvator), har du sannsynligvis byttet om X og Y. Husk at **X alltid tilsvarer Øst (Easting)** og **Y alltid tilsvarer Nord (Northing)**.
* **CSV-filer er skrivebeskyttet**: Et importert CSV-lag er kun en kobling til en tekstfil. Du kan ikke redigere tabellen eller legge til nye punkter i QGIS direkte. For å gjøre laget redigerbart, må du eksportere det til et GIS-format: Høyreklikk på laget -> **Eksporter** -> **Lagre objekter som (Save Features As)** -> Velg **GeoPackage** og trykk OK.
