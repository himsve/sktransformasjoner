---
layout: page
title: Brukerdefinerte transformasjoner
---

I stedet for transformasjoner med EPSG-koder har Proj stor fleksibilitet på å definere egne transformasjoner og konverteringer. Brukerdefinerte transformasjoner bygger på proj-kommandoen *cct*. En transformasjon med *cct* kan være et sett av flere operasjoner som er satt sammen i en *pipeline*.		


``cct +proj=*operation*...``		


## Eksempler på brukerdefinerte transformasjoner

I eksemplet nedenfor transformeres geografiske til jordsentriske koordinater:

``cct +proj=cart +ellps=GRS80``		


### Transformasjon med pipelines



### Basisoperasjoner i Proj


* helmert
	* 7-parameter Helmert-transformasjon. Eventuelt 14-parameter hvis hastigheter er definert.
	- "Den andre metoden"
* molobadekas
	* Molodensky-Badekas-transformasjon er en utvida 7-parameter Helmert-transformasjon med mulighet for å definere rotasjonspunktet for rx, ry og rz.
* molodensky
	* Molodensky-transformasjon i Proj er en transformasjon som består i parametrene $\delta x, $\delta y, $\delta z, $\delta a og $\delta b. $\delta a og $\delta a er forskjellen i stor og liten halvakse på kilde- og målkoordinatsystemet. 
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
	* Denne operasjonen interpolerer hastigheter fra griddet. Griddet kan være 1-, 2- eller 3-dimensjonalt. Men for å benytte denne operasjonen må man ha oppgitt epoken (tida) på målingen og epoken på koordinaten det skal transformeres til.
* defmodel
	* Ved denne operasjonen kan man korrigere for deformasjoner innen et gitt området. Korreksjoner kan være aktuelt i områder som for eksempel er utsatt for jordskjelv eller jordras. Metadata for operasjonen er gitt i json og korreksjonsdata på GeoTiff.
* horner
	* I "horner" kan man legge inn parametre for Horner polynom, også kallt multipple regresjonligninger. Operasjonen er opprinnelig brukt i den forelda Nordsjøformelen, en transformasjon mellom ED50 og WGS84 i Nordsjøområdet.

#### Konverteringer

* cart
	 * Denne operasjonen konverterer fra geodetiske koordinater til jordsentriske koordinater. Ved å legge til "+inv" i operasjonen går transformasjonen motsatt vei.
* geoc
	 * Konverterer fra geodetisk breddegrad til jordsentrisk breddegrad
* topocentric
	 * Ved "topocentic" blir jordsentriske koordinater konvertert til topsentriske koordinater. Origo for det toposentriske koordinatsystemet må være oppgitt.
* unitconvert
	 * Innebærer konvertering av input- og outputkoordinater til ulike enheter.
* axisswap
	 * Ved denne operasjonen kan man swappe rekkefølgen på koordinatverdier

#### Konvertering til projeksjoner

Proj har støtte for en mengde ulike projeksjoner. I norske områder bruker for det meste UTM-, TM- eller Mercatorprojeksjoner.

* utm
	 * Ved denne operasjonen kan man transformere til UTM-soner (01-60) fra geografiske koordinater. Ellipsoiden er være oppgitt. 
* tmerc
	 * Ved "tmerc" kan man definere transversale mercatorprojeksjoner.		
	
	Eksempel med "tmerc"; Konvertering fra geografiske koordinater til NGO48 III:
	``+proj=tmerc +lat_0=58.0 +lon_0=10.72291666666666667 +a=6377492.0176 +rf=299.15281285``	 
* merc
	 * "merc" er standard Merkatorprojeksjon. Et eksempel på dette er WGS84 / World Mercator
