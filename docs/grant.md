# Grant

The entity [Grant](#grant) describes funding awarded to a [Person](Person) or an [Organisation](Organisation) 
by a funding body. These bodies, both public and private, can be funders, foundations, governments, agencies or institutions. 



### `local_identifier`
*String* (mandatory): Unique code identifiying the [Grant](#grant) at the funder.
 
```json
    "local_identifier": "101095129"
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
*String* (optional): Title of the [Grant](#grant).
 
```json
    "title": "GraspOS: next Generation Research Assessment to Promote Open Science"
```

### `abstract`
*String* (optional): The abstract or a description of the [Grant](#grant).
 
```json
    "abstract": "GraspOS aims to build and operate a data infrastructure to support the policy reforms and pave the way towards a responsible research assessment system that embeds OS practices and accelerates its adoption in Europe. GraspOS will focus on extending the EOSC ecosystem with tools and services that will facilitate monitoring the use and uptake of various types of research services and outputs (publications, datasets, software) and will catalyse the implementation of policy-level rewards to foster OS practices. These tools and services will build upon multiple sources of metric data (e.g. OpenCitations, Scholexplorer) including capabilities offered by the EOSC Core, that will be federated in the context of the project, and will take into consideration both contemporary guidelines for Responsible Research Assessment (RRA), like those provided by initiatives like DORA and the Leiden Manifesto, and the suggestions from a diversity of relevant stakeholders. GraspOS will also incorporate piloting activities to co-design, showcase, validate, and evaluate GraspOS’s key results considering domain-specific aspects and different levels of OS-aware RRA, such as the researcher (individual/group), institution, and national level."
```

### `acronym`
*String* (optional): The acronym of the [Grant](#grant).
 
```json
    "acronym": "GraspOS"
```

### `funder`
*String* (optional): The name of the body funding the [Grant](#grant).

```json
    "funder": "EC"
```

### `funding_stream`
*String* (optional): The funding stream of the [Grant](#grant).

```json
    "funding_stream": "Horizon Europe"
```

### `currency`
*String* (mandatory, if `funded_amount` is provided; optional otherwise): Currency of the funded amount, following [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217).

```json
    "currency": "EUR"
```

### `funded_amount`
*Numeric* (optional): Amount funded for the [Grant](#grant).

```json
    "funded_amount": 2.985.441
```

### `keywords`
*List* (optional): A list of keywords for the [Grant](#grant).
 
```json
    "keywords": ["Open science", "mutual learning", "open research"]
```

### `start_date`
*String* (optional): The date the [Grant](#grant) started expressed as [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601).

```json
    "start_date": "2019-09-13"
```

### `end_date`
*String* (optional): The date the [Grant](#grant) finished expressed as [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601).
 
```json
    "end_date": "2022-12-03"
```

### `website`
*String* (optional): An URL poiting to the website of the funded project.
 
```json
    "website": "https://graspos.eu"
```

### `beneficiaries`
*List* (optional): A list of the [Organisation]() identifiers funded by the [Grant](#grant).
 
```json
    "beneficiaries": ["org_2", "org_5"]
```

### `contributors`
*List* (optional): A list of the [Person]() contributing to the [Grant](#grant).
 
- `person`: The identifier of the [Person] who is the principal investigator  
- `organisation`: The identifier of the [Organisation](Organisation) the principal investigator has declared as affiliation for the [Grant](#grant).
- `poles` *List* (recommended): A list of the roles that the [Person] has in the [Grant](#grant).

```json
    "contributors": [
        {
            "person": "person_2",
            "organisation": "org_3",
            "roles": ["principal investigator"]
        }
    ]
```