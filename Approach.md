## Approach

### Approach step by step

The approach consisted of the following steps:

- establish requirements
- organize a High5 week with stakeholders in the week starting at June 21 2021
- Choose data sets (Dutch INSPIRE addresses and Statistical Units)
- Implement an OAPIF at the Geonovum testbed for OGC-API-Features
- start communication on Github 
- report to INSPIRE community
- organize presentations

###	Stakeholders

Stakeholders are:
- Geonovum as initiator and author of this document (https://www.geonovum.nl)
- PDOK (Publieke Dienstverlening op de Kaart, http://www.pdok.nl) as hosting organization for geoservices
- [Dutch Kadaster](https://www.kadaster.nl) and [Statistics Netherlands](https://www.cbs.nl/) as data providers

### Used tools

PDOK has used self developed software based on Go and PostgreSQL/Postgis. (https://github.com/PDOK/goaf).
At the Geonovum testbed for OGC-API-Features we chose for [Pygeoapi](https://pygeoapi.io/). 

### Used data

The test at PDOK used the As-is dataset for the addresses in a csv format. This data was mapped to GeoJSON with OGR modules in Goaf. This dataset was chosen, because a description of the GeoJSON encoding was already available at [[PUB-4]].
The harmonized data was not chosen, because it did not contain the actual addresses, but only a link. This is caused by the complexity of the INSPIRE model.


The test at the Geonovum testbed for OGC-API-Features used the WFS of the INSPIRE harmonized dataset for [Statistical Units](https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/e08079df-6c19-486e-916e-5c9948cfafea).
This dataset was chosen, because the harmonized WFS returns simple GML, so we had no problems with complex GML.

###	Requirements

The requirements are listed in detail in https://github.com/Geonovum/OAPIF-PDOK-INSPIRE/tree/main/requirements
Below the most relevant requirements are listed:

| nr | requirement | priority | reference | 
|----|---------|---------|------------------| 
|  1 | [OGC API Features Core](https://docs.opengeospatial.org/is/17-069r3/17-069r3.html) | 1 | [[PUB-1]] |
|  2 | [INPSIRE-MIF document: Setting up an INSPIRE Download service based on the OGC API-Features standard](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md) | 1 | [[PUB-2]] |
|  3 | [multilinguality](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#82-requirements-class-inspire-multilinguality-) | 3  | [[PUB-2]] #82-requirements-class-inspire-multilinguality- |
|  4 | [predefined download](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-pre-defined) | 1 | [[PUB-2]] #req-pre-defined |
|  5 | [GeoJSON](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-oapif-json) | 1 | [[PUB-2]] #req-oapif-json |
|  6 | [bulk download](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-bulk-download) | 1 | [[PUB-2]] #req-bulk-download  |
|  7 | [CRS ETRS89 and WGS84](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-crs) | 2  | [[PUB-5]] and [[PUB-2]] #req-crs |
|  8 | INSPIRE validated GML as [input](https://inspire.ec.europa.eu/validator/about/) and [output](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_requirements_class_geography_markup_language_gml_simple_features_profile_level_0) | 3  | https://inspire.ec.europa.eu/validator/about/ and [[PUB-1]] #_requirements_classes_for_encodings |
|  9 | [Dutch API design rules](https://www.geonovum.nl/over-geonovum/actueel/rest-api-design-rules-op-pas-toe-leg-uit-lijst) | 1 | [[PUB-3]] |
|  10 | [describing encoding](https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/geojson-encoding-rule.md#inspire-requirements-for-encoding-rules) | 1 | [[PUB-4]] |
|  11 | [filtering](https://docs.ogc.org/DRAFTS/19-079r1.html) | 2 | [[PUB-6]] |
|  12 | [metadata links](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#rec_core_fc-md-descriptions) | 1 | [[PUB-1]] #rec_core_fc-md-descriptions |


###	Relevant documentation 

Relevant documentation is shown in [appendix A](#references)


