(gnss_opptak)=
# GNSS-opptak på Mobiltelefon

Smarttelefoner har innebygde GNSS-mottakere (GPS), men standard kart-apper som Google Maps lagrer som regel ikke posisjonsdata som filer. Denne brukerveiledningen viser hvordan du bruker egne apper til å logge posisjonsspor og eksportere dem som **GPX** eller **KML** for analyse.

---

## 📋 Oversikt
* **KML (Keyhole Markup Language)**: Et xml-basert format opprinnelig utviklet for Google Earth. Det egner seg svært godt til visualisering av spor og punkter i både Google Earth og QGIS.
* **GPX (GPS Exchange Format)**: Den globale standarden for GPS-måledata. Inneholder koordinater, tidspunkt og høyde for hvert enkelt loggede punkt.

For statistiske analyser (som nøyaktighets-oppgaven) bør du sette oppdateringsfrekvensen i appen til **1 sekund**. Da får du flest mulig målepunkter å regne gjennomsnitt av.

---

## 🔧 Veiledning for Android: BasicAirData GPS Logger

**BasicAirData GPS Logger** er en åpen kildekode-app som logger posisjonsdata helt lokalt på telefonen uten behov for internettilkobling.

### 1. Konfigurere appen
1. Last ned appen fra Google Play Butikk.
2. Åpne menyen (tre prikker øverst til høyre) -> **Settings**.
3. Under **TRACKING**:
   * Sett **Time Filter** til *1 second* (for nøyaktighetstest) eller *3 seconds* (for vanlig sporing).
4. Under **EXPORTATION**:
   * Huk av for **Export Tracks in KML** (eller GPX).
   * Angi lagringsmappe under *Export Folder*.

### 2. Starte og eksportere opptak
1. Gå utendørs og åpne appen.
2. Vent til du ser teksten **GPS Fix** øverst i grønt. Dette betyr at telefonen har kontakt med tilstrekkelig mange satellitter.
3. Trykk på den store **Record**-knappen nederst for å starte loggingen.
4. Gå ruten din (eller la telefonen ligge i ro over en bolt i 10 minutter).
5. Trykk på **Stop** og bekreft.
6. Gå til fanen **TRACKLIST**, klikk på sporet ditt og velg **Export** (del filen via e-post eller OneDrive til PCen din).
   ```{figure} ../bilder/gpslogger/screenshot_01.jpg
   :width: 150px
   :align: center
   ```

---

## 🔧 Veiledning for iOS: myTracks

**myTracks** er en stabil og brukervennlig GPS-logger for iPhone, iPad og Apple Watch som støtter iCloud-synkronisering.

### 1. Starte opptak
1. Last ned myTracks fra App Store.
2. Åpne appen og trykk på **Record**-knappen (kamera- og lyd-ikonet) for å åpne kontrollskjermen.
3. Klikk på **Start Recording** for å starte datainnsamlingen.
   ```{figure} ../bilder/mytracks/start.jpg
   :width: 150px
   :align: center
   ```
   ```{figure} ../bilder/mytracks/start_recording.jpg
   :width: 150px
   :align: center
   ```

### 2. Eksportere sporet som KML
1. Trykk på **Stop Recording** når du er ferdig.
2. Åpne sporet fra listen i appen.
3. Trykk på **Del (dele-ikonet)** øverst til høyre.
   ```{figure} ../bilder/mytracks/opened_track_export.jpg
   :width: 150px
   :align: center
   ```
4. I eksport-dialogen, sørg for å huke av for **Use Google Format (KML)**. (myTracks eksporterer til GPX som standard, men vi ønsker KML for Google Earth-kompatibilitet).
   ```{figure} ../bilder/mytracks/export_dialog.jpg
   :width: 150px
   :align: center
   ```
5. Klikk **Export** og send filen til deg selv via e-post, AirDrop eller skylagring.

---

## 💡 Tips & feilsøking

* **🚨 Batterisparing kutter opptaket midtveis**: Både Android og iOS har strenge strømsparingsfunksjoner. Dersom du legger telefonen i lomma og låser skjermen, vil operativsystemet ofte "drepe" GPS-appen for å spare batteri. 
  * **Løsning**: Gå inn på telefonens innstillinger -> Batteri -> App-batteribruk, finn GPS Logger-appen og endre innstillingen fra *Optimalisert* til *Ubegrenset (Unrestricted / Background activity allowed)*.
* **Ustabil start (hakkete rute i begynnelsen)**: Når du starter opptaket, bruker telefonen litt tid på å beregne banene til satellittene (efemeridedata). Vent alltid i **1 minutt utendørs** etter at du har fått "GPS Fix" før du starter opptaket. Da unngår du store koordinat-hopp i starten av loggen din.
