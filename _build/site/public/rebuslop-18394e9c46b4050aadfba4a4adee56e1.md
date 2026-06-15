(rebuslop)=
# Rebusløp på Campus

I dette rebusløpet skal dere gjennom ti varierte oppgaver finne frem til steder på campus ved hjelp av målinger, koordinat-transformasjoner og geometrisk analyse. Ta en gruppeselfie på hvert hemmelig sted dere finner for å dokumentere gjennomføringen!

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">NMBU Campus (Start og mål TF-bygget)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">Smarttelefon, skrivesaker, kompass</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value">Google Maps, <a href="https://earth.google.com">Google Earth</a>, <a href="https://what3words.com">what3words</a>, nettleser</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">4 - 6 timer</span>
  </div>
</div>

---

## 🎯 Introduksjon
Geoinformatikk handler om å tolke, konvertere og visualisere romlige data. Gjennom dette rebusløpet skal dere bruke ulike koordinatsystemer (geografiske, projiserte, ECEF, Plus-koder og what3words) og klassisk navigasjonsteori til å løse ti oppgaver.

---

## 🏃‍♂️ Rebusløpets Oppgaver

### Oppgave 1: En slags foss på en måte
Nede på NMBU Campus, skjult blant trærne og omfavnet av naturens ro, ligger en mystisk dam. Midt i denne dammen, som glitrer i sollyset og speiler himmelens skiftende farger, finnes en liten, bortgjemt øy. På denne øyen står et sjarmerende, gammelt hus, som ser ut som det er hentet rett ut av et eventyr. Huset, med sitt krokete tak, bærer på hemmeligheter fra en svunnen tid.

Vannet i dammen er ikke krystallklart, men renner stille ut i en bekk som slynger seg gjennom landskapet. Bekken, med sitt melodiske klukk, fører vannet videre til en bitte liten foss. Denne fossen, selv om den er liten, bruser med en kraft som kanskje kan høres dersom du legger godviljen til.

```{image} ../bilder/foss.jpg
:alt: Fossen på campus
:class: bg-primary mb-1
:width: 600px
:align: center
```

* **Spørsmål**: Hva heter fossen?

---

