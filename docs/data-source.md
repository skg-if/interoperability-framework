---
title: Data source
parent: Interoperability framework
layout: default
nav_order: 6
---

# Data source

A [Data source] is a service or platform where a [Research product] (its metadata and files) is stored, preserved, and made discoverable and accessible. A data source is described by the [EOSC Profile for data sources](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile).

{: .highlight }
>**Example:** [Episciences](https://episciences.org)  is an overlay platform supporting the management of open-access journals on top of the Open Access repository [HAL](https://hal.science). In this context, episciences.org is a publishing [Venue] (journal, open access, open peer review), while HAL is a [Data source]. Articles published via episciences.org will be therefore linked to the respective journal (publishing [Venue]) and the data source HAL. 
>
>However, HAL is also a publishing [Venue] for researchers that are directly uploading their [Research product]. More specifically, a publishing [Venue] with peer-review and some support for metadata curation. In this case, a [Research product] will be linked to HAL both as a publishing [Venue] and as a [Data source]. 

<!-- **Note:** each [Research product] must be associated with its publishing [Venue] and its [Data source]. -->


## Properties

### `local_identifier`		
*String* (mandatory): Unique code identifying a [Data source] in the SKG (if any, otherwise "stateless identifier").

{: .highlight }
**Suggestion:** Use a URL as a string to make this entity dereferenceable on the Web. For additional information, see the [section 'Local identifiers of entities' of the Interoperability Framework](/interoperability-framework/#local-identifiers-of-entities).

```json
    "local_identifier": "https://ror.org/00m2zh467"
```

### `identifiers`
*List* (recommended):  Objects representing external identifiers for the entity. Each object is structured as follows.
- `scheme` *String* (mandatory): The scheme for the external identifier (e.g., a DOI).
- `value` *String* (mandatory): The external identifier.

```json
    "identifiers": [
        {
            "scheme": "doi"
            "value": "https://doi.org/..."
        }
    ]
```

### `entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. Needed for parsing purposes; fixed to `datasource`.

```json
    "entity_type": "datasource"
```    

### `name`
*String* (optional): Name of the [Data source].
 
```json
    "name": "Zenodo"
```

### `persistent_identity_systems`	
*List* (optional): The persistent identifier systems that are used by a [Data source] to identify the `ProductType` it supports.

- `for` *String* (mandatory): The Product type to which the persistent identifier is referring to. To choose from
    - `literature` (from [EOSC vocabulary Research Product Type])
    - `research data` (from [EOSC vocabulary Research Product Type])
    - `software` (from [EOSC vocabulary Research Product Type])
    - `metadata`
    - `any` 

- `pid_schemes` *List* (mandatory): Persistent identifier schemes used to refer to ProductTypes. Each elements must be drawn by the EOSC vocabulary Persistent Identity Scheme, i.e.,
    - `doi`
    - `handle`
    - `ror`
    - `orcid`
    - `isni`
    - `arxiv`
    - `pmcid`
    - `ark`

```json
    "persistent_identity_systems": [
        {
            "pid_schemes": [ "doi", "arxiv" ],
            "for": [ "literature" ]
        },
        {
            "pid schemes": [ "doi" ],
            "for": [ "metadata" ]
        }
    ]
```

### `audience`	
*List* (optional): The property defines the target audiences of the users of a [Data source]. 

Each item specifies the following information:
- `audience_type` *String* (mandatory): the type of the audience based on the vocabulary Jurisdiction. 
  
  It may have the following values:
    - `Global`: intended for all users
    - `National`: intended for users of a country, e.g., national data repository
    - `Regional`: intended for users of a region (e.g., Europe)
    - `Institution`: intended for users of an institution, e.g. university publication repository
    - `Research Infrastructure`: intended for users of RIs and Clusters communities
    - `e-Infrastructure`: intended for users of horizontal e-infra services (e.g., EGI, GEANT, OpenAIRE, EUDAT, Fenix, gaia-x)

```json
    "audience": [
        { "audience_type": "National" },
        { "audience_type": "e-Infrastructure" }
    ]
```

### `data_source_classification`
*String* (optional): The specific type of a [Data source], based on the vocabulary [Data source] Classification. It can be chosen among the following values:
- `repository`: services for the deposition, preservation, discovery, and access of research products metadata and files, e.g. PANGAEA, Zenodo, B2SHARE, EGI AppDB, BioTools
- `aggregator`: services for the aggregation of metadata about research products (and other entities) that are mainly collected (aka harvested) from data sources via APIs and then possibly curated/enriched by end-users, e.g. BASE, NARCIS, GESIS, B2FIND, OpenAIRE Research Graph
- `scientific database`: Scientific Databases intended to store structured information about scientific entities, e.g. PROTDB, ENA, ECRIN Studies Database
- `journal archive`: Data sources for the deposition (submission), preservation, discovery, and access of scientific journal articles (metadata and files), e.g. publishers sites, journal sites, etc.
- `publisher archive`: Scientific literature publisher, e.g. Elsevier, Copernicus, Frontiers, Springer, providing metadata and files of scientific publications relative to journals and conferences
- `cris system`: A current research information system (CRIS) is an information system to store, manage and exchange contextual metadata for the research products funded by a research funder or conducted at a research-performing organisation
 
```json
    "data_source_classification": "repository"
```

### `research_product_type`	
*List* (optional): The types of entities managed by a [Data source]. Each item in the list should be compliant with the following terms:
- `metadata`
- `research data` (from [EOSC vocabulary Research Product Type])
- `literature` (from [EOSC vocabulary Research Product Type])
- `software` (from [EOSC vocabulary Research Product Type])
- `any`
 
```json
    "research_product_type": ["metadata", "literature"]
```

### disciplines
*List* (optional): The disciplines for which a [Data source] is dedicated. The disciplines must be specified using the Library of Congress Classification codes, available at <https://id.loc.gov/authorities/classification> (e.g. `PA3000-PA3049` for classical literature). In case a [Data source] is discipline agnostic, the string `all` should be specified.
 
```json
    "discipline": [
        "QC790.95-QC791.8"
    ]
```

### `policy`
*List* (optional): The policies followed by a [Data source].

Each item specifies the following information:

- `about` *String* (mandatory): The type of policy to consider. 
To choose among the following possibilities:
    - `submission`: This policy provides a comprehensive framework for the contribution of research products. Criteria for submitting content to the repository as well as product preparation guidelines can be stated. Concepts for quality assurance may be provided.
    - `preservation`: This policy provides a comprehensive framework for the long-term preservation of the research products. Principles aims and responsibilities must be clarified. An important aspect is the description of preservation concepts to ensure the technical and conceptual utility of the content.
    - `embargoed access`: This policy provides the possibility of having / handling embargoed access refers to the resources in the [Data source] (from [COAR Access Rights 1.0]).
    - `metadata only access`: This policy provides the possibility of having / handling metadata only access refers to the resources in the [Data source] (from [COAR Access Rights 1.0]).
    - `open access`: This policy provides the possibility of having / handling [Data source] resources that are immediately and permanently online (from [COAR Access Rights 1.0]).
    - `restricted access`: This policy provides the possibility of having / handling restricted access to the resources in the [Data source] (from [COAR Access Rights 1.0]).
- `target` *List* (recommended): The types of resources to which the policy applies to. Each item in the list should be compliant with the following terms:
    - `metadata`
    - `research data` (from [EOSC vocabulary Research Product Type])
    - `literature` (from [EOSC vocabulary Research Product Type])
    - `software` (from [EOSC vocabulary Research Product Type])
    - `any`
- `documented_at` *String* (recommended): The URL of the document that describes the policy.
- `description` *String* (recommended): Describe the type of policy, if necessary.

```json
    "policy": [
        {
            "about": "submission",
            "target": [ "any" ],
            "documented_at": "http://www.example.com/submission"
        }, 
        {
            "about": "preservation",
            "target": [ "any" ],
            "documented_at": "http://www.example.com/preservation"
        }, 
        {
            "about": "open access",
            "target": [ "metadata", "literature" ],
            "documented_at": "https://creativecommons.org/licenses/by/4.0/legalcode.en",
            "description": "Creative Commons Attribution (CC-BY) 4.0"
        }
    ]
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
[EOSC vocabulary Research Product Type]: https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile#D.v4.00EOSCDataSourceProfile-ResearchProductType
[COAR Access Rights 1.0]: https://vocabularies.coar-repositories.org/access_rights/