(qgis_dtm)=
# Høydedata og terrenganalyse i QGIS

Denne bruksanvisningen viser hvordan du laster ned en digital terrengmodell (DTM) fra [hoydedata.no](https://hoydedata.no) og bruker den til terrenganalyse i QGIS. Den er skrevet som støtte til oppgaven [Terrenganalyse med høydedata](/oppgaver/høydemodell.md).

En DTM er et rutenett der hver celle inneholder en høydeverdi i meter over havet. QGIS kan lese dette direkte som et rasterlag og bruke det som grunnlag for å beregne hillshade, konturlinjer, helning og høydeprofiler.

## Last ned DTM fra hoydedata.no

1. Gå til [hoydedata.no](https://hoydedata.no) og trykk **Velg område**
2. Zoom inn til NMBU campus og tegn et rektangel rundt området du vil ha data for
3. Under **Produkter**, velg ett av disse:
   - **DTM 1** – 1 meters oppløsning (detaljert, stor fil)
   - **DTM 10** – 10 meters oppløsning (raskere å jobbe med, passer godt til oversiktsanalyser)
4. Filformatet **GeoTIFF (.tif)** er standard og fungerer direkte i QGIS
5. Trykk **Last ned** og lagre filen på en plass du husker

## Last inn DTM i QGIS

1. Åpne QGIS og last inn malfila (se [Introduksjon til QGIS](/bruksanvisninger/qgis_intro.md))
2. Dra og slipp `.tif`-filen direkte inn i **Lagpanelet**
3. Laget vises som et gråtonekart — dette er høydeverdiene visualisert direkte
4. Høyreklikk på laget → **Zoom til lag** for å sentrere kartet

:::{tip}
Vil du se farger istedenfor gråtoner? Høyreklikk på laget → **Egenskaper → Symbologi** → endre *Rendertype* til **Enkeltbånd pseudofarge** og velg en fargeskala.
:::

:::{figure} ../bilder/qgis/dtm/pseudofarge.png
:name: dtm-pseudofarge
Enkeltbånd pseudofarge-rendering i lagegenskapene. Fargeskalering gjør det lettere å lese høydeforskjeller.
:::

## Hillshade (skyggerelieff)

Hillshade simulerer hvordan solen belyser terrenget og gjør det mye lettere å se åser, daler og skråninger.

1. Gå til **Behandling → Verktøykasse** (eller trykk `Ctrl+Alt+T`)
2. Søk etter **Hillshade** i søkefeltet
3. Under **Rasterterrengsanalyse → Hillshade**, dobbeltklikk for å åpne verktøyet
4. Velg din DTM som **Høydelag**
5. Juster parametrene etter ønske:
   - **Azimut** (standard 300°): retningen lyset kommer fra, regnet med klokka fra nord
   - **Vertikal vinkel** (standard 40°): hvor høyt solen står
   - **Z-faktor** (standard 1.0): øk denne (f.eks. til 2–3) for å overdrive høydeforskjellene
6. Trykk **Kjør**
7. Det nye laget vises i gråtoner — plasser det *under* andre lag i lagpanelet for best effekt

:::{figure} ../bilder/qgis/dtm/hillshade.png
:name: dtm-hillshade
Eksempel på hillshade-lag (azimut 300°, vertikal vinkel 45°). Merk tydelige åser og daler i terrenget.
:::

Du kan også aktivere hillshade-rendering direkte i lagegenskapene uten å kjøre et eget verktøy — dette er raskere for rask visualisering:

:::{figure} ../bilder/qgis/dtm/hillshade_egenskaper.png
:name: dtm-hillshade-egenskaper
Hillshade-innstillinger under **Egenskaper → Symbologi** for et rasterlag. Her kan azimut og høydevinkel justeres direkte.
:::

## Konturlinjer

Konturlinjer forbinder punkter med lik høyde og gir et klassisk topografisk kartutseende.

1. Gå til **Raster → Utdrag → Konturlinjer**
2. Velg din DTM som inndatalag
3. Sett **Avstand mellom konturlinjene** — prøv 1 m og 5 m og se hva som passer best
4. Trykk **Kjør**
5. Det nye laget er vektorlinjer som kan stiles fritt under **Egenskaper → Symbologi**

:::{tip}
Høydeverdien til hver konturlinje er lagret i kolonnen `ELEV` i attributttabellen. Du kan bruke **Etiketter** til å vise disse tallene langs linjene i kartet.
:::

:::{figure} ../bilder/qgis/dtm/konturlinjer.png
:name: dtm-konturlinjer
Konturlinjerendering i QGIS-lagegenskapene viser innstillinger for intervall og stilisering.
:::

## Helningskart (slope)

Helningskartet viser hvor bratt terrenget er i grader (0° = flatt, 90° = loddrett).

1. Gå til **Behandling → Verktøykasse** og søk etter **Helning**
2. Under **Rasterterrengsanalyse → Helning**, dobbeltklikk
3. Velg din DTM som **Høydelag**
4. Trykk **Kjør**
5. Resultatet er et rasterkart der lyse farger betyr bratt terreng
6. Åpne **Egenskaper → Symbologi** og velg **Enkeltbånd pseudofarge** med en passende fargeskala for å gjøre kartet lettere å lese

:::{figure} ../bilder/qgis/dtm/slope.png
:name: dtm-slope
Helningskart der flate områder vises i rødt og bratte skråninger i blått.
:::

## Høydeprofil

QGIS har et innebygd verktøy for å tegne en tverrprofil gjennom terrenget langs en valgfri linje.

1. Gå til **Vis → Høydeprofil** — et nytt panel åpnes nederst i vinduet
2. Trykk på **Tegn profillinje** (blyant-ikonet) og klikk deg frem i kartet. Høyreklikk for å avslutte linjen
3. Sørg for at DTM-laget ditt er synlig i lagpanelet — QGIS bruker det automatisk
4. Profilen tegnes opp i panelet med avstand langs x-aksen og høyde langs y-aksen
5. Hold musepekeren over profilen for å se nøyaktig høyde og avstand i hvert punkt

:::{figure} ../bilder/qgis/dtm/elevation_profile.png
:name: dtm-elevation-profile
Høydeprofil-panelet i QGIS viser terrengprofil langs en tegnet linje. Kurven viser høyde (y) mot avstand (x).
:::

:::{tip}
For å analysere en bestemt strekning, f.eks. fra ett hjørne av campus til et annet, kan du tegne linjen nøyaktig ved å aktivere snapping i QGIS. Bruk **Vis → Verktøylinjer → Snapping-verktøylinje** og slå på snapping til bakgrunnskartlag.
:::
