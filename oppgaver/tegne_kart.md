(tegne_kart)=
# Tegn ditt eget kart

I denne oppgaven skal dere lage en kartskisse over en bygning eller et område på NMBU-campus uten å bruke digitale kart eller GPS.

```{image} ../bilder/tegne_kart.jpg
:alt: tegne kart
:class: bg-primary mb-1
:width: 600px
:align: center
```

Velg et område dere synes er interessant – det kan være Studentenes Hus, en av dammene eller et annet sted på campus. Tegn kartskissen på et A4-ark og bruk farger og symboler for å vise ulike typer objekter og områder.

## Gjennomføring

### 1. Velg et område
Velg et avgrenset område som ikke er for stort – et par hundre meter på hver side er passe. Diskuter i gruppen hva som er viktig å få med, og bli enige om hva som er ytterpunktene for kartleggingen.

### 2. Mål opp området

**Avstander** kan måles med:
- Skritt – tell antall skritt mellom to punkter. Kalibrér skrittlengden din ved å gå en kjent avstand (f.eks. 100 m langs en vei) og tell antall skritt.
- Målebånd – mer nøyaktig for korte avstander.

**Retninger** kan bestemmes med:
- Kompass – les av retningen i grader mellom to punkter (0–360°, med nord = 0°).
- Vinkelrett og parallell – mange bygninger og stier går enten parallelt eller vinkelrett på hverandre, noe som forenkler skissen.

Start med å måle opp de store linjene (vegger, veier, gjerder) og fyll inn detaljer etterpå.

### 3. Tegn feltskisse
Ta med papir og blyant ut i felt. Tegn løpende mens dere måler – ikke vent til dere er tilbake. Skriv på målte avstander og retninger direkte på skissen, så husker dere hva tallene betyr.

### 4. Tegn det ferdige kartet
Overfør feltskissen til et rent A4-ark. Et ferdig kart bør inneholde:
- **Nordpil** – vis hvilken retning som er nord.
- **Målestokk** – f.eks. 1:500 betyr at 1 cm på kartet tilsvarer 500 cm (5 m) i terrenget.
- **Tegnforklaring** – forklar hvilke symboler og farger dere har brukt.
- **Tittel** – hva viser kartet, og når ble det laget?

### 5. Georeferér kartet i QGIS

Når kartskissen er ferdig skal dere legge den inn i QGIS slik at den er plassert riktig i virkeligheten. Dette kalles **georeferering**.

1. Ta et godt bilde av kartskissen med mobiltelefonen, eller skann den.
2. Åpne QGIS og last inn bildet i georefereringsverktøyet.
3. Velg ut minst 4 passpunkter – punkter i skissen der dere vet de geografiske koordinatene (f.eks. hjørner av bygninger dere kan slå opp på [norgeskart.no](https://norgeskart.no)).
4. Sett koordinatsystem til **ETRS89 / UTM sone 32** og transformasjonstype til **Projektiv**.
5. Kjør georefereringen og kontrollér at kartet havner på riktig sted.

Se [bruksanvisning for georeferering](#qgis_georef) for steg-for-steg beskrivelse.



1. Hvordan gikk dere frem for å lage kartet?
2. Hvilke tegn og farger brukte dere, og hvorfor?
3. Hva fungerte bra, og hva var utfordrende?
4. Hvordan opplevde dere å kartlegge uten digitale hjelpemidler?
5. Hva lærte dere om området og om kartlegging gjennom denne oppgaven?
