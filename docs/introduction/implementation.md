# Architecture & Implementation

## Foundational architecture

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

## Modular design & Extensibility
While the foundation of the Helmholtz-KG will reuse standard web architectural elements and proven, globally adopted conventions, the KG itself is modular by nature: Graphs can be merged, split, independently managed, and readily interfaced with other digital resources without compromising core integrity and functionality. In this manner, Helmholtz data scientists and engineers will be able to propose and test extensions to the graph with minimal overhead, which will support the ability to extend into existing and well-established systems in the HGF.

This modularity (especially the ability to securely and independently manage parts of the overall graph) will also allow to realize different modes of access to digital assets (e.g. respecting sensitivity and confidentiality but also permitting full openness). The initial implementation of the Helmholtz-KG will not contain sensitive or confidential data, but such capacities (e.g. user management, license recognition across (meta)data holdings, and authentication) can be explored and implemented when the core technology and operational procedures are stabilised. 

The backbone architecture of the Helmholtz Knowledge Graph will be licensed under [CC0/CCBY](https://creativecommons.org/about/cclicenses/) to enable crosswalks to the outside world and gain visibility as e.g. a sub-cloud of the [Linked Open Data Cloud](https://lod-cloud.net/).

## Inspiration

The implementation of the Helmholtz-KG architecture is inspired by the federation of stakeholders in IOC-UNESCO's Ocean Data and Information System (ODIS), interconnected by the [ODIS Architecture](https://book.oceaninfohub.org/) [2], and rendered into a knowledge graph federating over 50 partners across the globe by the Ocean InfoHub Project (OIH). Personnel from the HMC's Earth and Environment Hub chair the ODIS federation and lead the technical implementation of OIH, offering direct alignment with unHIDE.

