(maqueen_dead_reckoning)=
# Dead reckoning og feilanalyse med micro:Maqueen

I denne oppgaven skal vi utforske **dead reckoning** (bestikkregning), en klassisk navigasjonsmetode som brukes til å estimere nåværende posisjon basert på en tidligere kjent posisjon, retning (kurs) og hastighet over tid. Vi skal programmere micro:Maqueen til å navigere en lukket rute (polygon), kartlegge den reelle banen den kjører, beregne robotens **lukkeavvik**, og bruke geodetiske beregninger til å korrigere feilen.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">Innendørs lab eller gang med flatt gulv (f.eks. TF-bygget)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">BBC micro:bit, micro:Maqueen, USB-kabel, batterier, tape, tegne-/skrivesaker, stort papirark (eller rull), målebånd/linjal</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="https://makecode.microbit.org">MakeCode Editor</a>, Python (VS Code), QGIS</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">2 - 3 timer</span>
  </div>
</div>

```{image} ../bilder/maqueen_dead_reckoning.png
:alt: micro:Maqueen Dead Reckoning and Closing Error Diagram
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon

Før satellittnavigasjon (GPS/GNSS) ble oppfunnet, navigerte skip på havet ved hjelp av **dead reckoning** (på norsk kalt *bestikkregning*). Ved å loggføre kompasskursen og anslå farten gjennom vannet, kunne navigatøren tegne inn den estimerte posisjonen på kartet. Innen robotikk kalles denne metoden **odometri**, der man bruker hjulrotasjon og interne sensorer til å beregne hvor roboten befinner seg.

Det fundamentale problemet med dead reckoning er at **små målefeil akkumuleres over tid**. Hvis hjulene slurer litt, eller kompasset påvirkes av metall i gulvet, vil feilen vokse for hvert sekund roboten beveger seg. Dette kalles *sensor-drift*.

Når vi måler opp en lukket polygonbane i landmåling, vil vi nesten aldri ende opp nøyaktig i startpunktet når vi regner ut koordinatene. Differansen kalles **lukkeavvik** ($f_L$). For å rette opp denne feilen bruker landmålere matematiske metoder for å fordele feilen utover målingene. En av de mest kjente metodene er **kompassregelen** (Bowditch-metoden), som fordeler feilen proporsjonalt med lengden på hver delstrekning.

---

## 🛠️ Forberedelser

1.  Finn et stort, flatt gulvareal. Legg ut et stort papirark (f.eks. fra en papirrull) og fest det med tape til gulvet.
2.  Fest en tynn tusj eller penn til roboten (f.eks. tapet fast i senter bak eller foran) slik at den tegner en linje på papiret mens den kjører. Alternativt kan dere sette små tapebiter på papiret der roboten svinger.
3.  **Motorkalibrering (viktig!)**:
    *   Siden to elektromotorer aldri er 100 % identiske, vil Maqueen ofte svinge litt til siden selv om begge motorene er programmert til samme hastighet.
    *   Skriv et lite testprogram i MakeCode der roboten kjører rett frem. Juster motorstyrken på den raskeste motoren ned (f.eks. Venstre motor = 40, Høyre motor = 38) til roboten kjører helt rett over en distanse på 2 meter. Noter disse verdiene.

---

## 🏃‍♂️ Gjennomføring

### Del 1: Programmering av polygonbanen

Dere skal programmere roboten til å kjøre en lukket kvadratisk rute på $1.0\text{ m} \times 1.0\text{ m}$.

1.  Opprett et nytt prosjekt i MakeCode kalt `Maqueen_DeadReckoning`.
2.  Finn ut hvor lenge roboten må kjøre for å tilbakelegge nøyaktig $1.0\text{ meter}$ ved den kalibrerte hastigheten. (Bruk en stoppeklokke og målebånd for å kalibrere, f.eks. "fart 40 i 3.2 sekunder gir 1.0 meter").
3.  Programmer svingene: Roboten skal svinge nøyaktig $90.0^\circ$ til høyre i hvert hjørne. Dere kan velge mellom to metoder:
    *   **Tidsstyrt sving**: Sving ved å rotere hjulene i motsatt retning i et bestemt antall millisekunder (f.eks. `motor venstre fart 30, motor høyre fart -30` i `820` ms). Kalibrer dette nøye slik at svingen blir så nær $90^\circ$ som mulig.
    *   **Kompassstyrt sving**: Les av kompasset og roter til retningen har endret seg med $90^\circ$.
4.  Lag en løkke som kjører følgende sekvens 4 ganger (slik at roboten beskriver et kvadrat):
    1. Kjør rett frem i 1.0 meter.
    2. Stopp motorene helt i 1 sekund.
    3. Sving $90^\circ$ til høyre.
    4. Stopp motorene helt i 1 sekund.
5.  Last ned programmet til roboten.

### Del 2: Datainnsamling i felt

1.  Plasser roboten på papiret og sett et merke nøyaktig der pennen starter. Dette defineres som startpunktet $(E=0.0\text{ m}, N=0.0\text{ m})$.
2.  Start roboten. La den fullføre ruten.
3.  Når roboten har stoppet etter den fjerde svingen og siste rette strekning, sett et tydelig merke der pennen stopper (sluttpunktet).
4.  Marker også de tre andre hjørnene (svingepunktene) på arket.
5.  Bruk målebåndet til å måle:
    *   Den faktiske lengden på hver av de fire sidene i kvadratet ($d_1, d_2, d_3, d_4$) i centimeter.
    *   Koordinatene til hjørnepunktene og sluttpunktet i et lokalt koordinatsystem på papiret. *Tips: Bruk startpunktet som origo (0,0), og la den første linjen dere kjørte ligge langs N-aksen (eller E-aksen) for å forenkle målingen.*
    *   Avstanden fra startpunktet til sluttpunktet (lukkeavviket $f_L$).

---

## 📝 Rapportoppgaver

:::{important} Viktig
Svar på spørsmålene under i grupperapporten. Vis utregningene deres og legg ved grafer/kartfigurer.
:::

### Spørsmål

1.  **Programkode**:
    *   Legg ved skjermbilde av MakeCode-koden dere programmerte for å kjøre ruten. Angi hvilke tids- eller kompassverdier dere endte opp med etter kalibreringen.
2.  **Beregning av lukkeavvik**:
    *   Hva ble det fysisk målte lukkeavviket $f_L$ i centimeter?
    *   Regn ut total kjørelengde $L = d_1 + d_2 + d_3 + d_4$.
    *   Beregn det **relative lukkeavviket**:
        $$f_{rel} = \frac{f_L}{L}$$
    *   Vurder resultatet: I profesjonell eiendomsoppmåling kreves det ofte et relativt lukkeavvik på bedre enn $1:1000$ (0.1 %). Hva ble deres robots relative avvik (f.eks. $1:20$ eller $1:50$)? Diskuter om dette er som forventet for en slik robotplattform.
3.  **Koordinatkorreksjon (Bowditch-utjevning) med Python**:
    *   Bruk Python-skriptet under til å beregne de teoretiske, de faktiske (målte) og de korrigerte koordinatene ved hjelp av kompassregelen (Bowditch).
    *   Tilpass verdiene i skriptet til deres egne målinger.
    *   Forklar kort hvordan kompassregelen fordeler feilen utover punktene. Hvorfor får det siste punktet den største korreksjonen?

```python
import numpy as np

