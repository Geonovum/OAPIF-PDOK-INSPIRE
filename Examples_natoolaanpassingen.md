## Examples of implementations after tooladjustments

Because from earlier test, Geonovum concluded tools were not compliant with the requirements, at the beginning of the year 2023, an open tender was set up to adjust the tooling.
This resulted in 3 demo services that each show how you can be compliant with the requirements for OGC, INSPIRE and Dutch ADR.
All demo services used the same selection of the Dutch INSPIRE Addresses in a GML file as input.

|   tool    | main contributions  | landing page|
|-----------|---------------------|-------------|
| Pygeoapi  |Justobject and Geocat|https://apitestbed.geonovum.nl/adr_pygeoapi/v1 |
| Geoserver |Geosolutions         |https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1 |
| Deegree   |Wetransform          |https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1 |

Per tool, findings are elaborated in the next chapters when relevant.

#### Pygeoapi versus requirements

The following findings show how Pygeoapi complies to the requirements.

***RQ 1:OGC API Features Core***  
The OGC CITE validator gave no error.

***RQ 4:predefined download***  
link to metadata of dataset: passed at /collections/AddressesNL and at /collections level:
        {
            "type": "text/html",
            "rel": "describedby",
            "title": "Metadata as HTML",
            "href": "https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83",
            "hreflang": "nl"
        },
        {
            "type": "application/xml",
            "rel": "describedby",
            "title": "Metadata as ISO 19139 XML",
            "href": "https://www.nationaalgeoregister.nl/geonetwork/srv/api/records/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83/formatters/xml",
            "hreflang": "nl"
        }
link to INSPIRE feature concept dictionary: passed at /collections/AddressesNL and at /collections level
        {
            "type": "text/html",
            "rel": "tag",
            "title": "INSPIRE feature concept dictionary for addresses",
            "href": "https://inspire.ec.europa.eu/featureconcept/Address",
            "hreflang": "en"
        }
link to the license: passed at /collections/AddressesNL and at /collections level
        {
            "type": "text/html",
            "rel": "license",
            "title": "CC0 1.0 Public Domain license",
            "href": "https://creativecommons.org/publicdomain/zero/1.0/deed.en",
            "hreflang": "en"
        }
See also https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections?f=json and 
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL?f=json

***RQ 5:GeoJSON***
Items can be retrieved in Geo+Json by:  
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items?f=json

***RQ 6:bulk download***
Link to bulkdownload of dataset: passed at /collections/AddressesNL and at /collections level

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
For RD: https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items/1?f=json&crs=http://www.opengis.net/def/crs/EPSG/0/28992
For WGS84: https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items/1?f=json&crs=http://www.opengis.net/def/crs/OGC/1.3/CRS84
for ETRS89:  https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items/1?f=json&crs=http://www.opengis.net/def/crs/EPSG/0/4258

The storagecrs can be found at the end of:
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL?f=json 

With the following command line request, one can see the Content-CRS value in the header :
curl -i https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items/1?f=json

An adjustment has been made tot the bbox filter. It now also supports the bbox-crs parameter.
Only 2 addresses are available in the below defined bbox.
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/items?f=json&bbox-crs=http://www.opengis.net/def/crs/EPSG/0/28992&bbox=252200,593000,252710,594000

***RQ 8:GML*** 
As input, a simple features GML file was used as produced by Wetransform from the complex feature GML with the transformation software Hale.
As output, there is a link to the original complex feature GML-file:
https://service.pdok.nl/kadaster/ad/atom/downloads/addresses.gml.gz 
Pygeoapi does not support GML-output at item-level, but this is not a requirement.

***RQ 9:Dutch API design rules***  
It complies with all the rules, except for rule https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-48.
This rule in the Dutch ADR prescribes that none of the API endpoints should have a trailing slash. On the other end, the OGC specification states
that the landing page (i.e. "Home") should have a trailing slash. So the rules contradict.
It is expected that in future, this ADR-rule will make an exeption for the landingpage.

