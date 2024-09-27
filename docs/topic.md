# Topic

A [Topic](#topic) describes the scientific disciplines, subjects and keywords potentially relevant for a [Research product](https://skg-if.github.io/interoperability-framework/research-product).


This section describes the metadata fields for a [Topic](#topic).


### `local_identifier`		
*String* (mandatory): Unique code identifiying the [Topic](#topic) in the SKG (if any, otherwise "stateless identifier").
 
```json
    "local_identifier": "topic_1"
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

### `name`
*String* (optional): The display name of the [Topic](#topic).

```json
    "name": "Semantic Web"
```