# 1. Tast inn dine fysiske målinger av de 4 hjørnene (Easting, Northing)
# Startpunkt er (0, 0). Det siste punktet (indeks 4) er der roboten faktisk stoppet.
maalte_punkter = np.array([
    [0.0, 0.0],      # Startpunkt (0, 0)
    [0.05, 0.98],    # Hjørne 1 (ca. 1m frem)
    [1.02, 1.01],    # Hjørne 2 (ca. 1m høyre)
    [0.97, -0.03],   # Hjørne 3 (ca. 1m tilbake)
    [-0.08, -0.06]   # Sluttpunkt (der roboten stoppet etter 4. strekning)
])

# Teoretiske koordinater for et perfekt kvadrat på 1.0 x 1.0 m
teoretiske_punkter = np.array([
    [0.0, 0.0],
    [0.0, 1.0],
    [1.0, 1.0],
    [1.0, 0.0],
    [0.0, 0.0]
])

# 2. Beregn lukkeavviket (differansen mellom start og reell stopp)
delta_e = maalte_punkter[-1, 0] - maalte_punkter[0, 0]
delta_n = maalte_punkter[-1, 1] - maalte_punkter[0, 1]
f_L = np.sqrt(delta_e**2 + delta_n**2)

print(f"Lukkeavvik i Øst (dE): {delta_e:.3f} m")
print(f"Lukkeavvik i Nord (dN): {delta_n:.3f} m")
print(f"Absolutt lukkeavvik (f_L): {f_L:.3f} m ({f_L*100:.1f} cm)")