***RQ 10:describing encoding***  
There is a link to https://github.com/INSPIRE-MIF/2017.2/tree/master/GeoJSON/ads at [colection/AddressesNL level](https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL?f=json )
{
            "type": "text/html",
            "rel": "about",
            "title": "Description of the encoding",
            "href": "https://github.com/INSPIRE-MIF/2017.2/tree/master/GeoJSON/ads",
            "hreflang": "en"
        },

***RQ 11:filtering***  
For the use of filters, the bbox and items options were already available. Next to that, one can filter on the attributes which can be retrieved from:
https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL/queryables.
The specification for filtering [[PUB-6]] does not yet have the status "approved" and has not yet been considered.

***RQ 12:metadata links***  
1. Metadata link of the dataset can be found at [/collections/AddressesNL level](https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL?f=json):
        {
            "type": "text/html",
            "rel": "describedby",
            "title": "Metadata as HTML",
            "href": "https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83",
            "hreflang": "nl"
        } 
The metadata still needs adjustment for adding the OAPIF to the download links. To do this, a new protocol needs to be added to the code list. (https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1). 
As long as it is not there, the Dutch profile for metadata can be used with the value: "OGC:API features" https://geonovum.github.io/Metadata-ISO19119/#codelist-protocol.
2. Metadata of the service can be obtained from: https://apitestbed.geonovum.nl/adr_pygeoapi/v1/openapi?f=json and https://apitestbed.geonovum.nl/adr_pygeoapi/v1/collections/AddressesNL.

***Other findings***
More information about the Pygeoapi adjustments to the standards can be found at https://pygeoapi.io/presentations/geonovum-tender-2023/

### Geoserver versus requirements

The following findings show how Geoserver complies to the requirements.

***RQ 1:OGC API Features Core***  
The OGC CITE validator gave no error.

***RQ 4:predefined download***  
link to metadata of dataset: passed at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json) and at [/collections level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections?f=json).
{"href":"https://www.nationaalgeoregister.nl/geonetwork/srv/api/records/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83/formatters/xml?approved=true","rel":"describedBy","type":"application/xml","title":"ISO metadata for this dataset"}
  
link to INSPIRE feature concept dictionary: passed at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json).
{"href":"https://inspire.ec.europa.eu/featureconcept/Address","rel":"tag","type":"text/html","title":"INSPIRE Address feature concept."}

link to the license: passed at [/collections level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections?f=json).
{"href":"http://creativecommons.org/publicdomain/zero/1.0/deed.nl","rel":"license","type":"text/html","title":"Dataset license."}

***RQ 5:GeoJSON***
Items can be retrieved in Geo+Json by:  
https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items/1?f=application%2Fgeo%2Bjson

***RQ 6:bulk download***
Link to bulkdownload of dataset: passed at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json).
{"href":"https://geonovum.geosolutionsgroup.com/geoserver/www/ADNL.gpkg","rel":"enclosure","type":"application/geopackage+sqlite3","title":"Addresses raw data."}

***RQ 7:CRS ETRS89 and WGS84***

For RD: https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items/1?f=json&crs=http://www.opengis.net/def/crs/EPSG/0/28992
For WGS84: https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items/1?f=json&crs=http://www.opengis.net/def/crs/OGC/1.3/CRS84
for ETRS89:  https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items/1?f=json&crs=http://www.opengis.net/def/crs/EPSG/0/4258

The storagecrs can be found at the end of:
https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json

With the following command line request, one can see the Content-CRS value in the header :
curl -i https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items/1?f=json

An adjustment has been made tot the bbox filter. It now also supports the bbox-crs parameter.
Only 2 addresses are available in the below defined bbox.
https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items?f=json&bbox-crs=http://www.opengis.net/def/crs/EPSG/0/28992&bbox=252200,593000,252710,594000

***RQ 8:GML*** 
As input, a simple features GML file was used as produced by Wetransform from the complex feature GML with the transformation software Hale.
As output, the following link can be found at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json). It can be used to download the first 50 records.
{"href":"https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses/items?f=application%2Fgml%2Bxml%3Bversion%3D3.2","rel":"items","type":"application/gml+xml;version=3.2","title":"Addresses items as application/gml+xml;version=3.2"}

