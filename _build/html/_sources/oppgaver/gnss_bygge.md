(gnss_bygge)=
# Bygg din egen GNSS mottaker

## GNSS
GNSS er en fellesbetegnelse for satellittbaserte navigasjonssystemer. Det finnes flere slike satellittbaserte navigasjonssystemer, men de to mest utbredte er det amerikanske GPS systemet og det russiske GLONAS. Begge disse er militære navigasjonssystemer.
Det europeiske navigasjonssystemet heter Galileo og er et sivilt navigasjonssystem. Nyere mottakere har også begynt å ta i bruk dette navigasjonssystemet.
Desto flere navigasjonssystemer en mottaker kan bruke, desto flere satellitter har man tilgang til. Dette fører som regel til en bedre og mer nøyaktig posisjonsbestemmelse.
Kort og enkelt forklart så måles avstanden mellom mottakeren og satellittene for å finne en posisjon. Man måler tiden det tar fra signalet sendes ut fra satellitten til det når mottakeren. 
Man trenger fire satellitter for å beregne sin posisjon. Dette er fordi vi har de romlige koordinatene i x, y og z-retning som ukjente, i tillegg til en klokkefeil i satellitt og mottakerklokke.
  
Mottakerene dere skal bygge logger dataene på NMEA format. Dere skal bruke dette formatet til å lese av data som er aktuelle for å løse oppgavene. Se link for full beskrivelse av formatet.


## NMEA format


## Arduino IDE


## Logge GNSS NMEA til SD-kort

```{image} ../bilder/gnss_arduino.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

## Visualisere GNSS spor

### Google Earth
[NMEA->KML](http://www.h-schmidt.net/NMEA/)


### QGIS
[KML->CVS](http://www.monster.com.tw/kml2csv)







