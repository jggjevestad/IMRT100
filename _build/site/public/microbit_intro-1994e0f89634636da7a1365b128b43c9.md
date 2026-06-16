(microbit_intro)=
# Brukerveiledning: Programmering av micro:bit kompass

BBC micro:bit er en liten, rimelig mikrokontroller utstyrt med en rekke innebygde sensorer. For geoinformatikk og landmåling er det spesielt **magnetometeret** (det digitale kompasset) som er nyttig. Magnetometeret måler styrken og retningen på magnetiske felt, og lar oss beregne retningsvinkler (asimuter) i felt.

---

## 📋 Oversikt

For å bruke micro:bit som et digitalt kompass må vi:
1.  **Programmere enheten**: Skrive kode som henter retningsverdier ($0\text{–}360^\circ$) fra kompasset og viser dem på skjermen.
2.  **Overføre programmet**: Laste koden over til micro:bit.
3.  **Kalibrere sensoren**: micro:bit må kalibreres for å skille jordas naturlige magnetfelt fra magnetisk støy (f.eks. fra batteripakken eller metallrammer).

### Støttede plattformer og språk
*   **MakeCode Editor**: Grafisk blokk-programmering og JavaScript/TypeScript (anbefalt for nybegynnere). Nettadresse: [makecode.microbit.org](https://makecode.microbit.org/).
*   **MicroPython**: Tekstbasert Python-programmering (ypperlig for de som vil lære mer avansert koding). Nettadresse: [python.microbit.org](https://python.microbit.org/).

---

## 🔧 Steg-for-steg bruksanvisning

### Metode 1: Blokkprogrammering i MakeCode

Dette er den enkleste måten å komme i gang på. Vi programmerer micro:bit-en til å vise vinkelen på LED-skjermen når vi trykker på knapp **A**.

1.  Åpne nettleseren og gå til [makecode.microbit.org](https://makecode.microbit.org/). Opprett et **Nytt prosjekt**.
2.  Hent en `når knapp A trykkes`-blokk fra **Inndata (Input)**-kategorien.
3.  Inni denne blokken legger du en `vis tall`-blokk fra **Basis (Basic)**-kategorien.
4.  I hullet for tallet legger du blokken `kompassretning (valg)` fra **Inndata (Input)**.

Programmet ditt vil se slik ut i JavaScript/Blocks-form:

```typescript
input.onButtonPressed(Button.A, function () {
    basic.showNumber(input.compassHeading())
})
```

5.  Koble micro:bit-en til PC-en med USB-kabelen.
6.  Klikk på **Last ned (Download)** nederst i venstre hjørne av MakeCode-skjermen.
7.  Dersom du har paret micro:bit over WebUSB, overføres koden direkte. Hvis ikke, lastes en `.hex`-fil ned til din PC. Dra og slipp denne filen over til micro:bit-stasjonen i Utforskeren (Windows) eller Finder (macOS).

---

### Metode 2: Programmering med MicroPython

For de som foretrekker tekstbasert programmering, kan micro:bit settes opp med Python. Her bruker vi biblioteket `microbit` og funksjonen `compass.heading()`.

1.  Åpne nettleseren og gå til [python.microbit.org](https://python.microbit.org/).
2.  Skriv inn følgende kode:

```python
from microbit import *

# Sjekk om kalibrering er nødvendig ved oppstart
if not compass.is_calibrated():
    compass.calibrate()

while True:
    # Hvis knapp A trykkes, les av kompasset og rull verdien på skjermen
    if button_a.is_pressed():
        heading = compass.heading()
        display.scroll(str(heading))
    sleep(100)
```

3.  Koble til micro:bit-en og klikk **Send to micro:bit** (eller last ned `.hex`-filen og overfør den manuelt).

---

## 🧭 Slik gjennomfører du kalibreringen

Første gang koden prøver å hente en verdi fra kompasset, vil micro:bit kreve kalibrering. Dette skjer automatisk.

1.  LED-skjermen vil begynne å rulle teksten **TILT TO FILL SCREEN** (eller vise en sirkel av blinkende lys).
2.  Hold micro:bit-en flatt i hånden din.
3.  Tilt micro:bit-en forsiktig i alle retninger (som om du prøver å rulle en liten kule rundt på skjermen) slik at alle de 25 LED-lysene tennes.
4.  Når du har tent alle lysene, vil skjermen vise et **smilefjes** og spille en liten lyd (hvis høyttaler er tilkoblet). Kalibreringen er da fullført!

---

## 💡 Tips & feilsøking

*   **Kalibreringen starter aldri**: Kalibreringen utløses kun når programmet ber om kompassretningen. Sørg for at du har trykket på knapp **A** slik at koden faktisk kjører kompass-funksjonen.
*   **Vanskelig å fylle skjermen (kalibreringen henger)**:
    *   Prøv å bevege micro:bit-en roligere og i større vinkler.
    *   Stå unna store metallbord, dataskjermer og mobiltelefoner mens du kalibrerer.
    *   Du kan tvinge frem en ny kalibrering i Python-kode med `compass.calibrate()` eller MakeCode-blokken `kompass kalibrer`.
*   **Kompasset viser feil retning utendørs**:
    *   Det innebygde kompasset er følsomt for magnetisk støy. Sørg for at batteripakken ligger minst 10–15 cm unna selve micro:bit-en (ledningene er lange nok), da metaller og batterier i nærheten forstyrrer magnetfeltet.
    *   Hold alltid micro:bit-en helt vannrett (horisontalt) når du gjør en måling. Dersom den tiltes, vil tyngdekraftsensoren prøve å kompensere, men det kan oppstå unøyaktigheter.