***RQ 9:Dutch API design rules***  
It complies with all the rules, except for rule https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-48.
This rule in the Dutch ADR prescribes that none of the API endpoints should have a trailing slash. On the other end, the OGC specification states
that the landing page (i.e. "Home") should have a trailing slash. So the rules contradict.
It is expected that in future, this ADR-rule will make an exeption for the landingpage.

***RQ 10:describing encoding***  
There is a link to https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/ads/simple-addresses.md at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json).
{"href":"https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/ads/simple-addresses.md","rel":"describedBy","type":"text/html","title":"GeoJSON Encoding Rule for INSPIRE Addresses"}

***RQ 11:filtering***  
For the use of filters, the bbox and items options were already available. Next to that, one can filter on the attributes which can be retrieved from:
https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?queryables.
The specification for filtering [[PUB-6]] does not yet have the status "approved" and has not yet been considered.

***RQ 12:metadata links***  
1. Metadata link of the dataset can be found at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json):
{"href":"https://www.nationaalgeoregister.nl/geonetwork/srv/api/records/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83/formatters/xml?approved=true","rel":"describedBy","type":"application/xml","title":"ISO metadata for this dataset"}
The metadata of the dataset still needs adjustment for adding the OAPIF to the download links. To do this, a new protocol needs to be added to the code list. (https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1). 
As long as it is not there, the Dutch profile for metadata can be used with the value: "OGC:API features" https://geonovum.github.io/Metadata-ISO19119/#codelist-protocol.
2. Metadata of the service can be obtained from: https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/openapi and https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses.

***Other findings***
More information about the Geoserver adjustments to the standards can be found at https://www.geonovum.nl/uploads/documents/Geosolutions.pdf
 
#### Deegree versus requirements

The following findings show how Geoserver complies to the requirements.

***RQ 1:OGC API Features Core***  
The OGC CITE validator gave no error.

***RQ 4:predefined download***  
link to metadata of dataset: passed at [/collections level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections?f=json).
{"href":"https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83","rel":"describedby","type":"text/html","title":"Metadata"}  

link to INSPIRE feature concept dictionary: passed at [/collections/collection level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress?f=json) and at [/collections level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections?f=json).
{"href":"https://inspire.ec.europa.eu/featureconcept/Address","rel":"tag","type":"text/html","title":"Feature concept Address"}

link to the license: passed at [/collections level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections?f=json).
{"href":"http://creativecommons.org/publicdomain/zero/1.0/deed.nl","rel":"license","type":"text/html","title":"License"}

***RQ 5:GeoJSON***
Items can be retrieved in Geo+Json by:  
https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/collections/SimpleAddress/items?f=json&limit=1 or
https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/collections/SimpleAddress/items/nl-imbag-ad-address-0003200000133985?f=json

***RQ 6:bulk download***
Link to bulkdownload of dataset: passed at [/collections/collection level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress?f=json) and at [/collections level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections?f=json).
{"href":"http://test.haleconnect.de/ogcapi/datasets/simplified-addresses/collections/SimpleAddress/items?bulk=true","rel":"enclosure","type":"application/xml","title":"Download all features as GML"}
{"href":"http://test.haleconnect.de/ogcapi/datasets/simplified-addresses/collections/SimpleAddress/items?bulk=true","rel":"enclosure","type":"application/json","title":"Download all features as GeoJSON"}

***RQ 7:CRS ETRS89 and WGS84***

For RD: https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress/items/1?f=json&crs=http://www.opengis.net/def/crs/EPSG/0/28992
For WGS84: https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress/items/1?f=json&crs=http://www.opengis.net/def/crs/OGC/1.3/CRS84
for ETRS89: https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress/items/1?f=json&crs=http://www.opengis.net/def/crs/EPSG/0/4258

The storagecrs can be found at the end of:
https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress?f=json

