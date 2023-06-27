# Building Block View

:::{admonition} Arc42 Information
:class: note, dropdown
**Content**

The building block view shows the static decomposition of the system
into building blocks (modules, components, subsystems, classes,
interfaces, packages, libraries, frameworks, layers, partitions, tiers,
functions, macros, operations, data structures, ...) as well as their
dependencies (relationships, associations, ...)

This view is mandatory for every architecture documentation. In analogy
to a house this is the *floor plan*.

**Motivation**

Maintain an overview of your source code by making its structure
understandable through abstraction.

This allows you to communicate with your stakeholder on an abstract
level without disclosing implementation details.

**Form**

The building block view is a hierarchical collection of black boxes and
white boxes (see figure below) and their descriptions.

![Hierarchy of building blocks](images/05_building_blocks-EN.png)

**Level 1** is the white box description of the overall system together
with black box descriptions of all contained building blocks.

**Level 2** zooms into some building blocks of level 1. Thus it contains
the white box description of selected building blocks of level 1,
together with black box descriptions of their internal building blocks.

**Level 3** zooms into selected building blocks of level 2, and so on.

See [Building Block View](https://docs.arc42.org/section-5/) in the
arc42 documentation.
:::

## Whitebox Overall System

:::{admonition} Arc42 Information
:class: note, dropdown

Here you describe the decomposition of the overall system using the
following white box template. It contains

-   an overview diagram

-   a motivation for the decomposition

-   black box descriptions of the contained building blocks. For these
    we offer you alternatives:

    -   use *one* table for a short and pragmatic overview of all
        contained building blocks and their interfaces

    -   use a list of black box descriptions of the building blocks
        according to the black box template (see below). Depending on
        your choice of tool this list could be sub-chapters (in text
        files), sub-pages (in a Wiki) or nested elements (in a modeling
        tool).

-   (optional:) important interfaces, that are not explained in the
    black box templates of a building block, but are very important for
    understanding the white box. Since there are so many ways to specify
    interfaces why do not provide a specific template for them. In the
    worst case you have to specify and describe syntax, semantics,
    protocols, error handling, restrictions, versions, qualities,
    necessary compatibilities and many things more. In the best case you
    will get away with examples or simple signatures.

***Overview Diagram***

Motivation

:   *text explanation*

Contained Building Blocks

:   *Description of contained building block (black boxes)*

Important Interfaces

:   *Description of important interfaces*

Insert your explanations of black boxes from level 1:

If you use tabular form you will only describe your black boxes with
name and responsibility according to the following schema:

| **Name**              | **Responsibility**                         |
| --------------------- | ------------------------------------------ |
| *black box 1*         |  *Text*                                    |
| *black box 2*         |  *Text*                                    |

If you use a list of black box descriptions then you fill in a separate
black box template for every important building block . Its headline is
the name of the black box.

You can specify the inner structure of (some) building blocks from
level 1 as white boxes.

You have to decide which building blocks of your system are important
enough to justify such a detailed description. Please prefer relevance
over completeness. Specify important, surprising, risky, complex or
volatile building blocks. Leave out normal, simple, boring or
standardized parts of your system.
:::
## Whitebox Overall System

A rough overview of UnHIDE related repositories under the [project](https://codebase.helmholtz.cloud/hmc/hmc-public/unhide)
are shown in the figure below.
![repository_overview](../../diagrams/unhide_overview_repositories.svg)

The *administration repository* is private and used for project related things that should not be made
public. Therefore you can link of to secret information from the docs to there.

The *documentation repository* is for the documentation of the overall project, which basically is
what you are reading here and now.

The *unhide-docker* repository contains different docker files for full or partly deployment of the 
whole project. Docker files for developments environments also go there.

The *data-harvesting* repository is a python library with a command line tool to run harvesters and
data processing. Functionality should be kept general where ever possible and only UnHIDE 
specifically configured.

The *unhide-ui* repository contains the [web front-end](https://search.unhide.helmholtz-metadaten.de) for UnHIDE, 
exposing the full text search through the data.
Currently, it also contains the backend pieces which are needed for the full text search index, i.e 
the indexer, an API and some SOLR config related things and schemas.