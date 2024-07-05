(gnss_bygge)=
# Bygg din egen GNSS mottaker

## GNSS
GNSS er en fellesbetegnelse for satellittbaserte navigasjonssystemer. Det finnes flere slike satellittbaserte navigasjonssystemer, men de to mest utbredte er det amerikanske GPS systemet og det russiske GLONAS. Begge disse er militære navigasjonssystemer.
Det europeiske navigasjonssystemet heter Galileo og er et sivilt navigasjonssystem. Nyere mottakere har også begynt å ta i bruk dette navigasjonssystemet.
Desto flere navigasjonssystemer en mottaker kan bruke, desto flere satellitter har man tilgang til. Dette fører som regel til en bedre og mer nøyaktig posisjonsbestemmelse.
Kort og enkelt forklart så måles avstanden mellom mottakeren og satellittene for å finne en posisjon. Man måler tiden det tar fra signalet sendes ut fra satellitten til det når mottakeren. 
Man trenger fire satellitter for å beregne sin posisjon. Dette er fordi vi har de romlige koordinatene i x, y og z-retning som ukjente, i tillegg til en klokkefeil i satellitt og mottakerklokke.
  
Mottakerene dere skal bygge logger dataene på NMEA format. Dere skal bruke dette formatet til å lese av data som er aktuelle for å løse oppgavene. Se link for full beskrivelse av formatet.


## NMEA formatet
NMEA (National Marine Electronics Association) er et standard format som brukes for datakommunikasjon mellom forskjellige GNSS-enheter⁵. Det ble først definert av National Marine Electronics Association og er i dag det mest vanlige dataformatet som støttes av GNSS-utstyr³. 

NMEA-meldinger består av såkalte "setninger" med GNSS-data som overføres fra en "talker"-enhet til en "listener"-enhet (eller flere enheter)³. Meldingene er generelt utgått av Rover-enheter og de fleste GNSS-mottakere støtter NMEA-utgang⁴.

Noen av de vanligste NMEA-meldingene inkluderer¹:
- **GGA** — Global Positioning System Fixed Data
- **GLL** — Geographic Position - Latitude/Longitude
- **GSA** — GNSS DOP and Active Satellites
- **GSV** — GNSS Satellites in View
- **RMC** — Recommended Minimum Specific GNSS Data
- **VTG** — Course Over Ground and Ground Speed

Hver datafelt i en NMEA-melding starter med `$`-tegnet, og hvert felt er adskilt med et komma. For eksempel, i `$GPGGA`-meldingen representerer `GP` at det er en GPS-posisjon (GL ville betydd GLONASS).

Formålet med NMEA er å gi utstyrsbrukere muligheten til å blande og matche maskinvare og programvare. NMEA-formatterte GPS-data gjør også livet lettere for programvareutviklere å skrive programvare for et bredt utvalg av GPS-mottakere i stedet for å måtte skrive et tilpasset grensesnitt for hver GPS-mottaker.

Kilder:
1. Differences and Applications of RINEX, RTCM, and NMEA. https://www.tersus-gnss.com/tech_blog/Differences-and-Applications-of-RINEX-RTCM-and-NMEA.
2. What Is NMEA and How to Feed Data from Reach to a Third-party ... - Emlid. https://blog.emlid.com/what-is-nmea-and-how-to-feed-data-from-reach-to-a-third-party-device/.
3. GNSS Software and Data Formats - unoosa.org. https://www.unoosa.org/documents/pdf/icg/2024/Tokyo2024/B04_GNSS_Software_and_Data_Formats_Avinab.pdf.
4. NMEA Reference Manual - SparkFun Electronics. https://www.sparkfun.com/datasheets/GPS/NMEA%20Reference%20Manual-Rev2.1-Dec07.pdf.
5. What Exactly Is GPS NMEA Data? - GPS World. https://www.gpsworld.com/what-exactly-is-gps-nmea-data/.


## Arduino IDE
Arduino IDE (Integrated Development Environment) er en åpen kildekode programvare som er designet av Arduino.cc. Den brukes hovedsakelig for å skrive, kompilere og laste opp kode til forskjellige Arduino-moduler. 

Her er noen viktige funksjoner og egenskaper ved Arduino IDE:

- **Kompatibilitet**: Arduino IDE er kompatibel med forskjellige operativsystemer som Windows, Mac OS X, og Linux¹³.
- **Programmeringsspråk**: Den støtter programmeringsspråkene C og C++.
- **Brukervennlig**: Arduino IDE gjør koden kompilering så enkelt at selv en vanlig person uten tidligere teknisk kunnskap kan begynne med læringsprosessen.
- **Skisser**: Programmer skrevet ved hjelp av Arduino Software (IDE) kalles skisser. Disse skissene er skrevet i tekstredigereren og lagres med filtypen .ino.
- **Editor og Kompiler**: IDE-miljøet inneholder hovedsakelig to grunnleggende deler: Editor og Kompiler. Førstnevnte brukes for å skrive den nødvendige koden og sistnevnte brukes for å kompilere og laste opp koden til den gitte Arduino-modulen.

Arduino IDE er et viktig verktøy for alle som jobber med Arduino-prosjekter, enten det er hobbyister, studenter, lærere eller profesjonelle utviklere.

Kilder:
1. Arduino. https://www.arduino.cc/en/software/.
2. Introduction to Arduino IDE - The Engineering Projects. https://www.theengineeringprojects.com/2018/10/introduction-to-arduino-ide.html.
3. Arduino IDE - JavaTpoint. https://www.javatpoint.com/arduino-ide.
4. Using the Arduino Software (IDE). https://docs.arduino.cc/learn/starting-guide/the-arduino-software-ide/.
5. Arduino IDE. https://apps.microsoft.com/detail/9NBLGGH4RSD8?launch=true&mode=full&hl=en-gb&gl=us.


## Teste GNSS mottaker
...

## Logge GNSS NMEA til SD-kort

```{image} ../bilder/gnss_arduino.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

## Visualisere GNSS posisjoner

### Google Earth
[NMEA->KML](http://www.h-schmidt.net/NMEA/)


### QGIS
[KML->CVS](http://www.monster.com.tw/kml2csv)


## Spørsmål
...




