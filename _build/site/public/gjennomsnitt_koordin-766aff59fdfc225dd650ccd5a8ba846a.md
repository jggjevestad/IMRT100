(gjennomsnitt_koordinater)=
# Brukerveiledning: Beregne Gjennomsnittskoordinater i QGIS

Denne brukerveiledningen viser hvordan du bruker QGIS sitt innebygde statistikkverktøy til å beregne ett enkelt gjennomsnittspunkt fra en sky av GPS-målinger (statiske målinger logget over tid). Dette støtter oppgaven [Måling av fastpunkter med GNSS og RTK](../oppgaver/gnss_punkt.md).

---

## 📋 Oversikt
Når en mobiltelefon eller en enkel GPS-mottaker ligger i ro på et fastpunkt, vil posisjonsangivelsen "hoppe" litt rundt fra sekund til sekund på grunn av atmosfærisk støy og satellittkonfigurasjoner. Ved å logge punkter kontinuerlig i noen minutter, kan vi ta gjennomsnittet av alle disse enkeltmålingene. Dette utligner de tilfeldige feilene og gir en posisjon som ligger mye nærmere den virkelige bolteposisjonen.

QGIS kan lese KML-, GPX- og CSV-filer og beregne dette gjennomsnittet automatisk med få klikk.

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Last inn måledataene
1. Åpne QGIS-prosjektet ditt.
2. Importere GPS-loggfilen (f.eks. KML, GPX eller CSV) ved å dra den direkte inn i kartvinduet eller Lagpanelet. Du vil se en tett klyngesky av punkter som ligger rundt fastpunktet.
   ```{figure} ../bilder/qgis/gjennomsnitt/lag.png
   :align: center
   ```

### 2. Aktiver prosesserings-verktøykassen
Dersom du ikke har sidepanelet *Verktøykasse (Processing Toolbox)* synlig på høyre side:
1. Gå til toppmenyen: **Prosessering (Processing)**.
2. Huk av for **Verktøykasse (Toolbox)** (eller trykk `Ctrl+Alt+T`).
   ```{figure} ../bilder/qgis/gjennomsnitt/meny.png
   :align: center
   ```

### 3. Kjøre verktøyet for gjennomsnittskoordinater
1. I verktøykassesøket til høyre, søk etter `Gjennomsnitt` (Mean).
2. Dobbeltklikk på verktøyet **Gjennomsnittskoordinat(er) / Mean coordinate(s)** under kategorien *Vektoranalyse*.
   ```{figure} ../bilder/qgis/gjennomsnitt/verktoy.png
   :align: center
   ```
3. I dialogvinduet som åpnes:
   * **Inndatalag**: Velg GPS-laget ditt som inneholder punktskyen.
   * **Gjennomsnittskoordinater**: Klikk på `...` for å velge om du vil lagre punktet permanent som en fil (f.eks. GeoPackage), eller la den stå som et *Midlertidig lag* (Temporary layer).
4. Klikk **Kjør (Run)** og deretter **Lukk**.
   ```{figure} ../bilder/qgis/gjennomsnitt/vindu.png
   :align: center
   ```
Et nytt lag kalt *Gjennomsnittskoordinater* legges til i prosjektet ditt, representert ved et enkelt punkt midt i klyngen.

### 4. Lese av de gjennomsnittlige koordinatene
For å finne de nøyaktige tallene for gjennomsnittsposisjonen:
1. Velg verktøyet **Identifiser objekter (Identify Features)** på topplinjen (ikonet med en pil og en liten blå info-hake `i`).
   ```{figure} ../bilder/qgis/gjennomsnitt/identifiser.png
   :align: center
   ```
2. Klikk på det nye gjennomsnittspunktet i kartet.
3. I sidepanelet som åpnes på høyre side, kan du lese av koordinatene:
   * **X**: Den gjennomsnittlige øst-koordinaten i prosjektets koordinatsystem (f.eks. i UTM-meter).
   * **Y**: Den gjennomsnittlige nord-koordinaten (i UTM-meter).
   * **MEAN_X / MEAN_Y**: De opprinnelige rå-gjennomsnittsverdiene (som regel i desimalgrader dersom råfilen brukte WGS84).
   ```{figure} ../bilder/qgis/gjennomsnitt/koordinater.png
   :align: center
   ```

---

## 💡 Tips & feilsøking

* **🚨 Avviket er i desimalgrader i stedet for meter**: Når du skal beregne avstander og standardavvik, sørg for at du leser av verdiene for **X og Y** (prosjektets koordinatsystem, som må være satt til UTM sone 32N, EPSG:25832), ikke *MEAN_X* og *MEAN_Y* (som ofte er i desimalgrader som `10.76...`).
* **Verktøyet gir tomt resultat**: Sjekk at GPS-laget ditt faktisk inneholder punkter og ikke er tomme sporlinjer. Dersom det er en linje, må du først kjøre *Punktuttrekk* (se [bruksanvisning for CSV-eksport](qgis_csv_eksport.md)) før du kan kjøre verktøyet for gjennomsnittskoordinater.
