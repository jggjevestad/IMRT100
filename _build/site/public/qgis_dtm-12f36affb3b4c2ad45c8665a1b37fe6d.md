(qgis_dtm)=
# DTM og terrenganalyse i QGIS

Denne brukerveiledningen viser hvordan du laster ned en digital terrengmodell (DTM) fra Kartverkets portal og bruker den til visualisering og terrenganalyse i QGIS. Den støtter oppgaven [Terrenganalyse med høydedata](../oppgaver/høydemodell.md).

---

## 📋 Oversikt
En **Digital Terrengmodell (DTM)** representerer den nakne jordoverflaten i 3D, uten hus, trær og vegetasjon. Dataene lagres som **rasterdata** (et rutenett av piksler), der hver piksel inneholder et enkelt tall som angir høyden over havet i meter. 

Ved å prosessere en DTM i QGIS kan vi utlede verdifull informasjon om landskapet, som hvor bratt det er (slope), hvordan sollyset faller på det (hillshade), og hvor vannet vil renne (avrenningslinjer).

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Last ned høydedata fra hoydedata.no
1. Gå til [hoydedata.no](https://hoydedata.no) og logg inn (opprett gratis bruker).
2. Klikk på **Eksporter data**-verktøyet.
3. Zoom inn til NMBU campus og tegn et rektangel rundt området du ønsker.
4. Under **Produkter**, velg **DTM 1** (1 meters oppløsning for detaljert visning) eller **DTM 10** (10 meters oppløsning for raskere prosessering).
5. Velg filformatet **GeoTIFF (.tif)** og koordinatsystemet **ETRS89 / UTM zone 32N (EPSG:25832)**.
6. Trykk **Eksporter** og last ned den resulterende zip-filen. Pakk den ut på din PC.

### 2. Importere og fargelegge DTM i QGIS
1. Dra `.tif`-filen direkte inn i **Lagpanelet** i QGIS. Det vises som et mørkt gråtonebilde.
2. For å legge på farger: Høyreklikk på laget -> **Egenskaper (Properties)** -> **Symbologi (Symbology)**.
3. Endre *Rendertype* fra *Enkeltbånd grå* til **Enkeltbånd pseudofarge (Singleband pseudocolor)**.
4. Velg en passende fargeskala (f.eks. *Terrain* eller *Wiki*) og trykk **OK**.
   ```{figure} ../bilder/qgis/dtm/pseudofarge.png
   :align: center
   ```

### 3. Generere Hillshade (Skyggerelieff)
Hillshade simulerer sollys over terrenget, noe som gjør 3D-former synlige på et 2D-kart:
1. Gå til toppmenyen: **Raster** -> **Analyse** -> **Hillshade**.
2. Velg DTM-en som inndatalag.
3. Trykk **Kjør (Run)**. Det opprettes et nytt gråtonelag som viser skyggene i terrenget.
   ```{figure} ../bilder/qgis/dtm/hillshade.png
   :align: center
   ```
4. *Tips:* Du kan oppnå samme effekt direkte i lagegenskapene under **Symbologi** ved å endre *Rendertype* til **Hillshade**.
   ```{figure} ../bilder/qgis/dtm/hillshade_egenskaper.png
   :align: center
   ```

### 4. Generere konturlinjer (Høydekurver)
1. Gå til toppmenyen: **Raster** -> **Utdrag** -> **Konturlinjer (Contour)**.
2. Velg DTM-en din som inndatalag.
3. Sett **Avstand mellom konturlinjene** (ekvidistanse) til f.eks. `1.0` meter eller `5.0` meter.
4. Trykk **Kjør**. Konturlinjene legges til som et nytt vektorlag.
   ```{figure} ../bilder/qgis/dtm/konturlinjer.png
   :align: center
   ```
5. *Tips:* For å vise tall på linjene, høyreklikk på konturlaget -> **Egenskaper** -> **Etiketter (Labels)**. Endre til *Enkeltetiketter* og sett verdi til kolonnen `ELEV`.

### 5. Generere helningskart (Slope)
Helning viser hvor bratt terrenget er målt i grader ($0^\circ$ er flatt, $90^\circ$ er loddrett):
1. Gå til **Behandling (Processing)** -> **Verktøykasse (Toolbox)** (eller trykk `Ctrl+Alt+T`).
2. Søk etter `Helning` (Slope) og dobbeltklikk på verktøyet under *Rasterterrengsanalyse*.
3. Velg DTM-en som høydelag og trykk **Kjør**.
4. Fargelegg det nye helningslaget med pseudofarge (f.eks. rødt for flatt og blått for bratt).
   ```{figure} ../bilder/qgis/dtm/slope.png
   :align: center
   ```

### 6. Opprette høydeprofil (Tverrsnitt)
QGIS har et innebygd verktøy for å analysere høyder langs en linje:
1. Gå til toppmenyen: **Vis (View)** -> **Høydeprofil (Elevation Profile)**. Et nytt vindu åpnes nederst.
2. Klikk på **Tegn profillinje**-ikonet (blyant-ikonet øverst i panelet).
3. Klikk på kartet for å starte linjen, klikk for å lage knekkpunkter, og **høyreklikk** for å avslutte profilen.
4. Høydeprofilen tegnes umiddelbart opp i det nedre panelet.
   ```{figure} ../bilder/qgis/dtm/elevation_profile.png
   :align: center
   ```

---

## 💡 Tips & feilsøking

* **Feilmeldinger ved rasteranalyse**: Dersom verktøyene som *Hillshade* eller *Slope* gir en feilmelding, sjekk at inndata-rasterfilen ikke har mellomrom eller særnorske tegn (æ, ø, å) i filbanen eller filnavnet. Dette er en klassisk årsak til at GDAL-biblioteket i QGIS krasjer.
* **Utydelige høydekurver**: Hvis du setter ekvidistansen til 1 meter over et veldig bratt eller stort område, vil skjermen fylles med tette, svarte linjer. Hvis dette skjer, slett laget og kjør verktøyet på nytt med 5 eller 10 meters avstand.
* **Høydeprofilen er tom**: Sørg for at øye-ikonet ved siden av DTM-laget ditt i Lagpanelet er huket av (laget må være synlig), og at DTM-en dekker området der du tegnet profillinjen.
