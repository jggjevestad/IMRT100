(qgis_wms)=
# Koble til karttjenester (WMS) i QGIS

Denne bruksanvisningen viser hvordan du kobler QGIS til en **WMS-tjeneste** (Web Map Service) for å hente inn kart direkte fra en server — uten å laste ned store filer. Den er skrevet som støtte til oppgaven [Historiske kart og arealendringer](/oppgaver/historiske_kart.md).

WMS er en internasjonal standard for å levere kartbilder over internett. Det betyr at kart fra for eksempel Kartverket kan vises direkte i QGIS, alltid oppdaterte og uten at du trenger å lagre dem lokalt.

## Åpne tilkoblingsvinduet

1. Gå til **Lag → Legg til lag → Legg til WMS/WMTS-lag**
   (eller trykk `Ctrl+L` og velg fanen **WMS/WMTS**)
2. Klikk **Ny** for å opprette en ny servertilkobling

## Koble til Kartverkets historiske kart

Kartverket tilbyr historiske kart gratis som en åpen WMS-tjeneste.

1. I dialogvinduet som åpnes, fyll inn:
   - **Navn:** `Historiske kart – Kartverket`
   - **URL:** `https://wms.geonorge.no/skwms1/wms.historiskekart`
2. La resten stå som standard og trykk **OK**
3. Tilbake i WMS-vinduet, velg tilkoblingen du nettopp opprettet og trykk **Koble til**
4. QGIS henter nå en liste over tilgjengelige lag. Du vil se:
   - **amt1** – Amtskart (historiske fylkeskart fra 1800-tallet)
   - **georefererte** – Andre georefererte historiske kart
5. Velg laget **amt1** og trykk **Legg til**

Det historiske kartet vises nå i QGIS og er plassert riktig i koordinatsystemet. Du kan zoome inn og ut akkurat som på andre lag.

## Koble til Kartverkets bakgrunnskart

For å sammenligne det historiske kartet med et moderne kart, legg til et bakgrunnskart:

1. Opprett en ny tilkobling med disse verdiene:
   - **Navn:** `Norgeskart – Kartverket`
   - **URL:** `https://opencache.statkart.no/gatekeeper/gk/gk.open_wmts?service=WMTS&request=GetCapabilities`
2. Trykk **OK**, velg tilkoblingen og trykk **Koble til**
3. Velg fanen **WMTS** øverst i vinduet (Norgeskart bruker WMTS, ikke WMS)
4. Velg laget **norgeskart** og trykk **Legg til**

:::{tip}
WMTS er en raskere variant av WMS som bruker forhåndsrenderte kartfliser. Fungerer på samme måte i QGIS, men er langt raskere å vise ved zooming og panorering.
:::

## Sammenlign historisk og moderne kart

Nå har du to lag i lagpanelet. For å sammenligne dem:

1. Plasser det historiske kartet (**amt1**) *over* bakgrunnskartet i lagpanelet
2. Bruk **Gjennomsiktighet** til å blende mellom dem:
   - Høyreklikk på det historiske kartet → **Egenskaper → Gjennomsiktighet**
   - Sett verdien til ca. 50 % og se hvordan de to kartene overlapper
3. Slå lag av og på ved å klikke på øye-ikonet i lagpanelet

## Legg til Kartverkets terrengmodell

Vil du ha et hillshade-bakgrunnskart for støtte til terrengoppgaven? Koble til:

- **Navn:** `Terrengmodell – Kartverket`
- **URL:** `https://wms.geonorge.no/skwms1/wms.terrengmodell`
- Velg laget **relieff**

## Tips: Lagre tilkoblingene

WMS-tilkoblingene dine lagres automatisk i QGIS og er tilgjengelige neste gang du åpner programmet. Du finner dem igjen under **Lag → Legg til lag → Legg til WMS/WMTS-lag**.
