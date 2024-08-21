(rebuslop)=
# Rebusløp på Campus

I dette rebusløpet skal dere gjennom 8 oppgaver finne frem til steder på Campus ved hjelp av målinger og enkel geometri. Når dere har funnet stedet, så skal dere dokumentere hvor dere mener det er ved å ta en selfie av hele gruppa. Til hver oppgave er det også et spørsmål som dere må finne frem til svaret på.

Lykke til!

**NB**: Før dere begynner på rebusløpet er det viktig at dere har lekt dere litt med Google Earth på forhånd og prøvd noen av funksjonene.


## Spørsmål 1 - En slags foss på en måte
Nede på NMBU Campus, skjult blant trærne og omfavnet av naturens ro, ligger en mystisk dam. Midt i denne dammen, som glitrer i sollyset og speiler himmelens skiftende farger, finnes en liten, bortgjemt øy. På denne øyen står et sjarmerende, gammelt hus, som ser ut som det er hentet rett ut av et eventyr. Huset, med sitt krokete tak, bærer på hemmeligheter fra en svunnen tid.

Vannet i dammen er ikke krystallklart, men renner stille ut i en bekk som slynger seg gjennom landskapet. Bekken, med sitt melodiske klukk, fører vannet videre til en bitte liten foss. Denne fossen, selv om den er liten, bruser med en kraft som kanskje kan høres dersom du legger godviljen til og skaper en følelse av eventyr og mystikk. 

```{image} ../bilder/foss.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 300px
:align: center
```

Spørsmål: Hva heter fossen?


## Spørsmål 2 - Transformasjon
I geomatikk bruker vi noen ganger ECEF koordinater istedenfor breddegrad og lengdegrad fordi de er enklere å gjøre beregninger med. Problemet med disse ECEF koordinatene er bare at det ikke er så helt enkelt å tolke hvor posisjonen er. Senere i studiet må dere programmere denne transformasjonen selv, men i dag  holder det å bruke denne [linken](https://www.sysense.com/products/ecef_lla_converter/index.html) for å transformere mellom disse to koordinattypene.

```{image} ../bilder/coordinates.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

Transformer ECEF koordinatene nedenfor til breddegrad og lengdegrad.

$$
\begin{align}
  X =& 3172519.24m\\
  Y =& 603401.31m\\
  Z =& 5481825.82m\\
\end{align}
$$

Spørsmål: Hvilket årstall?


## Spørsmål 3 - Uleselig
Du finner en lapp på bakken hvor noen har skrevet en posisjon med breddegrad og lengdegrad. Lappen er helt utvasket og du klarer såvidt å tyde tallene, men dessverre så er sekundene i lengdegraden blitt helt borte. Bygningen dere skal finne ligger midt imellom ytterpunktene til de mulige posisjonene.

```{image} ../bilder/note.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

$$
\begin{align}
  &N59^0 40' 01''\\
  &E10^0 46' xx''\\
\end{align}
$$

Spørsmål: Hvem holder til i dette bygget?


## Spørsmål 4 - En flat verden
Kartkoordinater blir ofte gitt i nord og øst når jordkloden er gjort flat med en kartprojeksjon.
Da er hele den krumme jordoverflaten brettet ut som et kart. Problemet er bare at avstander, vinkler eller
areal blir litt feil i forhold til virkeligheten - det er ikke mulig å bevare alt.

Kartsystemet EUREF89 UTM (Sone 32) er det som er vanligste i Norge.

```{image} ../bilder/map_projection.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

$$
\begin{align}
  N =& 6615465.09 m\\
  E =& 599443.63 m\\
\end{align}
$$

N koordinaten er antall meter fra ekvator, mens E er 500 000 pluss antall meter fra en bestemt
lengdegrad (9 grader øst i sone 32). Øst-koordinaten begynner på 500 000 for å unngå
negative tall.

Gå til disse UTM koordinatene, og dere vil finne et bygg med noe spesielt på taket.

Spørsmål: Hva heter bygget og hva tror dere dette bygget har vært brukt til?


## Spørsmål 5 - Rundt og rundt
Rundt om i Ås er det mange rundkjøringer. I tabellen nedenfor finner dere posisjonen til tre av dem. Stedet dere skal frem til er i skjæringspunktet mellom tre sirkler.

```{image} ../bilder/circles.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

Breddegrad|Lengdegrad|Radius
---:|---:|---:
$N59^0 39' 53.26''$|$E10^0 46' 21.48''$|$952m$
$N59^0 39' 59.95''$|$E10^0 48' 20.45''$|$2730m$
$N59^0 39' 53.37''$|$E10^0 45' 39.69''$|$454m$

Spørsmål: Hvor lang er den?


## Spørsmål 6 - Syn som en ørn
Du står ved Gaustadtoppen turisthytte ved Rjukan. Du har syn som en ørn og langt borte i det fjerne ser noe som ligner på en marmorblokk. Nysgjerrig som du er finner du frem kompasset og leser av en retning på $98.83^0$. Etter mye strev og nøye måling finner du tilslutt ut at avstanden er $120267m$.

```{image} ../bilder/mountain.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

Spørsmål: Hva heter skulpturen?


## Spørsmål 7 - A numbers game
Du er ute å går på Campus. Plutselig snubler du i et hull i bakken. Nede i hullet finner du en gammel Nokia mobiltelefon. Den siste som brukte telefonen hadde skrevet en SMS, men det eneste du kan se ser er rekkefølgen på tastene som ble trykket inn. Tallsekvensen finner du nedenfor.

```{image} ../bilder/nokia.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

`224445588223366`

**Hint**: Se f.eks. YouTube for hvordan man skriver SMS med tastaturet til en eldre Nokia mobiltelefon

Spørsmål: Hvor er dette?

## Spørsmål 8 - Google Plus Codes
Google Plus Codes er en åpen, enkel og konsistent adresseordning utviklet av Google. De er designet for å gi en adresse til ethvert sted på jorden, spesielt steder som ikke har en bestemt gateadresse.

```{image} ../bilder/google_plus.jpg
:alt: fishy
:class: bg-primary mb-1
:width: 600px
:align: center
```

En Google Plus Code er en serie av sifre og bokstaver, med et pluss-tegn (+) i mellom, som representerer et område på jorden. De første 4-6 tegnene angir et stort område, mens de siste 6 tegnene angir et mer spesifikt sted innenfor det store området. For eksempel representerer koden `9C4M8XJ6+2V` et spesifikt sted i Lagos, Nigeria.

For å bruke Google Plus Codes, kan du bare skrive inn koden i Google Maps søkefelt, akkurat som du ville skrevet inn en gateadresse. Dette vil umiddelbart ta deg til det nøyaktige stedet som koden representerer.

`9FFGMQ7F+GR`

Spørsmål: Hvor er dette?


