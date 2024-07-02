(gnss_noyaktighet)=
# Hvor nøyaktig er GNSS?

Målet med denne oppgaven er å utvikle en forståelse av hvordan man kan estimere nøyaktigheten til forskjellige typer GNSS-mottakere ved å analysere posisjonsdata lagret i NMEA-format.


1. Datainnsamling: </br> Samle inn NMEA-data fra forskjellige typer GNSS-mottakere. Legg GNSS-mottakeren i ro over et punkt og lagre inn data hvert sekund i f.eks. 5 minutter.

2. Lese inn data: </br>
Analyser de innsamlede NMEA-dataene. Fokuser på GGA-setningene fordi disse inneholder informasjon om posisjon (breddegrad og lengdegrad), antall satellitter og HDOP-verdier.

3. Sann posisjon: </br>
Beregn gjennomsnittet av alle posisjonen. Dette vil være din "sanne" posisjon for sammenligning.

4. Beregning av nøyaktighet: </br>
For hver posisjonsobservasjon, beregn avstanden fra den observerte posisjonen til middelposisjonen. Bruk disse avstandene til å beregne standardavviket, som vil være et mål for nøyaktigheten til GNSS-mottakeren.

5. Sammenligning mottakerne: </br>
Gjenta trinnene ovenfor for forskjellige typer GNSS-mottakere. Sammenlign nøyaktigheten du har beregnet for hver mottaker.


## Spørsmål

1. Hvilken mottaker hadde høyest nøyaktighet? Hvorfor tror du det er slik?
2. Hvordan påvirker antall satellitter som er synlige nøyaktigheten til GNSS-mottakerne?
3. Hva er noen potensielle kilder til feil i GNSS-posisjonering?

Husk at nøyaktigheten til GNSS-mottakere kan variere avhengig av mange faktorer, inkludert antall synlige satellitter, atmosfæriske forhold, og kvaliteten på mottakerens hardware og software.