---
title: Research product
parent: Interoperability Framework
layout: default
nav_order: 1
---

# Research product

**Research products** may be of four types: research literature, research data, research software, or other.

- **Research literature**: Intended for reading by humans (articles, conference papers, thesis, peer-review, blog posts, books, reports, etc.)
- **Research data**: Self-contained, persistently identified digital assets intended for processing (e.g. files containing: tables, metadata collections, dumps; persistent dynamic queries to scientific databases)
- **Research software**: (definition from RDA WG) Research Software includes source code files, algorithms, scripts, computational workflows and executables that were created during the research process or for a research purpose. Note that software components (e.g., operating systems, libraries, dependencies, packages, scripts, etc.) that are used for research but were not created during or with a clear research intent should be considered software in research and not Research Software. This differentiation may vary between disciplines. The minimal requirement for achieving computational reproducibility is that all the computational components (Research Software, software used in research, documentation and hardware) used during the research are identified, described, and made accessible to the extent that is possible.
- **Other products**: any digital asset, uniquely identified, whose nature does not fall in the first three types


## Properties

### `local_identifier`
*String* (mandatory): Unique code identifiying a [Research product] in the SKG (if any, otherwise "stateless identifier").

{: .highlight }
**Suggestion:** Use a URL as a string to make this entity dereferenceable on the Web. For additional information, see the [section 'Local identifiers of entities' of the Interoperability Framework](/interoperability-framework/#local-identifiers-of-entities).

```json
    "local_identifier": "https://w3id.org/oc/meta/br/062501777134"
```


### `identifiers`
*List* (recommended): Objects representing external identifiers for the entity. 

Each identifier is structured as follows:
- `scheme` *String* (mandatory): The scheme for the external identifier.
- `value` *String* (mandatory): The external identifier.

{: .attention }
**Note:** the current version of SKG-IF includes the following types of identifiers (to be specified as strings in the field “scheme”): `doi`, `handle`, `pmid`, `url`, `omid`, ...

```json
    "identifiers": [
        {
            "scheme": "doi",
            "value": "10.1162/qss_a_00023"
        },
        {
            "scheme": "omid",
            "value": "br/062501777134"
        }
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. 

Needed for parsing purposes; fixed to `product`.

```json
    "entity_type": "product"
```

### `titles`
*Object* (optional): The titles of a [Research product] (multiple for multilinguism). 

The object is a dictionary, the keys represent language codes following [ISO 639-1]; the special key `none` is reserved whenever the informtion about the language is not available or cannot be shared.

```json
    "titles": {
        "en": ["Title of the paper", "Title variant"],
        "it": ["Titolo in italiano"],
        "none": ["Itletay ofyay ethay aperpay"]
    }
```

### `abstracts`
*Object* (optional): The abstracts of a [Research product] (multiple for multilinguism).

The object is a dictionary, the keys represent language codes following [ISO 639-1]; the special key `none` is reserved whenever the informtion about the language is not available or cannot be shared.

```json
    "abstracts": {
        "en": ["Abstract", "Summary"],
        "es": ["Resumen"],
        "none": ["Aperpay ummarysay"]
    }
```

### `product_type`
*String* (optional): The type of the [Research product]. 

One of the following values:
- `literature`
- `research data`
- `research software`
- `other`

```json
    "product_type": "literature"
```

### `topics`
*List* (optional): Objects referring to [Topic] covered by the [Research product]. 

Each object in the list has the following properties:
- `term` *String* (mandatory): The identifier of a [Topic] relevant for the [Research product].
- `provenance` *List* (recommended): Provenance information tracking the origin of the relation between a [Topic] and a [Research product]. 

    Each topic provenance object has the following properties:
    - `associated_with` *String* (mandatory): the `local_identifier` of the [Agent] responsible for the topic relation.
    - `trust` *Float* (mandatory): A numeric value associated to the trust given to the relation to a [Topic]. The float should be normalised in the range [0,1].
 
```json
    "topics": [
        {
            "term": "topic_1",
            "provenance": [
                {
                    "associated_with": "openaire-infra",
                    "trust": 0.7
                }
            ]
        },
        {
            "term": "topic_2",
            "provenance": [
                {
                    "type": "openalex-infra",
                    "trust": 0.9
                }
            ]
        }
    ]
```

### `contributions`
*List* (optional): Objects that describe an [Agent], its role, contribution, rank and declared affiliations to [Organisations] when working on a [Research product]. 

Each object is structured as follows:
- `by` *String* (mandatory): The identifier of an [Agent] contributing to a [Research product].
- `declared_affiliations` *List* (recommended): [Organisations] identifiers that reflect the declared affiliations of a [Agent] for a [Research product].
- `rank` *Integer* (recommended): The rank (i.e., order of appearance) of a [Agent] with a specific role (e.g., the order of an author in a list) of a [Research product].
- `role` *String* (recommended): The role that an [Agent] had in a [Research product], to choose among `author`, `editor`, and `publisher`.
- `contribution` *List* (recommended): The contributions that an [Agent] had in a [Research product]. 

    Each element in the list is a String compliant with the [CRediT taxonomy](https://credit.niso.org), i.e.,
    - `conceptualization`
    - `data curation`
    - `formal analysis`
    - `funding acquisition`
    - `investigation`
    - `methodology`
    - `project administration`
    - `resources`
    - `software`
    - `supervision`
    - `validation`
    - `visualization`
    - `writing – original draft`
    - `writing – review & editing`

```json
    "contributions": [
        {
            "by": "person_123",
            "declared_affiliations": ["org_1", "org_3"],
            "rank": 1,
            "contribution": ["writing – original draft", "conceptualization"],
            "role": "author"
        }
    ]
```

### `manifestations`
*List* (optional):  Objects representing multiple manifestations of the same [Research product] (e.g., a preprint, a postprint, etc.). 

Each manifestation object has the following structure:
- `type` *Object* (recommended): The type of the manifestation (e.g., preprint). 

  The object has the following properties:
    - `class` *String* (recommended): The URL of the class identifying the entity (e.g., in an ontology) describing that type.
    - `labels` *Object* (recommended): the labels describing the type (multiple for multilinguism). 
      The object is a dictionary, the keys represent language codes following [ISO 639-1]; the special key `none` is reserved whenever the information about the language is not available or cannot be shared.
    - `defined_in` *String* (recommended): the URL of the schema of the manifestation type, e.g., a link to the vocabulary of allowed product types.
- `dates` *Object* (recommended): Relevant dates for the manifestation. 
  
  The object is a dictionary, the keys represent the type of date and the value is expressed as either a string or a list of string, where each string is compliant with the [ISO 8601] datetime string. The possible dates that are specifiable are:
    - `acceptance`: The date of acceptance of an entity. Examples of entities to which a date accepted may be relevant are a thesis (accepted by a university examination board) or an article (accepted by a journal editor).
    - `access`: The date on which a particular digital item, such as a PDF or an HTML file, has been accessed by somebody.
    - `collected`: The date on which some item has been collected, for example the data gathered by means of questionnaires.
    - `copyright`: The date on which an entity has been copyrighted.
    - `correction`: The date on which something, for example a document, is corrected.
    - `creation`: The date on which an entity has been created.
    - `decision`: The date on which a particular endeavour, such as a grant application, has been or will be approved or rejected by somebody.
    - `deposit`: The date on which an entity has been deposited, for example in a library, repository, supplementary information archive, database or similar place of document or information storage.
    - `distribution`: The date on which something is distributed, for example the date on which a preprint of a document is e-mailed to colleagues and other academics by the author(s), or the date on which a printed announcement of forthcoming theatre events is mailed to those those on the theatre's mailing list.
    - `embargo`: The date before which an entity should not be published, or before which a press release should not be reported on. For open-access journal articles, the embargo date is the date before which availability of the open-access version of the article is restricted by the publisher, following subscription-access availability of the published work.
    - `modified`: The date on which an entity has been modified.
    - `publication`: The date of formal issuance of a resource (e.g. a publication or a patent).
    - `received`: The date on which some item is received, for example a document being received by a publisher.
    - `request`: The date on which an agent is requested to do something, for example a reviewer is requested to write a review of a paper submitted to a journal for publication, or an author is requested to supply a revised version of the paper in response to the reviews received.
    - `retraction`: The date on which something, for example a claim or a journal article, is retracted.
    - `validity`: Date of validity of a resource.
- `identifiers` *List* (recommended): Objects representing external identifiers for the manifestation. 
  
  Each object is structured as follows:
    - `scheme` *String* (mandatory): The scheme for the external identifier (e.g., doi, handle, url, pubmed, etc.).
    - `value` *String* (mandatory): The external identifier.
- `peer review` *Object* (recommended): Whether the manifestation has undergone a peer review. It must be specify only if information about peer reviewing exists. 
  
  It has the following properties:
    - `status` *String* (mandatory): describe if the manifestation has been already reviewed (i.e. “peer reviewed”) or if it is currently under review (i.e. “under review”).
    - `description` *String* (recommended): describe the type of peer review that applies, to choose from `single-blind peer review`, `double-blind peer review`, `open peer review`.
- `access_rights` *Object* (recommended): The access right for the specific materialisation. 

  It specifies the following properties:
    - `status` *String* (mandatory): describe if the manifestation is open access (`open`), closed access (`closed`), under embargo (`embargoed`), restricted access (`restricted`), or unavailable for some reason (`unavailable`).
    - `description` *String* (recommended): describe and qualify the specific status selected.
- `licence` *String* (recommended): The URL of the licence specific to the manifestation.
- `version` *String* (recommended): The version for a software or research data product.
- `biblio` *Object* (optional): An object containing bibliographic information about a manifestation. 

  The object has the following properties:
    - `issue` *String* (optional): Issue number.
    - `pages` *Object* (optional): the pages where the manifestation in defined (within its [Venue]). 
      
      It includes the following information 
        - `first` *String* (mandatory): The starting page.
        - `last` *String* (mandatory): The ending page.
    - `volume` *String* (optional): Volume number (for journals, books, conferences).
    - `edition` *String* (optional): The edition (for journals and books).
    - `number` *String* (optional): a number of the manifestation within the [Venue] (e.g., chapter number).
    - `in` *String* (optional): A [Venue] identifier for the manifestation.
    - `hosting_data_source` *String* (optional): A [Data source] identifier for the manifestation.

```json
    "manifestations": [
        {
            "type": {
                "class": "http://purl.org/spar/fabio/Preprint",
                "labels": {
                    "en": "preprint"
                },
                "defined_in": "http://purl.org/spar/fabio"
            },
            "dates": {
                "modified": ["2024-01-15T14:15:43Z", "2024-02-11T11:12:04Z"],
                "distribution": "2024-02-12T12:00:00Z"
            },
            "identifiers": [
                {
                    "scheme": "arxiv",
                    "value": "2407.13329"
                },
                {
                    "scheme": "url",
                    "value": "https://arxiv.org/abs/2407.13329"
                }
            ],
            "peer_review": {
                "status": "peer reviewed",
                "description": "single-blind peer review"
            },
            "access_rights": {
                "status": "restricted",
                "description": "Only publishers can access the manifestation"
            },
            "licence": "https://creativecommons.org/licenses/by/4.0/legalcode.en",
            "version": "1.0.0",
            "biblio": {
                "issue": "1",
                "pages": {
                    "first": "640",
                    "last": "645"
                },
                "volume": "17",
                "in": "ven1",
                "hosting_data_source": "123"
            }
        }
    ]
```

### `relevant_organisations`
*List* (optional): Relevant [Organisation] identifiers associated with a [Research product], in case the individual affiliations of an [Agent] are not available.

```json
    "relevant_organisations": ["org_1", "org5"]
```
 
### `funding`
*List* (optional): Relevant [Grant] identifiers associated with a [Research product].

```json
    "funding": ["grant_1", "grant_2"]
```    

### `related_products`
*Object* (optional): A dictionary of objects representing related [Research products], where the semantics of such relationships is specified as a key. 

It is structured as follows:
- `cites` *List* (optional): [Research products] identifiers that are cited by a given [Research product].
- `is_supplemented_by` *List* (optional): [Research products] identifiers that are supplement of a given [Research product].
- `is_documented_by` *List* (optional): [Research products] identifiers that documents a given [Research product].
- `is_new_version_of` *List* (optional): [Research products] identifiers that are prior versions of a given [Research product].
- `is_part_of` *List* (optional): [Research products] identifiers that contain the current [Research product].


```json
    "related_products": {
        "cites": ["product_2", "product_3", "product_4"],
        "is_supplemented_by": ["product_7", "product_8", "product_9"],
        "is_documented_by": ["product_10", "product_13"],
        "is_new_version_of": ["product_10", "product_13"],
        "is_part_of": ["product_11"]
    }
```

----
[Agent]: {% link interoperability-framework/docs/agent.md %}
[Person]: {% link interoperability-framework/docs/agent.md %}
[Organisation]: {% link interoperability-framework/docs/agent.md %}
[Organisations]: {% link interoperability-framework/docs/agent.md %}
[Research product]: {% link interoperability-framework/docs/research-product.md %}
[Research products]: {% link interoperability-framework/docs/research-product.md %}
[Venue]: {% link interoperability-framework/docs/venue.md %}
[Grant]: {% link interoperability-framework/docs/grant.md %}
[Topic]: {% link interoperability-framework/docs/topic.md %}
[Data source]: {% link interoperability-framework/docs/data-source.md %}
[ISO 639-1]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
[ISO 8601]: https://en.wikipedia.org/wiki/ISO_8601