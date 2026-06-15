(qgis_intro)=
# Introduksjon til QGIS

```{image} ../bilder/qgis/forside.png
```

## Hva er QGIS?

QGIS er et gratis og åpen kildekode-program for geografiske informasjonssystemer (GIS).
Programmet er tilgjengelig for Windows, Mac og Linux, og brukes av alt fra studenter til
profesjonelle innen kartografi, planlegging og geomatikk verden over.

GIS-programvare lar deg jobbe med geografiske data som kart, satellittbilder,
GPS-punkter og høydemodeller – alt organisert i lag som kan analyseres og visualiseres
sammen. QGIS er ett av de mest brukte åpne GIS-programmene i verden, og siden det er
fri programvare kan alle bidra til utviklingen og laste det ned kostnadsfritt.

## Hva kan du gjøre med QGIS?

QGIS har fire hovedfunksjoner:

- **Kartproduksjon** – Lag profesjonelle kart med avanserte designverktøy, tilpasset
  skriving, digitalt bruk og mobil.
- **Redigering av geodata** – Digitaliser og konstruer punkter, linjer og flater.
  Programmet støtter CAD-lignende verktøy.
- **Analyse og prosessering** – Analyser data med innebygde verktøy som kan kobles
  visuelt i gjenbrukbare arbeidsflyter.
- **Datadeling** – Importer og eksporter mange ulike filformater, og koble til
  webtjenester via industristandarder som WMS og WFS.

## Brukergrensesnittet

Når du åpner QGIS for første gang, ser du et grensesnitt som ligner dette:

```{image} ../bilder/qgis/startup.png
:alt: QGIS-grensesnittet med fem hoveddeler nummerert 1–5
```

Grensesnittet er delt inn i fem hoveddeler:

1. **Menybar** – Øverst i vinduet. Gir tilgang til alle funksjoner via hierarkiske menyer
   som *Prosjekt*, *Rediger*, *Vis*, *Lag*, *Innstillinger*, *Vektor*, *Raster* og *Prosessering*.
2. **Verktøylinjer** – Rader med knapper som gir rask tilgang til de vanligste funksjonene.
   Du kan vise eller skjule verktøylinjer via menyen *Vis → Verktøylinjer*.
3. **Paneler** – Interaktive sidepaneler for lagadministrasjon, datakilder og stilsetting.
   De viktigste er *Lag*-panelet og *Utforsker*-panelet.
4. **Kartvisning** – Hoveddelen av grensesnittet. Her vises og redigeres kartene dine.
   Du kan ha flere kartvisninger åpne samtidig.
5. **Statuslinje** – Nederst i vinduet. Viser koordinater, målestokk, projeksjon og
   gir rask tilgang til søk og innstillinger.

### Menybar

Menylinja gir tilgang til alle verktøy og funksjoner i QGIS:

| Meny | Innhold |
|------|---------|
| **Prosjekt** | Åpne, lagre og skrive ut prosjekter |
| **Rediger** | Angre/gjøre om, kopiere og lime inn objekter |
| **Vis** | Navigering, zoom og tilpasning av grensesnittet |
| **Lag** | Legge til, fjerne og administrere kartlag |
| **Innstillinger** | Brukerprofiler, tastatursnarveger og programalternativer |
| **Vektor / Raster** | Analyseverktøy for vektordata og rasterdata |
| **Prosessering** | Avanserte analyseverktøy og modelldesigner |

### Verktøylinjer

Verktøylinjene gir rask tilgang til de mest brukte funksjonene uten å gå gjennom menyene.
De viktigste er:

- **Navigering** – Zoom inn/ut, panorering og hjem-knapp
- **Administrer lag** – Legg til og åpne ulike datakilder
- **Digitalisering** – Tegn og rediger geometri
- **Attributter og utvalg** – Velg og inspiser objekter
- **Måling** – Mål avstand, areal og vinkler

Du kan flytte, skjule og tilpasse verktøylinjene etter behov.

### Lagpanel og Utforskerpanel

```{image} ../bilder/qgis/forklaring.png
:alt: Detaljert oversikt over QGIS-grensesnittet på norsk
```

**Lagpanelet** viser alle kartlag som er lastet inn i prosjektet. Lagene tegnes
fra bunn og opp – det øverste laget i listen vises øverst på kartet.
Her kan du:

- Slå lag av og på med avkrysningsboksen
- Endre rekkefølgen ved å dra og slippe
- Høyreklikke for å endre egenskaper, symbologi og etiketter

**Utforskerpanelet** (tidligere kalt *Filleseren*) gir tilgang til datafiler på
datamaskinen, databaser og webtjenester uten å gå ut av QGIS.

### Kartvisning

Kartvisningen er arbeidsområdet der dataene dine vises. Her kan du:

- Navigere med musehjulet (zoom) og venstre museknapp (panorering)
- Klikke på objekter for å se attributter
- Tegne og redigere geometri i redigeringsmodus

GPS-filer og andre datafiler kan enkelt dras direkte inn i kartvisningen eller lagpanelet.

### Statuslinje

Statuslinja nederst viser:

- **Søkefelt** – Hurtigsøk etter lag, funksjoner og innstillinger (Ctrl+K)
- **Koordinater** – Musepekeren sin posisjon i kartet
- **Målestokk** – Gjeldende kartmålestokk, kan endres manuelt
- **Projeksjon** – Koordinatreferansesystemet (KRS) for prosjektet

## Laste ned og installere QGIS

- **Windows / macOS:** Last ned fra [qgis.org/download](https://qgis.org/download/)
- **Linux:** Tilgjengelig via [Flathub](https://flathub.org/apps/org.qgis.qgis) eller
  som pakke fra QGIS sitt offisielle programvarelager

Vi anbefaler å laste ned den nyeste **langtidsstøttede (LTS)** versjonen for
stabilitet i undervisningssammenheng.

## Last ned mal

Vi har laget en malfil med noen nyttige bakgrunnskart og koordinatsystemet satt til
UTM sone 32 (EPSG:25832), som er standard i Norge.
[Last ned malfila her](/filer/qgis/mal.qgz)

## Videre læring

- [QGIS Offisiell dokumentasjon](https://docs.qgis.org/3.44/en/docs/)
- [QGIS Brukergrensesnittet (offisiell manual)](https://docs.qgis.org/3.44/en/docs/user_manual/introduction/qgis_gui.html)
- [QGIS Tutorials and Tips](https://www.qgistutorials.com/en/)

I høstblokka skal dere ha LAD102 hvor dere går dypere inn i QGIS og jobber med
mer avanserte analyser og kartproduksjon.
