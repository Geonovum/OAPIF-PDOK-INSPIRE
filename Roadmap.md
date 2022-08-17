## Roadmap for data providers

The following steps could be considerated to follow.

1. Read this document and all the documents in https://geonovum.github.io/OAPIF-PDOK-INSPIRE/#references
2. Make a choice between publishing by yourself with, or contact a hosting organization that can help you publisch the OAPIF services.
3. Look what other data providers have done in this field for the concerning INSPIRE themes and have a look at these exapmles: https://github.com/INSPIRE-MIF/gp-ogc-api-features/tree/master/deployments.
4. If you diced to serve the OAPIF by youself, make a choice for the best tooling, while regarding the CRS options (see next step).
5. Figure out the best way of supporting more than one CRS, and at least [WGS84](https://epsg.io/4326) and [ETRS89](https://epsg.io/4258) since the last is the most common in INSPIRE and mostly mandatory, but also provide the [Dutch RD](https://www.opengis.net/def/crs/EPSG/0/28992). If tooling is chosen that is not able to serve more than CRS, a second INSPIRE download option should be provided that does give the required CRS.
6. Decide on the best input encoding for the OAPIF. It depends on the previous steps.
7. Decide on the best output encoding, which also depends on the previous steps. The tooling used in the examples did a simple 1 to 1 mapping between the input and output encoding. 
8. If a previously published mapping to an encoding other than GML can not be found for the concerned INSPIRE theme, research the mapping of your harmonized data to this other encodings together with other INSPIRE data providers in Europe and use the principles as stated in [[PUB-4]].
Consider leaving out the empty fields to reduce the output size, or use an option not to show them.
9. Execute the transormation into the chosen input encoding. This can be done with software like [HALE studio](https://wetransform.to/halestudio/) or [FME](https://www.safe.com/)
10. If not described before, describe the mappimg from the INSPIRE datamodel to the output encoding of the OAPIF and publish it in order to be INSPIRE compliant.
11. Adjust your metadata of the dataset with the addition of extra OAPIF service. As long as there is no official protocol defined in https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue:1, use the extended code list for the protocol in the Dutch metadata standard 2.1.0 (https://docs.geostandaarden.nl/md/mdprofiel-iso19119/#codelist-protocol) contains: "OGC:API features".
12. If you host your OAPIF by yourself, research how to make INSPIRE compliant metadata of the OAPIF service. It is probably simular to the metadata of a WFS.
13. Add all the links as mentioned in the chapter on [requirements](#requirements) (metadata of dataset, INSPIRE feature concept dictionary, Licence, mapping description, bulk download).
14. The steps for final actual publishing of the OAPIF service, depend on the chosen tool, so there the tooling guidelines need to be followed:
- Geonovum testbed: https://github.com/Geonovum/ogc-api-testbed/tree/main/docs/docs/howto 
- GOAF: https://github.com/PDOK/goaf
- Pygeoapi: https://github.com/Geonovum/ogc-api-testbed/blob/main/docs/docs/howto/howto_pygeoapi.md or https://docs.pygeoapi.io/_/downloads/en/stable/pdf/
- Geoserver: https://github.com/Geonovum/ogc-api-testbed/blob/main/docs/docs/howto/howto_geoserver.md or https://docs.geoserver.org/latest/en/user/
15. When a working INSPIRE OAPIF is published with a well described mapping to the output encoding, it could be shared at https://github.com/INSPIRE-MIF/2017.2/issues or https://github.com/Geonovum/OAPIF-PDOK-INSPIRE/issues.




