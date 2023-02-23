## Requirements

Below the most relevant requirements (or requirement classes) for setting up an INSPIRE OAPIF are listed:

| nr | requirement | priority | reference | 
|----|---------|---------|------------------| 
|  1 | [OGC API Features Core](https://docs.opengeospatial.org/is/17-069r4/17-069r4.html) | 1 | [[PUB-1]] |
|  2 | [INPSIRE-MIF document: Setting up an INSPIRE Download service based on the OGC API-Features standard](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md) | 1 | [[PUB-2]] |
|  3 | [multilinguality](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#82-requirements-class-inspire-multilinguality-) | 3  | [[PUB-2]] #82-requirements-class-inspire-multilinguality- |
|  4 | [predefined download](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-pre-defined) | 1 | [[PUB-2]] #req-pre-defined |
|  5 | [GeoJSON](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-oapif-json) | 1 | [[PUB-2]] #req-oapif-json |
|  6 | [bulk download](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-bulk-download) | 1 | [[PUB-2]] #req-bulk-download  |
|  7 | [CRS ETRS89 and WGS84](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-crs) | 2  | [[PUB-5]] and [[PUB-2]] #req-crs |
|  8 | INSPIRE validated GML as [input](https://inspire.ec.europa.eu/validator/about/) and [output](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_requirements_class_geography_markup_language_gml_simple_features_profile_level_2) | 3  | https://inspire.ec.europa.eu/validator/about/ and [[PUB-1]] #_requirements_classes_for_encodings |
|  9 | [Dutch API design rules](https://www.geonovum.nl/over-geonovum/actueel/rest-api-design-rules-op-pas-toe-leg-uit-lijst) | 1 | [[PUB-3]] |
|  10 | [describing encoding](https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/geojson-encoding-rule.md#inspire-requirements-for-encoding-rules) | 1 | [[PUB-4]] |
|  11 | [filtering](https://docs.ogc.org/DRAFTS/19-079r1.html) | 2 | [[PUB-6]] |
|  12 | [metadata links](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#metadata-elements-of-the-data-set) | 1 | [[PUB-1]] #rec_core_fc-md-descriptions  and  [[PUB-2]] #metadata-elements-of-the-data-set|

### OGC API Features Core

[OGC API Features Core](https://docs.opengeospatial.org/is/17-069r4/17-069r4.html), [[PUB-1]] describes the basic requirements (50) and recommendations (17) according to OGC that one needs to follow, independent of INSPIRE. 
It describes which paths can be used and what responses one should receive. 
It does not make the use of [OpenAPI Specification 3.0](https://oai.github.io/Documentation/specification.html) mandatory, but if it is used, it gives an extra [requirement class](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#rc_oas30).

There is a validation on the OGC standards for OAPIF available.

&nbsp;&nbsp;&nbsp;![INSPIRE Validator](media/INSPIRE_validator_OAPIF.png "Validation on the OGC standards for OAPIF")

### INPSIRE-MIF document: Setting up an INSPIRE Download service based on the OGC API-Features standard

[INPSIRE-MIF document: Setting up an INSPIRE Download service based on the OGC API-Features standard](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md), [[PUB-2]] describes the specific INSPIRE requirements.
Most of them are explained in the next chapters.
This document does propose in [Note 2](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#81-requirements-class-inspire-pre-defined-data-set-download-oapif--) to make it a mandatory requirement for INSPIRE to comply with [OAPIF requirements class OpenAPI 3.0.](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#rc_oas30)

### Multilinguality

The [multilinguality requirement class](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#82-requirements-class-inspire-multilinguality-), [[PUB-2]] is mandatory for all data sets that contain information in more than one natural language.
This is mostly not the case in the Netherlands, so it is of less importance.

### Predefined download

The [predefined download requirement class](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-pre-defined),[[PUB-2]] consists of 3 requirements for each collection to link to:
1. the metadata of the corresponding dataset
2. the corresponding entry in the [INSPIRE feature concept dictionary](https://inspire.ec.europa.eu/featureconcept)
3. the license

### GeoJSON

The [GeoJSON requirement class](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_requirements_class_geojson) in [[PUB-1]] recommends to support GeoJSON for features with geometry, but as stated in https://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_encodings, no encoding is mandatory. 
The [GeoJSON requirement class](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-oapif-json) in [[PUB-2]] also recommends to document how the GeoJSON encoding is retrieved from the INSPIRE data models.

### Bulk download

The [bulk download requirement class](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-bulk-download), [[PUB-2]] requires links for enclosure of the total data set and/or of each seperate collection.

### CRS ETRS89 and WGS84

The [CRS requirement](https://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_coordinate_reference_systems) in [[PUB-1]] requires [WGS84](http://www.opengis.net/def/crs/OGC/1.3/CRS84) for 2D-data and [WGS84h](http://www.opengis.net/def/crs/OGC/0/CRS84h) for 3D-data as default.
The [INSPIRE-CRS requirement class](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#req-crs) in [[PUB-2]] requires also one of the INSPIRE CRS's based on ETRS89 to be supported
The [OGC API - Features - Part 2 standard](http://docs.opengeospatial.org/is/18-058r1/18-058r1.html), [[PUB-5]] prescribes how to support different coordinate systems with OAPIF.

For the Dutch data providers, it is recommended to also support [RD](https://www.opengis.net/def/crs/EPSG/0/28992) for 2D data or [RD +NAP](https://www.opengis.net/def/crs/EPSG/0/7415) for 3D data. See also: https://docs.geostandaarden.nl/crs/crs. 

### GML
The use of GML as encoding for INSPIRE data can be considered in two ways. As input and as output.

When we consider the input, one would like to be able to use a source dataset of harmonized data. In most cases, this will be a GML encoded dataset. 
The GML encoding is at least needed to validate the data set with the [EU INSPIRE  validator](https://inspire.ec.europa.eu/validator/about/)
Unfortunately, not many tooling for creating a OAPIF service is able to use GML as input. Especially when it concerns a complex GML dataset. So, a transformation to another encoding like GeoJSON is needed.

Output of GML from the OAPIF service can only be in simple features [level 0](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_requirements_class_geography_markup_language_gml_simple_features_profile_level_0) and [level 2](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_requirements_class_geography_markup_language_gml_simple_features_profile_level_2).
So no complex features will be supported.

### Dutch API design rules

Dutch data providers are recommended to follow the [Dutch API design rules](https://www.geonovum.nl/over-geonovum/actueel/rest-api-design-rules-op-pas-toe-leg-uit-lijst), [[PUB-3]]. This is not an INSPIRE requirement.

### Describing encoding

The standards considered in this guideline do not set a specific encoding as mandatory. https://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_encodings [[PUB-1]]
Once another encoding than GML is used, data providers need to document how the encoding relates to the concerned INSPIRE data model.
The good practice on the use of [geopackages](https://inspire.ec.europa.eu/good-practice/geopackage-encoding-inspire-datasets) as encoding, describes how this describing could be done.

### Filtering

The specification for [filtering](https://docs.ogc.org/DRAFTS/19-079r1.html), [[PUB-6]] is still a draft version and has therefore not yet been taken into account.
Some basic filtering requirements are described in [OGC API - Features - Part 1: Core](http://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_items_) [[PUB-1]].
This only concerns filtering on a bounding box and on properties.

### Metadata links

The [requirement for metadata links to the data](https://github.com/INSPIRE-MIF/gp-ogc-api-features/blob/master/spec/oapif-inspire-download.md#metadata-elements-of-the-data-set) in [[PUB-2]] have also been described in predefined download requirement class.
The [requirement for metadata of the API](https://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_api_definition_2) in [[PUB-1]] describes the metadata of the API via the API definition.

###	Relevant documentation 

Relevant documentation is shown in [appendix A](#references).


