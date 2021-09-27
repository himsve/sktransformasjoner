# Ressursfiler i Proj

Kopier alle filene i [public](public/) til den lokale ressursmappe di. Ressursmappa vil variere avhengig av korleis Proj er installert.

### Public

Filer som allerede er publisert av Kartverket og NKG i [proj-data](https://github.com/OSGeo/PROJ-data) på [https://cdn.proj.org/](https://cdn.proj.org/)

### Private

Kartverket sine private ressursfiler. Filene er kan vere under arbeid.


### Innhald

| Fil                                  | Beskrivelse                         |
| ------------------------------------ | ----------------------------------- |
| eur_nkg_nkgrf03vel_realigned.tif     | NKGRF03 bevegelsesmodel             |
| eur_nkg_nkgrf17vel.tif               | NKGRF17 bevegelsesmodel             |
| no_kv_ETRS89NO_NGO48_TIN.json        | TIN translasjonsmodell ETRS89-NGO48 |
| no_kv_href2008a.tif                  | NN1954 høgdereferansemodell         |
| no_kv_HREF2018B_NN2000_EUREF89.tif   | NN2000 høgdereferansemodell         |
| no_kv_NKGETRF14_EPSG7922_2000.tif    | Korreksjonsgridd ITRF14-ETRS89      |
| no_kv_CD_above_Ell_ETRS89_v2021a.tif | Separasjonsgridd ETRS89-Sjøkartnull |
| NNTrans2018B.tif                     | Separasjonsgridd NN2000-NN54        |

### Norske ref.rammer/koordinatsystemer støtta av Proj

| Namn ref.rammer         | Autoritet | Kode        | Merkad       |
| ----------------------- | --------- | ----------- | ------------ |
| ETRS89 2D geogr.        | EPSG      | 4258        |              |
| ETRS89 geosentrisk      | EPSG      | 4936        |              |
| ETRS89 3D geogr.        | EPSG      | 4937        |              |
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


### Tilgjengeleg transformasjonar (eksempler)

| Transformasjon                            | Fra autoritet | Fra kode | Til autoritet | Til kode | Autoritet - area | Kode - area |
| ----------------------------------------- | ------------- | -------- | ------------- | -------- | ---------------- | ----------- |
| ETRS89 geogr. ell <> ETRS89 geogr. NN54   | EPSG          | 4258     | EPSG          | 5776     |                  |             |
| ETRS89 geogr. ell <> ETRS89 geogr. NN2000 | EPSG          | 4258     | EPSG          | 5941     |                  |             |
| ETRS89 geos. <> ITRF2014 geos.            | EPSG          | 4936     | EPSG          | 7789     | EPSG             | 1352        |
| ETRS89 UTM32 <> NGO48 III                 | EPSG          | 25831    | EPSG          | 27391    |                  |             |


### Benchmarks fra Proj

| Fra autoritet | Fra kode | Til autoritet | Til kode | Input X/lon/E  | Input Y/lat/N | Input Z/h/H    | Epoke    | Output X/lon/E  | Output Y/lat/N  | Output Z/h/H    |
| ------------- | -------- | ------------- | -------- | -------------- | ------------- | -------------- | -------- | --------------- | --------------- | ----------------|
| EPSG          | 7789     | EPSG          | 4936     |  1874722.01378 |  912943.23060 |  6007499.79547 |  2020.00 |  1874722.639045 |   912942.995053 |  6007499.589109 |
| EPSG          | 4937     | EPSG          | 4273     |         10.000 |        60.000 |              - |        - | 10.004772119609 | 59.999247563843 |               - |
| EPSG          | 4230     | EPSG          | 4258     |         10.000 |        60.000 |              - |        - |  9.998607125889 | 59.999554603379 |               - |
| EPSG          | 4230     | EPSG          | 4258     |          3.000 |        60.000 |              - |        - |  2.998386934850 | 59.999479948945 |               - |
| EPSG          | 4258     | EPSG          | 5941     |         12.000 |        60.000 |        100.000 |        - |          12.000 |          60.000 |       64.266998 |
| EPSG          | 4937     | EPSG          | 5776     |         12.000 |        60.000 |        100.000 |        - |          12.000 |          60.000 |       64.054001 |
| EPSG          | 25832    | EPSG          | 5972     |     500000.000 |   6600000.000 |        100.000 |        - |      500000.000 |     6600000.000 |       58.042431 |
| EPSG          | 25832    | EPSG          | 6172     |     500000.000 |   6600000.000 |        100.000 |        - |      500000.000 |     6600000.000 |       58.039824 |


### Transformasjon med EPSG-kodar

#### Transformasjon ved standard installasjon av Proj

``cs2cs EPSG:7789 EPSG:4936 --area EPSG:1352`` 

