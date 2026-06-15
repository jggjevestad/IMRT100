(3d_scan_mobil)=
# 3D-skanning og Virkelighetsfangst

I denne oppgaven skal dere utforske teknologier for 3D-skanning og digitalisering av den fysiske verden. Dere skal sammenligne resultatene fra en avansert profesjonell terrestrisk laserskanner (FARO Focus) med mobilbasert 3D-skanning (Polycam) som bruker fotogrammetri eller LiDAR.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">Landmålingslaben / TF-bygget</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">FARO Focus 3D Laserskanner, smarttelefon (iPhone/Android)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value">Polycam App, <a href="https://www.cloudcompare.org">CloudCompare</a>, <a href="https://www.blender.org">Blender</a></span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">3 - 4 timer</span>
  </div>
</div>

```{image} ../bilder/frukt.png
:alt: Fruktkurv digitalisert
:class: mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
3D-skanning (også kjent som virkelighetsfangst eller reality capture) har revolusjonert kartlegging, arkitektur, skogbruk og spillutvikling. Det finnes to hovedmetoder for å skanne objekter i 3D:
1. **Aktiv laserskanning (LiDAR)**: Skanneren sender ut milliarder av laserstråler og måler tiden det tar før de reflekteres tilbake. Dette gir en nøyaktig punktsky (point cloud).
2. **Passiv fotogrammetri**: Man tar en rekke overlappende bilder fra ulike vinkler. Avanserte algoritmer (Structure from Motion - SfM) analyserer pikslene for å rekonstruere dybde og teksturer, noe som resulterer i en teksturert 3D-modell.

---

## 🛠️ Forberedelser
* **Fellesdemo**: Delta på den felles demonstrasjonen av FARO Focus-laserskanneren. Den ferdige punktskyen fra demonstrasjonen blir lagt ut på Canvas.
* **Installasjon**: Installer appen **Polycam** på din smarttelefon. 
* **PC-Verktøy**: Sørg for at du har installert [CloudCompare](https://www.cloudcompare.org) for punktskyanalyse, og [Blender](https://www.blender.org) for visning av 3D-modellen.
* **Veiledere**: Les manualen for [Polycam](../bruksanvisninger/polycam.md) og manualen for [Blender](../bruksanvisninger/blender_intro.md).

---

## 🏃‍♂️ Gjennomføring

### Del 1: Punktsky fra FARO 3D-laserskanner (LiDAR)
1. Last ned punktskyen fra fellesdemoen på Canvas.
2. Åpne `.las` (eller tilsvarende) filen i **CloudCompare**.
3. Naviger rundt i punktskyen. Legg merke til tettheten av punkter og fargeinformasjonen.

### Del 2: Mobil 3D-skanning (Fotogrammetri)
1. Gå sammen i gruppa og velg et egnet objekt (gjerne noe av det samme som ble skannet med FARO-skanneren, f.eks. en statue, en bil, eller en detalj på en bygning).
2. Følg [bruksanvisningen for Polycam](../bruksanvisninger/polycam.md) og ta bilder hele veien rundt objektet. Sørg for godt lys og jevne bevegelser.
3. Send skanningen til prosessering og eksporter den ferdige modellen i `.gltf` eller `.obj` format.
4. Følg [bruksanvisningen for Blender](../bruksanvisninger/blender_intro.md) til å importere 3D-modellen på PCen og inspisere overflaten og teksturen.

---

## 📝 Rapportoppgaver

> [!IMPORTANT]
> Svar på spørsmålene under i grupperapporten og illustrer svarene med skjermbilder av punktskyen i CloudCompare og 3D-modellen i Blender.

1. **Evaluering av Profesjonell Laserskanning**: 
   * Studer punktskyen fra FARO-laserskanneren i CloudCompare. Hvilke detaljer ble gjengitt med høy nøyaktighet?
   * Hvilke områder mangler punkter (såkalte "skyggeeffekter" eller hull i dataene)? Forklar hvorfor disse hullene oppstår.
2. **Evaluering av Mobilskanning**:
   * Studer 3D-modellen fra Polycam i Blender. Hvordan ser overflatestrukturen (geometrien) ut sammenlignet med teksturen (bildet lagt oppå)?
   * Hvilke feil (f.eks. ujevnheter, sammensmeltede detaljer eller "smelta" geometri) oppstår i modellen, og hva kan være årsaken til disse?
3. **Komparativ Analyse**:
   * Sammenlign terrestrisk laserskanning (FARO) med mobilbasert fotogrammetri (Polycam). 
   * Lag en tabell som oppsummerer fordeler og ulemper ved de to metodene med tanke på: nøyaktighet, utstyrskostnad, tidsbruk i felt, prosesseringstid, og brukervennlighet.
