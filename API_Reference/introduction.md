# API and Resource reference

This section goes into more detail on the Hydra API and the resources it operates on.

The DLCS API is at https://api.dlcs.io/ and requires credentials using basic auth over https. There is also an open API at http://dlcs.azurewebsites.net/ that requires no credentials and is backed by mock data. This is a good way to explore the resource model used by the DLCS and relate the descriptions int his documentation to API responses.

The API uses JSON-LD and the [Hydra vocabulary](http://www.hydra-cg.com/). Hydra+JSON-LD turns JSON over HTTP into a self-describing HyperMedia API. Each resource type has an associated JSON-LD context, and the full description of the types and their supported properties and operations is discoverable by clients.

The root of the API is of the special type "EntryPoint":

```javascript
{
    "@context": "http://dlcs.azurewebsites.net/contexts/DLCS.Client.Model.EntryPoint.jsonld",
    "@id": "http://dlcs.azurewebsites.net",
    "@type": "EntryPoint",
    "customers": "http://dlcs.azurewebsites.net/customers"
}
```

Each type-specific context defines the vocabulary for that type, for example:

```javascript
{
    "@context": {
        "hydra": "http://www.w3.org/ns/hydra/core#",
        "vocab": "http://dlcs.azurewebsites.net/vocab#",
        "EntryPoint": "vocab:EntryPoint",
        "customers": {
            "@id": "vocab:EntryPoint/customers",
            "@type": "@id"
        }
    }
}
```

The full description of the types and their supported properties and operations is available at the "vocab" URI:

```
http://dlcs.azurewebsites.net/vocab
```

A diagram showing the full model is [available here](resource_model.md); the rest of this section looks at each resource type in detail.



