(gis)=

# GIS

GIS står for Geografisk informasjonssystem og er egentlig bare litt avanserte kartprogram til PCen.

De fleste dataprogram som brukes i geomatikk kan egentlig kalles GIS, men ofte tenker man på program som Qgis hvor man jobber med forskjellige lag med data som kan analysereres sammen.

Selv om de fleste ikke ville kalt Google Earth et GIS oppfyller det egentlig definsjonen og er et nyttig verktøy. Første del av oppgava er å bli kjent med Google Earth og i andre del skal dere digitalisere kartet dere tegna i QGIS.

## Introduksjon til Google Earth

Google Earth er et kraftig verktøy som gir brukere muligheten til å utforske vår planet i detaljert 3D-grafikk. Her er noen av de grunnleggende funksjonene som kan være nyttige for geomatikkstudenter:

**Utforskning av jorden**: Du kan zoome inn og ut, rotere og panorere for å se forskjellige deler av verden. Du kan også bruke søkefeltet til å finne spesifikke steder.

**Satellittbilder**: Google Earth gir deg tilgang til høyoppløselige satellittbilder fra hele verden. Disse bildene kan være svært nyttige for å studere geografiske trekk.

**3D-bygninger og terreng**: I mange byer kan du se 3D-modeller av bygninger. Du kan også se terrengdetaljer som fjell og daler i 3D.

**Måleverktøy**: Du kan bruke måleverktøyene til å måle avstander og arealer på jorden. Dette kan være nyttig for å beregne avstanden mellom to punkter eller arealet av en bestemt region.

**Lag**: Google Earth har mange forskjellige lag du kan slå på og av. Disse inkluderer ting som veier, stedsnavn, grenser, bilder, bygninger og mer.

**Historiske bilder**: For noen områder kan du se historiske satellittbilder. Dette kan være nyttig for å studere endringer i landskapet over tid.

**Street View**: I mange områder kan du se bilder tatt på gateplan. Dette kan gi deg en følelse av hvordan det er å være på det aktuelle stedet.

**KML og KMZ filer**: Du kan importere og eksportere geografiske data ved hjelp av KML (Keyhole Markup Language) og KMZ (en komprimert versjon av KML) filer. Dette er nyttig for å dele kart og geografisk informasjon.

```{image} ../bilder/google_earth.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```


### Oppgaver
1. Hva er egentlig koordinater?
   - Hvilke koordinattyper kan Google Earth vise?
   - Velg et objekt i Google Earth og vis posisjonen til objektet med alle de ulike koordinattypene i Google Earth.
   - Klarer du å finne ut sammenhengen mellom noen av disse koordinattypene: "DD", "DMS", "DDM", "UTM" og "MGRS"?


2. Hvilken breddegrad og lengdegrad har disse landemerkene?
   - Eiffeltårnet, Frankrike
   - Machu Picchu, Peru
   - Kheopspyramiden, Egypt


3. Hva finner du i disse to posisjonene?

|Breddegrad|Lengdegrad|
|---|---|
| $N41^0 53' 24.68''$ | $E12^0 29' 32.19''$ |
| $S72^0 00' 41.14''$ | $E02^0 32' 06.09''$ |


4. Bruk GNSS mottakeren i mobiltelefonen din til å finne fram til disse tre posisjonene rundt på Campus. Ta en selfie med gruppen på stedet for å dokumentere hvor det er.

|Breddegrad|Lengdegrad|
|---|---|
|$N59^0 39' 59.45''$|$E10^0 46' 06.64''$|
|$N59^0 39' 57.26''$|$E10^0 45' 52.29''$|
|$N59^0 40' 02.80''$|$E10^0 46' 18.47''$|


5. Hva er avstanden fra ekvator til Nordpolen?

Anta et jorden er en kule med radius på 6371 km og forsøk å regne ut avstanden selv. Sammenlign ditt svar med den målte avstanden i Google Earth.


> **Fun fact** <br> Meteren ble opprinnelig definert i 1791 av den franske nasjonalforsamlingen som en ti milliondel av avstanden fra ekvator til Nordpolen langs en storsirkel. Med andre ord, det ble definert som en ti milliondel av kvadranten av jordens omkrets, målt langs en meridian gjennom Paris.

## Digitalisere kartskissa i QGIS

Nå sitter dere forhåpentligvis med et nydelig kartutsnitt av campus, men kommunen vil slettes ikke ha noe papirkart. De krever at dere digitaliserer og  georeferer det slik at det kan rett inn i kommunens kartsystem!

Å georefere kartet vill si å plassere kartet i et koordinatsystem. Det gjør man ved å finne koordinatene til  fire velldefinerte punkert som f.eks. husjørner. Deretter tastes dette inn i qgis som ved hjelp av matemattikk klarer å vri og strekke kartet til å passe med jordmodellen.

Før dere starter må dere [laste ned og sette opp qgis](/bruksanvisninger/qgis_intro.html). Dere må også ha scannet inn kartet og fått lagra det som en bildefil på pcen.

*Trygve skriver en steg for steg forklaring ✏️*