(blender_intro)=
# Brukerveiledning: Visning av 3D-modeller i Blender

Blender er et gratis, profesjonelt 3D-program med åpen kildekode. I denne veiledningen lærer du å importere, fargelegge og navigere i 3D-modellene dere har skannet med Polycam.

---

## 📋 Oversikt
Når du har skannet et objekt eller en bygning i 3D ved hjelp av mobil-fotogrammetri, lagres dette som en teksturert 3D-modell (mesh). Blender lar oss åpne denne modellen på PCen, rotere den i alle tre akser, og studere de geometriske detaljene samt gå virtuelt rundt inne i modellen.

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Last ned og klargjør Blender
1. Last ned og installer Blender fra [blender.org](https://www.blender.org/).
2. **For bærbare PC-er uten ekstern mus**:
   * Åpne *Edit* -> *Preferences* -> *Input*.
   * Under *Mouse*, huk av for **Emulate 3 Button Mouse** (☑️). Dette lar deg rotere i 3D-rommet ved å holde `Alt` + venstreklikk på styreflaten.

### 2. Importere 3D-modellen (.glb)
Polycam eksporterer modeller i standardformatet GLTF 2.0 (som lagres som en enkelt `.glb`-fil).
1. Åpne Blender. Det opprettes automatisk en standardscene med en kube, et kamera og en lyskilde.
2. **Slett kuben**: Høyreklikk på kuben i 3D-vinduet og velg **Delete** (eller klikk på kuben og trykk `X` -> *Delete*).
   ```{figure} ../bilder/blender/slett.png
   :align: center
   ```
3. Gå til toppmenyen: **File** -> **Import** -> **glTF 2.0 (.glb/.gltf)**.
   ```{figure} ../bilder/blender/import_gltf.png
   :align: center
   ```
4. Bla deg frem til `.glb`-filen du overførte fra Polycam, og dobbeltklikk på den.
   ```{figure} ../bilder/blender/velg_fil.png
   :align: center
   ```

### 3. Vise farger og teksturer (Viewport Shading)
Når modellen er importert, ser den ofte helt grå og fargeløs ut. Dette er fordi Blender starter i *Solid* visningsmodus. For å se fargene fra bildene dine:
1. Finn kule-ikonene øverst i høyre hjørne av 3D-vinduet (Viewport Shading).
2. Klikk på den nest øverste kula: **Material Preview** (Materialvisning).
   ```{figure} ../bilder/blender/shading.png
   :align: center
   ```
3. Modellen vil nå fargelegges med bildene dere tok under skanningen.

---

## 🏃‍♂️ Navigering i 3D-rommet

### Grunnleggende navigasjon
Bruk mus og tastatur til å rotere, panorere og zoome:

| Handling | Med ekstern mus | Uten ekstern mus (Emulering slått på) |
| :--- | :--- | :--- |
| **Rotere** | Hold midtre museknapp og dra | Hold `Alt` + venstreklikk og dra |
| **Panorere (Flytte)** | Hold `Shift` + midtre museknapp og dra | Hold `Shift` + `Alt` + venstreklikk og dra |
| **Zoome** | Rull på musehjulet | Dra med to fingre på styreflaten (pinch) |
| **Sentrere på modell** | Klikk på modellen og trykk `.` (punktum) på Numpad | Gå til meny: *View* -> *Frame Selected* |

### Gå-navigasjon (Walk Navigation)
Hvis du har skannet et bygg eller et rom og ønsker å gå virtuelt rundt på bakkenivå:
1. Aktiver modusen ved å trykke: **`Shift` + `` ` ``** (backtick-tasten, rett under `Esc` og til venstre for tallet `1`).
   ```{figure} ../bilder/blender/walk.png
   :align: center
   ```
2. Bruk tastene som i et PC-spill:
   * **`W` / `S` / `A` / `D`**: Gå henholdsvis fremover, bakover, til venstre og til høyre.
   * **Musebevegelse**: Snu deg rundt og se i ulike retninger.
   * **`Mellomrom`**: Fly oppover / **`Shift`**: Fly nedover.
   * **Musehjulet**: Juster ganghastigheten.
   * **Venstreklikk / `Enter`**: Bekreft og stopp på nåværende sted.
   * **Høyreklikk / `Esc`**: Avbryt og hopp tilbake til utgangspunktet.

---

## 💡 Tips & feilsøking

* **Modellen er usynlig etter import**: Dette skjer ofte fordi modellen er ekstremt stor eller ekstremt liten, eller at den har havnet langt unna origo (0,0,0) på grunn av GPS-koordinatene i bildefilene. Løsning: Marker modellen i *Outliner*-treet (listen øverst til høyre) og trykk på **punktum-tasten** på det numeriske tastaturet (eller gå til *View* -> *Frame Selected*). Blender zoomer da rett inn på modellen.
* **Modellen ser ujevn ut / mangler hull**: Fotogrammetri krever skarpe bilder. Hvis deler av 3D-modellen din er borte eller ser "smeltet" ut, har du hatt for få bilder eller for mye uskarpe detaljer i det opprinnelige opptaket.
