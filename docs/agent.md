---
title: Agent
parent: Interoperability Framework
layout: default
nav_order: 2
---

# Agent
 
The [Agent] entity represents an individual (e.g., a person, an organisation, or another kind of entity being able to act) who is involved in the creation, publication, dissemination, etc. of a [Research product]. An [Agent] can be an author, a reviewer, an editor, a publisher, a researcher, or any other stakeholder involved in the scholarly communication process.

This page describes the metadata fields for an [Agent] and all its subtypes (i.e., persons and organisations).


## Properties

### `local_identifier`
*String* (mandatory): Unique code identifying an [Agent] in the SKG (if any, otherwise "stateless identifier").

{: .highlight }
**Suggestion:** Use a URL as a string to make this entity dereferenceable on the Web. For additional information, see the [section 'Local identifiers of entities' of the Interoperability Framework](/interoperability-framework/#local-identifiers-of-entities).

```json
    "local_identifier": "https://w3id.org/oc/meta/ra/0614010840729"
```

### `identifiers`

*List* (recommended): Objects representing external identifiers for the entity. 

Each object is structured as follows:
- `scheme` *String* (mandatory): The scheme for the external identifier.
- `value` *String* (mandatory): The external identifier.

{: .important }
The current version of SKG-IF includes the following types of identifiers (to be specified as strings in the field “scheme”): `orcid`, `viaf`, ...

```json
    "identifiers": [
        {
            "scheme": "orcid",
            "value": "0000-0002-5193-7851"
        }           
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. 

It can be `agent` (generic agent), `person`, or `organisation`.

```json
    "entity_type": "person"
```

### `name`
*String* (optional): The string containing whatever concatenation of an [Agent] name(s).

```json
    "name": "Andrea Mannocci, PhD"
```

### `given_name`
*String* (optional): The given name of a [Person].

```json
    "given_name": "Andrea"
```

### `family_name`
*String* (optional): The family name of a [Person].

```json
    "family_name": "Mannocci"
```

### `affiliations`
*List* (optional): All the affiliations of a [Person] (à la ORCID). 

Each element of the list is structured as follows:
- `affiliation` *String* (mandatory): The identifier of an [Organisation] a [Person] is affiliated with.
- `role` *String* (recommended): The role that a [Person] had in the context of an [Organisation]. Needed for parsing purposes; fixed to `affiliate`.
- `period` *Object* (recommended): The time period where the [Person] was affiliated with an [Organisation]. It includes the following information:
    - `start` *String* (recommended): The start datetime of the affiliation with an [Organisation]. The string should be compliant with the [ISO 8601] datetime string.
    - `end` *String* (recommended): The end datetime (if any) of the affiliation with an [Organisation]. The string should be compliant with the [ISO 8601] datetime string.

```json
    "affiliations": [
        {
            "affiliation": "org_1",
            "role": "affiliate",
            "period": {
                "start": "2017-04-13T00:00:00Z",
                "end": "2019-02-11T23:59:59Z"
            }
        },
        {
            "affiliation": "org_2",
            "role": "affiliate",
            "period": {
                "start": "2019-02-12T00:00:00Z"
            }
        }
    ]
```

### `short_name`
*String* (optional): The short name/acronym for an [Organisation].

```json
    "short_name": "CNR"
```

### `other_names`
*List* (optional): Other names, perhaps in different languages, identifiying an [Organisation].

```json
     "other_names": [ 
        "National Research Council", 
        "Conseil National de la Recherche"
    ]
```

### `website`
*String* (optional): The website URL for an [Organisation].

```json
    "website": "https://www.cnr.it/"
```

### `country`
*String* (optional): The country code of an [Organisation] expressed as [ISO 3166-1 alpha-2].

```json
    "country": "IT"
```

### `type`
*List* (optional): The types of an [Organisation]. 

One or more from the following values:
- `archive`
- `company`
- `education`
- `facility`
- `government`
- `healthcare`
- `nonprofit`
- `funder`
- `research`
- `unspecified`

```json
    "type": ["research"]
```

----
[Agent]: {% link interoperability-framework/docs/agent.md %}
[Person]: {% link interoperability-framework/docs/agent.md %}
[Organisation]: {% link interoperability-framework/docs/agent.md %}
[Research product]: {% link interoperability-framework/docs/research-product.md %}
[Venue]: {% link interoperability-framework/docs/venue.md %}
[Grant]: {% link interoperability-framework/docs/grant.md %}
[Topic]: {% link interoperability-framework/docs/topic.md %}
[Data source]: {% link interoperability-framework/docs/data-source.md %}
[ISO 3166-1 alpha-2]: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
[ISO 8601]: https://en.wikipedia.org/wiki/ISO_8601