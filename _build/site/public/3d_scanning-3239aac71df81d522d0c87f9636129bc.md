(3d_scan_mobil)=
# 3D Skanning

De siste årene har 3D skanning gjort det mulig å lage detaljerte 3D modeller av virkeligheten på veldig kort tid. Det finnes forskjellige metoder og utstyr for dette. I denne oppgaven skal dere sammenligne resultatet fra en app på mobilen mot en kommersiell laserskanner.

```{image} ../bilder/frukt.png
:alt: Fruktkurv, digitalisert
:class: mb-1
:width: 600px
:align: center
```

## FARO 3D skanner

Det blir en felles demo med FARO skanneren. Etterpå legges 3D modellen ut på canvas.
Dette er en liten og enkel laserskanner som kostet ca. 500 000kr ny. Den fungerer ved å finne avstand og vinkel til en haug med punkt som den samler i en punktsky.

For å åpne punktskyen på PCen deres trenger dere [CloudCompare](https://www.cloudcompare.org/), som dere også brukte til å lese inn punktskyen over tuntreet.

**Last inn punktskyen i CloudCompare og se dere rundt**

## 3D-skanning på mobilen

Laserskanning er ikke eneste muligheten for 3d skanning. En annen teknikk heter [fotogrammetri](https://snl.no/fotogrammetri). I fotogrammetri bruker man mange vanlige bilder av motivet fra forskjellige vinkler til å finne dybdeinformasjon. En moderne smarttelefon har i tillegg sensorer som gyroskop og akselerometer som gjør det mulig å, rimelig presist, finne ut hvor telefonen beveger seg mens bildene tas.

Å prosessere så mye data krever mye tallknusing, så for å få lagd 3d modellen må dataen fra smarttelefonen sendes til en server for å bli prosessert. Dette er dyrt så det finnes per nå ingen gratis apper med åpen kildekode som kan gjøre det. Polycam er derimot en proprietær app med en gratisversjon som funker bra.

**Bruk PolyCam til å skanne noe av det samme som ble skanna med Faro skanneren. [Se bruksanvisning](../bruksanvisninger/polycam.md).**
**Last inn 3d modellen i blender og se dere rundt**

## Spørsmål
1. Se på punktskyen fra laserskanneren. Hva ble bra og hva ble dårlig? Prøv å svar på hvorfor
2. Se på 3d modellen fra mobilen. Hva ble bra og hva ble dårlig? Prøv å svar på hvorfor
3. Sammenlign laserskanninga med 3d modellen fra mobilen. Hva er styrker og svakheter til de to metodene?
