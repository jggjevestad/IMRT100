(gnss_bygge)=
# Bygg din egen GNSS mottaker

## Hva er GNSS?
GNSS er en fellesbetegnelse for globale satellittbaserte navigasjonssystemer. Det finnes flere slike satellittbaserte navigasjonssystemer, men mest kjente er nok det amerikanske GPS systemet som er et militært navigasjonssystem. Det eneste sivile satellittbaserte navigasjonssystemet heter Galileo og eies og driftes av EU. De fleste nyere mottakere kan bruke dette navigasjonssystemet.

Desto flere navigasjonssystemer en mottaker kan bruke, desto flere satellitter har man tilgang til. Dette fører som regel til en bedre og mer nøyaktig posisjonsbestemmelse. Kort og enkelt forklart så måles avstanden mellom mottakeren og satellittene for å finne en posisjon. Man måler altså tiden det tar fra signalet sendes ut fra satellitten til det når mottakeren.

For å beregne en posisjon trenger man fire satellitter. Dette er fordi vi har tre romlige koordinatene i X, Y og Z-retning som ukjente, i tillegg til en klokkefeil i satellitt- og mottakerklokke. Koordinattypen X, Y og Z kalles ECEF (Earth Centered Earth Fixed) og er 3D koordinater i et jordsentrisk koordinatsystem. Selvom GNSS mottakeren egentlig beregner ECEF koordinater, så vises de til brukeren som f.eks. breddegrad, lengdegrad og høyde, og det er denne koordinattypen som dere finner i NMEA formatet.
  
Mottakerene dere skal bygge presenterer posisjonene på NMEA format. Dere skal bruke dette formatet til å lese av data som er aktuelle for å løse oppgavene.


## Hva kommer ut av en GNSS mottaker?

For å finne ut av hva en GNSS mottaker egentlig sender ut, så må vi koble sammen en GNSS mottaker med en mikrokontroller. En mikrokontroller er en liten datamaskin som i vi kan bruke til å oversetter signalene som kommer ut av GNSS mottakeren til digitale data som vi kan se på.

### Innstaller programvare

Begynn med å innstallere [Arduino IDE](https://www.arduino.cc/en/software) (Integrated Development Environment).

Dette programmet gjør det mulig å skrive programkode som kan lastes opp i mikrokontrolleren. Her er det også mulig å se på data som kommer ut av mikrokontrolleren - dette kalles en *terminal*.

1. Last opp eksempelkode (blink) som får LED på mikrokontrolleren til å blinke.

Klarer du å få LED til å blinke fortere eller saktere?

Nå som dere har testet mikrokontrolleren litt, så er neste steg å bruke den til å vise hva en GNSS mottaker sender ut.

### Se på NMEA data

- GNSS mottaker (breakout board)
- Mikrokontroller for å lese data på NMEA format (Arduino UNO / MKR1000)

2. Koble strøm til GNSS mottakeren
3. Koble seriell signal fra GNSS mottaker til en mikrokontroller TX (transmit) / RX (receive)
4. Åpne en terminal (Serial monitor) og se på NMEA data som kommer ut av GNSS mottakeren

Hva er innholdet i NMEA strengene?

### Lagre NMEA data til SD-kort

For å slippe å ha med seg en laptop for å kunne lagre NMEA strengene, så kan vi isteden lagre dem på et SD-kort.

5. Koble strøm til SD-kort leser/skriver
6. koble seriell signal fra GNSS mottaker til SD-kort enhet TX (transmit) / RX (receive)

Nå har dere en GNSS mottaker som lagrer NMEA strenger til et SD-kort. 

### Vis hvor du har vært i Google Earth
...