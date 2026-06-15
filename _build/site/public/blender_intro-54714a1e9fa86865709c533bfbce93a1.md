(blender_intro)=
# Introduksjon til Blender

**Blender** er et gratis og åpen kildekode-program for 3D-modellering, animasjon og rendering. I denne bruksanvisningen bruker vi det til å importere og inspisere 3D-modellen vi lager med Polycam.

Last ned Blender:
- Windows og Mac: [https://www.blender.org/](https://www.blender.org/)
- Linux: [Flathub](https://flathub.org/apps/org.blender.Blender)

---

## Grensesnittet

Når du starter Blender ser du velkomstskjermen med en standardscene som inneholder en kube, en lampe og et kamera:

![Blender velkomstskjermen](../bilder/blender/blender.png)

Blender har mange arbeidsområder, men for denne oppgaven bruker vi bare **3D Viewport** – det store vinduet der du ser og navigerer i scenen.

Øverst til høyre i 3D Viewport finner du knapper for visningsmoduser (shading). Disse styrer hvordan modellen ser ut på skjermen.

---

## Importere en 3D-modell fra Polycam

Polycam eksporterer modellen som en `.glb`-fil (GLTF 2.0-format). Slik importerer du den i Blender:

**Steg 1** – Slett standardkuben. Høyreklikk på kuben og velg **Delete**:

![Slett standardkuben](../bilder/blender/slett.png)

**Steg 2** – Importer modellen via menyen **File → Import → glTF 2.0 (.glb/.gltf)**:

![Importmeny](../bilder/blender/import_gltf.png)

**Steg 3** – Naviger til mappa der `.glb`-filen er lagret og dobbeltklikk på filen:

![Velg fil](../bilder/blender/velg_fil.png)

Modellen skal nå vises i 3D Viewport.

---

## Vise teksturer (Shading)

Rett etter import kan modellen se grå ut. For å se de faktiske fargene og teksturene fra Polycam må du endre visningsmodus øverst til høyre i 3D Viewport:

| Ikon | Modus | Beskrivelse |
|---|---|---|
| ![](../bilder/blender/ingen_shading.png) | Solid | Grå overflate, ingen tekstur |
| ![](../bilder/blender/shading.png) | Material Preview | Viser tekstur og farger |

Klikk på kulesymbolet (**Material Preview**) for å se modellen med tekstur og farger slik den faktisk ser ut.

---

## Navigere i 3D-visningen

### Mus og tastatur

Standard navigasjon i Blender bruker musehjulet og midtknappen:

| Handling | Mus | Numpad |
|---|---|---|
| Rotere rundt scenen | Midtknapp + dra | `4` / `6` / `8` / `2` |
| Panorere (flytte) | `Shift` + midtknapp + dra | `Shift` + `4` / `6` / `8` / `2` |
| Zoome | Scrollhjul | `+` / `−` |
| Frontvisning | – | `1` |
| Sidevisning | – | `3` |
| Toppvisning | – | `7` |
| Sentrere på valgt objekt | – | `.` (punktum) |
| Kameravisning | – | `0` |

```{note}
Uten ekstern mus (f.eks. på bærbar PC): aktiver **Emulate 3 Button Mouse** under **Edit → Preferences → Input**. Da kan du holde `Alt` + venstreklikk for å rotere.
```

### Walk Navigation – gå rundt i modellen

Walk Navigation lar deg bevege deg gjennom scenen som i et førstepersonsspill. Dette er nyttig for å utforske store modeller innenfra, for eksempel et rom som er skannet med Polycam.

Aktiver Walk Navigation med **`Shift` + `` ` ``** (backtick, tasten til venstre for `1`):

![Walk Navigation](../bilder/blender/walk.png)

| Tast | Handling |
|---|---|
| `W` / Pil opp | Gå fremover |
| `S` / Pil ned | Gå bakover |
| `A` / Pil venstre | Gå til venstre |
| `D` / Pil høyre | Gå til høyre |
| Musebevegelse | Snu kameraet |
| Scrollhjul | Endre ganghastighet |
| `Mellomrom` | Gå opp |
| `Shift` | Gå ned |
| `Enter` / venstreklikk | Bekreft ny kameraposisjon |
| `Esc` / høyreklikk | Avbryt og gå tilbake |

---

## Mer informasjon

For utfyllende dokumentasjon, se Blender sin offisielle brukermanual:

- [Navigasjon i 3D Viewport](https://docs.blender.org/manual/en/latest/editors/3dview/navigate/navigation.html)
- [Walk og Fly Navigation](https://docs.blender.org/manual/en/latest/editors/3dview/navigate/walk_fly.html)
- [Importere GLTF](https://docs.blender.org/manual/en/latest/addons/import_export/scene_gltf2.html)
