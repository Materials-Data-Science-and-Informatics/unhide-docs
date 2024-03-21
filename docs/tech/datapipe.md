# Data pipeline

In UnHIDE metadata about research outputs is harvested from connected providers and partners. 
Then the original metadata is 'uplifted', i.e semantically enriched and or completed, 
where possible from aggregated data or schema.org semantics as an example of how it can be.

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


The technical implementation is currently a minimal running version, by exposing each 
component and functionality through the command line interface `hmc-unhide` and then using 
cron jobs to run them from time to time. On the deployment instance this can be run monthly or
weekly. In the longer term, the pipeline orchestration itself should become more sophisticated.
For this one could deploy a workflow manager with provenance tracking like (AiiDA)
or one with less overhead depending on the needs, also if one wants to move to a more event based system
with more fault tolerance for errors of individual records or data sources. Currently, 
in the minimal implementation there is the risks that a not caught failure in a subtask 
fails a larger part of the pipeline. Which is then only logged, but has to be resolved in a manual way.

