---
title: Venue
parent: Interoperability framework
layout: default
nav_order: 4
---

# Venue
A [Venue] is an entity that models a publishing “gateway” used by an [Agent] to make their [Research products] available to others.

[Venues] are defined with an editorial point of view.
- A scholarly journal is a typical example of [Venue] for a [Research product] sub-typed as `literature`;
- A dataset catalog is a typical example of [Venue] for a [Research product] subtyped as `research data`.
Depending on the context an entity can be represented as a [Venue] or a [Research product]; a book is one of these specific entities.

{: .highlight }
>**Example:** [Episciences](https://episciences.org)  is an overlay platform supporting the management of open-access journals on top of the Open Access repository [HAL](https://hal.science). In this context, episciences.org is a publishing [Venue] (journal, open access, open peer review), while HAL is a [Data source]. Articles published via episciences.org will be therefore linked to the respective journal (publishing [Venue]) and the data source HAL. 
>
>However, HAL is also a publishing [Venue] for researchers that are directly uploading their [Research product]. More specifically, a publishing [Venue] with peer-review and some support for metadata curation. In this case, a [Research product] will be linked to HAL both as a publishing [Venue] and as a [Data source]. 

<!-- **Note:** Each [Research product] must be associated with its publishing [Venue] and its [Data source].  -->



## Properties

### `local_identifier`		
*String* (mandatory): Unique code identifying a [Venue] in the SKG (if any, otherwise "stateless identifier").
 
{: .highlight }
**Suggestion:** Use a URL as a string to make this entity dereferenceable on the Web. For additional information, see the [section 'Local identifiers of entities' of the Interoperability Framework](/interoperability-framework/#local-identifiers-of-entities).

```json
    "local_identifier": "https://w3id.org/oc/meta/br/062501778099"
```

### `identifiers`
*List* (recommended): Objects representing external identifiers for the entity. 

Each object is structured as follows.

- `scheme` *String* (mandatory): The scheme for the external identifier. It can be one of the following
- `value` *String* (mandatory): The external identifier.

{: .attention }
**Note:** the current version of SKG-IF includes the following types of identifiers (to be specified as strings in the field “scheme”): `issn`, `eissn`, `lissn`, `isbn`, `opendoar`, `re3data.org`, `fairsharing`, `doi`, `handle`

```json
    "identifiers": [
        {
            "scheme": "issn"
            "value": "0302-9743"
        },
        {
            "scheme": "isbn"
            "value": "978-3-031-25049-1"
        }
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. 

Needed for parsing purposes; fixed to `venue`.

```json
    "entity_type": "venue"
```

### `name` 
 *String* (optional): The name of a [Venue].

```json
    "name": "The Semantic Web – ISWC 2020: 19th International Semantic Web Conference, Athens, Greece, November 2–6, 2020, Proceedings, Part II"
```

### `acronym` 
 *String* (optional): Acronym used by a [Venue].

```json
    "acronym": "JASIST"
```

### `type`
*String* (optional): The type of a [Venue]. 

The String follows the vocabulary below:
- `journal`
- `conference`
- `book`
- `repository`
- `other`
- `unknown`

```json
    "type": "journal"
```

### `series`
*String* (optional): The name of the conference or book series.

```json
    "series": "Lecture Notes in Computer Science (LNCS)"
```

### `access_rights` 
*Object* (recommended): The access right for the specific journal. 

It specifies the following properties:

- `status` *String* (mandatory): describe if the journal is open access (`open`), closed access (`closed`), or hybrid (`hybrid`).
- `description` *String* (recommended): describe and qualify the specific status selected.

```json
    "access_rights": {
        "status": "open",
        "description": "Diamond Open Access journal"
    }
```

### `creation_date`
*String* (optional): The date of creation of a [Venue]. The string should be compliant with the [ISO 8601] datetime string.
 
```json
    "creation_date": "2019-09-13T00:00:00+00:00"
```

### `contributions`
*List* (optional): [Agents] that contributed to a [Venue]. 

Each element of the list is structured as follows:
- `by` *String* (mandatory): The identifier of an [Agent].
- `roles` *List* (recommended): The roles of an [Agent] contributing to a [Venue].
  
  To choose from the following list:
    - `publisher`
    - `editor`

```json
    "contributions": [
        {
            "by": "pub1",
            "role": "publisher"
        },
        {
            "by": "ed1",
            "role": "editor"
        },
        {
            "by": "ed2",
            "role": "editor"
        }
    ]
```

----
[Agent]: {% link interoperability-framework/docs/agent.md %}
[Agents]: {% link interoperability-framework/docs/agent.md %}
[Person]: {% link interoperability-framework/docs/agent.md %}
[Organisation]: {% link interoperability-framework/docs/agent.md %}
[Research product]: {% link interoperability-framework/docs/research-product.md %}
[Research products]: {% link interoperability-framework/docs/research-product.md %}
[Venue]: {% link interoperability-framework/docs/venue.md %}
[Venues]: {% link interoperability-framework/docs/venue.md %}
[Grant]: {% link interoperability-framework/docs/grant.md %}
[Topic]: {% link interoperability-framework/docs/topic.md %}
[Data source]: {% link interoperability-framework/docs/data-source.md %}
[ISO 8601]: https://en.wikipedia.org/wiki/ISO_8601