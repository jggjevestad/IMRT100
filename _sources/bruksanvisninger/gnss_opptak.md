(Ta GNSS opptak)=
# Ta GNSS opptak med mobilen
Alle smarttelefoner kan ta i mot GNSS signaler, men du trenger en egen app for å lagre de som en fil. Her kommer vi til å bruke [kml](https://en.wikipedia.org/wiki/Keyhole_Markup_Language) som filformat, men det finnes andre som gpx og geojson som også har god støtte i GIS programmer.

## Android

[OpenTracks](https://opentracksapp.com) er en gnss logger for android som har åpen kildekode.



For å få appen til å spytte ut vanlige kml filer må du endre noen innstillinger.

Trykk på tannhjulet, "Import og eksport" og så under Filformat velger du kml. Du må også velge en mappe filene skal lagres i ved å trykke på "Mappe for sporeksport"


```{image} ../bilder/opentracks/hjemskjerm.jpg
:width: 200px
:align: left'
:class: bg-primary mb-1
```


```{image} ../bilder/opentracks/innstillinger.jpg
:width: 200px
:class: bg-primary mb-1
```
```{image} ../bilder/opentracks/eksport.jpg
:width: 200px
:class: bg-primary mb-1
```

Nå kan begynne å gjøre opptak. Gå til hjemmeskjermen og trykk på den røde knappen

```{image} ../bilder/opentracks/start.jpg
:width: 200px
```
```{image} ../bilder/opentracks/opptak.jpg
:width: 200px
```

Når du er ferdig gir du fila et fornuftig navn og overføre den til pcen.

```{image} ../bilder/opentracks/lagre.jpg
:width: 200px
```

KML filer kan åpnes i qgis, google earth og mange andre programmer. Som regel er det bare å dra fila inn i vinduet.