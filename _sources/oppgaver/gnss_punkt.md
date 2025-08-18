(gnss_mobil)=
# Måle inn punkt med GNSS

```{image} ../bilder/rtk.jpg
:alt: Ekte landmåler i aksjon
:class: mb-1
:width: 300px
:align: center
```

Etter GNSS ble åpnet for sivile på 80-tallet har satelittbaserte målinger tatt over mye av arbeidet innenfor landmåling. Du bruker sannsynligvis også GNSS hver dag til å finne frem eller kontinuerlig kringkaste posisjonen din til alle du kjenner.

Det finnes mange metoder og systemer for å øke nøyaktigheten på GNSS slik at de kan brukes til landmåling m.m. 
RTK er et slikt system og i denne oppgavene dere sammenligne det med nøyaktigheten til mobilen deres.

På campus er det et nettverk av såkalte fastmerker. Det vil si punkter i bakken vi kjenner veldig nøyaktige koordinater til og som vi bruker som utgangspunkt for andre målinger.
Dere skal velge et fastmerke og se hvor nøyaktig mobilen og RTK mottakeren er på å måle posisjonen og hvor langt de er fra sannheten. 

**Dere kan f.eks måle NMB1 (dvs. søylen ved boksmia) som har disse koordinatene i UTM 32:**

| Punkt | N (m) | E (m) | H (m) |
|---|---|---|---|
| NMB1 | 6615708.451 | 599809.075 | 103.153 |

Resten av fastmerkene ligger her: [fastmerker.csv](/ressurser/fastmerker.csv)

[Her](/bruksanvisninger/qgis_csv_import.md) er en bruksanvisning på å legge inn csv filer i QGIS. Skal dere legge egne punkt er det lurt å skrive de inn i en csv fil.

## Måling med mobilen
1. Legg mobilen oppå et fastmerke og logg GNSS posisjonen i f.eks. 5 minutt.
2. Konverter kml eller GPX fila fra mobilen til CSV med QGIS. [Se bruksanvisning](/bruksanvisninger/qgis_csv_eksport.md)
2. Finn gjennomsnittet og standardavviket til målingene med python. [Se koden her](python_gjennomsnitt)

## Måling med RTK
RTK (Real-Time Kinematic) er en måte å måle posisjon med GNSS satellitter mer nøyaktig. RTK bruker en basestasjon som korrigerer målingene vi gjør med mottakeren ute i felt.

**Øvingslærere kjører demo for en og en gruppe hvor dere måler samme fastmerke**

## Spørsmål:
1. Hvor nøyaktig ble målingen fra mobilen?
1. Hvor nøyaktig ble målingen fra RTK mottakeren?
1. Hvor mye mer nøyaktig er RTK enn mobilen din? Hvorfor er det så stor forskjell?

```{image} ../bilder/presisjon_vs_noyaktighet.png
:alt: Presisjon vs nøyaktighet
:class: mb-1
:width: 600px
:align: center
```