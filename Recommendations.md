## Recommendations

Recommendations can be divided in recommendations for a hosting organization like [PDOK](https://www.pdok.nl), recommendations for the INSPIRE data provider and recommendations for the INSPIRE community.
A general recommendation to all three parties is to adjust as much as possible to the INSPIRE requirements as stated in this document.

### Recommendations for INSPIRE data providers

1. Before starting, look what other data providers have done in this field for the concerning INSPIRE themes.
2. When hosting at PDOK you have to discuss the mapping of your harmonized data to other encodings together with other data providers in Europe and use the principles as stated in [[PUB-4]].
3. If a not previously published mapping to an output encoding is used, you have to publish the mapping to this encoding to be INSPIRE compliant.
4. Look at exapmles: https://github.com/INSPIRE-MIF/gp-ogc-api-features/tree/master/deployments.
5. When a working INSPIRE OAPIF is published with a well described mapping to the output encoding (probably GeoJSON), it could be shared at https://github.com/INSPIRE-MIF/2017.2/issues or https://github.com/Geonovum/OAPIF-PDOK-INSPIRE/issues.
6. Adjust your metadata of the dataset with the extra OAPIF service. As long as there is no official protocol defined in https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1, use the extended code list for the protocol in the Dutch metadata standard 2.1.0 (https://docs.geostandaarden.nl/md/mdprofiel-iso19119/#codelist-protocol) contains: "OGC:API features".

### Recommendations for a Hosting organization

1. Figure out the best way of supporting more than one CRS, and at least [WGS84](https://epsg.io/4326) and [ETRS89](https://epsg.io/4258) since the last is the most common in INSPIRE and mostly mandatory.
2. Stimulate data providers who want OAPIF as a download service for their harmonized INSPIRE data to define the mapping of this data to an alternative encodings together with other data providers in Europe. In case of PDOK, this means geopackage for input, and GeoJSON for output.
3. Follow the developments of the alternative encodings.
4. Research how the metadata of the OAPIF service should look like.
5. Try to reach other data providers that are interested in OAPIF service.
6. Try to reach users for the OAPIF services.
7. Consider leaving out the empty fields, or use an option not to show them.
8. Implement the improvements listed in the results.

### Recommendations for the INSPIRE community

1. Stimulate a centralized establishment for rules on mapping the INSPIRE data for each feature type that exists within the INSPIRE data specifications to other encodings like GeoJSON, geopackage and in some cases theme specific encodings like SDMX for statistics. 
[[PUB-4]] for GeoJSON and for [geopackages](https://github.com/INSPIRE-MIF/gp-geopackage-encodings) are a very good start, but it needs to be specified per INSPIRE feature type per INSPIRE theme.
If this is not organized, each EU member will try it on their own, with the result of no data interoperability. It is important for the OAPIF, because the input and output of many OAPIF implementations are based on these encodings, although [[PUB-1]] does not bound you to these alternative encodings. GML is also allowed. 
2. Develop validation tool for these encodings, otherwise the encodings will stay additional instead of alternative encodings for GML, since at the moment only validators for GML exist.
3. Specify a protocol for OAPIF like: "OGC:API features" as in the extended Dutch code list (https://docs.geostandaarden.nl/md/mdprofiel-iso19119/#codelist-protocol).
4. Look at the issues in the [European INSPIRE helpdesk](https://github.com/INSPIRE-MIF/helpdesk) and specially [issue nr 9](https://github.com/INSPIRE-MIF/helpdesk/issues/9).
