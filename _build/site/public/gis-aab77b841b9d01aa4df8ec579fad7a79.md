(gis)=
# Digitalisering med GIS

I denne oppgaven skal dere ta papirkartet dere tegnet for hånd, skanne det, og georeferere/digitalisere det i QGIS slik at det kan legges direkte inn i et moderne geografisk informasjonssystem.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">PC-Lab (TF-bygget) / Hjemmearbeid</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">Skannet eller avfotografert papirkart</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="../bruksanvisninger/qgis_intro.md">QGIS</a></span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">3 - 4 timer</span>
  </div>
</div>

```{image} ../bilder/gis.png
:alt: GIS data lag
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
Et Geografisk Informasjonssystem (GIS) er et PC-basert verktøy for å samle inn, lagre, analysere og presentere geografisk data. Kjernen i GIS er konseptet med **kartlag**: data organiseres i forskjellige lag (som veier, bygninger, høydekonturer og satellittbilder) som ligger oppå hverandre i et felles koordinatsystem. I denne oppgaven lærer du å hente analoge data inn i denne digitale strukturen.

---

## 🛠️ Forberedelser
* Sørg for at du har [installert og konfigurert QGIS](../bruksanvisninger/qgis_intro.md) på din maskin.
* Skann inn håndtegnede kart fra oppgaven [Tegn ditt eget kart](tegne_kart.md) og lagre det som en bildefil (PNG/JPG).
  * *Skannemuligheter:* Det står skannere nord i 2. etasje i **TF1** ([kartlenke Mazemap](https://link.mazemap.com/lBEoe8OY)) og i **Biotekbygningen** ([kartlenke Mazemap](https://link.mazemap.com/DDupHkQX)). 
  * Logg inn på [myprint.nmbu.no](https://myprint.nmbu.no/) for å koble studentkortet ditt til printeren første gang. Skannede filer havner i mappen `Scan` på din OneDrive.

---

## 🏃‍♂️ Gjennomføring

### 1. Oppsett av QGIS-prosjekt
1. Start QGIS og opprett et nytt prosjekt.
2. Sett prosjektets koordinatsystem (CRS) til **ETRS89 / UTM zone 32N (EPSG:25832)** i nederste høyre hjørne.
3. Legg til et bakgrunnskart (f.eks. Norgeskart eller flybilde) ved å koble til en WMS-tjeneste (se [bruksanvisning for WMS](../bruksanvisninger/qgis_wms.md)).

### 2. Georeferering
1. Gå til menyen *Rastr* -> *Georefererer* (Georeferencer).
2. Last inn det skannede bildet av kartet deres.
3. Følg trinnene i [bruksanvisningen for georeferering](../bruksanvisninger/qgis_georef.md) til å legge inn passpunkter (GCPs). Dere må velge minst 4 godt fordelte punkter på kartet (som f.eks. hushjørner eller stikryss) som dere også kan identifisere på bakgrunnskartet i QGIS.
4. Kjør transformasjonen og se at kartet legger seg riktig på plass på campus.

---

## 📝 Rapportoppgaver

> [!IMPORTANT]
> Svar på følgende spørsmål i grupperapporten og illustrer med relevante skjermbilder fra QGIS.

1. **Georefererings-prosess**: Beskriv hvordan dere gikk frem for å georeferere kartet. Hvilke punkter valgte dere som passpunkter (GCPs), og hvorfor?
2. **Nøyaktighets-analyse**: Undersøk i QGIS hvor godt det georefererte kartet samsvarer med det offisielle bakgrunnskartet. Diskuter eventuelle feilkilder (f.eks. ujevn skanning, feil skrittmåling, skjevhet i papir, passpunkt-plassering).
3. **Sammenligning**: Sammenlign detaljnivået og kvaliteten på kartet dere tegnet for hånd med offisielle digitale kart over campus (f.eks. Norgeskart). Hvilke detaljer fikk dere med som mangler på de offisielle kartene?
4. **Erfaringer med digitalisering**: Hva var de største utfordringene med å oversette det analoge papirkartet til et digitalt GIS-lag?
5. **Faglig utbytte**: Hva har dere lært om georeferering og digital kartografi gjennom denne oppgaven?