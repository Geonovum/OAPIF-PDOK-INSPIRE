## Examples of implementations after tooladjustments

Because from earlier test, Geonovum concluded tools were not compliant with the requirements, at the beginning of the year 2023, an open tender was set up to adjust the tooling.
This resulted in 3 demo services that each show how you can be compliant with the requirements for OGC, INSPIRE and Dutch ADR.
All demoservice used the same selection of the Dutch INSPIRE Addresses in a GML file as input.

|   tool    | main contributions  | landing page|
|-----------|---------------------|-------------|
| Pygeoapi  |Justobject and Geocat|https://apitestbed.geonovum.nl/adr_pygeoapi/v1|
| Geoserver |Geosolutions         |https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1| 
| Deegree   |Wetransform          |https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1|

Per tool, findings are elaborated in the next chapters when relevant.

#### Pygeoapi versus requirements

The following findings show how Pygeoapi complies to the requirements.

***RQ 1:OGC API Features Core***  
The OGC CITE validator gave no error.

***RQ 4:predefined download***  
link to metadata of dataset: passed at /collections/AddressesNL and at /collections level
link to INSPIRE feature concept dictionary: passed at /collections/AddressesNL and at /collections level
link to the license: passed at /collections/AddressesNL and at /collections level

See also https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections?f=json and 
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL?f=json

***RQ 5:GeoJSON***  
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items?f=json

***RQ 6:bulk download***
link to bulkdownload of dataset: passed at /collections/AddressesNL and at /collections level

See also https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections?f=json and   
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL?f=json

        {
            "type": "application/x-gmz",
            "rel": "enclosure",
            "title": "Download complete dataset as GML",
            "href": "https://service.pdok.nl/kadaster/ad/atom/downloads/addresses.gml.gz",
            "hreflang": "nl",
            "length": 685450191
        },

***RQ 7:CRS ETRS89 and WGS84***  


***RQ 8:GML***  

***RQ 9:Dutch API design rules***  

***RQ 10:describing encoding***  

***RQ 11:filtering***  
For implementing filters, the bbox and items options were implemented. Next to that, one can filter on the attributes which can be retrieved from:
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/queryables.
The specification for filtering [[PUB-6]] does not yet have the status "approved" and has not yet been considered.

***RQ 12:metadata links***  
1. Metadata link of the dataset was not difficult to implement, because we easily referred to it via https://apisandbox.geonovum.nl/pygeoapi_SU/collections/StatisticalUnits_Gemeente_2018 with:
https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/10d1153e-778f-4995-9b6c-7c69b196cccb.  It still needs adjustment, for adding the OAPIF to the download links. A new protocol needs to be added to the code list for this. (https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1). 
As long as it is not there, the Dutch profile for metadata can be used with the value: "OGC:API features" https://geonovum.github.io/Metadata-ISO19119/#codelist-protocol.
2. The metadata of the services were not implemented, but could be copied from the WFS metadata with some slight adjustments.
3. Metadata of the service could also be obtained from: https://apisandbox.geonovum.nl/pygeoapi_SU.

***Other findings***  


### Geoserver versus requirements

Based on the geoserver implementation on the Geonovum testbed, it was possible to publish two layers from Statistical Units as OAPIF.
The Geocat Bridge plugin in QGIS was used for this. The result is a two-layer OAPIF:
https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/collections/
The following findings were encountered during the test at the Geonovum testbed for OGC-API-Features with Geoserver via Geocat Bridge.

***RQ 1:OGC API Features Core***  
The INSPIRE validator gave one error on the response of the filters, links and featureID

***RQ 4:predefined download***  
There is no link to the metadata of the dataset.  
There is no link to the featureconcept metadata of the dataset.  
The licence link is missing.

***RQ 5:GeoJSON***  
The source encoding used was the GML as resulted from the WFS request mentioned above. It was converted into geopackage via QGIS v3.16. which was input to Geoserver via Geocat Bridge.
The conversion to the output in GeoJSON was an automated process within Geoserver.

***RQ 6:bulk download***  
There was no bulk download link. 

***RQ 7:CRS ETRS89 and WGS84***  
https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/collections/su_nuts1_2016_RDNew?f=application%2Fjson
clearly shows that multiple CRSs are supported.
The items can be retrieved with multiple CRS's as output.  
Compare in RD New:
https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/collections/su_nuts1_2016_RDNew/items?f=application%2Fgeo%2Bjson&crs=http://www.opengis.net/def/crs/EPSG/0/28992/  
with ETRS89:
https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/collections/su_nuts1_2016_RDNew/items?f=application%2Fgeo%2Bjson&crs=http://www.opengis.net/def/crs/EPSG/0/4258/

