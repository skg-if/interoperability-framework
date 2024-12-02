---
title: Topic
parent: Interoperability Framework
layout: default
nav_order: 5
---

# Topic

A [Topic] describes the scientific disciplines, subjects and keywords potentially relevant for a [Research product].


This section describes the metadata fields for a [Topic].


## Properties

### `local_identifier`		
*String* (mandatory): Unique code identifiying the [Topic] in the SKG (if any, otherwise "stateless identifier").

**Suggestion:** Use a URL as a string to make this entity dereferenceable on the Web. For additional information, see the [section 'Local identifiers of entities' of the Interoperability Framework](https://skg-if.github.io/interoperability-framework/#local-identifiers-of-entities).

```json
    "local_identifier": "http://id.loc.gov/authorities/classification/Q"
```

### `identifiers`
*List* (recommended):  A list of objects representing external identifiers for the entity. Each object is structured as follows.
- `scheme` *String* (mandatory): The scheme for the external identifier.
- `value` *String* (mandatory): The external identifier.
 
```json
    "identifiers": [
        {
            "scheme": "Computer Science Ontology",
            "value": "https://cso.kmi.open.ac.uk/topics/semantic_web"
        },
        {
            "scheme": "dbpedia",
            "value": "https://dbpedia.org/page/Semantic_Web"
        }
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. Needed for parsing purposes; fixed to `topic`.

```json
    "entity_type": "topic"
```

### `labels`
*Object* (optional): the labels describing the [Topic] (multiple for multilinguism). The object is a dictionary, the keys represent language codes following [ISO 639-1]; the special key `none` is reserved whenever the informtion about the language is not available or cannot be shared.

```json
    "labels": {
        "en": "Computer Science",
        "it": "Informatica"
    }

```

----
[Topic]: https://skg-if.github.io/interoperability-framework/docs/topic.html
[Research product]: https://skg-if.github.io/interoperability-framework/docs/research-product.html
[ISO 639-1]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes