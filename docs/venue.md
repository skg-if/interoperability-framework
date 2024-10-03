# Venue
A [Venue]() is an entity that models a publishing “gateway” used by [Person]() to make their [Research products](https://skg-if.github.io/interoperability-framework/research-product) available to others.

**Example:** [Episciences](https://episciences.org)  is an overlay platform supporting the management of open-access journals on top of the Open Access repository [HAL](https://hal.science). In this context, episciences.org is a publishing [Venue]() (journal, open access, open peer review), while HAL is a [Data source](https://skg-if.github.io/interoperability-framework/data-source). Articles published via episciences.org will be therefore linked to the respective journal (publishing [Venue]()) and the data source HAL. 
    However, HAL is also a publishing [Venue]() for researchers that are directly uploading their [Research product](https://skg-if.github.io/interoperability-framework/research-product). More specifically, a publishing [Venue]() with peer-review and some support for metadata curation. In this case, a [Research product](https://skg-if.github.io/interoperability-framework/research-product) will be linked to HAL both as a publishing [Venue]() and as a [Data source](https://skg-if.github.io/interoperability-framework/data-source). 

**Note:** Each [Research product](https://skg-if.github.io/interoperability-framework/research-product) must be associated with its publishing [Venue]() and its [Data source](https://skg-if.github.io/interoperability-framework/data-source). 



## Properties

### `local_identifier`		
*String* (mandatory): Unique code identifiying the [Venue]() in the SKG (if any, otherwise "stateless identifier").
 
```json
    "local_identifier": "123_local_id"
```

### `identifiers`
*List* (recommended): A list of objects representing external identifiers for the entity. Each object is structured as follows.

- `scheme` *String* (mandatory): The scheme for the external identifier. It can be one of the following
    - `issn`
    - `eissn`
    - `lissn`
    - `isbn`
    - `opendoar`
    - `re3data.org`
    - `fairsharing`
    - `doi`
    - `handle`
- `value` *String* (mandatory): The external identifier.

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
*String* (mandatory): Field stating what kind of entity is being serialised. Needed for parsing purposes; fixed to `venue`.

```json
    "entity_type": "venue"
```

### `name` 
 *String* (optional): The name of the [Venue]().

```json
    "name": "The Semantic Web – ISWC 2020: 19th International Semantic Web Conference, Athens, Greece, November 2–6, 2020, Proceedings, Part II"
```

### `acronym` 
 *String* (optional): Acronym used by a [Venue]().

```json
    "acronym": "JASIST"
```

### `type`
*String* (optional): The type of the [Venue](). The String follows the vocabulary below
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
*Object* (mandatory): The access right for the specific journal. It specifies the following properties:
    - `status` *String* (mandatory): describe if the journal is open access (`open`), closed access (`closed`), or hybrid (`hybrid`).
    - `description` *String* (recommended): describe and qualify the specific status selected.

```json
    "access_rights": {
        "status": "open",
        "description": "Diamond Open Access journal"
    }
```

### `creation_date`
*String* (optional): The date of creation of the [Venue]() expressed as [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601).
 
```json
    "creation_date": "2019-09-13"
```

### `contributions`
*List* (optional): A list of all the [Agents](https://skg-if.github.io/interoperability-framework/agent) that contributed to the [Venue](). Each element of the list is structured as follows:

- `by` *String* (mandatory): The identifier of an [Agent](https://skg-if.github.io/interoperability-framework/agent).
- `roles` *List* (mandatory): The roles of the [Agent](https://skg-if.github.io/interoperability-framework/agent) contributing to the [Venue](), to choose from the following list:
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