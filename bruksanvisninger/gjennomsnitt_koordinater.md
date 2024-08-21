(gjennomsnitt_koordinater)=
## Ta gjennomsnittet av koordinater i en kml fil

Her er en måte å ta gjennomsnittet av koordinater i excel, uten å bruke python. Python gjør jobben mye enklere, så bruk det om dere får det til. Da er det fortsatt lurt å starte med en csv fil som forklares i punkt en.

## 1.  Konvertering fra KML til CSV (Lengde og breddegrader)

- Benytt følgende nettside for å konvertere KML-filen til en CSV fil: [**https://anyconv.com/kml-to-csv-converter/**](https://anyconv.com/kml-to-csv-converter/)

- Åpne CSV filen i Excel. Det kan være litt utfordrende å åpne en CSV fil riktig i Excel dersom dere ikke har gjort dette før. Prøv dere frem litt, og så kan dere spørre om hjelp dersom dere ikke forstår hvorfor det ikke fungerer som dere forventet.

- Resultatfilen inneholder lengde- og breddegrader **kun** i de første 2 kolonene.

- I Excel, fjern de andre kolonene fra filen og lagre filen på nytt som en CSV fil.

## 2.  Konvertering fra CSV (Lengde og breddegrader) til CSV (UTM)

- Benytt følgende nettside for konvertering til UTM: [**http://www.zonums.com/online/coords/cotrans.php?module=13**](http://www.zonums.com/online/coords/cotrans.php?module=13)

- Trykk på Upload file. Velg csv filen med lengde og breddegrader og
  trykk Accept

- Bruk innstillingene som vist i bildet under, men pass på at Lat Lon
  rekkefølgen er riktig i csv filen. Det vil si hvis lengdegrader er
  første kolonne så skal dere bruke Lon Lat i «columns», eller blir det
  Lat Lon.

- Trykk Transform

- Copy paste resultatdataen inn i en teksteditor som Notepad++

- Lagre filen med extension .csv

- Åpne denne filen i Excel

- Beregn gjennomsnittet av alle Nord og Øst koordinater. Dette blir da
  deres beste estimat for det korrekte koordinatet

- Beregn standardavvik av alle Nord og Øst koordinater. Dette blir da
  deres beste estimat på nøyaktigheten av koordinatet deres.