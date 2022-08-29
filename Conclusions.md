## Recommendations and conclusions

Recommendations for the INSPIRE data providers have been mentioned in the roadmap in the previous chapter.
Other recommendations can be divided in recommendations for a hosting organization like [PDOK](https://www.pdok.nl) and recommendations for the INSPIRE community.
A general recommendation to all three parties is to adjust as much as possible to the INSPIRE requirements as stated in this document.

### Recommendations for a Hosting organization

1. Figure out the best way of supporting more than one CRS, and at least [WGS84](https://epsg.io/4326) and [ETRS89](https://epsg.io/4258) since the last is the most common in INSPIRE and mostly mandatory, but also provide the [Dutch RD](https://www.opengis.net/def/crs/EPSG/0/28992).
2. Stimulate data providers who want OAPIF as a download service for their harmonized INSPIRE data to define the mapping of this data to an alternative encodings together with other data providers in Europe. In case of PDOK, this means geopackage for input, and GeoJSON for output.
3. Follow the developments of the alternative encodings.
4. Research what the metadata of the OAPIF service should look like.
5. Try to reach other data providers that are interested in OAPIF service.
6. Try to reach users for the OAPIF services.
7. Consider leaving out the empty fields or use an option not to show them.
8. Implement the improvements as listed in the examples.

### Recommendations for the INSPIRE community

1. Stimulate a centralized establishment for rules on mapping the INSPIRE data for each feature type that exists within the INSPIRE data specifications to other encodings like GeoJSON, geopackage and in some cases theme specific encodings like SDMX for statistics. 
[[PUB-4]] for GeoJSON and for [geopackages](https://github.com/INSPIRE-MIF/gp-geopackage-encodings) are a very good start, but it needs to be specified per INSPIRE feature type per INSPIRE theme.
If this is not organized, each EU member will try it on their own, with the result of no data interoperability. It is important for the OAPIF, because the input and output of many OAPIF implementations are based on these encodings, although [[PUB-1]] does not bound you to these alternative encodings. GML is also allowed. 
2. Stimulate the market to make the tooling fulfil all the INSPIRE requirements
3. Develop validation tool for these encodings, otherwise the encodings will stay additional instead of alternative encodings for GML, since at the moment only validators for GML exist.
4. Specify a value for the protocol code list for OAPIF like: "OGC:API features" as in the extended Dutch code list (https://docs.geostandaarden.nl/md/mdprofiel-iso19119/#codelist-protocol).
5. Look at the issues in the [European INSPIRE helpdesk](https://github.com/INSPIRE-MIF/helpdesk) and specially [issue nr 9](https://github.com/INSPIRE-MIF/helpdesk/issues/9).

### Conclusions

1. Unfortunately, none of the tools used in the examples fulfil all INSPIRE requirements and no tooling is known to do so at this moment (August 2022).
2. The main barrier for implementing OAPIF services conform INSPIRE is the complexity of the INSPIRE data models which is not supported in the standard OAPIF encoding GeoJSON, which is the most preferred encoding by the target user group.
The data needs to be flattened and converted into simple encodings and most importantly: The mapping needs to be described and published.
Complex GML is allowed as output of the OAPIF, but so far, no server application is known to be able to deal with this without losing the complex structure half way the process from input to output of the OAPIF.
3. The second barrier is the coordinate system (CRS) ETRS89 which is not supported by the standard OAPIF encoding GeoJSON.
There is an approved specification for implementing more than one CRS: [[PUB-5]].
There is an extension in development for GeoJSON to support other coordinate reference systems than WGS84. It is called [JSON FG](https://github.com/opengeospatial/ogc-feat-geo-json).
It is not clear whether applications support these new standards already, but they will probably do so in the future.
4. OAPIF conform INSPIRE download services is possible when both previous barriers are solved. There are work arounds.
The complex data models can be dealt with by a good description of the mapping from and towards the INSPIRE model.
Both problems can be dealt with by providing a bulk download with complex GML in the required CRS, but that means providing an extra service.
5. It is not expected that OAPIF will evolve into a service with complex GML-output soon, since that is not something the aimed users would be able to deal with easily.
6. At this moment OAPIF can be considered more as an additional service, than as a replacement of the OGC WFS 2.0. They both have their advantages and disadvantages and serve different type of users. Though, it is expected that OAPIF will replace WFS2.0 in the future.
