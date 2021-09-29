# Brukerdefinerte transformasjoner i Proj

I stedet for transformasjoner med EPSG-koder har Proj stor fleksibilitet på å definere egne transformasjoner og konverteringer. En transformasjon kan være et sett av flere operasjoner som er satt sammen i en "pipeline".		


## Basisoperasjoner i Proj

#### Transformasjoner

* helmert
	* 7-parameter Helmert-transformasjon. Eventuelt 14-parameter hvis hastigheter er definert.
	- "Den andre metoden"
* molobadekas
	* Molodensky-Badekas-transformasjon er en utvida 7-parameter Helmert-transformasjon med mulighet for å definere rotasjonspunktet for rx, ry og rz.
* molodensky
	* Molodensky-transformasjon i Proj... TODO
* affine
	* Affin transformasjon i Proj følger standard 3D-affin transformasjon med 14 parametre
* hgridshift
	* Ved hgridshift kan man påføre plane translasjoner fra gridd med to kanaler
* vgridshift
	* Denne operasjonen korrigerer høyder med interpolasjon i gridd. For eksempel vertikal datumtransformasjon av ellipsoidiske høyder til NN2000 benytter denne operasjonen
* xyzgridshift
	* xyzgridshift korrigerer jordsentriske koordinater med translasjoner fra gridd med tre kanaler
* tinshift
	* tinshift-modell består av plane translasjoner linka sammen i en TIN-modell. Operasjonen egner seg godt hvis man har punkter i to ulike koordinatsystemer. For eksempel transformasjonen fra EUREF89 til NGO48 er implementert med denne operasjonen.
* deformation
	* 
* defmodel
* horner

#### Konverteringer

* cart
* geoc
* geocent
* topocentric
* unitconvert
* axisswap
-----
* utm
* tm


## Eksempler på brukerdefinerte transformasjoner

I eksemplet ovenfor transformeres geografiske til jordsentriske koordinater:

``cct +proj=cart +ellps=GRS80``		

### Transformasjon med pipelines

