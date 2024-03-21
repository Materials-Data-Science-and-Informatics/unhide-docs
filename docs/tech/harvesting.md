# Data harvesting: extracting metadata from the web

How does UnHIDE harvested data?

Data harvesting and mining for the knowledge graph is done by `Harvester classes`.
For each interface a specific Harvester class should be implemented.
All Harvester classes should inherit from existing Harvesters or the [`BaseHarvester`](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide/data_harvesting/-/blob/main/data_harvesting/base_harvester.py?ref_type=heads), which currently specifies that:

1. Each harvester needs a `run` method
2. Can read from the [`config.yml`](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide/data_harvesting/-/blob/main/data_harvesting/configs/config.yaml?ref_type=heads)
3. Reads from a `<harvesterclass>.last_run` file the time the harvester was last run

Implemented harvester classes include:

|  Name (Cli) | Class Name | Interface | Comment |
|-------------|------------|-----------|---------|
|sitemap     | SitemapHarvester | sitemaps | Selecting record links from the sitemap requires expression matching. Relies on the advertools lib.|
|oai | OAIHarvester | OAI-PMH | Relies on the oai lib. For the library providers, dublin core is converted to schema.org |
|git | GitHarvester | Git, Gitlab/Github API | Relies on codemetapy and codemeta-harvester as well as gitlab/github APIs.  |
|datacite | DataciteHarvester | REST API & GraphQL endpoint | schema.org extracted through content negotiation.|
|feed | FeedHarvester | RSS & Atom Feeds | Relies on the atoma library, and also only works if on the landing pages schema.org metadata can be extracted. Can only get recent data, useful for event metadata.|
|indico | IndicoHarvester | Indico REST API | Directly extracts schema.org metadata through API, requires an access token |

Json-ld metadata from landing pages of records is extracted via the `extruct` library, if it cannot be directly retrieved through some standardized interface.

All harvesters are exposed on the `hmc-unhide` commandline interface.
They store the extracted metadata per default in the internal data model [`LinkedDataObject`](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide/data_harvesting/-/blob/main/data_harvesting/data_model.py?ref_type=heads).
Which has a serialization with some provenance information, original source data and uplifted data and provides method for validation.

In a single central yaml configuration file called [`config.yml`](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide/data_harvesting/-/blob/main/data_harvesting/configs/config.yaml?ref_type=heads), specifies for each harvester class the sources to harvest and harvester or source specific configuration.