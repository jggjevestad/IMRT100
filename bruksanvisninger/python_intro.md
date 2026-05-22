(python_intro)=
# Introduksjon til Python

## Hva er Python?

Python er et gratis og åpen kildekode-programmeringsspråk som er kjent for sin enkle
og lesbare syntaks. Det brukes i alt fra dataanalyse og automatisering til web-utvikling
og kunstig intelligens – og er et av de mest populære programmeringsspråkene i verden.

For geomatikk og landmåling er Python spesielt nyttig fordi:

- **QGIS** har innebygd Python-støtte og kan automatiseres med Python-skript
- **Databehandling** av GPS-data, koordinater og målinger kan effektiviseres
- Mange fagbiblioteker finnes for romlig analyse, f.eks. `geopandas` og `shapely`

## Installere Python

- **Windows / macOS:** Last ned fra [python.org/downloads](https://www.python.org/downloads/)
- **Linux:** Python er ofte forhåndsinstallert; sjekk med `python3 --version` i terminalen

Vi anbefaler å bruke **Visual Studio Code** som editor, med offisiell Python-utvidelse installert.

## Kjøre Python

Du kan bruke Python på to måter:

**Interaktiv modus** – skriv `python3` i terminalen for å få en live-konsoll:
```python
>>> 2 + 2
4
>>> print("Hei verden!")
Hei verden!
```

**Skriptfil** – lagre kode i en `.py`-fil og kjør med `python3 filnavn.py`.

## Grunnleggende syntaks

### Tall og regneoperasjoner

Python støtter alle vanlige regneoperasjoner:

```python
>>> 10 + 3
13
>>> 10 - 3
7
>>> 10 * 3
30
>>> 10 / 3        # divisjon gir alltid desimaltall
3.3333333333333335
>>> 10 // 3       # heltallsdivisjon
3
>>> 10 % 3        # rest etter divisjon
1
>>> 2 ** 8        # potens (2 opphøyd i 8)
256
```

Variabler trenger ingen typedeklarasjon – du bare tildeler en verdi:

```python
bredde = 20
hoyde = 5
areal = bredde * hoyde
print(areal)      # 100
```

### Tekst (strenger)

Tekst skrives med enkle eller doble anførselstegn:

```python
navn = "Stavanger"
melding = 'Hei fra ' + navn
print(melding)    # Hei fra Stavanger
```

Nyttige strengoperasjoner:

```python
tekst = "Python"
print(len(tekst))     # 6  – antall tegn
print(tekst[0])       # P  – første tegn (0-indeksert)
print(tekst[-1])      # n  – siste tegn
print(tekst[0:3])     # Pyt – utsnitt (slicing)
print(tekst.upper())  # PYTHON
print(tekst.lower())  # python
```

Formaterte strenger (`f-strings`) er den enkleste måten å sette inn variabler i tekst:

```python
nord = 6543210.5
ost = 432100.3
print(f"Nord: {nord:.2f}, Øst: {ost:.2f}")
# Nord: 6543210.50, Øst: 432100.30
```

### Lister

En liste holder flere verdier i én variabel:

```python
koordinater = [6543210.5, 6543211.2, 6543209.8, 6543210.1]
print(koordinater[0])    # 6543210.5 – første element
print(koordinater[-1])   # 6543210.1 – siste element
print(len(koordinater))  # 4 – antall elementer
```

Lister er *muterbare* – du kan endre, legge til og fjerne elementer:

```python
malepunkter = ["PP01", "PP02", "PP03"]
malepunkter.append("PP04")       # legg til på slutten
malepunkter[0] = "Referansepunkt"
print(malepunkter)
# ['Referansepunkt', 'PP02', 'PP03', 'PP04']
```

## Kontrollflyt

### if-setninger

```python
noyaktighet = 0.03  # meter

if noyaktighet < 0.02:
    print("Meget god nøyaktighet")
elif noyaktighet < 0.05:
    print("Akseptabel nøyaktighet")
else:
    print("Dårlig nøyaktighet – mål på nytt")
```

### for-løkker

Iterer over en liste eller et tallområde:

```python
malepunkter = ["PP01", "PP02", "PP03"]
for punkt in malepunkter:
    print(f"Behandler {punkt}")
```

```python
for i in range(5):   # 0, 1, 2, 3, 4
    print(i)
```

### while-løkker

```python
teller = 0
while teller < 3:
    print(f"Måling {teller + 1}")
    teller += 1
```

## Funksjoner

Funksjoner lar deg gjenbruke kode:

```python
def beregn_gjennomsnitt(verdier):
    return sum(verdier) / len(verdier)

nord_maelinger = [6543210.5, 6543211.2, 6543209.8, 6543210.1]
snitt = beregn_gjennomsnitt(nord_maelinger)
print(f"Gjennomsnitt nord: {snitt:.3f} m")
# Gjennomsnitt nord: 6543210.400 m
```

Funksjoner kan ha standardverdier for parametre:

```python
def skriv_koordinat(nord, ost, epsg=25832):
    print(f"N: {nord:.3f}  Ø: {ost:.3f}  (EPSG:{epsg})")

skriv_koordinat(6543210.4, 432100.3)
skriv_koordinat(6543210.4, 432100.3, epsg=4326)
```

## Datatyper

| Type | Eksempel | Beskrivelse |
|------|----------|-------------|
| `int` | `42` | Heltall |
| `float` | `3.14` | Desimaltall |
| `str` | `"tekst"` | Tekst |
| `bool` | `True` / `False` | Sann/usann |
| `list` | `[1, 2, 3]` | Muterbar sekvens |
| `tuple` | `(1, 2, 3)` | Umuterbar sekvens |
| `dict` | `{"navn": "PP01"}` | Nøkkel–verdi-par |

Sjekk typen til en variabel med `type()`:

```python
x = 6543210.5
print(type(x))   # <class 'float'>
```

## Dictionaries

Dictionaries er nyttige for å lagre strukturerte data:

```python
punkt = {
    "id": "PP01",
    "nord": 6543210.4,
    "ost": 432100.3,
    "hoyde": 42.15
}

print(punkt["id"])    # PP01
print(punkt["nord"])  # 6543210.4

# Legg til nytt felt
punkt["kvalitet"] = "god"
```

## Lese og skrive filer

Lese en tekstfil linje for linje:

```python
with open("maelinger.txt", "r") as fil:
    for linje in fil:
        print(linje.strip())
```

Skrive til fil:

```python
with open("resultat.txt", "w") as fil:
    fil.write("Nord: 6543210.400\n")
    fil.write("Øst: 432100.300\n")
```

## Feilhåndtering

Bruk `try`/`except` for å håndtere feil uten at programmet krasjer:

```python
try:
    verdi = float(input("Skriv inn koordinat: "))
    print(f"Du skrev: {verdi:.3f}")
except ValueError:
    print("Ugyldig inndata – forventet et tall")
```

## Ferdige skript

Her er to ferdige skript som er nyttige i faget. Kopier koden inn i en ny `.py`-fil
og kjør den med `python3 filnavn.py`.

Begge skriptene bruker biblioteket `numpy`. Installer det én gang med:

```
pip install numpy
```

---

### Omregning av vinkelmål

Konverterer mellom grader, radianer og gon (nygrad).

```python
from numpy import pi

def deg2rad(deg):
    return deg * (pi / 180)

def rad2deg(rad):
    return rad * (180 / pi)

def grad2deg(grad):
    return grad * (360 / 400)

def deg2grad(deg):
    return deg * (400 / 360)


# --- Test ---
deg = 90

rad = deg2rad(deg)
print(f"{deg:.5f} grader  =  {rad:.7f} radianer")

grad = deg2grad(deg)
print(f"{deg:.5f} grader  =  {grad:.5f} gon")
```

**Forventet utskrift:**
```
90.00000 grader  =  1.5707963 radianer
90.00000 grader  =  100.00000 gon
```

---

### Gjennomsnitt og standardavvik fra CSV

Leser inn en CSV-fil med koordinater og beregner gjennomsnitt og standardavvik
for øst- og nordverdiene. Tilpass variablene `csv_file`, `easting` og `northing`
til din fil.

```python
import csv
from numpy import mean, std, array

# Tilpass disse til din fil
csv_file = 'data.csv'   # filnavn
easting  = 0            # kolonnenummer for øst (0 = første kolonne)
northing = 1            # kolonnenummer for nord

def read_csv(file_name):
    with open(file_name, 'r') as file:
        reader = csv.reader(file)
        next(reader)            # hopp over overskriftsrad
        data = array(list(reader))
    return data

def compute_mean(data):
    coords = data[:, [easting, northing]].astype(float)
    return mean(coords, axis=0)

def compute_std(data):
    coords = data[:, [easting, northing]].astype(float)
    return std(coords, axis=0)


# --- Test ---
data = read_csv(csv_file)
snitt = compute_mean(data)
avvik = compute_std(data)

print(f"Gjennomsnitt  –  Øst: {snitt[0]:.3f} m   Nord: {snitt[1]:.3f} m")
print(f"Standardavvik –  Øst: {avvik[0]:.3f} m   Nord: {avvik[1]:.3f} m")
```

**Forventet utskrift (med eksempeldata):**
```
Gjennomsnitt  –  Øst: 600012.283 m   Nord: 6615537.482 m
Standardavvik –  Øst: 1.225 m        Nord: 1.397 m
```

---

## Videre læring

- [Offisiell Python-tutorial](https://docs.python.org/3/tutorial/)
- [Python-dokumentasjon](https://docs.python.org/3/)
- [Real Python](https://realpython.com/) – praktiske artikler og videoer

I IMRT100 bruker vi Python primært til å automatisere databehandling og arbeide med
koordinatfiler. Grunnleggende forståelse av variabeltyper, løkker og funksjoner
er tilstrekkelig for de fleste oppgavene.
