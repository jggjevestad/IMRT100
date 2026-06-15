(gnss_noyaktighet)=
# GNSS Nøyaktighetsanalyse

I denne oppgaven skal dere gå systematisk til verks for å analysere og beregne den faktiske nøyaktigheten til ulike GNSS-mottakere (smarttelefon, Arduino DIY-mottaker og eventuelt RTK). Dere vil lære å bruke statistiske verktøy i Python for å regne ut avvik og standardavvik på posisjonsmålinger.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">NMBU Campus (valgfritt fastpunkt i åpent terreng)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">Smarttelefon, DIY Arduino GPS Logger, målebånd</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="../bruksanvisninger/python_intro.html">Python (Jupyter Notebook)</a>, <a href="../bruksanvisninger/qgis_intro.html">QGIS</a></span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">3 - 4 timer</span>
  </div>
</div>

```{image} ../bilder/gps_acc.jpg
:alt: Satellitter og posisjonspresisjon
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
Nøyaktigheten til en posisjon bestemt med GNSS er aldri konstant. Den påvirkes kontinuerlig av eksterne faktorer som satellittenes geometri på himmelen (DOP-verdier), atmosfæriske forstyrrelser (ionosfæren og troposfæren), klokkefeil og ikke minst **flerveisfeil (multipath)** der signalene reflekteres fra bygninger eller trær før de når mottakeren. Ved å logge data over en tidsperiode mens mottakeren ligger helt stille over et punkt med kjente koordinater, kan vi bruke statistisk analyse til å kartlegge nøyaktigheten.

---

## 🛠️ Forberedelser
* Sørg for at dere har logget minst 10 minutter med posisjonsdata (1 sekunds intervall) fra minst to forskjellige enheter (f.eks. mobiltelefon og Arduino-mottakeren dere bygde).
* Finn de "sanne" koordinatene til punktet dere målte over (boltekoordinater fra [fastmerker.csv](../ressurser/fastmerker.csv), eller bruk gjennomsnittet av målingene deres som referanse dersom dere målte et umerket punkt).

---

## 🏃‍♂️ Gjennomføring

### Steg 1: Eksportere koordinatdata
1. Konverter loggfilene deres til CSV-format (se [bruksanvisning for eksport](../bruksanvisninger/qgis_csv_eksport.md)).
2. Sørg for at koordinatene er i meter (projisert referansesystem, som ETRS89 / UTM sone 32N) slik at avstandsberegningene blir enkle å gjøre i meter.

### Steg 2: Statistisk analyse i Python
Bruk Jupyter Notebook og Python til å:
1. Importere CSV-filene.
2. Beregne avstanden fra hver enkelt måling $(E_i, N_i)$ til den sanne posisjonen $(E_{\text{sann}}, N_{\text{sann}})$ ved bruk av Pythagoras' læresetning:
   $$d_i = \sqrt{(E_i - E_{\text{sann}})^2 + (N_i - N_{\text{sann}})^2}$$
3. Regne ut **gjennomsnittlig avvik (systematisk feil)** og **standardavvik (tilfeldig feil)** for avstandene:
   $$\sigma = \sqrt{\frac{1}{N-1}\sum_{i=1}^N (d_i - d_{\text{snitt}})^2}$$
4. Plot punktskyen (scatter plot) av målingene rundt det sanne punktet for å visualisere spredningen.

---

## 📝 Rapportoppgaver

> [!IMPORTANT]
> Besvar spørsmålene under og vis tabeller og plott fra Python-analysen i grupperapporten.

1. **Statistiske Resultater**:
   * Presenter gjennomsnittlig avvik og standardavvik for hhv. mobiltelefonen og Arduino-mottakeren i en ryddig tabell.
   * Legg ved spredningsplottet (scatter plot) av målingene fra Python for begge enhetene.
2. **Komparativ diskusjon**:
   * Hvilken mottaker hadde best nøyaktighet og presisjon? Stemte dette med forventningene deres? Hvorfor tror du det er slik (tenk på antennekvalitet, maskinvare og støy)?
3. **Satellittgeometri**:
   * Hvordan påvirker antall synlige satellitter og deres posisjon på himmelen (angitt som **DOP**-verdier i NMEA/GPX) målenøyaktigheten?
4. **Feilkilder**:
   * Hva er de største feilkildene i satellittposisjonering i et urbant miljø som NMBU Campus (f.eks. nær store murbygninger som Urbygningen eller TF-bygget)? Forklar begrepet *flerveisfeil* (multipath).