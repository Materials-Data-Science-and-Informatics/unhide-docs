# Data pipeline

In UnHIDE data is harvested from connected providers and partners. 
Then data is 'uplifted', i.e semantically enriched and or completed, 
where possible from aggregated data or schema.org semantics.

## Overview

All full view of the UnHIDE data pipeline is shown below:
![overview](../diagrams/unhide_harvester_datapipeline.svg)

In a single central yaml configuration [file](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide/data_harvesting/-/blob/main/data_harvesting/configs/config.yaml?ref_type=heads) called `config.yml`, all sources from data providers 
for the harvesters are listed. Further it defines provider specific things that a certain Harvester
class might need to find the metadata files. The configuration file also specifies since when changes
should be harvested. This allows for a frequent run of all harvesters only picking up lately new and 
changed metadata entries.

The harvesters then extract all metadata files specified from a given provider. 
The files are then in certain cases converted and overall validated for correct schema.org content.
The content of these json-ld files is stored together with some metadata of the harvesters in an 
internal json-serializable UnHIDE DataModel class. This class tracks the original data content as well
as the uplifted version, as well a reproducible detail level of provenance data with so called
RDF patches. More detail on this con be found [here](./harvesting.md).

In the `config.yml` also configuration for the `Aggregator` class is stored, which specifies, what
data operations in terms of uplifted should be performed on the incoming data.
The serialization of the UnHIDE DataModel files forms the `ground truth source` for UnHIDE.
More detail on this can be found [here](./uplifting.md).

To now fulfill different use cases of our stakeholders, this data flows now further in two direction.

In the first direction it is imported into a single rdf graph database using Apache Jena. 
This database can be accessed over a SPARQL endpoint exposed via Jena Fuseki.

The second direction is there to provide full text search on the data to end users.
For this an index of each uplifted data record is constructed and uploaded into a single SOLR index,
which is exposed to a certain extend via a custom fastAPI. A web front end using the javascript library 
React provides a user interface for the full text search and supports special use cases as a service
to certain stakeholder groups. 