(cc_intro)=
# Introduksjon til CloudCompare

**CloudCompare** er et kraftig, åpen kildekode-program for behandling og analyse av 3D-punktskyer og trekantede nett. Programmet ble opprinnelig utviklet for å sammenligne tette 3D-punktskyer direkte, men har siden blitt utvidet til å støtte en rekke funksjoner og filformater.

## Hovedfunksjoner:
**Punkt- og nettbehandling**: CloudCompare kan håndtere store mengder data og utføre komplekse operasjoner som registrering, segmentering og filtrering av punktskyer. <br>
**Visualisering**: Programmet tilbyr avanserte visualiseringsverktøy som gjør det mulig å se og analysere data i 3D. <br>
**Måling og analyse**: Brukere kan utføre nøyaktige målinger og analyser, inkludert volum- og overflateberegninger, samt sammenligning av forskjellige datasett. <br>
**Støtte for flere filformater**: CloudCompare støtter en rekke filformater, noe som gjør det enkelt å importere og eksportere data fra andre programmer. <br>

### Brukergrensesnitt:
- **Hovedvindu**: Her kan du se og manipulere 3D-dataene dine.
- **Verktøylinjer**: Tilbyr rask tilgang til de mest brukte funksjonene.
- **DB-tre**: Viser strukturen av de importerte dataene og lar deg organisere og administrere dem effektivt.

### Komme i gang:
**Last ned og installer**: Du kan laste ned CloudCompare fra den offisielle nettsiden.
**Importer data**: Start med å importere punktskyer eller nett fra filene dine.
**Utforsk verktøyene**: Bruk verktøylinjene og menyene for å utføre ønskede operasjoner på dataene dine.

For mer detaljerte instruksjoner og veiledninger, kan du sjekke ut den offisielle dokumentasjonen og brukermanualen på CloudCompare sin nettside [CloudCompare User Manual](https://www.cloudcompare.org/doc/qCC/CloudCompare%20v2.6.1%20-%20User%20manual.pdf).


### Eksempel

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