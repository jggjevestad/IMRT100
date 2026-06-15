(tuntreet)=
# Hvor høyt er Tuntreet?

I denne oppgaven skal dere bestemme høyden på det historiske og majestetiske Tuntreet midt på NMBU-campus. Dere skal bruke to vidt forskjellige metoder: tradisjonell landmåling med totalstasjon (trigonometri) og moderne fjernmåling ved å analysere en 3D-lasersky (LiDAR) i CloudCompare.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">Tuntreet i Urbygningen-parken <br> <code>59.66598° N, 10.76905° E</code> (UTM32N: 6614480, 600200)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">Totalstasjon, stativ, målebånd, prisme</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="https://www.cloudcompare.org">CloudCompare</a>, Laserdata (NMBU OneDrive)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">3 - 4 timer</span>
  </div>
</div>

```{image} ../bilder/tuntreet.jpg
:alt: Tuntreet ved NMBU
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
Tuntreet på NMBU-tunet er et av universitetets mest kjente symboler. Å bestemme høyden på et stort tre kan være overraskende utfordrende, ettersom man ikke enkelt kan klatre opp med et målebånd. Geomatikere løser dette enten ved å bruke vinkler og trigonometri på bakken, eller ved hjelp av flybåren laserskanning (LiDAR), der milliarder av laserpulser skytes ned fra et fly for å kartlegge terrenget og vegetasjonen i 3D.

---

## 🛠️ Forberedelser
* **Teori**: Repeter enkel trigonometri ($\tan(\theta) = \text{motstående} / \text{hosliggende}$).
* **Installasjon**: Last ned og installer [CloudCompare](https://www.cloudcompare.org) på din PC.
* **Nedlasting av data**: Last ned laserdata (.las/.laz filer) for NMBU Campus fra [Laserdata NMBU](https://eduumb-my.sharepoint.com/:f:/g/personal/jon_glenn_gjevestad_nmbu_no/EhZNW6vu5CFJrBjHd5rTwPIBYbGtYXwHpw2Tk1TwTj1q0g?e=XCT4er) eller direkte fra [hoydedata.no](https://hoydedata.no).
* **QGIS-hjelp**: Se manualen [Introduksjon til CloudCompare](../bruksanvisninger/cc_intro.md) for veiledning.

---

## 🏃‍♂️ Gjennomføring

### Metode 1: Trigonometrisk høydemåling (Feltarbeid)
1. **Måleplan**: Lag en enkel skisse på papir. Hvis du plasserer totalstasjonen i en avstand $D$ fra treet, og måler vertikalvinkelen (eller siktevinklene) til hhv. treets rot ($\theta_{\text{bunn}}$) og treets topp ($\theta_{\text{topp}}$), hvordan beregner du den totale høyden $H$?
2. **Lab-test**: Test ut måleplanen inne på landmålingslaben først ved å måle høyden på en dørkarm eller en markør på veggen.
3. **Feltmåling**: Sett opp totalstasjonen på plenen slik at dere har fri sikt til både toppen av Tuntreet og stammen nede ved bakken.
4. Mål den horisontale avstanden $D$ til stammen.
5. Sikt inn og les av vertikalvinklene til hhv. rot og topp.
6. Beregn høyden $H$ ved hjelp av vinkelformlene.

### Metode 2: Laserskanning (Fjernmåling i CloudCompare)
1. Åpne CloudCompare og importer `.las` / `.laz` fila for campus-området.
2. Bruk **Segment-verktøyet** (saksikonet) til å klippe ut en liten boks som kun inneholder Tuntreet og bakken rett under treet.
3. Se etter de høyeste punktene i trekronen og de laveste punktene på bakken under treet.
4. Bruk **måleverktøyet** (Point-to-Point Distance) i CloudCompare til å måle avstanden langs Z-aksen (vertikal avstand) fra det høyeste punktet i trekronen ned til bakken.

---

## 📝 Rapportoppgaver

:::{important} Viktig
Svar på spørsmålene under og vis beregninger og skjermbilder fra CloudCompare i grupperapporten.
:::

### Spørsmål

1. **Skisse og Måleplan**: Tegn opp en geometrisk skisse som viser måleoppsettet for totalstasjonen. Vis formlene dere brukte for å beregne høyden.
2. **Resultatsammenligning**:
   * Hvilken høyde kom dere frem til ved bruk av **totalstasjon**? (Vis rådata som avstander, vinkler og utregning).
   * Hvilken høyde kom dere frem til ved bruk av **laserskanning i CloudCompare**? (Legg ved et skjermbilde av den klippede punktskyen av treet med målingen markert).
3. **Feilanalyse og Diskusjon**:
   * Hvorfor er de to resultatene eventuelt avvikende?
   * Hva er de største feilkildene ved trigonometrisk måling i felt (f.eks. er det lett å sikte på det absolutte toppunktet av kronen)?
   * Hva er begrensningene til laserskanning fra fly (f.eks. punkttetthet, om laseren faktisk traff det aller øverste bladet på treet)?
   * Hvilken metode stoler dere mest på, og hvorfor?
