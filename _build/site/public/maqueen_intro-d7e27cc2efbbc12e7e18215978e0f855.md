(maqueen_intro)=
# Brukerveiledning: Kom i gang med micro:Maqueen

[micro:Maqueen](https://www.dfrobot.com/product-1783.html) er en liten, programmerbar robotplattform utviklet av DFRobot for BBC micro:bit. Den er utstyrt med motorer, hjul, linjefølgingssensorer, en ultralydsensor for avstandsmåling, samt LED- og RGB-lys. I geoinformatikk bruker vi den til å simulere autonome kjøretøy, LiDAR-skanning og dead reckoning-navigasjon.

---

## 📋 Oversikt over maskinvaren

Før du begynner å programmere, bør du gjøre deg kjent med robotens viktigste komponenter:

```{image} ../bilder/coordinates.jpg
:alt: micro:Maqueen komponentoversikt
:class: bg-primary mb-1
:width: 500px
:align: center
```
*(Merk: Plassering av porter og brytere kan variere noe mellom Maqueen Lite V1 og V2).*

1.  **N20 mikromotorer**: To hjulmotorer plassert på undersiden som styrer robotens bevegelse. De kontrolleres via robotens interne I2C-grensesnitt.
2.  **Ultralydsensor (HC-SR04)**: En avstandssensor som plugges inn foran på roboten. Den fungerer ved å sende ut en høyfrekvent lydbølge og måle tiden det tar å motta ekkoet (Time-of-Flight).
3.  **Linjesensorer (infrarøde)**: To sensorer på undersiden (venstre og høyre) som måler refleksjon fra underlaget for å registrere om de kjører på en svart strek eller hvit flate.
4.  **LED-frontlys**: To røde LED-lys foran på roboten som kan skrus av og på.
5.  **Chassis RGB-lys (NeoPixel)**: Fire adresserbare RGB LED-er på undersiden av roboten som kan lyse i alle mulige farger.
6.  **Buzzer**: En innebygd høyttaler (tilkoblet port P0) som kan spille toner og melodier.
7.  **Strømbryter og batteriholder**: Plassert bak på roboten. Bruker vanligvis 3x AAA-batterier.

---

## 🔧 Slik installerer du Maqueen-utvidelsen i MakeCode

For å få tilgang til ferdige blokker som kan styre robotens motorer og lese sensorene, må du installere utvidelsen i [MakeCode](https://makecode.microbit.org/):

1.  Gå til [makecode.microbit.org](https://makecode.microbit.org/) og opprett et nytt prosjekt.
2.  Klikk på **Utvidelser** (Extensions) under tannhjulet øverst til høyre, eller nederst i blokkmenyen.
3.  Søk etter `maqueen` i søkefeltet.
4.  Klikk på pakken kalt **maqueen** (eller `maqueen-lite`). 
5.  En ny grønn blokkmeny kalt **Maqueen** vil dukke opp i listen din.

---

## 💻 Kodesnutter og API-referanse

Her er de mest sentrale blokkene og hvordan de oversettes til tekstbasert kode (JavaScript/TypeScript):

### 1. Motorstyring (Kjøre og svinge)

Du kan kontrollere hver motor uavhengig for å kjøre fremover, bakover, eller svinge på stedet. Hastigheten angis som et tall mellom `0` (stopp) og `255` (maksfart).

*   **Kjøre rett frem**:
    ```typescript
    maqueen.motorRun(maqueen.Motors.All, maqueen.Dir.CW, 100)
    ```
*   **Svinge på stedet**:
    For å svinge på stedet settes den ene motoren forover og den andre bakover.
    ```typescript
    // Sving til høyre
    maqueen.motorRun(maqueen.Motors.M1, maqueen.Dir.CW, 50)  // Venstre motor forover
    maqueen.motorRun(maqueen.Motors.M2, maqueen.Dir.CCW, 50) // Høyre motor bakover
    ```
*   **Stoppe motorene**:
    ```typescript
    maqueen.motorStop(maqueen.Motors.All)
    ```

### 2. Ultralyd avstandsmåling

Ultralydsensoren måler avstanden til hindringer foran roboten i centimeter. Måleområdet er ca. $2\text{ cm}$ til $300\text{ cm}$.

*   **Lese avstand**:
    ```typescript
    let avstand_cm = maqueen.Ultrasonic(PingUnit.Centimeters)
    ```

*   **Eksempel: Enkel hindringsunngåelse (Obstacle Avoidance)**:
    ```typescript
    basic.forever(function () {
        if (maqueen.Ultrasonic(PingUnit.Centimeters) < 15) {
            // Hvis det er et objekt nærmere enn 15 cm, sving unna
            maqueen.motorRun(maqueen.Motors.M1, maqueen.Dir.CW, 80)
            maqueen.motorRun(maqueen.Motors.M2, maqueen.Dir.CCW, 80)
            basic.pause(500)
        } else {
            // Kjøre rett frem hvis banen er klar
            maqueen.motorRun(maqueen.Motors.All, maqueen.Dir.CW, 100)
        }
    })
    ```

### 3. LED- og RGB-chassislys

Roboten har to røde frontlys (LED) og fire RGB-lys på undersiden som kan lyse opp underlaget.

*   **LED-frontlys** (skru på høyre frontlys):
    ```typescript
    maqueen.writeLED(maqueen.LED.LEDright, maqueen.LEDswitch.turnOn)
    ```
*   **Chassis RGB-lys**:
    For å sette fargen på undersiden, bruker du RGB-blokken. Du kan velge enkeltlys (indeks 0–3) eller alle:
    ```typescript
    // Sett alle chassis-lys til blått
    maqueen.writeLED(maqueen.LED.LEDright, maqueen.LEDswitch.turnOn)
    ```
    *Merk: Maqueen-biblioteket har forenklede fargevalg for undersidelysene:*
    ```typescript
    maqueen.RGBlightFFF(maqueen.RGBLight.RGBLightAll, maqueen.RGBcolors.Blue)
    ```

### 4. Linjefølging (IR-sensorer)

Linjesensorene på undersiden returnerer enten `0` (registrerer en svart strek / absorberer lys) eller `1` (registrerer hvit bakke / reflekterer lys).

*   **Lese sensorer**:
    ```typescript
    let venstre_sensor = maqueen.readPatrol(maqueen.Patrol.PatrolLeft)
    let hoyre_sensor = maqueen.readPatrol(maqueen.Patrol.PatrolRight)
    ```

*   **Eksempel: Enkel linjefølger-algoritme**:
    ```typescript
    basic.forever(function () {
        // Hvis begge sensorene ser hvit bakke, kjør rett frem
        if (maqueen.readPatrol(maqueen.Patrol.PatrolLeft) == 1 && maqueen.readPatrol(maqueen.Patrol.PatrolRight) == 1) {
            maqueen.motorRun(maqueen.Motors.All, maqueen.Dir.CW, 80)
        }
        // Hvis venstre sensor treffer svart strek, korriger til venstre
        if (maqueen.readPatrol(maqueen.Patrol.PatrolLeft) == 0) {
            maqueen.motorRun(maqueen.Motors.M1, maqueen.Dir.CW, 0)
            maqueen.motorRun(maqueen.Motors.M2, maqueen.Dir.CW, 80)
        }
        // Hvis høyre sensor treffer svart strek, korriger til høyre
        if (maqueen.readPatrol(maqueen.Patrol.PatrolRight) == 0) {
            maqueen.motorRun(maqueen.Motors.M1, maqueen.Dir.CW, 80)
            maqueen.motorRun(maqueen.Motors.M2, maqueen.Dir.CW, 0)
        }
    })
    ```

---

## 💡 Tips & feilsøking

*   **Motorene går ikke i det hele tatt**:
    *   Sjekk at den fysiske **Power**-bryteren på baksiden av Maqueen er skrudd PÅ (det skal lyse rødt på kretskortet).
    *   Sjekk at batteriene er satt inn riktig vei og har nok strøm. Roboten krever minimum $3.5\text{V}$ til $5\text{V}$ for at motorene skal rotere. Hvis spenningen faller for lavt, vil micro:biten fortsette å lyse, men motorene vil stoppe eller oppføre seg hakkete.
*   **Roboten kjører i sirkler når den skal kjøre rett frem**:
    *   Dette skyldes produksjonsavvik i elektromotorene (den ene yter litt mer enn den andre).
    *   **Løsning**: Kalibrer motorene ved å sette ned farten på den raskeste motoren i programmet ditt (f.eks. kjør venstre motor på fart `100` og høyre motor på fart `93`).
*   **Ultralydsensoren returnerer bare 0 eller helt urealistiske verdier**:
    *   Sjekk at sensoren er plugget helt inn i den 4-pinners kontakten foran på roboten, og at pinnene ikke er bøyd.
    *   Pass på at sensoren står vannrett og ikke peker ned i gulvet, da den vil få falske ekko fra underlaget.
*   **Radiokommunikasjonen svikter**:
    *   Sørg for at begge micro:bit-ene (den på roboten og den på PC-en) er programmert med nøyaktig samme **radiogruppe** (f.eks. `radio.setGroup(42)`).
    *   Dersom det er mange grupper som jobber i samme rom, kan det oppstå støy. Prøv å bytte til et annet gruppenummer dersom dere opplever datatap.
