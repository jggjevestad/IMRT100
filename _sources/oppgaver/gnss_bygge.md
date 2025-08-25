(gnss_bygge)=
# Bygg din egen GNSS mottaker

## GNSS
GNSS er en fellesbetegnelse for satellittbaserte navigasjonssystemer. Det finnes flere slike satellittbaserte navigasjonssystemer, men de to mest utbredte er det amerikanske GPS systemet og det russiske GLONAS. Begge disse er militære navigasjonssystemer.
Det europeiske navigasjonssystemet heter Galileo og er et sivilt navigasjonssystem. Nyere mottakere har også begynt å ta i bruk dette navigasjonssystemet.
Desto flere navigasjonssystemer en mottaker kan bruke, desto flere satellitter har man tilgang til. Dette fører som regel til en bedre og mer nøyaktig posisjonsbestemmelse.
Kort og enkelt forklart så måles avstanden mellom mottakeren og satellittene for å finne en posisjon. Man måler tiden det tar fra signalet sendes ut fra satellitten til det når mottakeren. 
Man trenger fire satellitter for å beregne sin posisjon. Dette er fordi vi har de romlige koordinatene i x, y og z-retning som ukjente, i tillegg til en klokkefeil i satellitt og mottakerklokke.

```{image} ../bilder/gps_breakout.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```
  
Mottakerene dere skal bygge logger dataene på NMEA format. Dere skal bruke dette formatet til å lese av data som er aktuelle for å løse oppgavene. Se link for full beskrivelse av formatet.

## NMEA formatet
NMEA (National Marine Electronics Association) er et standard format som brukes for datakommunikasjon mellom forskjellige GNSS-enheter. Det ble først definert av National Marine Electronics Association og er i dag det mest vanlige dataformatet som støttes av GNSS-utstyr. 

NMEA-meldinger består av såkalte "setninger" med GNSS-data som overføres fra en "talker"-enhet til en "listener"-enhet (eller flere enheter). Meldingene er generelt utgått av Rover-enheter og de fleste GNSS-mottakere støtter NMEA-utgang.

Noen av de vanligste NMEA-meldingene inkluderer¹:
- **GGA** — Global Positioning System Fixed Data
- **GLL** — Geographic Position - Latitude/Longitude
- **GSA** — GNSS DOP and Active Satellites
- **GSV** — GNSS Satellites in View
- **RMC** — Recommended Minimum Specific GNSS Data
- **VTG** — Course Over Ground and Ground Speed

Hver datafelt i en NMEA-melding starter med `$`-tegnet, og hvert felt er adskilt med et komma. For eksempel, i `$GPGGA`-meldingen representerer `GP` at det er en GPS-posisjon (GL ville betydd GLONASS).

Formålet med NMEA er å gi utstyrsbrukere muligheten til å blande og matche maskinvare og programvare. NMEA-formatterte GPS-data gjør også livet lettere for programvareutviklere å skrive programvare for et bredt utvalg av GPS-mottakere i stedet for å måtte skrive et tilpasset grensesnitt for hver GPS-mottaker.

## Arduino IDE
Arduino IDE (Integrated Development Environment) er en åpen kildekode programvare som er designet av Arduino.cc. Den brukes hovedsakelig for å skrive, kompilere og laste opp kode til forskjellige Arduino-moduler. 

Her er noen viktige funksjoner og egenskaper ved Arduino IDE:

**Kompatibilitet**: Arduino IDE er kompatibel med forskjellige operativsystemer som Windows, Mac OS X, og Linux.

**Programmeringsspråk**: Den støtter programmeringsspråkene C og C++.

**Brukervennlig**: Arduino IDE gjør koden kompilering så enkelt at selv en vanlig person uten tidligere teknisk kunnskap kan begynne med læringsprosessen.

**Skisser**: Programmer skrevet ved hjelp av Arduino Software (IDE) kalles skisser. Disse skissene er skrevet i tekstredigereren og lagres med filtypen .ino.

**Editor og Kompiler**: IDE-miljøet inneholder hovedsakelig to grunnleggende deler: Editor og Kompiler. Førstnevnte brukes for å skrive den nødvendige koden og sistnevnte brukes for å kompilere og laste opp koden til den gitte Arduino-modulen.

Arduino IDE er et viktig verktøy for alle som jobber med Arduino-prosjekter, enten det er hobbyister, studenter, lærere eller profesjonelle utviklere.

Kilder:
1. [Arduino](https://www.arduino.cc/en/software/)
1. [Using the Arduino Software (IDE)](https://docs.arduino.cc/learn/starting-guide/the-arduino-software-ide/)

## Sette sammen GNSS mottakeren
Det er flere typer slike enkle GNSS  mottakerer, så vi skal gå igjennom hvordan hver av disse kan settes sammen for at vi skal få mottakeren til å lage de dataene som vi behøver til prosjektet.

Det er viktig å teste at GNSS mottakeren fungerer som den skal ved å sende NMEA data til en seriell terminal som f.eks. Arduino Serial Monitor.

> **Merk** <br> Dere må ta med dere GNSS mottakeren utendørs dersom den ikke klarer å få kontakt med satellittene innendørs.

## Logge GNSS NMEA til SD-kort
For å slippe å ta med PC'en ut for lagre NMEA data, så kan vi isteden sende datastrømmen til et SD kort. På denne måten kan GNSS enheten bli ganske liten og kompakt. Dersom dere bygger en slik GNSS mottaker, så må den drives av et eget batteri og dere må tømme SD kortet i ettertid for å kunne se hvor dere har vært.

## Visualisere GNSS posisjoner
Som vi har sett så presenterer de fleste an de enkleste GNSS mottakerne data på NMEA format. Det er mange måter å visualisere denne informasjonen, men da må vi vanligvis transformere disse posisjonene til et annet egnet format.

### Google Earth
[NMEA->KML 1](https://mygeodata.cloud/converter/nmea-to-kml)

### QGIS
[KML->CVS](http://www.monster.com.tw/kml2csv)

### Oppgave
1. Er det situasjoner der den fungere veldig bra - eller veldig dårlig?
2. Se nøyere på innholdet i NMEA filene og de transformerte KML/CSV filene. Hvilke data fra den opprinnelige NMEA filen blir transformert til KML/CSV?

