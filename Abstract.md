## Abstract

This document is a guideline for Dutch INSPIRE dataproviders who want to use OGC-API-Features to fulfill their INSPIRE obligations for download services.
The guideline has been written on the bases of the experiance gained from 4 Dutch example implementations of OGC-API-Features of INSPIRE datasets on test beds.
The aim of setting up these test beds and this guideline, was to stimulate the Dutch INSPIRE data providers and hosting organizations to start publishing INSPIRE data as OGC API Features.
By doing this, a greater goal is reached: A better use of Inspire data. Secondly it hopes te contribute to the Inspire community.

A general recommendation to all parties involved is to adjust as much as possible to the INSPIRE requirements as stated in this document.
The most important recommendations for the hosting organizations is to stimulate data providers to start with OGC API features to increase the use of the INSPIRE data.
Data providers are recommended to first orientate on the possible work of other data providers in this field. A roadmap is described with the steps needed to be taken by INSPIRE data providers.
OGC API features use simple encodings as input and output. For the interoperatability, it is important that all member states use the same encoding rules.
The INSPIRE community therefor needs a central organization for the mapping of the complex data models to the simple encodings.

An important conclusion is that non of the tools used in the examples fulfill all INSPIRE requirements and no toolings is known to do so at this moment (August 2022).
The INSPIRE commutity is recommended to stimulate the market to solve this.
The main barrier for implementing OAPIF services conform INSPIRE is the complexity of the INSPIRE data models.
The data needs to be flattened and converted into simple encodings like the GeoJSON encoding which is the OAPIF standard encoding for output.
Another barrier is the support for coordinate reference system (CRS): ETRS89 wich is required bij INSPIRE. Officially, only WGS84 is supported in GeoJSON.
New standards like OGC-API-Features - part 2 and an extension to GeoJSON (JSON FG) will help to solve this CRS problem, once tooling has adjusted to them.