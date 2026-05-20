(gnss_noyaktighet)=
# Hvor nøyaktig er GNSS?

Målet med denne oppgaven er å utvikle en forståelse av hvordan man kan estimere nøyaktigheten til forskjellige typer GNSS-mottakere ved å analysere posisjonsdata dom dere har lagret som f.eks. breddegrad, lengdegrad og høyde.

```{image} ../bilder/gps_acc.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

1. Datainnsamling: </br> Samle inn posisjonsdata fra forskjellige typer GNSS-mottakere. Legg GNSS-mottakeren i ro over et punkt og lagre inn data hvert sekund i 10 minutter.

2. Lese inn data: </br>
Analyser de innsamlede posisjonsdataene. Dersom dere har data på NMEA-format så kan dere fokusere på GGA-setningene fordi disse inneholder informasjon om posisjoner i form av breddegrad og lengdegrad.

3. Sann posisjon: </br>
Plasser GNSS-mottakeren i et punkt med kjente koordinater, evt. kan dere beregne gjennomsnittet av alle koordinatene og bruke dette som "sanne" koordinater.

4. Beregning av nøyaktighet: </br>
For hver posisjon dere har lagret så kan dere beregne avstanden til den kjente posisjonen. Bruk så disse avstandene til å beregne standardavviket til posisjonene. Dette vil være et mål for nøyaktigheten til GNSS-mottakeren.

5. Sammenligning mottakerne: </br>
Gjenta trinnene ovenfor for forskjellige typer GNSS-mottakere. Sammenlign nøyaktigheten du har beregnet for hver mottaker.


## Spørsmål

1. Hvilken mottaker hadde høyest nøyaktighet? Hvorfor tror du det er slik?
2. Hvordan påvirker antall satellitter som er synlige nøyaktigheten til GNSS-mottakerne?
3. Hva er potensielle kilder til feil i GNSS-posisjonering?

Husk at nøyaktigheten til GNSS-mottakere kan variere avhengig av mange faktorer, inkludert antall synlige satellitter, atmosfæriske forhold, og kvaliteten på mottakerens hardware og software.