# Data source

A [Data source](#data-source) is a service where published material (metadata and files) are stored, preserved, and made discoverable and accessible. 
A data source is described by the [EOSC Profile for data sources](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile).

**Example:** [Episciences](https://episciences.org)  is an overlay platform supporting the management of open-access journals on top of the Open Access repository [HAL](https://hal.science). In this context, episciences.org is a publishing [Venue](https://skg-if.github.io/interoperability-framework/venue) (journal, open access, open peer review), while HAL is a [Data source](#data-source). Articles published via episciences.org will be therefore linked to the respective journal (publishing [Venue](https://skg-if.github.io/interoperability-framework/venue)) and the data source HAL. 
    However, HAL is also a publishing [Venue](https://skg-if.github.io/interoperability-framework/venue) for researchers that are directly uploading their [Research product](Research product). More specifically, a publishing [Venue](https://skg-if.github.io/interoperability-framework/venue) with peer-review and some support for metadata curation. In this case, a [Research product](https://skg-if.github.io/interoperability-framework/research-product) will be linked to HAL both as a publishing [Venue](https://skg-if.github.io/interoperability-framework/venue) and as a [Data source](#data-source). 

**Note:** each [Research product](https://skg-if.github.io/interoperability-framework/research-product) must be associated with its publishing [Venue](https://skg-if.github.io/interoperability-framework/venue) and its [Data source](#data-source).


## Properties

### `local_identifier`		
*String* (mandatory): Unique code identifiying a [Data source](#data-source) in the SKG (if any, otherwise "stateless identifier").
 
```json
    "local_identifier": "123"
```

### `identifiers`
*List* (recommended):  A list of objects representing external identifiers for the entity. Each object is structured as follows.

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
*String* (optional): Name of the [Data source](#data-source).
 
```json
    "name": "Zenodo"
```

### `submission_policy_url`	
*String* (optional): This policy provides a comprehensive framework for the contribution of research products. Criteria for submitting content to the repository as well as product preparation guidelines can be stated. Concepts for quality assurance may be provided.
 
```json
    "submission_policy_url": "https://..."
```

### `preservation_policy_url`	
*String* (optional): This policy provides a comprehensive framework for the long-term preservation of the research products. Principles aims and responsibilities must be clarified. An important aspect is the description of preservation concepts to ensure the technical and conceptual utility of the content.
 
```json
    "preservation_policy_url": "https://..."
```

### `version_control`	
*Boolean* (optional): True if data versioning is supported: the [Data source](#data-source) explicitly allows the deposition of different versions of the same object
 
```json
    "version_control": true
```

### `persistent_identity_systems`	
*List* (optional): The persistent identifier systems that are used by the [Data source](#data-source) to identify the ProductType it supports.
- `product_type` *String* (mandatory): The Product type to which the persistent identifier is referring to. Follows the EOSC vocabulary [Research Product Type](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile#D.v4.00EOSCDataSourceProfile-ResearchProductType).
- `pid_schemes` *List* (mandatory): the list of persistent identifier schemes used to refer to ProductTypes. Each elements must be drawn by the EOSC vocabulary [Persistent Identity Scheme](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile#D.v4.00EOSCDataSourceProfile-PersistentIdentityScheme).
 
```json
    "persistent_identity_systems": [
        {
            "product_type": "Research Literature",
            "pid_schemes": ["DOI", "Handle"]
        }
    ]
```

### `jurisdiction`	
*String* (optional): The property defines the jurisdiction of the users of the [Data source](#data-source), based on the vocabulary [Jurisdiction](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile#D.v4.00EOSCDataSourceProfile-Jurisdiction).
 
```json
    "jurisdiction": "National"
```

### `data_source_classification`	
*String* (optional): The specific type of the [Data source](#data-source) based on the vocabulary [Data Source Classification](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile#D.v4.00EOSCDataSourceProfile-DataSourceClassification).
 
```json
    "data_source_classification": "Journal Archive"
```

### `research_product_type`	
*List* (optional): The types of OpenAIRE entities managed by the [Data source](#data-source), based on the vocabulary [Research Product Type](https://wiki.eoscfuture.eu/display/PUBLIC/D.+v4.00+EOSC+Data+Source+Profile#D.v4.00EOSCDataSourceProfile-ResearchProductType).
 
```json
    "research_product_type": []
```

### `thematic`	
*Boolean* (optional): Boolean value specifying if the [Data source](#data-source) is dedicated to a given discipline or is instead discipline agnostic.
 
```json
    "thematic": false
```

### `research_product_license`	
*List* (optional): Licenses under which the research products contained within the [Data source](#data-source) can be made available. Repositories can allow a license to be defined for each research product, while for scientific databases the database is typically provided under a single license. Each element in the list is structured as follows:
 
* `Research Product License Name` *String* (mandatory): 
* `Research Product License URL` *String* (mandatory): 
 
```json
    "research_product_license": [
        {
            "name": "..."
            "url": "https://..."
        }
    ]
```

### `research_product_access_policy`		
*List* (optional): List of terms following vocabulary: [COAR Access Rights 1.0](https://vocabularies.coar-repositories.org/access_rights/).
 
```json
    "research_product_access_policy": ["open access"]
```

### `research_product_metadata_license`	
*List* (optional): Metadata Policy for information describing items in the repository: Access and re-use of metadata. Each element has the following properties:

* `name` *String* (mandatory): 
* `url` *String* (mandatory): 
 
```json
    "research_product_metadata_license": [
        {
            "name": "..."
            "url": "https://..."
        }
    ]
```

### `research_product_metadata_access_policy`		
*List* (optional): List of terms following vocabulary: [COAR Access Rights 1.0](https://vocabularies.coar-repositories.org/access_rights/).
 
```json
    "research_product_metadata_access_policy": ["open access"]
```

