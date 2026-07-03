(qgis_wms)=
# Koble til karttjenester (WMS/WMTS) i QGIS

Denne brukerveiledningen viser hvordan du kobler QGIS til eksterne karttjenester (WMS/WMTS) for å streame bakgrunnskart, flybilder og historiske kart direkte over internett, uten å måtte laste ned filene lokalt.

---

## 📋 Oversikt
* **WMS (Web Map Service)** sender kartet fra serveren som et ferdig generert bilde (f.eks. PNG eller JPG) tilpasset ditt kartutsnitt og målestokk.
* **WMTS (Web Map Tile Service)** er en raskere variant der kartet er ferdig delt opp i kvadratiske bilder (fliser/tiles) på faste målestokksnivåer. Dette gjør at kartet laster mye raskere ved panorering og zoom.

Karttjenester gjør det mulig å bruke Kartverkets offisielle kart og historiske amtskart som bakgrunnsreferanse direkte i dine egne QGIS-prosjekter.

---

## 🔧 Steg-for-steg bruksanvisning

### 1. Opprette en ny WMS-tilkobling
1. Åpne QGIS og gå til toppmenyen: **Lag (Layer)** -> **Legg til lag (Add Layer)** -> **Legg til WMS/WMTS-lag (Add WMS/WMTS Layer)** (eller trykk `Ctrl+L` og gå til *WMS/WMTS*-fanen).
2. Klikk på **Ny (New)**-knappen for å åpne tilkoblingsvinduet.
   ```{figure} ../bilder/qgis/wms/add_connection_wms.png
   :align: center
   ```

### 2. Koble til kartverkets historiske kart (WMS)
1. Fyll inn følgende detaljer i tilkoblingsvinduet:
   * **Navn**: `Historiske kart - Kartverket`
   * **URL**: `https://wms.geonorge.no/skwms1/wms.historiskekart`
2. La resten av innstillingene stå som standard og trykk **OK**.
3. Velg den nye tilkoblingen i rullegardinmenyen og klikk på **Koble til (Connect)**.
4. Det dukker opp en liste over tilgjengelige historiske lag:
   * **amt1**: Amtskart (detaljerte historiske fylkeskart fra 1800-tallet).
   * **rektangel**: Rektangelkart fra tidlig 1900-tall.
5. Velg laget **amt1** og trykk **Legg til (Add)**.
   ```{figure} ../bilder/qgis/wms/connection_wms.png
   :align: center
   ```

### 3. Koble til moderne bakgrunnskart (WMTS)
For å koble til det offisielle, raske Norgeskartet:
1. Opprett en **Ny** tilkobling.
2. Fyll inn:
   * **Navn**: `Norgeskart - Kartverket`
   * **URL**: `https://opencache.statkart.no/gatekeeper/gk/gk.open_wmts?service=WMTS&request=GetCapabilities`
3. Trykk **OK** og klikk **Koble til**.
4. Gå til fanen **WMTS** øverst i tabellen.
5. Velg **topo** (eller *norgeskart*) og trykk **Legg til**.

### 4. Sammenligne og blende lagene
1. Sørg for at det historiske kartet (`amt1`) ligger plassert **over** det moderne bakgrunnskartet (`topo`) i Lagpanelet.
2. Høyreklikk på `amt1`-laget -> **Egenskaper (Properties)** -> **Gjennomsiktighet (Opacity)**.
3. Sett den globale gjennomsiktigheten til ca. $50\ \%$ og trykk **OK**. Du kan nå se nøyaktig hvor veier og bygg har endret seg.

---

## 💡 Tips & feilsøking

* **Kartet laster ekstremt tregt**: WMS-tjenester laster kartet på nytt fra serveren hver gang du zoomer eller panorerer. Dersom nettilkoblingen er treg, bør du bruke **WMTS** (hvis tilgjengelig) i stedet for WMS, da dette er optimalisert for rask flisvisning.
* **Tilkobling mislykkes**: Dobbeltsjekk at det ikke er skrivefeil i URL-en (pass på at det ikke er ekstra mellomrom før eller etter lenken). Husk også at NMBU-nettet kan ha sperrer for enkelte tjenester, men Kartverkets tjenester er åpne.
* **Finner ikke tilkoblingen min**: Når du har lagt til en WMS/WMTS-tjeneste i QGIS, lagres den i programmet. Du trenger ikke å taste inn URL-en neste gang du åpner QGIS; bare klikk på rullegardinmenyen og velg navnet du lagret den under.
* **Flybilder**: For flybilder (ortofoto) kan du koble til Geonorges WMS-tjeneste for ortofoto:
  `https://wms.geonorge.no/skwms1/wms.bilde_ortofoto` og velge laget *ortofoto*.
