(cc_intro)=
# Introduksjon til CloudCompare

**CloudCompare** er et kraftig, åpen kildekode-program for behandling og analyse av 3D-punktskyer og trekantede nett. Programmet ble opprinnelig utviklet for å sammenligne tette 3D-punktskyer direkte, men har siden blitt utvidet til å støtte en rekke funksjoner og filformater.

## Hovedfunksjoner
**Punkt- og nettbehandling**: CloudCompare kan håndtere store mengder data og utføre komplekse operasjoner som registrering, segmentering og filtrering av punktskyer. <br>
**Visualisering**: Programmet tilbyr avanserte visualiseringsverktøy som gjør det mulig å se og analysere data i 3D. <br>
**Måling og analyse**: Brukere kan utføre nøyaktige målinger og analyser, inkludert volum- og overflateberegninger, samt sammenligning av forskjellige datasett. <br>
**Støtte for flere filformater**: CloudCompare støtter en rekke filformater, noe som gjør det enkelt å importere og eksportere data fra andre programmer. <br>

## Brukergrensesnitt
- **Hovedvindu**: Her kan du se og manipulere 3D-dataene dine.
- **Verktøylinjer**: Tilbyr rask tilgang til de mest brukte funksjonene.
- **DB-tre**: Viser strukturen av de importerte dataene og lar deg organisere og administrere dem effektivt.

## Komme i gang
**Last ned og installer**: CloudCompare kan hentes på den [offisielle nettsida](https://www.cloudcompare.org/)

**Importer data**: Start med å importere en eller flere punktskyer eller 3D modeller. Du kan dra de inn i vinduet, eller trykke på mappesymbolet oppe til venstre. I import-menyen trykker du på _apply all_.

**Utforsk verktøyene**: Bruk verktøylinjene og menyene for å utføre ønskede operasjoner på dataene dine.

For mer detaljerte instruksjoner og veiledninger, kan du sjekke ut den offisielle dokumentasjonen og brukermanualen på CloudCompare sin nettside [CloudCompare User Manual](https://www.cloudcompare.org/doc/qCC/CloudCompare%20v2.6.1%20-%20User%20manual.pdf).


## Gjøre et utsnitt av en punktsky

Ofte er vi bare interresert i en liten bit av punktskyen, da er det greit å klippe vekk det uinterresante. Her brukes en [punktsky over NMBU](https://nmbu.instructure.com/courses/10981/files/2173646/download?download_frd=1) som eksempel:

Klippe ut Tuntreet, lage et "volum" av treet og mål høyden på treet:
1. File -> Open *41.laz (Apply/Yes)
2. File -> Open *42.laz (Apply/Yes)
3. DB tree select both scans -> Merge
4. Segment tool -> polygon rundt tuntreet
5. Segment In -> Confirm and Delete
6. Pick rotation center -> på bakken under tuntreet
7. Edit -> Normals -> Compute
8. Plugin -> Poisson Recon -> Output density as SF
9. Edit -> Scalar Field -> Filter by Value -> Export (Change color to RGB)
10. Point picking -> distance between 2 points

## Måle avstand

Ofte ønsker man å måle avstander i punktskyer. Start med å velge Point Picking verktøyet
```{figure} ../bilder/cloudcompare/maal1.png
```
Velg avstandsverktøyet:
```{figure} ../bilder/cloudcompare/maal2.png
```
Trykk så nøyaktig du klarer på punktene du vil måle avstanden mellom.
```{figure} ../bilder/cloudcompare/maal3.png
```

Vet du at punktskyen er i vater og du ønsker å måle loddrett er det lurt å lese av △Z verdien