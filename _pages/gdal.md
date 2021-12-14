---
layout: page
title: GDAL
---

GDAL er et "open source"-bibliotek for rasteroperasjoner.  

* [Nettside](https://gdal.org/)
* [Gdal på Github](https://github.com/OSGeo/gdal)

### Installasjon av GDAL med Conda

> conda create --name gdal \
> conda activate gdal \
> conda install -c conda-forge gda

### Transformasjon av enkeltpunkter med GDAL

> gdaltransform -s_srs EPSG:7912 -t_srs EPSG:4937 \
Enter X Y [Z [T]] values separated by space, and press Return. \
10 60 100 2020 \
9.99999191488498 59.9999951095245 99.86624677293

### Transformasjon av raster

> gdalwarp -s_srs EPSG:25833 -t_srs EPSG:25832 input.tif output.tif
