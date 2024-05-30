(gnss_mobil)=
# Måle inn punkt med GNSS

Etter GNSS ble åpnet for sivile på 90 tallet har satelittbaserte målinger tatt over mye av arbeidet innenfor landmåling. Du bruker sannsynligvis også GNSS hver dag til å finne frem eller kontinuerlig kringkaste posisjonen din til alle du kjenner.

Det finnes mange metoder og systemer for å øke nøyaktigheten på GNSS slik at de kan brukes til landmåling m.m. 
RTK er et slikt system og i denne oppgavene dere sammenligne det med nøyaktigheten til mobilen deres.

Dere skal måle punktet SSIR som har disse koordinatene i UTM 32:

| | N | E | H |
|---|---|---|---|
| SSIR | $6615572.623m$ | $600117.216m$ | $97.162m$ |

## Måling med mobilen
1. Legg mobilen oppå SSIR og logg GNSS possisjonen i 5 minutt. Se: [hvordan logge posisjon med mobilen](../bruksanvisninger/gnss_mobil.html)
2. Lag en Python kode for å finne gjennomsnittet av målingene

## Måling med RTK

RTK (Real-Time Kinematic) er en måte å måle posisjon med GNSS satellitter mer nøyaktig. RTK bruker en basestasjon som kan korrigere målingen vi gjør med mottakeren ute i felt.

Øvingslærere kjører demo for en og en gruppe.

## Spørsmål:
1. Hvor nøyaktig ble målingen fra mobilen?
2. Hvor nøyaktig ble målingen fra RTK mottakeren?
3. Hvor mye mer nøyaktig er RTK en mobilen din?