## Abstract

This document describes the results and recommendations that have been derived from setting up a test bed with OGC API features conform INSPIRE at the Dutch hosting organization [PDOK](https://www.pdok.nl) (Publieke Dienstverlening Op de Kaart) and at the [Geonovum testbed for OGC API features](https://github.com/Geonovum/ogc-api-testbed).
The aim of setting up these testbeds is to stimulate the INSPIRE data providers and hosting organizations to start publishing INSPIRE data as OGC API Features. By doing this, a greater goal is reached: A better use of Inspire data. Secondly it hopes te contribute to the Inspire community.

The approach was to predefine requirements and setup a week of strong collaboration (High5) with data provider Dutch Kadaster, hosting organization PDOK and Geonovum to build a OGC API feature service on the INSPIRE dataset of Dutch Addresses.
The results is a working [OGC API feature service](https://api.pdok.nl/geonovum/oaf/v1_0/), with a description of the compliance to the predefined requirements. Secondly this was done for the INSPIRE dataset of the Dutch Statistical Units on the Geonovum testbed for OGC API features with a comparable [result](https://apisandbox.geonovum.nl/pygeoapi_SU)

A general recommendation to all three parties is to adjust as much as possible to the INSPIRE requirements as stated in this document.
The most important recommendations for the hosting organizations is to stimulate data providers to start with OGC API features to increase the use of the INSPIRE data. Data providers are recommended to first orientate on the possible work of other data providers in this field. 
OGC API features use simple encodings as input and output. For the interoperatability, it is important that all member states use the same encoding rules. The INSPIRE community therefor needs a central organization for the mapping of the complex data models to the simple encodings.

An important conclusion is that as long as there is no proper validation based on the simple encodings for each INSPIRE theme, there will be the need for a download in the GML encoding. This can either be as a full bulk download via an INSPIRE Atom feed, or a INSPIRE WFS. We de not expect OAPIF to evolve into a service with complex GML-output in the near future.  
The main barrier for implementing OAPIF services conform INSPIRE is the complexity of the INSPIRE data models. The data needs to be flattened and converted into simple encodings like the GeoJSON encoding which is the OAPIF standard output.
Another barrier is the INSPIRE coordinate reference system (CRS): ETRS89 which is not supported in GeoJSON. Currently it only works with the CRS WGS84.