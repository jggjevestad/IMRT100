---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---
(ressurs)=
# Ressurser


## Software

[Arduino IDE](https://www.arduino.cc) <br>
[QGIS](https://www.qgis.org) <br>
[Google Earth](https://www.google.com/earth/about/versions/) <br>
[Cloud Compare (CC)](https://www.cloudcompare.org) <br>
[Python](https://docs.anaconda.com/) <br>
[GPSBabel](https://www.gpsbabel.org) <br>


## Hardware

[Ultimate GPS breakout board](https://www.adafruit.com/product/746) <br>
[Arduino MKR GPS Shield](https://store.arduino.cc/products/arduino-mkr-gps-shield?gad_source=1&gclid=Cj0KCQjws560BhCuARIsAHMqE0GcMGz16OT4DQchmQGp525-Cedd_PwuvEVKaMn0l7sHR5FsAh52r7caAg2YEALw_wcB) <br>
[Arduino MKR 1000](https://store.arduino.cc/products/arduino-mkr1000-wifi?selectedStore=eu) <br>
[Arduino Uno](https://store.arduino.cc/products/arduino-uno-rev3) <br>


## Datakilder

[Norgeskart](https://www.norgeskart.no) <br>
[Norge i bilder](https://www.norgeibilder.no) <br>
[Høydedata](https://www.hoydedata.no) <br>
[Laserdata NMBU](https://eduumb-my.sharepoint.com/:f:/g/personal/jon_glenn_gjevestad_nmbu_no/EhZNW6vu5CFJrBjHd5rTwPIBmjrtvMEFTLuKKkfl9J7ECQ?e=rKvIFD)


## Fastmerker

[fastmerker.csv](fastmerker.csv)

```{code-cell} ipython3
:tags: [hide-input]
from shapely.geometry import Point
import geopandas
import pandas

df = pandas.read_csv("fastmerker.csv")
# Kolonnene får mellomromm i starten av navnet ¯\_(ツ)_/¯
geometry = geopandas.points_from_xy(df["     easting"], df["    northing"])
crs = {'init': 'epsg:25832'} #http://www.spatialreference.org/ref/epsg/25832/
geo_df = geopandas.GeoDataFrame(df, crs=crs, geometry=geometry)
geo_df.explore(marker_kwds=dict(radius=5, fill=True),
                color="red",
                popup=["name", "     easting", "    northing"])
```