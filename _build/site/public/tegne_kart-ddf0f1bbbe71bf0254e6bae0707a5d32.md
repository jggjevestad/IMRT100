(tegne_kart)=
# Tegn ditt eget kart

I denne oppgaven skal dere gå tilbake til kartografiens røtter og lage en analog kartskisse over en valgt del av NMBU-campus uten bruk av digitale verktøy eller GPS. Deretter skal dere georeferere skissen i QGIS.

<div class="geo-dashboard">
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">📍 Lokasjon</span>
    <span class="geo-dashboard-value">Valgfritt område på Campus (f.eks. TF-plassen)</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">🛠️ Utstyr</span>
    <span class="geo-dashboard-value">A4-papir, blyant, fargestifter, målebånd, kompass</span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">💻 Programvare</span>
    <span class="geo-dashboard-value">Mobilkamera / Scanner, <a href="../bruksanvisninger/qgis_intro.html">QGIS</a></span>
  </div>
  <div class="geo-dashboard-item">
    <span class="geo-dashboard-label">⏱️ Tidsestimat</span>
    <span class="geo-dashboard-value">4 - 6 timer</span>
  </div>
</div>

```{image} ../bilder/tegne_kart.jpg
:alt: tegne kart
:class: bg-primary mb-1
:width: 600px
:align: center
```

---

## 🎯 Introduksjon
Før satellitter og luftfotos digitaliserte kartfaget, ble kart tegnet for hånd basert på manuelle målinger i felt. Denne oppgaven vil trene opp ditt romlige blikk og gi deg en dypere forståelse av målestokk, kartprojeksjoner, kompassretninger og passpunkter.

---

## 🛠️ Forberedelser
* Ta med tegnesaker (A4-ark, blyant, viskelær, gjerne farger).
* Lån kompass og målebånd fra veilederne om dere ikke har dette selv.
* Finn ut hvem på gruppa som har kalibrert skrittlengde (se feltmetode under).

---

## 🏃‍♂️ Gjennomføring

### 1. Områdevalg
Velg et avgrenset område på campus (f.eks. parken rundt Studentenes Hus, TF-plassen eller området rundt en av dammene). Ytterpunktene for kartleggingen bør være tydelig definert i gruppa.

### 2. Oppmåling i felt
* **Kalibrering av skritt**: Gå en kjent avstand (f.eks. 100 meter markert ved TF-bygget) tre ganger. Tell skrittene dine og beregn din gjennomsnittlige skrittlengde (avstand / antall skritt).
* **Avstandsmåling**: Mål opp de viktigste objektene (bygningsfasader, veibredder, gangstier) ved å telle skritt eller bruke målebånd.
* **Retningsbestemmelse**: Bruk kompasset til å lese av retninger i grader (0–360° der nord = 0°) langs vegger og stier.

### 3. Tegne feltskisse og ferdigstillelse
Tegn en grov skisse mens dere er ute i felt. Noter målte avstander og vinkler direkte på tegningen.
Når dere er tilbake, rentegner dere kartet på et nytt ark. Sørg for at følgende kartografiske elementer er med:
* **Nordpil**: Som viser retning mot nord.
* **Målestokk**: (F.eks. 1:500 eller linjalmålestokk).
* **Tegnforklaring (tegnforklaring)**: Definer farger og symboler.
* **Tittel & Dato**: Hva viser kartet, hvem har laget det, og når?

### 4. Digitalisering og georeferering
For å plassere papirkartet deres i et ekte koordinatsystem:
1. Skann eller ta et høyoppløselig og flatt bilde av kartet deres.
2. Følg [bruksanvisningen for georeferering](../bruksanvisninger/qgis_georef.md) i QGIS.
3. Bruk koordinatsystemet **ETRS89 / UTM sone 32N (EPSG:25832)** og finn minst 4 felles passpunkter mellom kartskissen og det offisielle bakgrunnskartet (f.eks. hushjørner).

---

## 📝 Rapportoppgaver

> [!IMPORTANT]
> Svar på følgende spørsmål i grupperapporten og legg ved både bilde av den originale papirskissen og det georefererte kartet lagt over satellittbilde i QGIS.

1. **Metodebeskrivelse**: Hvordan gikk dere frem for å måle opp området manuelt? Hvordan kalibrerte dere skrittlengden?
2. **Kartografiske valg**: Hvilke symboler og farger valgte dere for de ulike objektene, og hvorfor?
3. **Erfaring**: Hva fungerte bra med den analoge oppmålingen, og hva var de største feilkildene? Hvordan var det å kartlegge uten digitale verktøy?
4. **Resultat**: Legg ved en PDF eller et bilde av det ferdige, georefererte kartet deres i QGIS over et flybilde. Hvor godt passet tegningen deres med virkeligheten?
