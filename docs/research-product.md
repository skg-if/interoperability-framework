# Research product
**Research products** may be of four types, as follows.

- **Literature**: Intended for reading by humans (article, thesis, peer-review, blog posts, books, reports, patents, etc.)
- **Research data**: Self-contained, persistently identified digital assets intended for processing (e.g. files containing: tables, metadata collections, dumps; persistent dynamic queries to scientific databases)
- **Research software**: (definition from RDA WG) Research Software includes source code files, algorithms, scripts, computational workflows and executables that were created during the research process or for a research purpose. Note that software components (e.g., operating systems, libraries, dependencies, packages, scripts, etc.) that are used for research but were not created during or with a clear research intent should be considered software in research and not Research Software. This differentiation may vary between disciplines. The minimal requirement for achieving computational reproducibility is that all the computational components (Research Software, software used in research, documentation and hardware) used during the research are identified, described, and made accessible to the extent that is possible.
- **Other products**: any digital asset, uniquely identified, whose nature does not fall in the first three types

## Properties

### `local_identifier`
*String* (mandatory): Unique code identifiying the [Research product](#research-product) in the SKG (if any, otherwise "stateless identifier")

```json
    "local_identifier": "product_1"
```


### `identifiers`
*List* (recommended):  A list of objects representing external identifiers for the entity. Each object is structured as follows.
- `scheme` *String* (mandatory): The scheme for the external identifier (e.g., doi, handle, purl, pubmed, etc.).
- `value` *String* (mandatory): The external identifier.

```json
    "identifiers": [
        {
            "scheme": "doi"
            "value": "10.1103/PhysRevE.80.056103"
        }
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. Needed for parsing purposes; fixed to `product`.

```json
    "entity_type": "product"
```

### `titles`
*Object* (optional): The titles of a [Research product](#research-product) (multiple for multilinguism). 
The object is a dictionary, the keys represent language codes following [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes); the special key `none` is reserved whenever the informtion about the language is not available or cannot be shared.

```json
    "titles": {
        "en": ["Title of the paper", "Title variant"],
        "it": ["Titolo in italiano"],
        "none": ["Itletay ofyay ethay aperpay"]
    }
```

### `abstracts`
*Object* (optional): The abstracts of a [Research product](#research-product) (multiple for multilinguism).
The object is a dictionary, the keys represent language codes following [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes); the special key `none` is reserved whenever the informtion about the language is not available or cannot be shared.

```json
    "abstracts": {
        "en": ["Abstract", "Summary"],
        "es": ["Resumen"],
        "none": ["Aperpay ummarysay"]
    }
```

### `product_type`
*String* (optional): The type of the [Research product](#research-product). One of the following values:
- `literature`
- `research data`
- `research software`
- `other`

```json
    "product_type": "literature"
```

### `topics`
*List* (optional): A list objects referring to [Topic](https://skg-if.github.io/interoperability-framework/topic) covered by the [Research product](#research-product). 
Each object in the list has the following properties:
- `topic` *String* (mandatory): The identifier of a [Topic](https://skg-if.github.io/interoperability-framework/topic) relevant for the [Research product](#research-product).
- `provenance` *List* (recommended): A list of provenance information tracking the origin of the relation between a [Topic](https://skg-if.github.io/interoperability-framework/topic) and a [Research product](#research-product). Each topic provenance object has the following properties:
    - `type` *String* (mandatory): A string tracking the provenance of the topic relation.
    - `trust` *Float* (mandatory): A numeric value associated to the trust given to the relation to a [Topic](https://skg-if.github.io/interoperability-framework/topic). The float should be normalised in the range [0,1].
 
```json
    "topics": [
        {
            "topic": "topic_1",
            "provenance": [
                {
                    "type": "OpenAIRE mining",
                    "trust": 0.7
                }
            ]
        },
        {
            "topic": "topic_2",
            "provenance": [
                {
                    "type": "OpenAlex",
                    "trust": 0.9
                }
            ]
        }
    ]
```

### `contributions`
*List* (optional): A list of objects that describe a [Person], his/her role, rank and declared affiliations to [Organisations] when working to a [Research product](#research-product).
Each object is structured as follows:
- `person` *String* (mandatory): The identifier of a [Person]() contributing to the [Research product](#research-product).
- `declared_affiliations` *List* (recommended): A list of [Organisations]() identifiers that reflect the declared affiliations of a [Person]() for the [Research product](#research-product).
- `rank` *Integer* (recommended): The rank (i.e., order of appearance) of the [Person]() in the author list of a [Research product](#research-product).
- `roles` *List* (recommended): A list of the specific roles that a [Person]() had in the [Research product](#research-product). Each element in the list is a *String* compliant with the `CRediT taxonomy](https://credit.niso.org)_.
- `is_listed_author` *Boolean* (recommended): True if the [Person]() indicated is listed as an author of the [Research product](#research-product), False otherwise (e.g., another kind of contribution).

```json
    "contributions": [
        {
            "person": "person_123",
            "declared_affiliations": ["org_1", "org_3"],
            "rank": 1,
            "roles": ["writing-original-draft", "conceptualization"],
            "is_listed_author": true
        }
    ]
```

### `manifestations`
*List* (optional):  A list of objects representing multiple manifestations of the same [Research product](#research-product) (e.g., a preprint, a postprint, etc.).
Each manifestation object has the following structure:
- `product_local_type` *String* (mandatory): The type of the manifestation, e.g., preprint. 
- `product_local_type_schema` *String* (mandatory): The schema of the manifestation type, e.g., a link to the vocabulary of allowed product types.
- `dates` *List* (mandatory): Relevant dates for the [Research product](#research-product). Each date has the following properties:
    - `value` *String* (mandatory): The relevant date for the [Research product](#research-product) expressed as a [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date string.
    - `type` *String* (mandatory): The type of the date (e.g., publishing, embargo, preprint, ...).
- `peer_review` *String* (mandatory): Whether the [Research product](#research-product) has undergone a peer review process. It can be one of the following:
    - `peer-reviewed`
    - `not peer-reviewed`
    - `single-blind`
    - `double-blind`
    - `open peer review`
- `metadata_curation` *String* (mandatory): Whether the [Research product](#research-product) has undergone a metadata curation process. It can be one of the following :
    - `yes`
    - `no`
    - `unavailable`
- `url` *String* (mandatory): An URL for the manifestation.
- `pid` *String* (recommended): The pid for the specific manifestation.
- `access_rights` *String* (mandatory): The access right for the specific materialisation. One of the following 
    - `open`
    - `closed`
    - `embargo`
    - `restricted`
    - `unavailable`
- `licence` *String* (recommended): Licence specific to the manifestation.
- `license_schema` *String* (recommended): Schema of the licence.
- `version` *String* (recommended): Version for a software or research data product.
- `biblio` *Object* (optional): An object containing bibliographic information about a [Research product](#research-product) of literature type. The object has the following properties:
    - `issue` *String* (optional): Issue number.
    - `start_page` *String* (optional): The starting page.
    - `end_page` *String* (optional): The ending page.
    - `volume` *String* (optional): Volume number (for journals, books, conferences).
    - `edition` *String* (optional): The edition (for journals and books).
    - `number` *String* (optional): Journal number.
    - `venue` *String* (optional): A [Venue]() identifier for the manifestation.
    - `hosting_data_source` *String* (optional): A [Data source]() identifier for the manifestation.`

```json
    "manifestations": [
        {
            "product_local_type": "",
            "product_local_type_schema": "",
            "dates": [
                {
                    "value": "2012-03-21",
                    "type": "preprint"
                }
            ],
            "peer_review": "open",
            "metadata_curation": "yes",
            "access_rights": "",
            "license": "",
            "license_schema": "",
            "version": "v1.0",
            "url": "https://link.springer.com/chapter/...",
            "pid": "https://doi.org/10.1007/...",
            "biblio": {
                "issue": "1",
                "start_page": "640",
                "end_page": "645",
                "volume": "13833",
                "edition": "1",
                "number": "7"
            }
            "venue": "venue_7",
            "hosting_data_source": "datasource_4",
        }
    ]
```

### `relevant_organisations`
*List* (optional): A list of relevant [Organisation]() identifiers associated with the [Research product](#research-product) (In case the individual affiliations of the [Person]() are not available).

```json
    "relevant_organisations": ["org_1", "org5"]
```
 
### `funding`
*List* (optional): A list of relevant [Grant]() identifiers associated with the [Research product](#research-product).

```json
    "funding": ["grant_1", "grant_2"]
```    

### `related_products`
*List* (optional): A list of objects representing related [Research product](#research-product) and the semantics of such relationships.
Each object in the list is structured as follows:

- `relation_type` *String* (mandatory): A list of [Research product](#research-product) identifiers supplementing the present one. One of the following selection of [DataCite relationTypes](https://schema.datacite.org/meta/kernel-4.4/doc/DataCite-MetadataKernel_v4.4.pdf) 
    - `cites`
    - `is_supplemented_by`
    - `is_documented_by`
    - `is_new_version_of`
    - `is_part_of`
- `products` *List* (mandatory): A list of [Research product](#research-product) identifiers describing the present one.

```json
    "related_products": [
        {
            "relation_type": "cites", 
            "products": ["product_2", "product_3", "product_4"]
        },
        {
            "relation_type": "is_supplemented_by",
            "products": ["product_7", "product_8", "product_9"],
        },
        {
            "relation_type": "is_documented_by",
            "products": ["product_10", "product_13"],
        },
        {
            "relation_type": "is_new_version_of",
            "products": ["product_5"],
        },
        {
            "relation_type": "is_part_of",
            "products": ["product_11"],
        }
    ]
```