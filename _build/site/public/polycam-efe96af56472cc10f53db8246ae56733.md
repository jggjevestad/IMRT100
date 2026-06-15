(polycam)=
# Polycam og Blender

Polycam er en app som lager 3D-modeller fra bilder du tar med mobilen, ved hjelp av [fotogrammetri](https://snl.no/fotogrammetri). Appen er ikke fri programvare, men gratisversjonen er tilstrekkelig for denne oppgaven.

Last ned Polycam til [Android](https://play.google.com/store/apps/details?id=ai.polycam) eller [iPhone](https://apps.apple.com/no/app/polycam-3d-scanner-lidar-360/id1532482376).

---

## Opptaksmodus

Polycam har to relevante opptaksmodi:

**Photo Mode** (tilgjengelig på alle enheter)
Appen tar automatisk bilder mens du beveger deg rundt motivet. Bildene sendes til en server som beregner en 3D-modell gjennom fotogrammetri. Krever god belysning og at motivet er detaljrikt nok til at appen finner like punkter på tvers av bildene.

**LiDAR Mode** (kun iPhone 12 Pro og nyere)
Bruker telefonens LiDAR-sensor til å måle dybde direkte. Raskere og fungerer bedre i svakt lys, men gir lavere oppløsning enn Photo Mode.

For best resultat med Photo Mode:
- Gå sakte og jevnt rundt motivet
- Sørg for god, jevn belysning uten sterke skygger
- Motiver med matte overflater og tydelig tekstur fungerer best
- Unngå blanke, gjennomsiktige eller eintfargede flater
- Ta bilder fra flere høyder (lavt, midt og ovenfra)

---

## Ta opp en 3D-modell

Første gang du åpner appen blir du bedt om å registrere en bruker. Etter innlogging får du opp startskjermen:

```{image} ../bilder/polycam/start.png
:width: 200px
```

Velg **Photo** og trykk på den hvite knappen. Appen tar automatisk bilder mens du beveger deg rundt motivet. Når du har dekket alle sider trykker du **Done**:

```{image} ../bilder/polycam/record.png
:width: 200px
```

---

## Eksportere modellen

Etter opptak får du opp prosesseringsmenyen:

```{image} ../bilder/polycam/eksport.png
:width: 200px
```

| Innstilling | Beskrivelse |
|---|---|
| **Detail** | Styrer kvalitet og filstørrelse. *Medium* er som regel tilstrekkelig. |
| **Object Masking** | Forsøker å fjerne bakgrunnen automatisk. Skru av i første omgang. |

Trykk **Upload & process** og vent til prosesseringen er ferdig. Når modellen er klar kan du forhåndsvise den i appen:

```{image} ../bilder/polycam/ferdig.png
:width: 200px
```

For å eksportere: trykk på nedlastingsikonet og velg **GLTF**. Overfør den nedlastede `.glb`-filen til PCen din.

```{image} ../bilder/polycam/gltf_eksport.png
:width: 200px
```

---

## Blender

Blender er et kraftig, gratis og åpen kildekode-program for 3D-modellering, animasjon og rendering. Vi bruker det her til å importere og inspisere 3D-modellen fra Polycam.

Last ned Blender:
- Windows og Mac: [https://www.blender.org/](https://www.blender.org/)
- Linux: [Flathub](https://flathub.org/apps/org.blender.Blender)

### Importere modellen

Når du starter Blender ser du velkomstskjermen med en standardscene:

![Blender velkomstskjermen](../bilder/blender/blender.png)

**Steg 1** – Slett standardkuben ved å høyreklikke og velge **Delete**:

![](../bilder/blender/slett.png)

**Steg 2** – Importer modellen via **File → Import → glTF 2.0 (.glb/.gltf)**:

![](../bilder/blender/import_gltf.png)

**Steg 3** – Naviger til mappa med `.glb`-filen og dobbeltklikk på den:

![](../bilder/blender/velg_fil.png)

### Shading

Rett etter import kan modellen se grå og uten farger ut. For å se teksturene må du slå på **Material Preview** øverst til høyre i 3D-visningen:

| Ikon | Modus | Beskrivelse |
|---|---|---|
| ![](../bilder/blender/ingen_shading.png) | Solid | Grå overflate, ingen tekstur |
| ![](../bilder/blender/shading.png) | Material Preview | Viser tekstur og farger |

Klikk på kulesymbolet (Material Preview) for å se modellen med tekstur.

---

## Navigere i 3D-visningen

### Mus og tastatur

| Handling | Mus | Tastatur |
|---|---|---|
| Rotere | Midtknapp + dra | Numpad 4 / 6 / 8 / 2 |
| Panorere | Shift + Midtknapp + dra | Shift + Numpad 4 / 6 / 8 / 2 |
| Zoome | Scrollhjul | Numpad + / − |
| Frontvisning | – | Numpad 1 |
| Sidevisning | – | Numpad 3 |
| Toppvisning | – | Numpad 7 |
| Kameravisning | – | Numpad 0 |
| Tilpass til vindu | – | Numpad . (punktum) |

Uten mus (f.eks. på bærbar PC): aktiver **Emulate 3 Button Mouse** under **Edit → Preferences → Input**.

Full navigasjonsdokumentasjon: [https://docs.blender.org/manual/en/latest/editors/3dview/navigate/navigation.html](https://docs.blender.org/manual/en/latest/editors/3dview/navigate/navigation.html)

### Walk Navigation (spaseringsmodus)

Walk Navigation lar deg bevege deg gjennom scenen som i et førstepersonsspill. Nyttig for å utforske store modeller innenfra.

Aktiver Walk Navigation med **Shift + `** (backtick, tasten til venstre for 1).

![Walk Navigation](../bilder/blender/walk.png)

| Tast | Handling |
|---|---|
| W / Pil opp | Gå fremover |
| S / Pil ned | Gå bakover |
| A / Pil venstre | Gå til venstre |
| D / Pil høyre | Gå til høyre |
| Mus | Snu kameraet |
| Scrollhjul | Endre ganghastighet |
| Mellomrom / Shift | Gå opp / ned |
| Enter | Bekreft ny kameraposisjon |
| Esc | Avbryt og gå tilbake |

Full dokumentasjon: [https://docs.blender.org/manual/en/latest/editors/3dview/navigate/walk_fly.html](https://docs.blender.org/manual/en/latest/editors/3dview/navigate/walk_fly.html)
