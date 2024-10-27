# JSON-LD preamble

Each document compliant with the SKG-IF format must start with the following preamble:

```
{
    "@context": [ 
        "https://w3id.org/skg-if/context/skg-if.json",
        { 
            "@base": "https://w3id.org/skg-if/sandbox/<provider acronym>/",
            "": "https://w3id.org/skg-if/sandbox/<provider acronym>/"
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

# Core model entities

The SKG-IF models six core entities and their relationships. These are:
- [Research product](https://skg-if.github.io/interoperability-framework/research-product)
- [Agent](https://skg-if.github.io/interoperability-framework/agent)
- [Grant](https://skg-if.github.io/interoperability-framework/grant)
- [Venue](https://skg-if.github.io/interoperability-framework/venue)
- [Topic](https://skg-if.github.io/interoperability-framework/topic)
- [Data source](https://skg-if.github.io/interoperability-framework/data-source)