With the following command line request, one can see the Content-CRS value in the header :
curl -i https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress/items/1?f=json

An adjustment has been made tot the bbox filter. It now also supports the bbox-crs parameter.
Only 2 addresses are available in the below defined bbox.
https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress/items?f=json&bbox-crs=http://www.opengis.net/def/crs/EPSG/0/28992&bbox=252200,593000,252710,594000

***RQ 8:GML*** 
As input, a simple features GML file was used as produced by Wetransform from the complex feature GML with the transformation software Hale.
As output, the following link can be found at [/collections/collection level](https://geonovum.geosolutionsgroup.com/geoserver/inspire/ogc/features/v1/collections/Addresses?f=json). It can be used to download the first 50 records.
{"href":"https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress/items?f=application%2Fgml%2Bxml%3Bversion%3D3.2","rel":"items","type":"application/gml+xml;version=3.2","title":"Addresses items as application/gml+xml;version=3.2"}

***RQ 9:Dutch API design rules***  
It complies with all the rules, except for rule https://publicatie.centrumvoorstandaarden.nl/api/adr/#api-48.
This rule in the Dutch ADR prescribes that none of the API endpoints should have a trailing slash. On the other end, the OGC specification states
that the landing page (i.e. "Home") should have a trailing slash. So the rules contradict.
It is expected that in future, this ADR-rule will make an exeption for the landingpage.

***RQ 10:describing encoding***  
There is a link to https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/ads/simple-addresses.md at [/collections/collection level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress?f=json).
{"href":"https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/ads/simple-addresses.md","rel":"describedBy","type":"text/html","title":"GeoJSON Encoding Rule for INSPIRE Addresses"}

***RQ 11:filtering***  
For the use of filters, the bbox and items options were already available. Next to that, one can filter on the attributes which can be retrieved from:
https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress?queryables.
The specification for filtering [[PUB-6]] does not yet have the status "approved" and has not yet been considered.

***RQ 12:metadata links***  
1. Metadata link of the dataset can be found at [/collections/collection level](https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress?f=json):
{"href":"https://www.nationaalgeoregister.nl/geonetwork/srv/api/records/a5f961e9-ebdd-41e2-b8e8-ab33ed340a83/formatters/xml?approved=true","rel":"describedBy","type":"application/xml","title":"ISO metadata for this dataset"}
The metadata of the dataset still needs adjustment for adding the OAPIF to the download links. To do this, a new protocol needs to be added to the code list. (https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1). 
As long as it is not there, the Dutch profile for metadata can be used with the value: "OGC:API features" https://geonovum.github.io/Metadata-ISO19119/#codelist-protocol.
2. Metadata of the service can be obtained from: https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/openapi and https://test.haleconnect.de/ogcapi/datasets/simplified-addresses/v1/collections/SimpleAddress.

***Other findings***
More information about the Deegree adjustments to the standards can be found at https://www.geonovum.nl/uploads/documents/deegree%20OGC%20API%20Features.pdf

### General findings

1. The protocol element in the metadata is based on a code list. A new protocol needs to be added to this list of [protocol values]https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1). As long as it is not there, the Dutch profile for metadata can be used with the value: "OGC:API features" https://geonovum.github.io/Metadata-ISO19119/#codelist-protocol.
2. Another blocking issue before implementation of the OAPIF for INSPIRE is that descriptions of encodings other than GML are not yet available for most INSPIRE themes.
3. Complex GML as input and output are difficult as long as tooling (server and client) expects simple encodings.
4. One could discuss if it is useful to publish complex GML as output, because it is not in line with the aim of OGI API Features: easy to use for developers.
5. Complex GML as input needs a flattening of the data. This is needed for the software that publishes the features. It can only work with simple features, with one value per attribute and without relations to other objects. This is often not the case with the more complex INSPIRE models.

### Resulting documentation

Presentations can be found here: https://www.geonovum.nl/over-geonovum/actueel/presentatie-resultaten-aanbesteding-ogc-api-features-toolaanpassing
