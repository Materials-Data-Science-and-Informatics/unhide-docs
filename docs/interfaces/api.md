# API

Public metadata in UnHIDE is also exposed with a small RESTful API using the fastapi library.
The web frontend talks to this API, but it can also be used by other purposes.

The API exposes the indexed versions of the json-ld metadata records, the individual original data records, 
the by UnHIDE uplifted data records as well as some statistics on the data collection.

The implemented of the API can be found [here](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide/unhide-ui/-/tree/main/api).

## Example queries

### Overview of indexed data content:

https://api.unhide.helmholtz-metadaten.de/search?rows=0&include_facets=false

This call will receive a record count list for all schema.org types and combined categories.
```
docs	[]
count	652509
counts	
Dataset	259326
DigitalDocument	244063
ScholarlyArticle	66294
CreativeWork	40466
Person	25711
Report	4965
DataCatalog	3557
MediaObject	2094
Book	1621
PublicationIssue	1488
Organization	990
Thesis	713
Chapter	541
Collection	247
SoftwareSourceCode	192
ImageObject	102
AudioObject	101
Article	18
Periodical	6
Event	4
PresentationDigitalDocument	4
Photograph	3
Service	2
BlogPosting	1
Experts	26701
facets	[]
```


### Receiving a specific metadata entry by PID:

As example for the doi: https://doi.pangaea.de/10.1594/PANGAEA.929262

This API call will
```
https://api.unhide.helmholtz-metadaten.de/source?id=https%3A%2F%2Fdoi.org%2F10.1594%2FPANGAEA.929262
```
will return a json object containing the original json-ld metadata record as provided by the provider. 

### Receiving a specific by UnHIDE uplifted metadata entry:

As example for the doi: https://doi.pangaea.de/10.1594/PANGAEA.929262

This API call will
```
https://api.unhide.helmholtz-metadaten.de/uplifted?id=https%3A%2F%2Fdoi.org%2F10.1594%2FPANGAEA.929262
```
will return a json object containing the UnHIDE uplifted json-ld metadata record as provided by the provider. 