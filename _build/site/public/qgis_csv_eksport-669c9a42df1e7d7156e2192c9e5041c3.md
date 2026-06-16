(qgis_csv_eksport)=
# Eksportere punkter fra QGIS til CSV

Denne brukerveiledningen viser hvordan du eksporterer et geografisk punktlag (eller trekker ut punkter fra en GPS-rute/linje) i QGIS og lagrer det som en CSV-fil. Dette er spesielt nyttig når du skal analysere koordinatene videre i f.eks. Python eller Excel.

---

## 📋 Oversikt
Når du eksporterer et punktlag fra QGIS til en CSV-fil, kan du automatisk beregne og legge til punktenes koordinater som egne kolonner i tabellen. 

Dersom du har registrert en rute som en kontinuerlig linje (f.eks. en `.gpx` eller `.kml` sporlogg fra mobilen), må du først splitte opp linjen i enkeltpunkter (noder/hjørnepunkter) før du kan eksportere koordinatene.

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Konvertere linje (sporlogg) til punkter (ved behov)
Dersom dataene dine allerede er enkeltpunkter, kan du hoppe rett til Steg 2. Hvis du har en linje:
1. Åpne QGIS-prosjektet ditt der sporloggen er lastet inn.
   ```{figure} ../bilder/qgis/csv_eksport/1.png
   :align: center
   ```
2. Gå til toppmenyen: **Vektor (Vector)** -> **Geometriverktøy (Geometry Tools)** -> **Punktuttrekk (Extract Vertices)**.
   ```{figure} ../bilder/qgis/csv_eksport/meny.png
   :align: center
   ```
3. Velg linjelaget ditt som *Inndatalag*.
4. Klikk **Kjør (Run)**. QGIS oppretter et nytt, midlertidig punktlag kalt *Uttrukne punkter* (Vertices) som inneholder alle knekkpunktene i linjen.
   ```{figure} ../bilder/qgis/csv_eksport/punktuttrekk.png
   :align: center
   ```

### 2. Eksportere punktlaget til CSV
1. Høyreklikk på punktlaget (eller *Uttrukne punkter*) i Lagpanelet.
2. Velg **Eksporter (Export)** -> **Lagre objekter som... (Save Features As...)**.
   ```{figure} ../bilder/qgis/csv_eksport/eksport1.png
   :align: center
   ```
3. I eksportvinduet setter du følgende innstillinger:
   * **Format**: Velg **Comma Separated Value [CSV]**.
   * **Filnavn**: Klikk på `...` og velg hvor filen skal lagres (f.eks. `mobil_maalinger.csv`).
   * **KRS (CRS)**: Velg **ETRS89 / UTM sone 32N (EPSG:25832)**. *Dette er viktig fordi det sikrer at koordinatene lagres i meter i stedet for grader.*
   * **Geometri (Geometry)**: Endre til **AS_XY**. *Dette forteller QGIS at koordinatene skal skrives inn i to egne kolonner kalt X (Øst) og Y (Nord) i CSV-filen.*
   * **Velg felt å eksportere**: Fjern haken på felter du ikke trenger (huk av kun for f.eks. `name` eller `time`).
   ```{figure} ../bilder/qgis/csv_eksport/eksportvindu.png
   :align: center
   ```
4. Klikk **OK**.

---

## 💡 Tips & feilsøking

* **🚨 Koordinater lagret i grader (desimalgrader) i stedet for meter**: Hvis du glemmer å sette KRS til et projisert system (som UTM sone 32N) under eksport, vil kolonnene X og Y inneholde verdier som `10.76905` og `59.66598` (breddegrad/lengdegrad). For å regne ut avvik og standardavvik i meter, *må* du eksportere på nytt med `EPSG:25832` slik at verdiene blir lagret i meter (f.eks. `600013.79` og `6615537.21`).
* **Format på desimaltegn**: Standardinnstillingen skriver tall med punktum som desimaltegn (`600013.79`). Dette fungerer utmerket i Python. Dersom du skal åpne filen i en norsk versjon av Microsoft Excel, kan det være enklere å sette *SEPARATOR* til **SEMICOLON** under *Lagsalternativer* i eksportvinduet, slik at tallene ikke blir tolket som tekst.
