(høydemodell)=
# Terrenganalyse med høydedata

Norge er blant de landene i verden med best tilgang på åpne geodata. Kartverket tilbyr gratis høydedata over hele landet — data som forteller oss nøyaktig hvor høyt hvert eneste punkt på bakken ligger. Disse dataene brukes til alt fra flomkartlegging og skredvarsling til planlegging av veier og bygninger.

```{image} ../bilder/mountain.jpg
:alt: Terrengmodell
:class: bg-primary mb-1
:width: 600px
:align: center
```

I denne oppgaven skal dere laste ned høydedata for Ås-området og utforske terrenget rundt campus i QGIS. Høydedata lagres som et rutenett av høydeverdier, ett tall per celle, og kalles en **digital terrengmodell (DTM)**. Dette er et eksempel på **rasterdata** — en annen type geodata enn de vektorpunktene og -linjene dere har jobbet med tidligere.

## Last ned høydedata

Gå til [hoydedata.no](https://hoydedata.no) og last ned en DTM for området rundt Ås og NMBU campus.

- Velg produktet **DTM 1** (1 meters oppløsning) eller **DTM 10** (10 meters oppløsning)
- Velg et passende kartutsnitt som dekker campus og litt av omgivelsene rundt
- Last ned filen og åpne den i QGIS

## Visualiser terrenget

Når dere har lastet inn DTM-en i QGIS kan dere lage flere ulike visualiseringer:

**Hillshade (skyggerelieff):** Simulerer hvordan solen ville belyst terrenget fra en gitt retning. Gjør det lett å se høyder og daler i kartet.
- Gå til *Raster → Analyse → Hillshade*

**Høydekurver (konturlinjer):** Linjer som forbinder punkt med lik høyde over havet.
- Gå til *Raster → Utdrag → Konturlinjer*
- Prøv intervaller på 1 m og 5 m — hva passer best?

**Helningskart (slope):** Viser hvor bratt terrenget er i grader eller prosent.
- Gå til *Raster → Analyse → Helning*

## Terrengprofil

Bruk QGIS-plugin'en **Profile tool** til å tegne en linje langs en rute på campus og se høydeprofilen langs den.

- Tegn en linje fra den laveste til den høyeste delen av campus
- Hva er høydeforskjellen langs denne linjen?

## Spørsmål

1. Hva er høydeforskjellen mellom det høyeste og det laveste punktet på NMBU campus?
2. Se på helningskartet: Hvilke deler av campus er bratteste, og hva brukes disse arealene til?
3. Vannstrømning følger terrenget. Tegn inn på kartet der du tror vann vil renne ved kraftig nedbør — stemmer dette med plasseringen av bekker og dammer på campus?
4. Hva er forskjellen på DTM 1 og DTM 10? Når vil det lønne seg å bruke den ene fremfor den andre?
