---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.12
    jupytext_version: 1.6.0
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Deployment View

:::{admonition} Arc42 Information
:class: note, dropdown
**Content**


The deployment view describes:

1.  technical infrastructure used to execute your system, with
    infrastructure elements like geographical locations, environments,
    computers, processors, channels and net topologies as well as other
    infrastructure elements and

2.  mapping of (software) building blocks to that infrastructure
    elements.

Often systems are executed in different environments, e.g. development
environment, test environment, production environment. In such cases you
should document all relevant environments.

Especially document a deployment view if your software is executed as
distributed system with more than one computer, processor, server or
container or when you design and construct your own hardware processors
and chips.

From a software perspective it is sufficient to capture only those
elements of an infrastructure that are needed to show a deployment of
your building blocks. Hardware architects can go beyond that and
describe an infrastructure to any level of detail they need to capture.

**Motivation**


Software does not run without hardware. This underlying infrastructure
can and will influence a system and/or some cross-cutting concepts.
Therefore, there is a need to know the infrastructure.

Maybe a highest level deployment diagram is already contained in section
3.2. as technical context with your own infrastructure as ONE black box.
In this section one can zoom into this black box using additional
deployment diagrams:

-   UML offers deployment diagrams to express that view. Use it,
    probably with nested diagrams, when your infrastructure is more
    complex.

-   When your (hardware) stakeholders prefer other kinds of diagrams
    rather than a deployment diagram, let them use any kind that is able
    to show nodes and channels of the infrastructure.

See [Deployment View](https://docs.arc42.org/section-7/) in the arc42
documentation.

## Infrastructure Level 1 {#_infrastructure_level_1}

Describe (usually in a combination of diagrams, tables, and text):

-   distribution of a system to multiple locations, environments,
    computers, processors, .., as well as physical connections between
    them

-   important justifications or motivations for this deployment
    structure

-   quality and/or performance features of this infrastructure

-   mapping of software artifacts to elements of this infrastructure

For multiple environments or alternative deployments please copy and
adapt this section of arc42 for all relevant environments.

***\<Overview Diagram>***

Motivation

:   *\<explanation in text form>*

Quality and/or Performance Features

:   *\<explanation in text form>*

Mapping of Building Blocks to Infrastructure

:   *\<description of the mapping>*
:::

## Infrastructure Level 1


UnHIDE is deployed on [HDF-cloud](https://www.fz-juelich.de/en/ias/jsc/systems/scientific-clouds/hdf-cloud)
at the Jülich supercomputing center. The cloud is an open stack instance hosted as a service by the supercomputing center.

The choice to host there, was to host on (institute) extern reliable infrastructure, for low cost.
So far the support is very nice and quick and there are no issues.
UnHIDE runs on a single virtual machine, while data is mounted via a volume.



***\<Overview Diagram>***

On the HDF-Cloud virtual machine the data pipeline with all the harvesters is executed through a cron job periodically.
(So the data pipeline is not event based, with for now is for simplicity.) The overview of this 
deployment system is shown below in Fig. @fig:overview_deploy.
![overview_deploy](../../diagrams/unhide_deployment_overview.svg){#fig:overview_deploy}
The figure clearly shows all docker container spawned for the deployment of UnHIDE. 
Each part and service is running in its own docker container, which can communicate with other containers
over an internal network. All connections from and to the outside world, i.e. our domains on the internet, go through
a reverse proxy using Nginx with ssl.

### Deployment of the documentation

![repository_overview](../../diagrams/documentation_deployment.svg)

The Figure above demonstrates, how the UnHIDE documentation is currently deployed.
Because `gitlab pages` is not enabled for our usecase and needs on the gitlab the unhide project is in,
we decided to mirror the documentation repository to [github](https://github.com/Materials-Data-Science-and-Informatics/unhide-docs) and deploy the documentation from there
over github pages.

