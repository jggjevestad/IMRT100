(gnss_bygge)=
# Bygg din egen GNSS mottaker

## GNSS
GNSS er en fellesbetegnelse for satellittbaserte navigasjonssystemer. Det finnes flere slike satellittbaserte navigasjonssystemer, men de to mest utbredte er det amerikanske GPS systemet og det russiske GLONAS. Begge disse er militære navigasjonssystemer.
Det europeiske navigasjonssystemet heter Galileo og er et sivilt navigasjonssystem. Nyere mottakere har også begynt å ta i bruk dette navigasjonssystemet.
Desto flere navigasjonssystemer en mottaker kan bruke, desto flere satellitter har man tilgang til. Dette fører som regel til en bedre og mer nøyaktig posisjonsbestemmelse.
Kort og enkelt forklart så måles avstanden mellom mottakeren og satellittene for å finne en posisjon. Man måler tiden det tar fra signalet sendes ut fra satellitten til det når mottakeren. 
Man trenger fire satellitter for å beregne sin posisjon. Dette er fordi vi har de romlige koordinatene i x, y og z-retning som ukjente, i tillegg til en klokkefeil i satellitt og mottakerklokke.
  
Mottakerene dere skal bygge logger dataene på NMEA format. Dere skal bruke dette formatet til å lese av data som er aktuelle for å løse oppgavene. Se link for full beskrivelse av formatet.


## Oppgave 1 Arduino GNSS logger
Utstyr:
•	Adafruit Ultimate GPS Breakout – Versjon 3 
•	SparkFun Openlog – SD data logger  
•	Kingston® Micro SD card 
•	Breadboard (terminal)  
•	Kompatible ledninger  
•	Batteri 3,7 V, 850 mAh 

1.	Klargjøring 
a.	Installer Arduino IDE (programvare). https://www.arduino.cc/en/Main/Software 
b.	Installer Adafruit GPS Library  https://learn.adafruit.com/adafruit-ultimate-gps/arduino-wiring

2.	Oppkobling

![](../bilder/gnss_arduino.jpg)

3.	Data 
a.	Koble til Arduino UNO til PC med USB . Åpne Arduino IDE (program)
b.	Innstillinger i Arduino IDE , verktøylinjen :
Verktøy -> Kort - velg Arduino/Genuino UNO
Verktøy -> Port – velg COM3


c.	Kommunisere med GNSS loggeren 

i.	Finne frem kode
Fil -> eksempler – velg Adafruit GPS Library – velg parsing


ii.	Laste opp kode til Arduino


Trykk på pil ikonet i høyre hjørne 


iii.	Lese av Arduinoen 
Trykk på forstørellseglass ikonet i venstrehjørne 
Sørg for å ha samme verdier som vist (115200 Baud)


NB Sørg for å ha fix (dekning til satelitter) på Adafruit Ultimate Breakout. Fix lampen blinker da hvert 15 sekund.

Oppgave 2.2 GNSS logger 

1.	Oppkobling 

•	Connect RX to  TXO   
•	Connect TX to  RXI  
•	 VIN to +(breadboard) - Adafruit Ultimate breakout
•	GND to -(breadboard) - Adafruit Ultimate breakout
•	VCC to +(breadboard) – Sparkfun Openlog 
•	GND to –(breadboard) – Sparkfun Openlog 


2.	Start opp GNSS loggeren 

NB Sørg for å ha fix (dekning til satelitter) på Adafruit Ultimate Breakout 

Nå kan du gå deg en runde for å teste loggeren.

3.	Konvertering
•	Sett inn SD kortet i PCen og last over fila som dataen er logget på. Det kan hende det er flere filer som ligger inne så her må du bare prøve deg frem, siden loggeren ikke lagrer filene med navn eller dato.
•	Last ned Google Earth
•	Man må først konvertere fila fra TXT format til KML. Bruk denne nettsiden til å konvertere: http://www.h-schmidt.net/NMEA/
•	Sett parameterne til det som er vist på bildet til høyre.
•	Ruten som er gått skal nå vises i Google Earth.
Videre kan man legge dette inn i QGIS som er et GIS verktøy. For å gjøre dette kan det være lurt å konvertere fra KML til CSV: http://www.monster.com.tw/kml2csv







