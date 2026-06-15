(polycam)=
# Brukerveiledning: 3D-skanning med Polycam

Polycam er en populær applikasjon som lar deg lage detaljerte 3D-modeller og punktskyer av fysiske objekter eller rom ved hjelp av smarttelefonen din.

---

## 📋 Oversikt
Appen bruker primært to ulike teknologier for 3D-skanning:
* **Photo Mode (Fotogrammetri)**: Tilgjengelig på alle telefoner. Du tar en serie med sterkt overlappende bilder rundt et objekt. Bildene lastes opp til en sky-server, som syr dem sammen til en teksturert 3D-modell ved hjelp av avanserte algoritmer (Structure from Motion).
* **LiDAR Mode (Aktiv skanning)**: Kun tilgjengelig på iPhone Pro-modeller (fra iPhone 12 Pro og oppover) og iPad Pro. Sensoren sender ut infrarøde laserstråler for å måle avstander direkte i sanntid. Det er raskt, men gir grovere geometriske detaljer enn fotogrammetri.

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Klargjøring av motivet
For å få en god fotogrammetrisk modell i *Photo Mode*, bør du velge et objekt som:
* Er **helt ubevegelig** (unngå trær i vind eller personer som rører seg).
* Har **matte og detaljerte overflater** (f.eks. stein, treverk, betong, sko, statuer).
* Har **god og jevn belysning** (unngå sterkt direkte sollys som skaper skarpe skygger, eller veldig mørke rom).

> [!WARNING]
> **Vanskelige objekter:** Unngå blanke overflater (biler, vinduer), speil, ensfargede glatte flater (hvite vegger) eller tynne strukturer (gress, sykkelhjul). Algoritmen vil feile fordi den ikke klarer å kjenne igjen fellespunkter i bildene.

### 2. Gjennomføre opptaket
1. Åpne Polycam og velg **Photo**-modus på hjemskjermen.
2. Sikt kameraet mot objektet og trykk på den store, hvite **startknappen**.
   ```{figure} ../bilder/polycam/start.png
   :width: 180px
   :align: center
   ```
3. Gå sakte rundt objektet i en sirkel. Appen tar bilder automatisk (du hører en klikkelyd) så lenge du beveger deg rolig.
4. Gjør opptaket i tre "høyder":
   * Første runde: Lavt nede, vinklet oppover.
   * Andre runde: I øyehøyde, rett på.
   * Tredje runde: Høyt oppe, vinklet nedover.
5. Sørg for at hvert bilde har ca. $60\text{–}80\ \%$ overlapp med det forrige.
6. Når du har dekket hele objektet fra alle mulige vinkler (typisk $50\text{–}150$ bilder), trykker du på den røde **stoppknappen (Done)**.
   ```{figure} ../bilder/polycam/record.png
   :width: 180px
   :align: center
   ```

### 3. Prosessering
Etter opptaket blir du presentert for prosesseringsalternativer:
   ```{figure} ../bilder/polycam/eksport.png
   :width: 180px
   :align: center
   ```
* **Detail**: Sett denne til *Medium* or *Full* (Full gir best detaljer, men tar lengre tid).
* **Object Masking**: Huk av denne dersom du ønsker at appen automatisk skal fjerne bakgrunnen rundt objektet.
* Klikk på **Upload & Process**. Bildene sendes nå til Polycam-serveren for beregning. Dette tar vanligvis 2–10 minutter.

### 4. Visning og eksport
Når prosesseringen er ferdig, kan du rotere og studere 3D-modellen direkte i appen:
   ```{figure} ../bilder/polycam/ferdig.png
   :width: 180px
   :align: center
   ```
For å eksportere modellen til PCen din for videre bruk i f.eks. Blender:
1. Trykk på **Eksport (Export)**-ikonet.
2. Under format-alternativene, velg **GLTF** or **OBJ**.
3. Last ned den resulterende `.glb` / `.gltf` (eller `.zip` for OBJ) filen og overfør den til din PC via e-post, OneDrive eller kabel.

---

## 💡 Tips & feilsøking

* **Skanningen blir avvist eller mislykkes**: Dette skyldes som regel for uskarpe bilder, eller at motivet beveget seg underveis. Sørg for å holde telefonen stødig, og gå sakte.
* **Modellen ser "smeltet" ut**: Dette skjer hvis du har glemt å ta bilder av objektet ovenfra, slik at toppen av objektet mangler data. Husk å ta bilder i en halvkule (dome) over objektet, ikke bare en flat sirkel rundt.
* **Problemer med gratisversjonen**: Polycam har en betalingsmur på enkelte eksportformater. GLTF-formatet (`.glb`) er imidlertid gratis å eksportere, og dette formatet støttes direkte av Blender!
