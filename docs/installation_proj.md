# Installasjon av Proj

## Conda (Anaconda)

Conda er den mest anbefalte grensesnittet for installasjon av Proj. Conda (Anaconda) fungerer på Windows, Mac og de fleste Linux-varianter. Dessuten vil pakkene for Proj alltid være oppdatert til siste versjon ved installasjon via Conda.

Link til installasjon av Conda (Anaconda/Miniconda) på ulike plattformer:

https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html

> conda install -c conda-forge proj

Erfaringsvis kan man med denne kommandoen risikere å installere forelda versjonen av pakken.

Tilgjengelige versjoner kan søkes opp ved: 

> conda search proj

Hvis Proj-versjonene for kanalen "conda-forge" ikke er tilgjengelig kan man legge den til ved:

> conda config --add channels conda-forge

Installer så et spesifikt build- og versjonsnummer ved:

> conda install proj=<versjon>=<buildnummer>


### Proj-data

Proj er også avhengig av tilgang på ressursfiler for transformasjonene. Ekspempel på ressursfiler kan være griddfiler, json-filer og proj.db-databasen.



> conda install -c conda-forge proj-data



### Proj.db



## Docker

## Windows

## PyProj

## libproj

## Proj API

Proj har sitt eget interne API i C/C++ hvor deler av kildekoden i Proj er tatt med i API'et. 

[Referanse til C++-API i Proj](https://proj.org/development/reference/cpp/index.html)

## 
