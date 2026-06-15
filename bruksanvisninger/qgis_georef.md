(qgis_georef)=
# Georeferering i QGIS

Georeferering er prosessen med å plassere et uregistrert rasterbilde (f.eks. et skannet papirkart, luftfoto eller en gammel kartskisse) inn i et geografisk koordinatsystem, slik at det samsvarer med den virkelige verden.

---

## 📋 Oversikt
QGIS gjør dette ved at brukeren definerer fellespunkter – kalt **passpunkter** (Ground Control Points - GCP) – mellom rasterbildet og et offisielt bakgrunnskart. QGIS bruker disse punktene til å utføre en matematisk transformasjon som strekker, roterer og plasserer bildet riktig.

For best mulig resultat må passpunktene oppfylle disse kravene:
* **Minimum 4 punkter** (for transformasjonstypen *Projektiv*).
* **Jevnt fordelt** utover hele kartutsnittet (unngå at alle punkter samles i ett hjørne).
* Plassert på **tydelige og uforanderlige detaljer** (f.eks. hushjørner, stikryss eller store steiner).

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Start Georefereringsverktøyet
1. Åpne prosjektet ditt i QGIS.
2. Gå til toppmenyen: *Raster* -> *Georefererer* (Georeferencer).
   ```{figure} ../bilder/qgis/georeferering/meny.png
   :align: center
   ```
3. Klikk på **Åpne raster**-ikonet (det blå rutearket øverst til venstre) og velg bildefilen av kartet deres.
   ```{figure} ../bilder/qgis/georeferering/georef_vindu.png
   :align: center
   ```
   Bildet lastes inn i georefereringsvinduet:
   ```{figure} ../bilder/qgis/georeferering/georef_vindu2.png
   :align: center
   ```

### 2. Endre transformasjonsinnstillinger
Klikk på **Tannhjul-ikonet** (Instillinger for transformering) og gjør følgende valg:
* **Transformasjonstype**: *Projektiv* (anbefales for håndtegnede/skjeve kart da det kan strekke bildet i alle retninger).
* **Resamplingsmetode**: *Kubisk* (gir penest utjevning av piksler).
* **Mål-KRS**: Velg prosjektets koordinatsystem: `ETRS89 / UTM zone 32N (EPSG:25832)`.
* **Resultat-raster**: Velg hvor den nye, georefererte `.tif`-filen skal lagres.
* **Bruk 0 for gjennomsiktighet når nødvendig**: Huk av denne (☑️) for å unngå en stor, svart ramme rundt det ferdige kartet.
* Trykk **OK**.
   ```{figure} ../bilder/qgis/georeferering/innstillinger.png
   :align: center
   ```

### 3. Legge til passpunkter (GCP)
1. Klikk på **Legg til punkt**-verktøyet (ikonet med gult kryss).
2. Klikk på et gjenkjennelig punkt på det skannede bildet. Det dukker opp en boks som ber om koordinater:
   ```{figure} ../bilder/qgis/georeferering/koordinat.png
   :align: center
   ```
3. Klikk på knappen **Fra kartlerret (From map canvas)**.
4. Klikk på det nøyaktig samme punktet på bakgrunnskartet i QGIS sitt hovedvindu. Koordinatene (Øst og Nord) hentes automatisk inn. Trykk **OK**.
5. Gjenta dette til dere har lagt inn **minst 4 jevnt fordelte punkter**.

### 4. Kjør georefereringen
1. Klikk på den grønne **Play-knappen** (Start georeferering) øverst.
   ```{figure} ../bilder/qgis/georeferering/georef_vindu3.png
   :align: center
   ```
2. Kartet transformeres og legges automatisk til som et nytt lag i QGIS-prosjektet ditt.
3. Kontroller at det ligger på riktig sted.
   ```{figure} ../bilder/qgis/georeferering/ferdig.png
   :align: center
   ```

---

## 💡 Tips & feilsøking

* **🚨 Koordinatsnu (Øst/Nord-feil)**: Hvis du taster inn koordinater manuelt fra Norgeskart eller andre tjenester, husk at **QGIS bruker formatet (X=Øst, Y=Nord)**, mens Norgeskart ofte oppgir Nord (7-sifret) før Øst (6-sifret). Hvis du bytter om disse, havner kartet ditt i Somalia eller Antarktis!
* **Transformasjonen mislykkes**: Sjekk at du ikke har lagt inn passpunkter som ligger på en rett linje. Det gjør det matematisk umulig å beregne en 2D-transformasjon. Fordel punktene i en firkant.
* **Svart boks rundt kartet**: Hvis det georefererte kartet har fått en stor, stygg svart ramme, har du glemt å huke av for *Bruk 0 for gjennomsiktighet* i transformasjonsinnstillingene. Gå inn i innstillingene, huk av, og kjør georefereringen på nytt.