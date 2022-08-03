## Requirements

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
|  12 | [metadata links](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#metadata-elements-of-the-data-set) | 1 | [[PUB-1]] #rec_core_fc-md-descriptions  and  [[PUB-2]] #metadata-elements-of-the-data-set|

### OGC API Features Core

[OGC API Features Core](https://docs.opengeospatial.org/is/17-069r3/17-069r3.html), [[PUB-1]] describes the basic requirements (50)and recommendations (17) according to OGC that one needs to follow, undependend of INSPIRE. 
It is based on the [OpenAPI Specification 3.0](https://oai.github.io/Documentation/specification.html) and describes which paths can be used what responses one should receive.

### INPSIRE-MIF document: Setting up an INSPIRE Download service based on the OGC API-Features standard

[INPSIRE-MIF document: Setting up an INSPIRE Download service based on the OGC API-Features standard](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md), [[PUB-2]] describes the specific INSPIRE requirements.
Most of them are explained in the next chapters.

### Multilinguality

The [multilinguality requirement](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#82-requirements-class-inspire-multilinguality-), [[PUB-2]] is mandatory for all data sets that contain information in more than one natural language. This is mostly not the case in teh Netherlands, so it is of less importants.

### Predefined download



### GeoJSON

### Bulk download

### CRS ETRS89 and WGS84

### GML

### Dutch API design rules

### Describing encoding

### Filtering

### Metadata links

###	Relevant documentation 

Relevant documentation is shown in [appendix A](#references)


