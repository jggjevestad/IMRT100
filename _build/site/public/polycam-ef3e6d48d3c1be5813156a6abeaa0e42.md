(polycam)=
# Polycam

Polycam er en app som lager 3D-modeller fra bilder du tar med mobilen, ved hjelp av [fotogrammetri](https://snl.no/fotogrammetri). Appen er ikke fri programvare, men gratisversjonen er tilstrekkelig for denne oppgaven.

Last ned Polycam til [Android](https://play.google.com/store/apps/details?id=ai.polycam) eller [iPhone](https://apps.apple.com/no/app/polycam-3d-scanner-lidar-360/id1532482376).

---

## Opptaksmodus

Polycam har to relevante opptaksmodi:

**Photo Mode** (tilgjengelig på alle enheter)
Appen tar automatisk bilder mens du beveger deg rundt motivet. Bildene lastes opp til en sky-server som beregner en 3D-modell gjennom fotogrammetri. Krever god belysning og at motivet har nok tekstur til at appen finner like punkter på tvers av bildene.

**LiDAR Mode** (kun iPhone 12 Pro og nyere, samt iPad Pro)
Bruker telefonens LiDAR-sensor til å måle dybde direkte. Raskere og fungerer bedre i svakt lys, men gir lavere geometrisk oppløsning enn Photo Mode.

For best resultat med Photo Mode:
- Gå sakte og jevnt rundt motivet
- Sørg for god, jevn belysning uten sterke skygger
- Motiver med matte overflater og tydelig tekstur fungerer best
- Unngå blanke, gjennomsiktige eller ensfargede flater
- Ta bilder fra flere høyder (lavt, midt og ovenfra)

---

## Ta opp en 3D-modell

Velg **Photo** fra hjemskjermen og pek kameraet mot motivet. Trykk på den store hvite knappen for å starte opptaket:

```{image} ../bilder/polycam/start.png
:width: 200px
```

Gå sakte rundt motivet mens appen automatisk tar bilder. Antall bilder tatt vises i hjørnet. Når du har dekket alle sider trykker du **Done**:

```{image} ../bilder/polycam/record.png
:width: 200px
```

---

## Prosessering og eksport

Etter opptaket får du opp prosesseringsmenyen:

```{image} ../bilder/polycam/eksport.png
:width: 200px
```

| Innstilling | Beskrivelse |
|---|---|
| **Detail** | Styrer kvalitet og filstørrelse. *Medium* er som regel tilstrekkelig. |
| **Object Masking** | Forsøker å fjerne bakgrunnen automatisk. La denne være av i første omgang. |

Trykk **Upload & Process** og vent til prosesseringen er ferdig. Når modellen er klar kan du se den i appen:

```{image} ../bilder/polycam/ferdig.png
:width: 200px
```

For å eksportere modellen: trykk på nedlastingsikonet øverst til høyre og velg **GLTF**. Overfør den nedlastede `.glb`-filen til PCen din.
