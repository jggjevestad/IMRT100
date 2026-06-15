(microbit_kompass)=
# Magnetfelt og Digitalt Kompass med micro:bit

I denne oppgaven skal vi lære hvordan mikrokontrolleren BBC micro:bit kan brukes som et digitalt kompass for retningsmåling. Vi skal programmere sensoren, kalibrere den utendørs på campus, og beregne den lokale magnetiske misvisningen (deklinasjonen) ved å sammenligne målingene mot kjente geografiske koordinater.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">NMBU Campus (Mellom fastpunkt P102 og P103)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">BBC micro:bit (V1 eller V2), batteripakke, USB-kabel, sikte-linjal (valgfritt)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="https://makecode.microbit.org">MakeCode Editor</a>, QGIS</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">2 - 3 timer</span>
  </div>
</div>

```{image} ../bilder/coordinates.jpg
:alt: Retningsnavigering og koordinater
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon

For å navigere og utføre oppmåling i felt må vi kunne bestemme retninger. Retningen til et objekt angis ofte som en **asimut** (vinkel målt med klokken fra Nord, fra $0^\circ$ til $360^\circ$).

Det er imidlertid viktig å skille mellom to ulike nord-retninger:
*   **Geografisk Nord (Sant Nord)**: Retningen langs jordoverflaten som peker rett mot den geografiske Nordpolen (jordens rotasjonsakse). Det er denne nord-retningen våre offisielle UTM-kartlag og QGIS-prosjekter baserer seg på.
*   **Magnetisk Nord**: Retningen magnetnåla i et kompass peker, mot jordens magnetiske nordpol.

Differansen mellom geografisk nord og magnetisk nord kalles **magnetisk deklinasjon** (eller **misvisning**). Denne misvisningen endrer seg over tid og varierer avhengig av hvor du befinner deg på jorda. I Sør-Norge ligger misvisningen i dag på ca. $3^\circ\text{ til }4^\circ$ østlig (kompasset peker litt for langt til høyre/øst).

BBC micro:bit har et innebygd magnetometer (en elektronisk kompass-brikke) som måler styrken og retningen på magnetiske felt i tre dimensjoner. Ved å kalibrere sensoren kan vi bruke den til å måle magnetiske retninger i felt.

---

## 🛠️ Forberedelser

*   Koble micro:bit-en til din PC ved hjelp av USB-kabelen.
*   Åpne nettleseren og gå til [makecode.microbit.org](https://makecode.microbit.org/).
*   Gjør deg kjent med hvordan du overfører programvare til micro:bit ved å dra den nedlastede `.hex`-filen over til micro:bit-stasjonen på PC-en din (eller bruk direkte paring over WebUSB).

---

## 🏃‍♂️ Gjennomføring

### Del 1: Programmering og Kalibrering av Magnetometeret

Før vi kan gjøre målinger, må vi programmere micro:bit-en til å lese av kompassretningen og vise den på LED-skjermen når vi trykker på en knapp.

1.  Opprett et nytt prosjekt i MakeCode.
2.  Lag et program som henter **kompassretning (compass heading)** i grader:
    *   *Tips*: Bruk en `når knapp A trykkes`-blokk som viser tallet på skjermen (`vis tall`).
    *   *Tips (valgfritt)*: Du kan programmere micro:bit-en til å vise bokstaven **N**, **Ø**, **S** eller **V** avhengig av om vinkelen er nær hhv. $0^\circ, 90^\circ, 180^\circ$ eller $270^\circ$.
3.  Last ned programmet til din micro:bit.
4.  **Kalibrering (TILT TO FILL SCREEN)**: Første gang programmet kjører og prøver å lese kompasset, vil micro:bit starte et kalibreringsspill. LED-skjermen vil vise teksten **TILT TO FILL SCREEN** (eller **DRAW A CIRCLE** på eldre modeller).
    *   Hold micro:bit-en flatt og tilt den i alle retninger slik at alle de 25 LED-lysene på skjermen tennes.
    *   Når alle lysene er tent, vises et smilefjes, og kompasset er klart til bruk.

### Del 2: Retningsmåling i felt på Campus

For å finne misvisningen skal vi stå på det kjente fastpunktet **P102** og måle retningen til nabopunktet **P103** ved hjelp av micro:bit-en.

1.  Gå ut til plenen på campus der fastpunktene **P102** og **P103** er plassert (metallbolter i bakken).
2.  Plasser deg nøyaktig over bolten **P102**.
3.  Hold micro:bit-en helt horisontalt. Sikt langs langsiden av micro:bit-en (eller legg en flat linjal oppå som sikte) rett mot bolten **P103**.
4.  Trykk på knapp **A** og les av vinkelen (kompasskursen i grader).
5.  Gjenta målingen 5 ganger for å minimere tilfeldige målefeil. Husk å ta et lite steg til siden, gå tilbake og sikte på nytt mellom hver måling.
6.  Noter målingene i tabellen:

| Måling nr. | Målt kompassretning (Magnetisk asimut) |
| :--- | :--- |
| 1 | *Fyll inn* |
| 2 | *Fyll inn* |
| 3 | *Fyll inn* |
| 4 | *Fyll inn* |
| 5 | *Fyll inn* |
| **Snitt** | **Beregnes i rapporten** |

---

## 📝 Rapportoppgaver

:::{important} Viktig
Besvar spørsmålene under i grupperapporten. Vis utregningene deres trinn-for-trinn og forklar de faglige begrepene.
:::

### Spørsmål

1.  **Programkode og kalibrering**:
    *   Legg ved et skjermbilde av MakeCode-blokkene (eller Python-koden) dere programmerte.
    *   Forklar kort hvorfor det er helt nødvendig å kalibrere et elektronisk kompass (magnetometer) før bruk. Hva er det som egentlig skjer under kalibreringen ("hard iron" / "soft iron" støy)?
2.  **Måleresultater**:
    *   Regn ut gjennomsnittlig målt kompassretning (magnetisk asimut) fra felteksperimentet deres.
3.  **Beregning av Geografisk Asimut**:
    *   Bruk de offisielle koordinatene til **P102** og **P103** (i UTM sone 32N):
        *   **P102**: $E = 600043.410\text{ m},\ N = 6615542.322\text{ m}$
        *   **P103**: $E = 600011.199\text{ m},\ N = 6615540.593\text{ m}$
    *   Beregn differansen i østlig retning ($\Delta E = E_{103} - E_{102}$) og nordlig retning ($\Delta N = N_{103} - N_{102}$).
    *   Bruk trigonometri ($\tan$) til å beregne den geografiske asimuten (retningsvinkelen fra Nord) fra **P102** til **P103**. Vis formel, mellomregning og endelig asimut i grader! *(Husk å sjekke hvilken kvadrant vinkelen ligger i!)*.
4.  **Beregning av magnetisk deklinasjon (misvisning)**:
    *   Bruk formelen:
        $$\text{Misvisning} = \text{Geografisk asimut} - \text{Magnetisk asimut (gjennomsnitt)}$$
    *   Hva ble misvisningen på campus basert på deres måling?
    *   Søk opp den offisielle magnetiske misvisningen for Ås på internett (f.eks. hos Kartverket eller NOAA). Samsvarer deres måling med den offisielle verdien? Forklar eventuelle avvik.
5.  **Feilkilder**:
    *   Hvilke feilkilder finnes når man måler magnetiske felt med micro:bit (tenk på metallgjenstander i nærheten, armeringsjern i betong, elektriske kabler eller mobiltelefoner)?
