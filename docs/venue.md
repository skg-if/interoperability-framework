# Venue
A [Venue](Venue) is an entity that models a publishing “gateway” used by [Person](Person) to make their [Research products](Research product) available to others.

:Example: [Episciences](https://episciences.org)  is an overlay platform supporting the management of open-access journals on top of the Open Access repository [HAL](https://hal.science). In this context, episciences.org is a publishing [Venue](Venue) (journal, open access, open peer review), while HAL is a [Data source](Data source). Articles published via episciences.org will be therefore linked to the respective journal (publishing [Venue](Venue)) and the data source HAL. 
    However, HAL is also a publishing [Venue](Venue) for researchers that are directly uploading their [Research product](Research product). More specifically, a publishing [Venue](Venue) with peer-review and some support for metadata curation. In this case, a [Research product](Research product) will be linked to HAL both as a publishing [Venue](Venue) and as a [Data source](Data source). 

**Note:** Each [Research product](Research product) must be associated with its publishing [Venue](Venue) and its [Data source](Data source). 




## Properties
`local_identifier`		
*String* (mandatory): Unique code identifiying the [Venue](Venue) in the SKG (if any, otherwise "stateless identifier").
 
```json
    "local_identifier": "123_local_id"
```

`identifiers`
*List* (recommended): A list of objects representing external identifiers for the entity. Each object is structured as follows.

- scheme` *String* (mandatory): The scheme for the external identifier. It can be one of the following
    - issn`
    - eissn`
    - lissn`
    - isbn`
    - opendoar`
    - re3data.org`
    - fairsharing`
    - doi`
    - handle`
- value` *String* (mandatory): The external identifier.

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

`entity_type`
*String* (mandatory): Field stating what kind of entity is being serialised. Needed for parsing purposes; fixed to `venue`.

```json
    "entity_type": "venue"
```

`name` 
 *String* (optional): The name of the [Venue](Venue).

```json
    "name": "Lecture Notes in Computer Science"
```

`acronym` 
 *String* (optional): Acronym used by a [Venue](Venue).

```json
    "acronym": "JASIST"
```

`type`
*String* (optional): The type of the [Venue](Venue). The String follows the vocabulary below

.. tabularcolumns:: p{0.132\linewidth}p{0.198\linewidth}p{0.330\linewidth}
.. csv-table:: Controlled vocabulary for different types of venue and its mapping towards OpenCitations
   :name: tables-csv-example
   :header: "SKG-IF", "OpenCitations"
   :class: longtable
   :align: center

   "`repository`", "Repository, Scientific database"
   "`journal`", "Journal issue, Journal volume, Journal"
   "`conference`", "Proceedings series, Proceedings"
   "`book`", "Book, Book part, Book section, Book series, Book set, Edited book, Reference book, Monograph"
   "`other`", "Report series, Standard series, Archival document"
   "`unknown`", ""

```json
    "type": "repository"
```

`publisher`
*String* (optional): The name of the publisher (for journals, books, conferences).

```json
    "publisher": "Springer Nature"
```

`series`
*String* (optional): The name of the conference or book series.

```json
    "series": "Lecture Notes in Computer Science (LNCS)"
```

`is_full_oa`
*Boolean* (optional): True if the [Venue](Venue) contains only open access products (to the best of knowledge, at the time of expert).
 
```json
    "is_currently_full_oa": true
```

`creation_date`
*String* (optional): The date of creation of the [Venue](Venue) expressed as [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601).
 
```json
    "creation_date": "2019-09-13"
```


`contributions`
*List* (optional) : A list of all the [Person]() that contributed to the [Venue](Venue). Each element of the list is structured as follows:

- person` *String* (mandatory): The id of a [Person]().
- roles` *List* (mandatory): The roles of the [Person]() contributing to the [Venue](Venue).

```json
   "contributions": [
        {
            "person": "person_3",
            "roles": ["editor"]
        }
   ]
```