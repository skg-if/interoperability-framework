---
title: SKG-IF Interoperability Framework
layout: default
nav_order: 2
has_toc: false
---

# SKG-IF Interoperability Framework

The SKG-IF Interoperability Framework enables to exchange data about six core entities and their relationships. These are:
- Research product
- Agent
- Grant
- Venue
- Topic
- Data source

This section contains the description of the JSON-LD format used for exchanging data compliant with the [SKG-IF Data Model](/data-model/).


## JSON-LD preamble
Each document compliant with the SKG-IF format must start with the following preamble:

```
{
    "@context": [ 
        "https://w3id.org/skg-if/context/skg-if.json",
        { 
            "@base": "https://w3id.org/skg-if/sandbox/<provider acronym>/",
            "skg": "https://w3id.org/skg-if/sandbox/<provider acronym>/"
        }
    ],
    "@graph": [ <here is where to specifies the various entities> ]
}
```

This preamble is crucial to enable software system to see the JSON document as a **parsable JSON-LD file**. It also allows for extending the [current default context](/context/) with additional mappings that may be necessary for using specific [SKG-IF extensions](/extensions/).

In addition, it is also crucial to specify the **base URLs** that will be used for local identifiers in case no URLs are specified in the appropriate fields (see the term `local_identifier` introduced for all the entities described by the Interoperability Framework). This is key to expose all Interoperability Framework entities as identifiable with an URL, which is a key condition for having data compliant with the RDF data model and Linked Data principles that we are strictly following in SKG-IF. Such URLs can be, indeed, derefereancable or not depending on the specific source that is providing it. Thus, in case no URLs are explicitly specified by the source, which may prefer to using only string values instead, the specification of a base as defined in the preamble above enables the automatic creation of sandbox URLs also in presence of string values. For doing so, the base URLs specified must follow a specific template, i.e.

```
https://w3id.org/skg-if/sandbox/<provider acronym>/
```

where the `<provider acronym>` should be substituted with the one of the provider of SKG-IF-compliant data – e.g. `https://w3id.org/skg-if/sandbox/oc/`. It is up to the provider to choose the right acronym to use.


## Local identifiers of entities
All the strings specified for defining local identifiers of SKG-ID entities are **always interpreted as URLs**. 

In case a full URL is specified as a local identifier, such URL is used for identifying the related entity without any additional intervention by the Interoperability Framework. It is up to the source providing the data, though, to be sure it is **deferenceable** on the Web. For instance, if an SKG-IF document specifies the following local identifier

```json
    "local_identifier": "https://w3id.org/oc/meta/br/062501777134"
```

then the URL `https://w3id.org/oc/meta/br/062501777134` is used as stateless identifier for the entity described. In this example, the URL specified resolves to some available data on the Web since the original source handles all the URLs it provides as local identifiers via content negotiation.

It is also possible to specify a non-URL string as a local identifier. In this case, the Interoperability Framework interprets it as a URL by combining the base URL specified in the [JSON-LD preamble above](#json-ld-preamble) of the SKG-IF document with the string specified. For instance, supposing that the base URL declared in the preamble is `https://w3id.org/skg-if/sandbox/oc/` as shown in the example above, if an SKG-IF document specifies the following local identifier

```json
    "local_identifier": "my-entity-id-1"
```

it is interpreted by the Interoperability Framework as `https://w3id.org/skg-if/sandbox/oc/my-entity-id-1`.

The local identifiers specified for any SKG-IF entity are usually those adopted by the particular source providing SKG-IF documents for referring to such entities internally to its system. However, it is also possible that a source may not have such an internal identifier explicitly defined and need to create new SKG-IF local identifiers on-the-fly, while creating the SKG-IF document to return. 

To this end, it is important to clarify that all these URLs specified as local identifiers of SKG-IF entities (either directly or indirectly via the combitation of the SKG-IF base and the string) identify the related entity **globally**, at least in theory. In particular, if the same URL is used in two or more SKG-IF documents, it refer always to the same entity. 

Thus, in case one specifies a non-URL string for a local identifier of an entity, and such non-URL string is created on-the-fly for the reason highlighted above, it is up to the source providing the SKG-IF data to prepare a string that does not create inconsistencies with other SKG-IF data generated in the past.

Please note that having two distinct local identifiers referring to the same real world entity does not create particular issues - in particular when other external identifiers (e.g. DOI, ORCID, ROR) are specified and can be used to decupling entities. Instead, having a local identifier that refers to two distinct entities (either in the same SKG-IF document or in different SKG-IF documents) creates consistency problems and may result in erroneous interpretation of the SKG-IF data.

Thus, in case there is the need of creating such on-the-fly identifiers, the recommendation is to clearly state that by adopting the following template:

```
otf___<session identifier>___<identifier string>
```

where

* `otf` stands for *on-the-fly* to explicitly clarify the local identifiers it has been created for the purpose of creating this SKG-IF document; 
* `<session identifier>` is a string portion that enables the source to uniquely identifier the session in which such SKG-IF document has been created - e.g. it could be the current time of the software run to create the SKG expressed in milliseconds;
* `<identifier string>` is a string portion that identifies the particular entity in consideration. For instance, a possible example of such a local identifier would be

```json
    "local_identifier": "otf___1730027051396___person-1"
```

that is interpreted by the Interoperability Framework (considering having `https://w3id.org/skg-if/sandbox/oc/` as base URL) as `https://w3id.org/skg-if/sandbox/oc/otf___1730027051396___person-1`.
