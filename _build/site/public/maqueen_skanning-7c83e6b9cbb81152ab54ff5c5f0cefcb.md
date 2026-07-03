(maqueen_skanning)=
# Autonom 2D-kartlegging og polarmåling med micro:Maqueen

I denne oppgaven skal vi lære hvordan robotplattformen micro:Maqueen kan brukes som en autonom laserskanner (LiDAR) eller robot-totalstasjon. Vi skal programmere roboten til å rotere på et fastpunkt, måle vinkel (kompasskurs) og avstand til omgivelsene med ultralydsensoren, sende dataene trådløst via radio, og bruke Python og QGIS til å rekonstruere og kartlegge rommet.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">Innendørs lab eller klasserom (f.eks. TF3-103)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">2x BBC micro:bit, micro:Maqueen (med ultralydsensor HC-SR04), USB-kabel, batterier, kartongesker/hindringer</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="https://makecode.microbit.org">MakeCode Editor</a>, Python (VS Code), QGIS</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">3 - 4 timer</span>
  </div>
</div>

```{image} ../bilder/maqueen_scan.png
:alt: micro:Maqueen 2D LiDAR Scanning Diagram
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon

Moderne kartlegging og 3D-modellering baserer seg i stor grad på **LiDAR** (Light Detection and Ranging) og **laserskanning**. Både flybåren laserskanning, mobile kartleggingssystemer og stasjonære bakkeskannere (TLS) fungerer etter samme prinsipp: De sender ut signaler, måler avstanden til et objekt, og registrerer nøyaktig hvilken retning (vinkel) målingen ble gjort i.

Dette kalles **polarmåling** (radial surveying). Hvis vi kjenner koordinatene til instrumentets stasjonspunkt $(E_0, N_0)$ og retningen instrumentet peker i (retningsvinkelen eller asimuten $\theta$), kan vi beregne koordinatene til treffpunktet $(E, N)$ ved hjelp av trigonometri:

$$E = E_0 + d \cdot \sin(\theta)$$
$$N = N_0 + d \cdot \cos(\theta)$$

Hvor:
*   $(E_0, N_0)$ er koordinatene til robotens oppstillingspunkt (stasjonspunktet).
*   $d$ er avstanden målt med sensoren (i meter).
*   $\theta$ er retningsvinkelen målt med klokken fra geografisk nord (asimut).

I denne oppgaven skal vi bygge vår egen forenklede 2D-laserskanner ved å montere en ultralydsensor på en Maqueen-robot. Roboten roterer rundt sin egen akse mens den fortløpende lagrer vinkel og målt avstand.

---

## 🛠️ Forberedelser

1.  Monter ultralydsensoren (HC-SR04) foran på micro:Maqueen-roboten.
2.  Sett inn en micro:bit i roboten (dette blir **senderen / robot-enheten**).
3.  Koble den andre micro:biten til din PC med USB-kabel (dette blir **mottakeren**).
4.  Åpne [MakeCode Editor](https://makecode.microbit.org/).
5.  For å styre roboten, må du legge til Maqueen-biblioteket i MakeCode:
    *   Klikk på **Utvidelser** (Extensions) under tannhjulet eller i menyen.
    *   Søk etter `maqueen` og installer pakken **maqueen** (av DFRobot).

---

## 🏃‍♂️ Gjennomføring

### Del 1: Programmering av roboten (Senderen)

Du skal programmere roboten til å rotere sakte og sende kompasskursen og avstanden via radio.

1.  Opprett et nytt prosjekt i MakeCode kalt `Maqueen_Sender`.
2.  I `ved start`-blokken:
    *   Sett radiogruppe til et unikt tall (f.eks. gruppenummeret deres) slik at dere ikke forstyrrer andre grupper: `radio sett gruppe [X]`.
    *   Sett radiosignalstyrke til maks (f.eks. `7`).
    *   Kalibrer kompasset (valgfritt, men anbefales for retningsnøyaktighet): Bruk `kalibrer kompass` (ligger under Mer-kategorien under Input).
3.  I en `når knapp A trykkes`-blokk (eller i en løkke):
    *   Start robotens motorer i motsatt retning med lav hastighet for å rotere roboten på stedet: `motor [venstre] roter [forover] fart [30]` og `motor [høyre] roter [bakover] fart [30]`.
    *   Kjør en løkke som gjentas eller går kontinuerlig:
        *   Les avstand fra ultralydsensoren i cm: `les ultralyd avstand (cm)`.
        *   Les av kompassretningen: `kompassretning (°)`.
        *   Konverter avstanden fra centimeter til meter: $d = \text{avstand} / 100$.
        *   Send disse to verdiene over radio som en kommaseparert tekststreng (f.eks. `vinkel,avstand`), eller send dem som to tall etter hverandre med en kort pause imellom.
        *   *Eksempel på tekststreng*: `radio send streng [ join (kompassretning) (join (",") (avstand_meter)) ]`.
        *   Legg inn en kort pause på `100` ms for hver måling.
4.  Last ned koden til micro:biten som står i roboten.

### Del 2: Programmering av mottakeren

Mottakeren skal ta imot dataene over radio og videresende dem til PC-en via USB (serielinjen).

1.  Opprett et nytt prosjekt i MakeCode kalt `Maqueen_Mottaker`.
2.  I `ved start`-blokken:
    *   Sett radiogruppe til det samme tallet `[X]` som senderen.
3.  I `når radio mottar streng (receivedString)`-blokken:
    *   Skriv strengen direkte ut til serielinjen: `serielinje skriv streng [receivedString]`.
4.  Last ned koden til mottaker-micro:biten (den som er koblet til PC-en med USB).
5.  Åpne **Show Console Device**-knappen i MakeCode eller bruk en seriell monitor (f.eks. i VS Code eller Mu Editor) for å sjekke at du mottar data på formatet `vinkel,avstand` når roboten roterer.

### Del 3: Datainnsamling i felt

1.  Søk ut et område på laben eller i klasserommet der det er vegger og noen esker/hindringer i en avstand på mellom 0.2 og 2.5 meter.
2.  Plasser en markør på gulvet. Dette er stasjonspunktet vårt. Vi definerer at dette punktet har de lokale koordinatene:
    *   $E_0 = 100.00\text{ m}$ (Øst)
    *   $N_0 = 100.00\text{ m}$ (Nord)
3.  Kalibrer robotens kompass ved å følge instruksjonene på LED-skjermen (vippe micro:biten til alle lysene tennes).
4.  Plasser roboten nøyaktig over stasjonspunktet, vendt mot Nord ($0^\circ$).
5.  Start loggføringen på PC-en og trykk på knapp **A** for å sette i gang skanningen.
6.  La roboten fullføre minst én hel omdreining ($360^\circ$).
7.  Kopier de loggede dataene fra den serielle monitoren og lagre dem som en tekstfil kalt `skanning.csv` med følgende innhold (sørg for at den første linjen er kolonnenavn):

```csv
vinkel,avstand
12,1.24
25,1.28
41,1.52
...
```

---

## 📝 Rapportoppgaver

:::{important} Viktig
Besvar spørsmålene under i grupperapporten. Vis all kode, forklar formler og legg ved kartfigurer fra QGIS.
:::

### Spørsmål

1.  **Programkode**:
    *   Legg ved skjermbilder av MakeCode-blokkene (eller Python-koden) dere har laget for både senderen og mottakeren.
2.  **Koordinatberegning i Python**:
    *   Bruk Python til å beregne de kartesiske koordinatene $(E, N)$ for alle målepunktene. Kopier kildemalen under og tilpass den til din CSV-fil.
    *   Legg ved koden i rapporten og forklar kort hvorfor vi må konvertere vinklene fra grader til radianer i Python før vi bruker trigometriske funksjoner (`math.sin` / `math.cos`).

```python
import csv
import math

