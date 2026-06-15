(Ta GNSS opptak)=

# Ta GNSS opptak med mobilen

Alle smarttelefoner kan ta i mot GNSS signaler, men du trenger en egen app for å lagre de som en fil. Her kommer vi til å bruke [kml](https://en.wikipedia.org/wiki/Keyhole_Markup_Language) som filformat, men det finnes andre som gpx og geojson som også har god støtte i GIS programmer.


## Android – OpenTracks

[OpenTracks](https://opentracksapp.com) er en GNSS logger som har åpen kildekode. Appen krever ingen internettforbindelse og lagrer all data lokalt på telefonen.

### Konfigurere KML-eksport

For å få appen til å eksportere vanlige kml-filer må du endre noen innstillinger.

Trykk på tannhjulet øverst til høyre for å åpne innstillinger. Velg **Import og eksport**, og under **Filformat** velger du **kml**. Du bør også velge en mappe filene skal lagres i ved å trykke på **Mappe for sporeksport**.

```{image} ../bilder/opentracks/hjemskjerm.jpg
:width: 200px
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

### Ta opp spor

Gå til hjemmeskjermen og trykk på den røde knappen for å starte opptaket. Appen viser nå posisjonen din i sanntid.

```{image} ../bilder/opentracks/start.jpg
:width: 200px
```
```{image} ../bilder/opentracks/opptak.jpg
:width: 200px
```

Når du er ferdig trykker du på stopp-knappen, gir fila et fornuftig navn og overfører den til pcen.

```{image} ../bilder/opentracks/lagre.jpg
:width: 200px
```


## iOS – myTracks

[myTracks](https://www.mytracks4mac.info) er en GPS-logger for iPhone, iPad og Apple Watch. Appen kan eksportere til KML og KMZ, og synkroniserer spor via iCloud mellom Apple-enheter.

### Starte opptak

Åpne appen og trykk på **Record**-knappen (kamera-/rekord-knappen) for å komme til oppstartsskjermen. Trykk deretter på **Start Recording** for å begynne opptaket.

```{image} ../bilder/mytracks/start.jpg
:width: 200px
:class: bg-primary mb-1
```

```{image} ../bilder/mytracks/start_recording.jpg
:width: 200px
:class: bg-primary mb-1
```

Under opptaket viser cockpit-skjermen hastighet, høyde, distanse og andre målinger i sanntid. Du kan også legge inn veipunkter underveis.

```{image} ../bilder/mytracks/cockpit_after_start.jpg
:width: 200px
```

### Konfigurere opptak

Under **Recording Settings** kan du justere nøyaktighet, tidsintervall mellom punkter og automatisk bevegelsesdeteksjon.

```{image} ../bilder/mytracks/recording_settings-1.jpg
:width: 200px
```

### Eksportere som KML

Stopp opptaket og åpne sporet fra listen. Fra detaljvisningen trykker du på **eksport-ikonet** (deleknappen øverst til høyre).

```{image} ../bilder/mytracks/opened_track_export.jpg
:width: 200px
:class: bg-primary mb-1
```

I eksportdialogen aktiverer du **Use Google Format (KML)**. Som standard eksporteres spor som GPX, så dette steget er viktig. Trykk deretter på **Export** på nytt.

```{image} ../bilder/mytracks/export_dialog.jpg
:width: 200px
:class: bg-primary mb-1
```

iOS-delemenyen åpnes og du kan lagre filen i Filer-appen, sende den på e-post eller overføre den til pcen via AirDrop eller kabel.

```{image} ../bilder/mytracks/export_sheet.jpg
:width: 200px
```


## Åpne KML-filen

KML-filer kan åpnes i QGIS, Google Earth og mange andre programmer. Som regel er det bare å dra fila inn i vinduet.
