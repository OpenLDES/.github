<div align="center">

[//]: # (  <img src="https://raw.githubusercontent.com/OpenLDES/OpenLDES/main/logos/openldes-logo-square.png" alt="OpenLDES logo" width="120"/>)
  <h1>OpenLDES</h1>
  <p><strong>Open Linked Data Event Streams</strong></p>
  <p>
    <a href="https://openldes.org">Website</a> ·
    <a href="https://openldes.github.io/LDESServer/latest/">LDES Server Docs</a> ·
    <a href="https://openldes.github.io/Linked-Data-Interactions/latest/">Linked Data Interactions Docs</a> ·
    <a href="https://w3id.org/ldes/specification">LDES Spec</a> ·
  </p>
</div>

---

## What is OpenLDES?

**Linked Data Event Streams (LDES)** is an open standard and ecosystem that lets data publishers
share an ever-growing collection of immutable facts — called *members* — in a way that allows any
consumer to cheaply replicate and continuously synchronise with the full dataset.

OpenLDES provides the **reference implementations, tooling and specifications** that make it
straightforward to:

- Publish datasets as a standards-compliant LDES (server side).
- Receive, transform and forward Linked Data between systems (pipeline side).
- Consume and replicate existing streams (client side).

The work is rooted in the [W3C TREE hypermedia specification](https://w3id.org/tree/specification)
and is partly funded by
the [Interoperable Europe (SEMIC) programme](https://joinup.ec.europa.eu/interoperable-europe) of
the European Commission.

---

## 🚀 Where to Start

| I want to…                                                        | Start here                                                                                                           |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Publish** data as an LDES                                       | [Onboarding-Example → minimal-server](https://github.com/OpenLDES/Onboarding-Example/tree/main/minimal-server)       |
| **Consume** an existing LDES                                      | [Onboarding-Example → minimal-client](https://github.com/OpenLDES/Onboarding-Example/tree/main/minimal-client)       |
| **Transform** Linked Data in a pipeline                           | [Onboarding-Example → minimal-workbench](https://github.com/OpenLDES/Onboarding-Example/tree/main/minimal-workbench) |
| **Sync** Linked Data in a pipeline to a relational database table | [Onboarding-Example → ldes-to-database](https://github.com/OpenLDES/Onboarding-Example/tree/main/ldes-to-database)   |
| Read the **full tutorial**                                        | [Onboarding-Example](https://github.com/OpenLDES/Onboarding-Example)                                                 |
| Read the **LDES specification**                                   | [LinkedDataEventStreams](https://github.com/OpenLDES/LinkedDataEventStreams)                                         |

---

## 🏛️ Core Projects

### [LDESServer](https://github.com/OpenLDES/LDESServer)

> The **reference LDES server** — ingest, store, fragment and publish event streams.

Built with Spring Boot (Java), the LDES Server is a configurable, production-ready component that
exposes REST APIs to:

- **Ingest** members via HTTP or Kafka.
- **Fragment** streams by pagination, time, geography or a reference property.
- **Serve** event stream pages to any LDES client.
- **Maintain** streams through compaction, retention and deletion.

The server is fully modular: enable only the profiles you need and deploy it as a Docker image or a
Maven application backed by PostgreSQL.

📖 [Documentation](https://openldes.github.io/LDESServer/latest/) |
🐳 [Docker Hub](https://hub.docker.com/r/openldes/ldes-server)

---

### [Linked-Data-Interactions](https://github.com/OpenLDES/Linked-Data-Interactions)

> A **toolkit of pipeline components** to receive, transform and output Linked Data.

The LDI repository bundles reusable building blocks that sit between data sources and the LDES
Server (or any Linked Data sink). It supports two execution frameworks:

| Framework            | Description                                                                |
|----------------------|----------------------------------------------------------------------------|
| **LDI Orchestrator** | Lightweight Spring Boot runner — ideal for simple pipelines                |
| **Apache NiFi**      | Full-featured data-flow platform — ideal for complex, multi-step pipelines |

Key components include:

| Component                  | What it does                                          |
|----------------------------|-------------------------------------------------------|
| LDES Client                | Replicates and synchronises with a remote LDES        |
| Create Version Object      | Converts a state object into a versioned LDES member  |
| Version Materialisation    | Reconstructs the current state from versioned members |
| SPARQL Construct / Select  | Transforms or queries Linked Data with SPARQL         |
| NGSI v2 → LD               | Converts NGSI v2 JSON to NGSI-LD                      |
| GeoJSON → WKT              | Converts GeoJSON geometries to WKT                    |
| RDF4J Repo Materialisation | Materialises an LDES into a triplestore               |

📖 [LDI Core docs](https://github.com/OpenLDES/Linked-Data-Interactions/blob/main/ldi-core/README.md) | [LDI Orchestrator docs](https://github.com/OpenLDES/Linked-Data-Interactions/blob/main/ldi-orchestrator/README.md)

---

## 📦 Other Repositories

### Tutorials & Examples

| Repository                                                            | Description                                                  |
|-----------------------------------------------------------------------|--------------------------------------------------------------|
| [Onboarding-Example](https://github.com/OpenLDES/Onboarding-Example)  | Step-by-step tutorials for publishers, consumers and brokers |
| [LDES-Demo (not up-to-date)](https://github.com/OpenLDES/LDES-Demo)   | Demo applications showcasing end-to-end LDES usage with Nifi |
| [Azure-Demo (not up-to-date)](https://github.com/OpenLDES/Azure-Demo) | LDES deployment on Microsoft Azure                           |

### Documentation

| Repository                                                                            | Description                           |
|---------------------------------------------------------------------------------------|---------------------------------------|
| [LDES-Tech-documentation](https://github.com/OpenLDES/LDES-Tech-documentation)        | Published technical docs site         |
| [onboarding-docs (not up-to-date)](https://github.com/OpenLDES/onboarding-docs)       | Onboarding and getting-started guides |
| [LDES-Subject-Pages (not up-to-date)](https://github.com/OpenLDES/LDES-Subject-Pages) | Subject-oriented reference pages      |

### Testing & Quality

| Repository                                                                                                | Description                                           |
|-----------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| [LDES-E2E-testing](https://github.com/OpenLDES/LDES-E2E-testing)                                          | End-to-end test suite                                 |
| [LDES-performance-testing](https://github.com/OpenLDES/LDES-performance-testing)                          | Performance and load testing harness                  |
| [LDES-E2E-message-generator](https://github.com/OpenLDES/LDES-E2E-message-generator)                      | Generates synthetic LDES member messages for testing  |
| [LDES-E2E-ldes-server-simulator](https://github.com/OpenLDES/LDES-E2E-ldes-server-simulator)              | Lightweight LDES server simulator for testing         |
| [LDES-E2E-message-sink](https://github.com/OpenLDES/LDES-E2E-message-sink)                                | HTTP sink that captures LDES members for verification |
| [LDES-E2E-ldes-list-fragments (not up-to-date)](https://github.com/OpenLDES/LDES-E2E-ldes-list-fragments) | Lists and inspects LDES fragments during testing      |
| [LDES-E2E-mongodb-rest-api (not up-to-date)](https://github.com/OpenLDES/LDES-E2E-mongodb-rest-api)       | MongoDB REST API used in end-to-end scenarios         |
| [TestBed-Shacl-Validator (not up-to-date)](https://github.com/OpenLDES/TestBed-Shacl-Validator)           | SHACL-based validation for LDES members               |
| [LDES-Testbed (not up-to-date)](https://github.com/OpenLDES/LDES-Testbed)                                 | Integration test environment                          |

### Tooling & Utilities

| Repository                                                                              | Description                                             |
|-----------------------------------------------------------------------------------------|---------------------------------------------------------|
| [LDES-Data-Migrator (not up-to-date)](https://github.com/OpenLDES/LDES-Data-Migrator)   | Migrates data between LDES server v2.x to v3.x          |
| [DCATAggregator (not up-to-date)](https://github.com/OpenLDES/DCATAggregator)           | Aggregates DCAT metadata across multiple LDES endpoints |
| [Dataspace-Connector (not up-to-date)](https://github.com/OpenLDES/Dataspace-Connector) | Connector for dataspace / IDSA integration              |

---

## 🤝 Contributing

We welcome contributions of all kinds — bug reports, feature requests, documentation improvements
and code.

1. Browse the [open issues](https://github.com/issues?q=org%3AOpenLDES+is%3Aopen) across the
   organisation.
2. Fork the relevant repository and open a pull request.

---

You can find the code of conduct [here](CODE_OF_CONDUCT.md).

## 📜 License

The OpenLDES repositories are licensed under the [EUPL (European Union Public License)](LICENSE).