# Konfigurasjon
stasjon_east = 100.0  # E0
stasjon_north = 100.0 # N0
innfil = 'skanning.csv'
utfil = 'skannede_punkter.csv'

with open(innfil, 'r') as f_inn, open(utfil, 'w', newline='') as f_ut:
    leser = csv.reader(f_inn)
    skriver = csv.writer(f_ut)
    
    # Skriv header til utfil
    header = next(leser)
    skriver.writerow(['Easting', 'Northing', 'Vinkel', 'Avstand'])
    
    for rad in leser:
        try:
            vinkel_deg = float(rad[0])
            avstand = float(rad[1])
            
            # TODO: Konverter vinkel fra grader til radianer
            vinkel_rad = math.radians(vinkel_deg)
            
            # TODO: Beregn koordinatene (polarmåling-formel)
            east = stasjon_east + avstand * math.sin(vinkel_rad)
            nord = stasjon_north + avstand * math.cos(vinkel_rad)
            
            # Skriv rad til ny fil
            skriver.writerow([f"{east:.3f}", f"{nord:.3f}", vinkel_deg, avstand])
        except (ValueError, IndexError):
            continue

print(f"Beregning ferdig. Koordinater lagret til {utfil}")
```

3.  **Visualisering i QGIS**:
    *   Importer den beregnede filen `skannede_punkter.csv` inn i QGIS som et **Delimited Text**-lag (bruk `Easting` og `Northing` som X- og Y-felt). *Husk å sette koordinatsystemet til et lokalt prosjektert koordinatsystem eller la det være uten CRS siden det er lokale koordinater*.
    *   Bruk digitaliseringsverktøyene i QGIS til å tegne linjer/polygoner mellom punktene for å rekonstruere veggene i rommet.
    *   Ta et skjermbilde av QGIS-kartet som viser punktskyen og de digitaliserte veggene, og legg det ved i rapporten.
4.  **Feilkilder**:
    *   Hvor godt stemmer den rekonstruerte modellen overens med det faktiske rommet (bruk målebånd for å kontrollere avstander til et par vegger)?
    *   Diskuter hvilke feilkilder som påvirker målingene. Tenk spesielt på:
        *   Hvor nøyaktig er magnetometeret (kompasset) på micro:bit inne i et betongbygg med armeringsjern og elektriske motorer?
        *   Hvordan påvirker robothjulenes sluring eller ujevn rotasjonshastighet målingene hvis vi kun baserer oss på kompasset?
        *   Hvilke begrensninger har ultralydsensoren når det gjelder spredningsvinkel og refleksjon på skrå flater?