Regarding to OGC-API-Features specification part 2 [[PUB-5]], 4 requirements were not met:
- [Requirement 3 and 4](http://docs.opengeospatial.org/is/18-058/18-058.html#_storage_crs) concern the Storage CRS which could not be found in the description of the collection object.
- [Requirement 15 and 16](http://docs.opengeospatial.org/is/18-058/18-058.html#_coordinate_reference_system_information_independent_of_the_feature_encoding) concern the use of a Content-CRS header where Geoserver uses a OGC-CRS header.

***RQ 8:GML***  
1. Since the input was from a WFS, the input originally was GML encoded. It was converted into geopackage via QGIS v3.16. which then was input to Geoserver via Geocat Bridge.
2. Output as GML is not possible within Geoserver via OAPIF. But Geoserver does automatically create a comparable OGC-WFS which does support GML as output. 

***RQ 9:Dutch API design rules***  
Not all requirements from the [Dutch API design rules](https://www.geonovum.nl/over-geonovum/actueel/rest-api-design-rules-op-pas-toe-leg-uit-lijst) have been implemented:
1. no 404 result when "/" was used on the end of an URL: (https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-48)
2. no version number in URL: https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-20
3. no complete version number in every return: https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-57
4. no use of the standard naming of the OAS document ('api' was used instead of 'openapi') https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-51

***RQ 10:describing encoding***  
The describing of the encoding has not been performed, but in fact it is a simple 1 to 1 conversion.
But, if there had been a description of how the encoding relates to the concerned INSPIRE data model, it would not have been possible to link to it.

***RQ 11:filtering***  
For implementing filters, the bbox and items options were implemented. Next to that, one can filter on the attributes which can be retrieved from:
https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/collections/su_nuts1_2016_RDNew/queryables.  
The specification for filtering [[PUB-6]] does not yet have the status "approved" and has not yet been considered.

***RQ 12:metadata links***  
1. There was no option for a link to the metadata. 
2. The metadata of the services were not implemented, but could be copied from the WFS metadata with some slight adjustments: https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/su_nuts1_2016_RDNew/wfs?request=GetCapabilities
3. Metadata of the service could also be obtained from: https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/api.

***Other findings***  
1. One big drawback sofar for Geosever (version 2.19.1) is that links to the metadata, bulk download or license were not included in the [list of links](https://apisandbox.geonovum.nl/geoserver/nl_su_nuts/ogc/features/collections/su_nuts1_2016_RDNew?f=application%2Fjson).
2. Based on a small inquiry, Geoserver appears to be the most used tooling for INSPIRE OAPIF in Europe. So, it is strange that relatively simple INSPIRE requirement for linking to metadata, bulk download and license are not implemented.
3. The status of Geoserver in relation to OGC specifications can be found at: https://docs.geoserver.org/stable/en/user/community/ogc-api/features/index.html

***Possible improvements***  
The following improvements could still be made:

1. link to metadata of the dataset
2. link to bulk download
3. link to encoding description
4. link to the license
5. Geoserver has good support for multiple CRS's, but could still adjust more to OGC-API-Features specification part 2 [[PUB-5]]
6. testing with more complex INSPIRE themes than Statistical Units
7. adjust to the Dutch API design rules

#### Deegree versus requirements

Another example of using more than one CRS as output for the OAPIF is the result of the company GISspecialisten:  
https://geoservice-ogc-api.azurewebsites.net/  
This Implementation had its focus mainly on serving more than one CRS, so that explains why not all requirements were met.
GISspecialisten has promised to keep this test implementation live 1 year after implementation which was the end of 2021.

***RQ 1:OGC API Features Core***  
The INSPIRE validator gave one error on the definition of the API, although it is available via https://geoservice-ogc-api.azurewebsites.net/api/

***RQ 4:predefined download***  
There is no link to the metadata of the dataset.  
There is no link to the featureconcept metadata of the dataset.  
The licence link is missing.

***RQ 5:GeoJSON***  
The source encoding used, was the geopackage that could be downloaded via the INSPIRE Atom feed of the dataset "geharmoniseerde Beschermde Gebieden - Cultuur Historie".
This Atom feed can be found via the metadata:  
https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search;jsessionid=8F7125E8DE957788ED181DE50F0A24DB#/metadata/493ab81b-75f8-4205-b030-6b2fd9eb4295
  
In QGIS, the geopackage was converted to PostgreSQL SQL database, which was the basis for the tool serving the OAPIF.
The output was converted by this tool to GeoJson:
https://geoservice-ogc-api.azurewebsites.net/collections/Inspire_RCE%20rce_inspire_polygons/items?limit=2

Interesting aspect is the use of JSON-FG as alternative format:
https://geoservice-ogc-api.azurewebsites.net/collections/Inspire_RCE%20rce_inspire_polygons/items?format=JSON-FG&limit=2  

***RQ 6:bulk download***  
The bulk download link has not been implemented. 

***RQ 7:CRS ETRS89 and WGS84***  

https://geoservice-ogc-api.azurewebsites.net/collections/ gives the following result:
![More than one CRS](media/Gisspecialisten_meerdereCRSen.png "More than one CRS in collection path")

This shows that multiple CRS's are supported.
The items can be retrieved with multiple CRS's as output. 
Compare in RD New:  
https://geoservice-ogc-api.azurewebsites.net/collections/Inspire_RCE%20rce_inspire_points/items/59631/?crs=http://www.opengis.net/def/crs/EPSG/0/28992  

with ETRS89:  
https://geoservice-ogc-api.azurewebsites.net/collections/Inspire_RCE%20rce_inspire_points/items/59631/?crs=http://www.opengis.net/def/crs/EPSG/0/4258 

Regarding to OGC-API-Features specification part 2 [[PUB-5]], 2 related [Requirements 3 and 4](http://docs.opengeospatial.org/is/18-058/18-058.html#_storage_crs) were not met. They concern the Storage CRS which could not be found in the description of the collection object.

***RQ 8:GML***  
1. The application only works with a PostgreSQL SQL database, so no GML as input.
2. Output as GML is not possible. 

***RQ 9:Dutch API design rules***  
Not all requirements from [Dutch API design rules](https://www.geonovum.nl/over-geonovum/actueel/rest-api-design-rules-op-pas-toe-leg-uit-lijst) have been implemented:
1. no 404 result when "/" was used on the end of an URL: (https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-48)
2. no version number in URL: https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-20
3. no complete version number in every return: https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-57
4. no use of the standard naming of the OAS document ('api' was used instead of 'openapi') https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-51

***RQ 10:describing encoding***  
The describing of the encoding has not been performed. 

***RQ 11:filtering***  
For implementing filters, the bbox and items options were implemented.
The specification for filtering [[PUB-6]] does not yet have the status "approved" and has not yet been considered.

***RQ 12:metadata links***  
1. There was no option for a link to the metadata. 
2. The metadata of the services were not implemented
3. Metadata of the service could also be obtained from: https://geoservice-ogc-api.azurewebsites.net/api/.

***Other findings***  
1. Interesting aspect is the use of JSON-FG as alternative format:
https://geoservice-ogc-api.azurewebsites.net/collections/Inspire_RCE%20rce_inspire_polygons/items?format=JSON-FG&limit=2  
2. The final result of this Pilot has been published on:
https://github.com/Geonovum/testbed-spatial-APIs/tree/main/topic%20%231%20Spatial%20data%20APIs%20CRS%20Extension   

***Possible improvements***  
The following improvements could be made, although it was not the intention of this example to make a fully compliant implementation:

1. link to metadata of the dataset
2. link to bulk download
3. link to encoding description
4. link to the license
5. the GISspecialisten tool has good support for multiple CRS's, but could still adjust more to OGC-API-Features specification part 2 [[PUB-5]]
6. adjust to the Dutch API design rules
7. give a result for https://geoservice-ogc-api.azurewebsites.net/collections/queryables to show all attributes and make it possible to filter on their values.

### General findings

1. The protocol element in the metadata is based on a code list. A new protocol needs to be added to this list of [protocol values]https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1). As long as it is not there, the Dutch profile for metadata can be used with the value: "OGC:API features" https://geonovum.github.io/Metadata-ISO19119/#codelist-protocol.
2. Much time is needed for flattening of the data and the associated description of the encoding to alternative simple encodings in relation to the INSPIRE data models. A centralized EU approach is needed.
3. Current tooling (server and client) does not yet fully support another CRS than WGS84 according to the currently accepted specification part 2 [[PUB-5]]. Geoserver and the example of GISspecialisten came close to this specification. Also, the extension of the GeoJSON (Json FG) standard for another CRS which is in development, might help in this issue.
5. Another blocking issue before implementation of the OAPIF for INSPIRE is that descriptions of encodings other than GML are not yet available for most INSPIRE themes.
6. Complex GML as input and output are difficult as long as tooling (server and client) expects simple encodings.
7. One could discuss if it is useful to publish complex GML as output, because it is not in line with the aim of OGI API Features: easy to use for developers.
8. Complex GML as input needs a flattening of the data. This is needed for the software that publishes the features. It can only work with simple features, with one value per attribute and without relations to other objects. This is often not the case with the more complex INSPIRE models.

### Resulting documentation

Documentation like presentations can be found here: https://github.com/Geonovum/OAPIF-PDOK-INSPIRE/tree/main/docs
