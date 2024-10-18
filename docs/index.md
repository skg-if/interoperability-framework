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

This preamble is crucial to enable software system to see the JSON document as a parsable JSON-LD file. In addition, it is also crucial to specify the base URLs that will be used for local identifiers in case no URLs are specified. These must follow a specific template, i.e.

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
