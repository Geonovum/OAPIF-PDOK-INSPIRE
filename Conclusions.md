## Conclusions

1. An important conclusion is that as long as there is no proper validation based on the simple encodings for each INSPIRE theme, there will always be the need for a download in the GML encoding. This can eihter be as a full bulkdownload via an INSPIRE Atom feed, or a INSPIRE WFS. We de not expect OAPIF to evolve into a service with complex GML-output. 
2. OAPIF can be considerated more as an additional service, than a replacing services next to the OGC WFS 2.0. They both have their advantages and disadvantages, and serve different type of users.
3. The main barrier for implementing OAPIF services conform INSPIRE is the complexity of the INSPIRE datamodels. The data needs to be flattened and converted in simple encodings.
4. The second less important barrier is the projection system (CRS). There is a specification for implementing more than one CRS: [[PUB-5]]. It is not clear whether applications support this already, but they will probably do so in the future. It is also a problem that can be solved at the client side. The applications used for this research did not support it yet.
