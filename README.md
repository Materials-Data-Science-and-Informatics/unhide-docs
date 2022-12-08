<img src="https://s3.desy.de/hackmd/uploads/upload_c3ba77674d5c58417c6df0f195b0c4ac.png" alt="unHIDE logo" height = "75">

## unHIDE - unified Helmholtz Information and data exchange

### Authors
Pier Luigi Buttigieg [<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/ORCID_iD.svg/2048px-ORCID_iD.svg.png" alt="ORCID Logo" height ="20"> 0000-0002-4366-3088](https://orcid.org/0000-0002-4366-3088)
Volker Hofmann [<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/ORCID_iD.svg/2048px-ORCID_iD.svg.png" alt="ORCID Logo" height ="20"> 0000-0002-5149-603X](https://orcid.org/0000-0002-5149-603X)

## Introduction & Scope

Research across the Helmholtz Association (HGF) depends and thrives on a complex network of inter- and multidisciplinary collaborations which spans across its 18 Centres and beyond. 

However, the (meta)data generated through the HGF's research and operations is typically siloed within institutional infrastructure and often within individual teams. The result is that the wealth of the HGF's (meta)data is stored and maintained in a scattered manner, and cannot be used to its full value to scientists, managers, stratgists, and policy makers. 

To address this challenge, the Helmholtz Metadata Collaboration (HMC) is launching the **unified Helmholtz Information and Data Exchange (unHIDE)**. This initiative seeks to create a lightweight and sustainable interoperability layer to interlink data infrastructures and provide greater, cross-organisational access to the HGF's (meta)data and information assets. Using proven and globally adopted knowledge graph technology (Box 1), unHIDE will develop a comprehensive association-wide Knowledge Graph (KG) the "Helmholtz-KG": a solution to connect (meta)data, information, and knowledge. 

> *Box 1*
> 
> What is a Knowledge Graph?
> - A "graph", from graph theory, is a structure that models pairwise connections between objects using "nodes" connected by "edges".
> - A "knowledge graph" uses such a graph structure to capture knowledge about how a collection of things (represented as nodes) relate to one another (via edges). This helps organisations keep track of their collective knowledge, especially in complex and rapidly changing scenarios.
> - Social networks are perhaps the best known graphs, that store knowledge about who knows whom and how, what their interests are, what groups they belong to, and what content they create and interact with.

With the implementation of the Helmholtz-KG, unHIDE will create substantial additinal value for the Helmholtz digital ecosystem and its interconnectivity:

**With the development of the Helmholtz-KG, unHide will:** 
- increase discoverability and actionability of HGF data across the whole Association* 
- motivate enhancement of (meta)data quality [1] and interoperability
- provide overviews and diagnositcs of the HGF dataspace and digital assets
- allow for traceable and reproducible recovery of (meta)data to enhance research
- support connectivity of HGF data to interact with global infrastructures and projects
- act as a central access and distribution point for stakeholders within and beyond the HGF

## Architecture & Implementation

### Foundational architecture

The Helmholtz Knowledge Graph (Helmholtz-KG) aims to enhance the HGF's digital capacities, transparency, and productivity through dissemination and implementation of Linked Data principles (Box 2). Thus, unHIDE will build the Helmholtz-KG on mature web architecture and state-of-the-art semantic web technologies. This will ensure reliability and compatibility with global systems, while also exploring innovative approaches to maximise the Helmholtz-KG's ability to accelerate research and operations. 

> Box 2
>
> Graph data is:
> - Open-world, allowing resilient operations with novel or unexpected data flows
> - Faster than using SQL and associated JOIN operations
> - Better suited to integrating data from heterogeneous sources
> - Better suited to situations where the data model is complex and (rapidly) evolving
> 
> **[Learn more: https://www.w3.org/2013/data/](https://www.w3.org/2013/data/)**

To ensure ease of use, the Helmholtz-KG will be based on a lightweight and internationally adopted interoperabiliy architecture based on schema.org semantics and JSON-LD serialisation [2]. This architecture widely used by data producers - including public, private, and governmental data systems - to link and expose scattered, diverse digital assets. By reusing this architecture, unHIDE will ensure that the Helmholtz-KG is able to natively interoperate with global systems.

### Modular design & Extensibility
While the foundation of the Helmholtz-KG will reuse standard web architectural elements and proven, globally adopted conventions, the KG itself is modular by nature: Graphs can be merged, split, independently managed, and readily interfaced with other digital resources without compromising core integrity and functionality. In this manner, Helmholtz data scientists and engineers will be able to propose and test extensions to the graph with minimal overhead, which wll support the ability to extend into existing and well-established systems in the HGF.

This modularity (especially the ability to securely and independently manage parts of the overall graph) will also allow to realize different modes of access to digital assets (e.g. respecting sensitivity and confidentiality but also permitting full openness). The initial implementation of the Helmholtz-KG will not contend with sensitive or confidential data, but such capacities (e.g. user management, license recognition across (meta)data holdings, and authentication) can be explored and implemented when the core technology and operational procedures are stabilised. 

The backbone architecture of the Helmholtz Knowledge Graph will be licensed under [CC0/CCBY](https://creativecommons.org/about/cclicenses/) to enable crosswalks to the outside world and gain visibility as e.g. a sub-cloud of the [Linked Open Data Cloud](https://lod-cloud.net/).

### Inspiration

The implementation the Helmholtz-KG architecture is inspired by the federation of stakeholders in IOC-UNESCO's Ocean Data and Information System (ODIS), interconnected by the [ODIS Architecture](https://book.oceaninfohub.org/) [2], and rendered into a knowledge graph federating over 50 partners across the globe by the Ocean InfoHub Project (OIH). Personnel from the HMC's Earth and Environment Hub chair the ODIS federation and lead the technical implementation of OIH, offering direct alignment with unHIDE.


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

## References
- [1] https://5stardata.info/en/
- [2] https://www.w3.org/TR/2014/REC-json-ld-20140116/
- [3] https://book.oceaninfohub.org/publishing/publishing.html
- [4] https://www.researchobject.org/ro-crate/
- [6] https://www.openarchives.org/pmh/
