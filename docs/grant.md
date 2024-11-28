---
title: Grant
parent: Interoperability Framework
layout: default
nav_order: 3
---

# Grant

The entity [Grant]() describes funding awarded to a [Agent](/interoperability-framework/agent/) by a funding body. 
These bodies, both public and private, can be funders, foundations, governments, agencies or institutions.


## Properties

### `local_identifier`
*String* (mandatory): Unique code identifying the [Grant]() in the SKG (if any, otherwise "stateless identifier").

**Suggestion:** Use a URL as a string to make this entity dereferenceable on the Web. For additional information, see the [section 'Local identifiers of entities' of the Interoperability Framework](/interoperability-framework/#local-identifiers-of-entities).

```json
    "local_identifier": "https://doi.org/10.3030/101095129"
```


### `grant_number`
*String* (recommended): Unique code identifiying the [Grant]() at the funder.
 
```json
    "grant_number": "101095129"
```

### `identifiers`
*List* (recommended):  A list of objects representing external identifiers for the entity. Each object is structured as follows.

- `scheme` *String* (mandatory): The scheme for the external identifier (e.g., DOI).
- `value` *String* (mandatory): The external identifier.

```json
    "identifiers": [
        {
            "scheme": "doi"
            "value": "10.3030/101095129"
        }
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. Needed for parsing purposes; fixed to `grant`.

```json
    "entity_type": "grant"
```

### `title`
*String* (optional): Title of the [Grant]().
 
```json
    "title": "GraspOS: next Generation Research Assessment to Promote Open Science"
```

### `abstract`
*String* (optional): The abstract or a description of the [Grant]().
 
```json
    "abstract": "GraspOS aims to build and operate a data infrastructure to support the policy reforms and pave the way towards a responsible research assessment system that embeds OS practices and accelerates its adoption in Europe. GraspOS will focus on extending the EOSC ecosystem with tools and services that will facilitate monitoring the use and uptake of various types of research services and outputs (publications, datasets, software) and will catalyse the implementation of policy-level rewards to foster OS practices. These tools and services will build upon multiple sources of metric data (e.g. OpenCitations, Scholexplorer) including capabilities offered by the EOSC Core, that will be federated in the context of the project, and will take into consideration both contemporary guidelines for Responsible Research Assessment (RRA), like those provided by initiatives like DORA and the Leiden Manifesto, and the suggestions from a diversity of relevant stakeholders. GraspOS will also incorporate piloting activities to co-design, showcase, validate, and evaluate GraspOS’s key results considering domain-specific aspects and different levels of OS-aware RRA, such as the researcher (individual/group), institution, and national level."
```

### `acronym`
*String* (optional): The acronym of the [Grant]().
 
```json
    "acronym": "GraspOS"
```

### `funding_agency`
*String* (optional): The local identifier of an Organisation funding the [Grant]().

```json
    "funder": "EC"
```

### `funding_stream`
*String* (optional): The funding stream of the [Grant]().

```json
    "funding_stream": "Horizon Europe"
```

### `currency`
*String* (mandatory, if `funded_amount` is provided; optional otherwise): Currency of the funded amount, following [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217).

```json
    "currency": "EUR"
```

### `funded_amount`
*Numeric* (optional): Amount funded for the [Grant]().

```json
    "funded_amount": 2.985.441
```

### `keywords`
*List* (optional): A list of keywords for the [Grant]().
 
```json
    "keywords": ["Open science", "mutual learning", "open research"]
```

### `duration`
*Object* (optional): the duration of the [Grant](). It includes the following information:
- `start` *String* (mandatory): The start datetime of the [Grant](). The string should be compliant with the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) datetime string.
- `end` *String* (optional): The end datetime (if any) of the [Grant](). The string should be compliant with the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) datetime string.

```json
    "duration": {
        "start": "2023-01-01T00:00:00",
        "end": "2025-12-31T23:59:59"
    }
```

### `website`
*String* (optional): An URL poiting to the website of the funded project.
 
```json
    "website": "https://graspos.eu"
```

### `beneficiaries`
*List* (optional): A list of the [Organisation](https://skg-if.github.io/interoperability-framework/agent) identifiers funded by the [Grant]().
 
```json
    "beneficiaries": ["org_2", "org_5"]
```

### `contributions`
*List* (optional): A list of objects, each describing an [Agent](https://skg-if.github.io/interoperability-framework/agent), its contribution, and declared affiliations to [Organisations](https://skg-if.github.io/interoperability-framework/agent) in the context of the [Grant](). Each object is structured as follows:
- `by` *String* (mandatory): The identifier of an [Agent](https://skg-if.github.io/interoperability-framework/agent) contributing to the [Grant]().
- `declared affiliations` *List* (recommended): A list of [Organisations](https://skg-if.github.io/interoperability-framework/agent) that reflect the declared affiliations of an [Agent](https://skg-if.github.io/interoperability-framework/agent) for the [Grant]().
- `roles` *List* (recommended): The roles that an [Agent](https://skg-if.github.io/interoperability-framework/agent) had in the [Grant](). Each element in the list is a String compliant with the project roles in [SCoRO](https://sparontologies.github.io/scoro/current/scoro.html#http://purl.org/spar/scoro/ProjectRole), i.e.,
    - `co-applicant`
    - `lead applicant`
    - `project leader`
    - `project manager`
    - `project member`
    - `workpackage leader`