### Oppgave 2: ECEF-Transformasjon
I geomatikk bruker vi noen ganger ECEF-koordinater (Earth-Centered, Earth-Fixed) i stedet for bredde- og lengdegrad fordi de er enklere å gjøre beregninger med i 3D. Men de er umulige å tolke uten transformasjon. Bruk en [ECEF til LLA-konverter](https://www.sysense.com/products/ecef_lla_converter/index.html) til å konvertere koordinatene nedenfor til vanlig bredde- og lengdegrad:

```{image} ../bilder/coordinates.jpg
:alt: ECEF-koordinater og jordmodell
:class: bg-primary mb-1
:width: 600px
:align: center
```

$$
\begin{align*}
  X &= 3172519.24\text{ m} \\
  Y &=  603401.31\text{ m} \\
  Z &= 5481825.82\text{ m}
\end{align*}
$$

Søk opp stedet i Google Earth og finn ut hva som er avbildet der.
* **Spørsmål**: Hvilket årstall knytter seg til monumentet på dette stedet?

---

### Oppgave 3: Den uleselige lappen
Du finner en lapp på bakken hvor noen har skrevet en posisjon med breddegrad og lengdegrad. Lappen er delvis utvasket. Sekundene i lengdegraden har forsvunnet helt. Bygningen dere skal finne ligger midt imellom ytterpunktene til de mulige posisjonene.

```{image} ../bilder/note.jpg
:alt: Lapp med koordinater
:class: bg-primary mb-1
:width: 600px
:align: center
```

$$
\begin{align*}
  N &= 59^\circ 40' 01'' \\
  E &= 10^\circ 46' xx''
\end{align*}
$$

* **Spørsmål**: Hvem eller hva holder til i dette bygget?

---

### Oppgave 4: En flat verden (UTM)
Kartkoordinater blir ofte gitt i meter (Nord og Øst) når jordkloden er projisert (flatklemmet). Det vanligste kartsystemet i Norge er EUREF89 UTM sone 32. Finn frem to følgende UTM-koordinater:

```{image} ../bilder/map_projection.jpg
:alt: Kartprojeksjoner og UTM sone
:class: bg-primary mb-1
:width: 600px
:align: center
```

$$
\begin{align*}
  N &= 6615465.09\text{ m} \\
  E &=  599443.63\text{ m}
\end{align*}
$$

Her vil dere finne et bygg med en spesiell installasjon på taket.
* **Spørsmål**: Hva heter bygget, og hva tror dere installasjonen på taket har vært brukt til?

---

### Oppgave 5: Rundt og rundt (Trilaterasjon)
Rundt om i Ås er det mange rundkjøringer. I tabellen under finner dere koordinater og radier for tre av dem. Stedet dere skal frem til er i skjæringspunktet (trilaterasjon) mellom disse tre sirklene.

```{image} ../bilder/circles.jpg
:alt: Trilaterasjon med sirkler
:class: bg-primary mb-1
:width: 600px
:align: center
```

| Rundkjøring | Breddegrad | Lengdegrad | Radius (m) |
| :--- | :--- | :--- | :--- |
| **A** | $N59^\circ 39' 53.26''$ | $E10^\circ 46' 21.48''$ | $952\text{ m}$ |
| **B** | $N59^\circ 39' 59.95''$ | $E10^\circ 48' 20.45''$ | $2730\text{ m}$ |
| **C** | $N59^\circ 39' 53.37''$ | $E10^\circ 45' 39.69''$ | $454\text{ m}$ |

* **Spørsmål**: Hva er dette objektet på campus, og hvor lang er den målt i meter?

---

### Oppgave 6: Syn som en ørn
Du står ved Gaustatoppen turisthytte ved Rjukan. Du retter blikket mot øst-nordøst. Langt borte i det fjerne ser du noe som ligner på en marmorblokk. Kompasset ditt leser av en retning (asimut) på $98.83^\circ$. Avstanden til objektet er $120\ 267\text{ meter}$.

```{image} ../bilder/mountain.jpg
:alt: Utsikt fra Gaustatoppen
:class: bg-primary mb-1
:width: 600px
:align: center
```

* **Spørsmål**: Hva heter skulpturen du ser på, og hvor er den plassert?

---

### Oppgave 7: A numbers game
Du snubler over en gammel Nokia mobiltelefon i gresset. På skjermen er det skrevet en SMS-kode, men det eneste du ser er rekkefølgen på tastetrykkene:

```{image} ../bilder/nokia.jpg
:alt: Tastaturet på en gammel Nokia
:class: bg-primary mb-1
:width: 600px
:align: center
```

`224445588223366`

* **Spørsmål**: Hva staves her (bruk gammeldags multi-tap SMS-tastatur), og hvor på campus er dette?

---

### Oppgave 8: Google Plus Codes
Google Plus Codes er en åpen adresseordning som gir unike koder til alle steder på jorden. Søk opp koden under i søkefeltet på Google Maps:

```{image} ../bilder/google_plus.jpg
:alt: Google Plus Codes kart
:class: bg-primary mb-1
:width: 600px
:align: center
```

`9FFGMQ7F+GR`

* **Spørsmål**: Hvor er dette, og hva er byggets funksjon?

---

### Oppgave 9: Tre magiske ord (what3words)
what3words har delt jorden inn i $3\times 3$ meters ruter og gitt hver rute en unik kombinasjon av tre norske ord. Slå opp ordene under på [what3words.com](https://what3words.com):

```{image} ../bilder/what3words.jpg
:alt: what3words rutenett
:class: bg-primary mb-1
:width: 600px
:align: center
```

`///kjeks.bedring.heiste`

* **Spørsmål**: Hva er dette stedet, og hvilken avdeling på NMBU holder til i nærheten?

---

### Oppgave 10: Steg for steg (Dead Reckoning)
Dead reckoning er en navigasjonsmetode der man beregner en ny posisjon ved å følge gitte kurser (asimut) og distanser fra et kjent startpunkt.
Start ved hovedinngangen til Urbygningen ($N59^\circ 39' 58.50''$, $E10^\circ 45' 57.92''$) og utfør følgende tre steg i Google Earth:

```{image} ../bilder/dead_reckoning.jpg
:alt: Dead Reckoning diagram
:class: bg-primary mb-1
:width: 600px
:align: center
```

1. Gå i retning $62^\circ$ (nordøst) i $95\text{ m}$.
2. Gå i retning $148^\circ$ (sørøst) i $70\text{ m}$.
3. Gå i retning $255^\circ$ (vest) i $55\text{ m}$.

* **Spørsmål**: Hvilket kjent bygg eller objekt står dere foran nå?

---

## 📝 Rapportoppgaver

:::{important} Viktig
Svar på de ti rebusspørsmålene over i grupperapporten din, og legg ved selfiene dere tok på postene for å dokumentere at dere har funnet stedene. Svar også på refleksjonsspørsmålene:
:::

1. **Vurdering av posisjonstyper**: Hva lærte dere om ulike måter å beskrive en geografisk posisjon på (Lat/Long, UTM, ECEF, Plus Codes og what3words)? Hvilke systemer er mest praktiske for hverdagsbruk, og hvilke passer best for beregninger?
2. **Evaluering av verktøy**: Hvilke verktøy (Google Earth, kart, kalkulatorer) brukte dere mest for å løse oppgavene, og hva fungerte best?
3. **Koordinater i hverdagen**: Hvordan har synet deres på bruk av koordinater og kartdata endret seg etter å ha løst dette rebusløpet?
