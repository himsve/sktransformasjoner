---
layout: page
title: Transformasjon med EPSG-koder
---

Transformasjonene og referanserammene i Proj følger kodene i EPSG-registeret. EPSG-registeret er administrert av IOGP (International Association of Oil & Gas Producers) og fungerer som en "de facto standard" vedrørende transformasjoner og referanserammer.

Transformasjoner med EPSG-koder er en enkel og anbefalt alternativ metodikk. Brukeren og systemene trenger da bare forholde seg til kodene som er gitt for referanserammene og transformasjonene.


## Norske ref.rammer/koordinatsystemer støtta av Proj

| Namn ref.rammer         | Autoritet | Kode        | Merknad      |
| ----------------------- | --------- | ----------- | ------------ |
| ETRS89 geogr. NN2000    | EPSG      | 5942        |              |
| ETRS89 2D geogr.        | EPSG      | 4258        |              |
| ETRS89 3D geogr.        | EPSG      | 4937        |              |
| ETRS89 geosentrisk      | EPSG      | 4936        |              |
| ETRS89 UTM 31-36 2D     | EPSG      | 25831-25836 |              |
| ETRS89 UTM 31-36 NN54   | EPSG      | 6171-6176   |              |
| ETRS89 UTM 31-36 NN2000 | EPSG      | 5971-5976   |              |
| ETRS89 NTM 5-30 2D      | EPSG      | 5105-5130   |              |
| ETRS89 NTM 5-30 NN54    | EPSG      | 6145-6170   |              |
| ETRS89 NTM 5-30 NN2000  | EPSG      | 5945-5970   |              |
| NN2000                  | EPSG      | 5941        |              |
| NN54                    | EPSG      | 5776        |              |
| CD Norway Depth         | EPSG      | 9672        | Under arbeid |
| NGO48 geografisk 2D     | EPSG      | 4273        |              |
| NGO48 akse I-VIII       | EPSG      | 27391-27398 |              |
| ITRF2014 geosentrisk    | EPSG      | 7789        |              |
| ITRF2014 geogr. 2D      | EPSG      | 9000        |              |
| ITRF2014 geogr. 3D      | EPSG      | 7912        |              |
| ED50                    | EPSG      | 4230        | Under arbeid |
| ED50 UTM 31-36 2D       | EPSG      | 23031-23036 | Under arbeid |


### Tilgjengelig transformasjoner (eksempler)

| Transformasjon                            | Fra autoritet | Fra kode | Til autoritet | Til kode | Autoritet - area | Kode - area |
| ----------------------------------------- | ------------- | -------- | ------------- | -------- | ---------------- | ----------- |
| ETRS89 geogr. ell <> ETRS89 geogr. NN54   | EPSG          | 4258     | EPSG          | 5776     |                  |             |
| ETRS89 geogr. ell <> ETRS89 geogr. NN2000 | EPSG          | 4258     | EPSG          | 5941     |                  |             |
| ETRS89 geos. <> ITRF2014 geos.            | EPSG          | 4936     | EPSG          | 7789     | EPSG             | 1352        |
| ETRS89 UTM32 <> NGO48 III                 | EPSG          | 25831    | EPSG          | 27391    |                  |             |


### Benchmarktesting av punkter med Proj

I tabellen nedenfor vilkårlige punkter transformert i Proj med EPSG-koder på fra- og til-koordinatsystemet. Resultatet her kan gjerne brukes ved enhetstesting ved bruk av Proj.

| Fra kode   | Til kode   | Input X/lon/E  | Input Y/lat/N | Input Z/h/H    | Epoke    | Output X/lon/E  | Output Y/lat/N  | Output Z/h/H    | Områdekode |
| ---------- | ---------- | -------------- | ------------- | -------------- | -------- | --------------- | --------------- | ----------------| ---------- | 
|  EPSG:7789 |  EPSG:4936 |  1874722.01378 |  912943.23060 |  6007499.79547 |  2020.00 |  1874722.639045 |   912942.995053 |  6007499.589109 |          - |
|  EPSG:4937 |  EPSG:4273 |         10.000 |        60.000 |              - |        - | 10.004772119609 | 59.999247563843 |               - |          - |
| EPSG:25832 | EPSG:27393 |     500000.000 |   6600000.000 |              - |        - |     -97197.1595 |     172511.9003 |               - |          - |
|  EPSG:4230 |  EPSG:4326 |         10.000 |        60.000 |              - |        - |  9.998594123185 | 59.999544266822 |               - |          - |
|  EPSG:4230 |  EPSG:4326 |          3.000 |        60.000 |              - |        - |  2.998327769141 | 59.999460761204 |               - |          - |
|  EPSG:4258 |  EPSG:5941 |         12.000 |        60.000 |        100.000 |        - |          12.000 |          60.000 |       64.266998 |          - |
|  EPSG:4937 |  EPSG:5776 |         12.000 |        60.000 |        100.000 |        - |          12.000 |          60.000 |       64.054001 |          - |
| EPSG:25832 |  EPSG:5972 |     500000.000 |   6600000.000 |        100.000 |        - |      500000.000 |     6600000.000 |       58.042431 |          - |
| EPSG:25832 |  EPSG:6172 |     500000.000 |   6600000.000 |        100.000 |        - |      500000.000 |     6600000.000 |       58.039824 |          - |
|  EPSG:4258 |  EPSG:4230 |         10.000 |        60.000 |              - |        - | 10.001392846773 | 60.000445365016 |               - |  EPSG:1182 |
|  EPSG:7912 |  EPSG:4937 |         10.000 |        60.000 |        100.000 |  2020.00 |  9.999991914885 | 59.999995109525 |       99.866247 |          - |
|  EPSG:7912 |  EPSG:4937 |         10.000 |        60.000 |        100.000 |  2010.00 |  9.999994722263 | 59.999996478159 |       99.913505 |          - |


#### Transformasjon ved standard installasjon av Proj

``cs2cs EPSG:7789 EPSG:4936 --area EPSG:1352``

I dette eksemplet initialiseres Proj til å transformere jordsentriske koordinater fra ITRF2014 til EUREF89. Opsjonen "--area" henviser til EPSG-koden på området transformasjonen skal gjelde for. EPSG:1352 som er brukt ovenfor, er koden for "Norway - onshore". Til sammenligning vil tilsvarende transformasjon for Danmark være:

``cs2cs EPSG:7789 EPSG:4936 --area EPSG:1080``
