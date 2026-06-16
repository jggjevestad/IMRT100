(orienteringslop)=
# Orienteringsløp: Korteste vei

I denne oppgaven skal dere ut i felt på campus for å løse et klassisk optimeringsproblem (Traveling Salesperson Problem). Dere skal planlegge og gå en rute som innom alle oppgitte orienteringsposter på kortest mulig distanse, mens posisjonen din logges kontinuerlig.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">NMBU Campus (Start og mål ved TF-bygget)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">Smarttelefon eller DIY Arduino GPS-logger, kart over poster</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value">GPS Logger App, <a href="../filer/qgis/Orienteringsløp_korteste_vei/korteste_vei.qgz">QGIS (resultatmal)</a></span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">2 - 3 timer</span>
  </div>
</div>

```{image} ../bilder/orientering.jpg
:alt: Orienteringsløper i aksjon
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
Å finne den mest effektive ruten mellom flere geografiske punkter er et av de mest kjente problemene i geoinformatikk og logistikk (rutingsanalyse). I denne øvelsen skal dere bruke hjernen som rutingsalgoritme for å finne den korteste veien mellom en rekke poster på campus. Dere logger sporet deres, og vi vil analysere hvem som klarte å planlegge den mest optimale ruten.

---

## 🛠️ Forberedelser
* Sørg for at minst én på gruppa har en fullt ladet mobil med en fungerende GNSS/GPS-sporingsapp (f.eks. GPS Logger, MyTracks) satt til å logge hvert sekund.
* Eventuelt kan dere bruke den selvbygde Arduino GPS-loggeren med SD-kort!
* Last ned kartet og resultatfilen i QGIS for å analysere andres ruter etterpå: [korteste_vei.qgz](../filer/qgis/Orienteringsløp_korteste_vei/korteste_vei.qgz).

---

## 🏃‍♂️ Gjennomføring

### Løpsregler
1. **Mål**: Besøk alle postene som er avmerket på utdelt kart.
2. **Fri rekkefølge**: Dere kan ta postene i akkurat den rekkefølgen dere selv ønsker.
3. **Sporing**: Start GPS-loggingen idet dere krysser startstreken ved TF-bygget, og stopp den først når dere er tilbake på start.
4. **Transport**: Det er kun tillatt å gå eller løpe. Sykling, el-sparkesykkel eller bil fører til umiddelbar diskvalifikasjon!
5. **Innlevering**: Eksporter sporet som en GPX- eller KML-fil og lever den på Canvas rett etter målgang.

:::{tip} Vinnere
Gruppen med det korteste loggede GNSS-sporet (målt i meter i QGIS) som har vært innom alle poster, stikker av med den offisielle seieren og en flott premie!
:::

---

## 📝 Rapportoppgaver

:::{important} Viktig
Besvar spørsmålene under i grupperapporten og legg ved et kartbilde av det loggede sporet deres lagt oppå campus-kartet i QGIS.
:::

### Spørsmål

1. **Ruteplanlegging**: Beskriv hvordan dere planla ruten før start. Hvilke geometriske eller topografiske hensyn tok dere da dere valgte rekkefølgen på postene?
2. **Resultatanalyse**: 
   * Hva ble den totale lengden på sporet deres i meter?
   * Sammenlign sporet deres med vinnergruppen eller andre gruppers spor. Hvor tapte/tente dere meter?
3. **Avvik**: Stemte den planlagte ruten overens med det dere faktisk gikk? Hvis ikke, hva skyldtes avvikene (f.eks. sperringer, feilnavigering, dårlig GPS-signal som hoppet)?
4. **Erfaring med GPS-data**: Hva har dere lært om nøyaktigheten til kontinuerlig GPS-logging (f.eks. ser dere "støy" eller sikksakk-linjer i sporet der dere stod stille ved postene)?
