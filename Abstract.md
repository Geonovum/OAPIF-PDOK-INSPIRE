## Abstract

This document was written for Dutch INSPIRE data providers who wanted to use OGC-API-Features to fulfil their INSPIRE obligations for download services.
It has been written on the bases of the experience gained from 4 Dutch example implementations of OGC-API-Features of INSPIRE datasets on test beds created in 2021.
The aim of setting up these test beds and this document, has been to stimulate the Dutch INSPIRE data providers and hosting organizations to start publishing INSPIRE data as OGC API Features.
By doing this, a greater goal is reached: A better use of Inspire data. Secondly it hopes to contribute to the Inspire community.

A general recommendation to all parties involved is to adjust as much as possible to the INSPIRE requirements as stated in this document.
The most important recommendations for the hosting organizations is to stimulate data providers to start with OGC API features to increase the use of the INSPIRE data.
Data providers are recommended to first orientate on the possible work of other data providers in this field. A roadmap is described with the steps needed to be taken by INSPIRE data providers.
OGC API features use simple encodings as input and output. For the interoperability, it is important that all member states use the same encoding rules.
The INSPIRE community therefor needs a central organization for the mapping of the complex data models to the simple encodings.

The main barrier for implementing OAPIF services conform INSPIRE is the complexity of the INSPIRE data models.
The data needs to be flattened and converted into simple encodings like the GeoJSON encoding which is the OAPIF standard encoding for output.
Another barrier is the support for coordinate reference system (CRS): ETRS89 which is required by INSPIRE. Officially, only WGS84 is supported in GeoJSON.
New standards like OGC-API-Features - part 2 and an extension to GeoJSON (JSON FG) will help to solve this CRS problem, once tooling has adjusted to them.

An important conclusion is that none of the tools used in the examples fulfil all INSPIRE requirements and no tooling is known to do so at this moment (August 2022).
The INSPIRE community is recommended to stimulate the market to solve this.
This conclusion resulted in an open tender for adjusting these tools. As a result from that tender, 3 tools were adjusted in the beginning of 2023.
How they now do comply to the standards is shown in the new [Guideline](https://geonovum.github.io/ogc-api-features-guideline) from repository https://github.com/Geonovum/ogc-api-features-guideline. 
