(gjennomsnitt_koordinater)=
# Beregne gjennomsnittet av koordinater

## Beregne gjennomsnittet av koordinater i QGIS

I QGIS er det et innebygd verktøy for å ta gjennomsnittet av en liste med koordinater. Dette funker med de fleste format som KML, GPX og CSV.

Først må man laste inn fila med den statiske målingen:

```{figure} ../bilder/qgis/gjennomsnitt/lag.png
```
For å få opp Prossesering - verktøykasse på høyre side må den aktiveres i Prosseseringsmenyen
```{figure} ../bilder/qgis/gjennomsnitt/meny.png
```

I verktøykassa velger dere _Gjennomsnittskoordinat(er)_. Det er et søkefelt på toppen for å finne frem.
```{figure} ../bilder/qgis/gjennomsnitt/verktoy.png
```

I vinduet som dukker opp kan dere la alt stå og trykke Kjør. Hvis dere vil kan dere lagre punktet som en fil ved å trykke på `...` knappen under Gjennomsnittskoordinater
```{figure} ../bilder/qgis/gjennomsnitt/vindu.png
```

Nå skal punktet ha dukket opp i QGIS.

For å se koordinatene kan dere velge _Identifiser objekter_  verktøyet og trykke på punktet i kartet:
```{figure} ../bilder/qgis/gjennomsnitt/identifiser.png
```

X og Y er koordinatene i prosjektets koordinatsystem (UTM32), mens MEAN_X og MEAN_Y er koordinatene fra fila, som regel geografiske koordinater.

```{figure} ../bilder/qgis/gjennomsnitt/koordinater.png
```
