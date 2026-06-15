(google_earth)=
# Koordinatsystemer og Google Earth

I denne oppgaven skal vi bli kjent med jordklodens koordinatsystemer ved å navigere virtuelt i Google Earth, utføre koordinat-transformasjoner og ta turen ut på campus for å lokalisere spesifikke punkter.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">Globalt (PC) & Tre lokasjoner på NMBU Campus</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">Smarttelefon med posisjonering-app</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value"><a href="https://earth.google.com">Google Earth (Web/Pro)</a>, GNSS App (f.eks. GPS Logger)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">2 - 3 timer</span>
  </div>
</div>

```{image} ../bilder/google_earth.jpg
:alt: Google Earth
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
For å angi en nøyaktig posisjon på vår tredimensjonale, ujevne jordklode bruker vi koordinatsystemer. Disse kan enten være geografiske (angitt i bredde- og lengdegrader på en sfære/ellipsoide) eller projiserte (flatklemte kartkoordinater angitt i meter, som UTM). Google Earth lar oss enkelt skifte mellom disse formatene og visualisere planeten vår i 3D.

---

## 🛠️ Forberedelser
* Installer Google Earth Pro på din PC eller gjør deg kjent med nettversjonen på [earth.google.com](https://earth.google.com).
* Sørg for at du har en GNSS/GPS-app installert på mobilen som kan vise sanntidskoordinater i bredde- og lengdegrad (grader, minutter, sekunder).

---

## 🏃‍♂️ Gjennomføring

### Del 1: Virtuell utforskning
1. Åpne Google Earth og finn innstillingene for koordinatvisning (under Verktøy -> Alternativer -> Vis lat/long i Pro, eller Innstillinger i nettversjonen).
2. Gjør deg kjent med hvordan du skifter mellom **DMS** (grader, minutter, sekunder), **DD** (desimalgrader) og **UTM** (Universal Transverse Mercator).

### Del 2: Feltarbeid på Campus
Bruk koordinatene i tabellen under til å navigere dere frem til tre hemmelige punkter på NMBU Campus ved hjelp av mobilens GNSS/GPS. Ta en gruppeselfie på hvert av de tre stedene for å dokumentere at dere har funnet dem!

---

## 📝 Rapportoppgaver

> [!IMPORTANT]
> Svar på følgende spørsmål og ta med selfiene fra campus-postene i rapporten.

### 1. Forstå koordinattyper
* Hva er egentlig geografiske koordinater, og hva er forskjellen på geografiske og projiserte koordinater?
* Vis posisjonen til et selvvalgt objekt i Google Earth med følgende fem formater:
  * **DD** (Desimalgrader / Decimal Degrees)
  * **DMS** (Grader, minutter, sekunder / Degrees, Minutes, Seconds)
  * **DDM** (Grader, desimalminutter / Degrees, Decimal Minutes)
  * **UTM** (Universal Transverse Mercator)
  * **MGRS** (Military Grid Reference System)
* Forklar kort sammenhengen mellom disse typene.

### 2. Globale Landemerker
Finn nøyaktig breddegrad og lengdegrad (i DMS-format) for følgende tre kjente steder:
* Eiffeltårnet, Frankrike
* Machu Picchu, Peru
* Kheopspyramiden, Egypt

### 3. Koordinatjakt
Hva befinner seg på disse to koordinatene? Søk dem opp i Google Earth og beskriv hva dere ser:

| Breddegrad | Lengdegrad | Hva finnes her? |
| :--- | :--- | :--- |
| $N41^\circ 53' 24.68''$ | $E12^\circ 29' 32.19''$ | *Svar her* |
| $S72^\circ 00' 41.14''$ | $E02^\circ 32' 06.09''$ | *Svar her (Tips: NMBU og Norge har tilknytning hit!)* |

### 4. Campus-sjekkpunkter
Dokumenter at dere har funnet de tre posisjonene på Campus ved å legge inn selfier og stedsnavn i tabellen:

| Breddegrad | Lengdegrad | Stedsnavn / Beskrivelse | Dokumentasjon (Selfie) |
| :--- | :--- | :--- | :--- |
| $N59^\circ 39' 59.45''$ | $E10^\circ 46' 06.64''$ | *Fyll inn* | *Legg inn bilde* |
| $N59^\circ 39' 57.26''$ | $E10^\circ 45' 52.29''$ | *Fyll inn* | *Legg inn bilde* |
| $N59^\circ 40' 02.80''$ | $E10^\circ 46' 18.47''$ | *Fyll inn* | *Legg inn bilde* |

### 5. Beregning av jordomkretsen
* Anta at jorden er en perfekt kule med en gjennomsnittlig radius på $R = 6371\text{ km}$.
* Regn ut den teoretiske avstanden fra ekvator til Nordpolen langs jordoverflaten. (Vis formel og utregning!).
* Sammenlign svaret ditt med avstanden du måler direkte i Google Earth ved hjelp av linjalverktøyet. Hvor stort er avviket?

> [!NOTE]
> **Fun fact:** I 1791 definerte den franske nasjonalforsamlingen **meteren** som nøyaktig én ti-milliondel ($1/10\ 000\ 000$) av avstanden fra ekvator til Nordpolen målt langs storsirkelen som går gjennom Paris.
