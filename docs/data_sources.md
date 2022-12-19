## Data Sources

#### Initial Scope
Initial efforts of the Helmholtz-KG implementation will focus on the representation of (meta)data describing the following digital core assets: 
- Documents / Publications
- published Datasets
- Software
- Institutions
- Infrastructure & Ressources
- Researchers & Experts
- Projects

The representation of these instances will semantically alligned with the [schema.org](https://schema.org/docs/full.html) vocabulary, a globally adopted standard offering a relaxed frame for the representation of heterogeneous data. Following the initial implementation the semantic expresivness of the graph can be increased by integrating domain ontologies such as the HMC developed [Helmholtz Digitization Ontology](https://codebase.helmholtz.cloud/hmc/hmc-public/hob/hdo) (HDO), which provides precise and comprehensive semantics of the concepts and practices used to manage digital assets.

#### Data Ingestion Process
The Helmholtz-KG will offer multiple options for existing and emerging HGF infrastructures, data providers, and communities to declare their resources and digital assets in the graph for discoverability. We will prioritise the recommended publishing process for structured data on the web (as used by ODIS/OIH and many others): data providers would either 1) provide a sitemap or robots.txt file which will direct harvesting software to a collection of JSON-LD/schema.org documents or 2) expose JSON-LD snippets in the document head element of a web resource (i.e. HTML document). Both approaches are described in the publisher documentation of the Ocean InfoHub Project [3].

Alternative publication patterns may include -- HTTP-accessible [RO-Crate](https://www.researchobject.org/ro-crate/) [4] metadata in `ro-crate-metadata.json`, the exposure of structured metadata records via the Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH) [5] or properly documented RESTful APIs in general [6]. We will explore the need and feasibility of alternate publishing and harvesting modes during the course of unHIDE.

HMC personnel will support the onboarding of data providers as well as the implementation of custom (meta)data pipelines / connectors and mapping to RDF / JSON-LD, if necessary and where appropriate.

#### Potential Data Providers 
Within the HGF a number of relevant web-based data architectures exist. These will be targeted by unHIDE to collaborate on building interfaces to the Helmholtz-KG.

The initial implementation fill focus on: 
- HGF institutional (data) repositories
- Central Libraries of Helmholtz Research Centers
- Domain-specific (data) repositories relevant to HGF
- Helmholtz GitLab Instances

Subsequent efforts will include further ressources such as:
- Helmholtz FAIR digital objects (via HMC)
- Helmholtz Ontology Base (HOB) (via HMC)
- The Helmholtz [software directory](https://helmholtz.software/) (centrally maintained by HIFIS)
- [Helmholtz Data Challenges Platform](https://helmholtz-data-challenges.de/)
- other ressources of the Helmholtz Metadata Collaboration (HMC) 
- Content management systems (CMS)
- Helmholtz Computing centers (e.g. JSC)
- Helmholtz Federated IT Services (HIFIS)
- Helmholtz instruments and sensor databases (e.g. @GFZ, DEPAS @AWI, RDMInfoPool, etc.)
- Helmholtz Scientific Project Workflow Platform (HELIPORT)
- [Helmholtz Imaging Modalities database](https://modalities.helmholtz-imaging.de/)
- Laboratory information management systems (LIMS)
- Helmholtz Open Science Office