# 3. Beregn sidelengder for å fordele feilen proporsjonalt
distanser = []
for i in range(1, len(maalte_punkter)):
    d = np.sqrt((maalte_punkter[i, 0] - maalte_punkter[i-1, 0])**2 + 
                (maalte_punkter[i, 1] - maalte_punkter[i-1, 1])**2)
    distanser.append(d)

total_lengde = sum(distanser)
kumulativ_lengde = np.cumsum(distanser)

# 4. Utfør kompassregelen (Bowditch-korreksjon)
korrigerte_punkter = np.zeros_like(maalte_punkter)
korrigerte_punkter[0] = maalte_punkter[0]  # Startpunktet er fast (0,0)

for i in range(1, len(maalte_punkter)):
    # Korreksjonen øker lineært med tilbakelagt distanse
    c_e = - delta_e * (kumulativ_lengde[i-1] / total_lengde)
    c_n = - delta_n * (kumulativ_lengde[i-1] / total_lengde)
    
    korrigerte_punkter[i, 0] = maalte_punkter[i, 0] + c_e
    korrigerte_punkter[i, 1] = maalte_punkter[i, 1] + c_n

print("\n=== Beregnede koordinater (E, N) ===")
print("Punkt | Teoretisk       | Målt (Reell)     | Korrigert (Utjevnet)")
for i in range(len(maalte_punkter)):
    print(f"  {i}   | ({teoretiske_punkter[i,0]:.2f}, {teoretiske_punkter[i,1]:.2f})   "
          f"| ({maalte_punkter[i,0]:.2f}, {maalte_punkter[i,1]:.2f})   "
          f"| ({korrigerte_punkter[i,0]:.2f}, {korrigerte_punkter[i,1]:.2f})")
```

4.  **Visualisering i QGIS**:
    *   Lagre de tre koordinatsettene (Teoretisk, Målt, Korrigert) fra Python-kjøringen i en CSV-fil.
    *   Importer CSV-filen i QGIS. Tegn opp banene som tre separate linjer/polygoner med ulike farger (f.eks. grønn for teoretisk, rød for målt, og blå for korrigert).
    *   Legg ved et skjermbilde av kartvisningen i QGIS og kommenter hvordan korreksjonen endret formen på ruten slik at den lukkes perfekt i origo.
5.  **Feilanalyse og diskusjon**:
    *   Hva slags feil i dette eksperimentet regnes som *systematiske feil*, og hva regnes som *tilfeldige feil*? Gi eksempler på begge.
    *   Hvordan ville resultatene endret seg dersom dere svingte ved hjelp av tidsstyring kontra kompassstyring? Hva er fordeler og ulemper med hver av metodene i et innendørs kontormiljø?
