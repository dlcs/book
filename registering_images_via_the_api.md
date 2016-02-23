# Registering images via the API

The following walkthrough shows how you can interact with the API at the command line via curl.

In these examples the customer's API key and secret is placed in the file ```dlcs-creds``` and passed to curl via the --netrc-file argument.

```$ curl --netrc-file dlcs-creds https://api-hydra.dlcs.io/customers/4```

This returns information about the customer:

```
{
  "@context": "http://api-hydra.dlcs.io/contexts/Customer.jsonld",
  "@id": "http://api-hydra.dlcs.io/customers/4",
  "@type": "vocab:Customer",
  "portalUsers": "http://api-hydra.dlcs.io/customers/4/portalUsers",
  "namedQueries": "http://api-hydra.dlcs.io/customers/4/namedQueries",
  "originStrategies": "http://api-hydra.dlcs.io/customers/4/originStrategies",
  "authServices": "http://api-hydra.dlcs.io/customers/4/authServices",
  "roles": "http://api-hydra.dlcs.io/customers/4/roles",
  "queue": "http://api-hydra.dlcs.io/customers/4/queue",
  "spaces": "http://api-hydra.dlcs.io/customers/4/spaces",
  "allImages": "http://api-hydra.dlcs.io/customers/4/allImages",
  "name": "iiifly",
  "displayName": "iiif.ly",
  "keys": [
    "xxx"
  ],
  "administrator": false,
  "created": "2016-01-29T10:20:00+00:00"
}
```

Behaving as a RESTful API client, we can then follow links:

```$ curl --netrc-file dlcs-creds https://api-hydra.dlcs.io/customers/4/spaces```

```
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@id": "http://api-hydra.dlcs.io/customers/4/spaces",
  "@type": "Collection",
  "totalItems": 9,
  "member": [
    {
      "@context": "http://api-hydra.dlcs.io/contexts/Space.jsonld",
      "@id": "http://api-hydra.dlcs.io/customers/4/spaces/1",
      "@type": "vocab:Space",
      "defaultRoles": "http://api-hydra.dlcs.io/customers/4/spaces/1/defaultRoles",
      "images": "http://api-hydra.dlcs.io/customers/4/spaces/1/images",
      "metadata": "http://api-hydra.dlcs.io/customers/4/spaces/1/metadata",
      "name": "11BF0924",
      "created": "2016-02-09T16:41:37.332282+00:00",
      "imageBucket": "",
      "defaultTags": [],
      "keep": false,
      "transform": false,
      "maxUnauthorised": 0
    },
    ...
    {
      "@context": "http://api-hydra.dlcs.io/contexts/Space.jsonld",
      "@id": "http://api-hydra.dlcs.io/customers/4/spaces/9",
      "@type": "vocab:Space",
      "defaultRoles": "http://api-hydra.dlcs.io/customers/4/spaces/9/defaultRoles",
      "images": "http://api-hydra.dlcs.io/customers/4/spaces/9/images",
      "metadata": "http://api-hydra.dlcs.io/customers/4/spaces/9/metadata",
      "name": "ecosystem-test",
      "created": "2016-02-23T11:33:46.164184+00:00",
      "imageBucket": "",
      "defaultTags": [],
      "keep": false,
      "transform": false,
      "maxUnauthorised": 0
    }
  ]
}
```

```$ curl --netrc-file dlcs-creds https://api-hydra.dlcs.io/customers/4/spaces/3```

(omitted)

```$ curl --netrc-file dlcs-creds https://api-hydra.dlcs.io/customers/4/spaces/3/images```

```
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@id": "http://api-hydra.dlcs.io/customers/4/spaces/3/images",
  "@type": "Collection",
  "totalItems": 22,
  "member": [
    {
      "@context": "http://api-hydra.dlcs.io/contexts/Image.jsonld",
      "@id": "http://api-hydra.dlcs.io/customers/4/spaces/3/images/06716cab-fcb5-4468-a27b-0b4cfa22f58e",
      "@type": "vocab:Image",
      "infoJson": "https://dlcs.io/iiif-img/4/3/06716cab-fcb5-4468-a27b-0b4cfa22f58e",
      "degradedInfoJson": "",
      "thumbnailInfoJson": "http://thumbs.dlcs.io/thumbs/4/3/06716cab-fcb5-4468-a27b-0b4cfa22f58e",
      "created": "2016-02-10T16:37:43.065907+00:00",
      "origin": "http://orig13.deviantart.net/4e91/f/2015/253/e/7/art_trade___godzilla_and_baby_godzilla_by_kingasylus91-d9925jf.png",
      "tags": [],
      "roles": [],
      "preservedUri": "",
      "string1": "52503a2d",
      "string2": "",
      "string3": "",
      "maxUnauthorised": -1,
      "number1": 0,
      "number2": 0,
      "number3": 0,
      "width": 2495,
      "height": 1662,
      "error": "",
      "batch": 4,
      "finished": "2016-02-10T16:38:06.988255+00:00",
      "ingesting": false
    },
...
    {
      "@context": "http://api-hydra.dlcs.io/contexts/Image.jsonld",
      "@id": "http://api-hydra.dlcs.io/customers/4/spaces/3/images/fae349eb-4e84-49e5-b724-3f6fbc8dd6bd",
      "@type": "vocab:Image",
      "infoJson": "https://dlcs.io/iiif-img/4/3/fae349eb-4e84-49e5-b724-3f6fbc8dd6bd",
      "degradedInfoJson": "",
      "thumbnailInfoJson": "http://thumbs.dlcs.io/thumbs/4/3/fae349eb-4e84-49e5-b724-3f6fbc8dd6bd",
      "created": "2016-02-12T12:43:27.993246+00:00",
      "origin": "http://www.desang.net/wp-content/uploads/2012/12/Mushrooms.jpg",
      "tags": [
        "mushroom"
      ],
      "roles": [],
      "preservedUri": "",
      "string1": "mystring",
      "string2": "",
      "string3": "",
      "maxUnauthorised": -1,
      "number1": 0,
      "number2": 0,
      "number3": 0,
      "width": 3008,
      "height": 2000,
      "error": "",
      "batch": 32,
      "finished": "2016-02-12T12:43:47.344131+00:00",
      "ingesting": false
    }
  ]
}
```

We can take a look at our queue:

```$ curl --netrc-file dlcs-creds https://api-hydra.dlcs.io/customers/4/queue```

```
{
  "@context": "http://api-hydra.dlcs.io/contexts/Queue.jsonld",
  "@id": "http://api-hydra.dlcs.io/customers/4/queue",
  "@type": "vocab:Queue",
  "size": 0,
  "batches": "http://api-hydra.dlcs.io/customers/4/queue/batches",
  "images": "http://api-hydra.dlcs.io/customers/4/queue/images"
}
```

And we can post new images to it for ingest, either directly in the body, or from a separate file:

```$ curl --netrc-file dlcs-creds -X POST --data @myimages.json https://api-hydra.dlcs.io/customers/4/queue```

myimages.json looks like this:

```
{
  "@type": "Collection",
  "member": [
    {
      "space" : "3",
      "origin": "http://customer.com/images/Mushrooms.jpg",
      "tags": ["mushroom"],
      "string1": "mystring"
    },
    {
      "space" : "3",
      "origin": "http://customer.com/images/chicken-w-mushrooms-1.jpg",
      "tags": ["mushroom", "tasty"],
      "string1": "mystring"
    }
  ]
}
```

and the post to the queue returns a batch resource:

```
{
  "@context": "http://api-hydra.dlcs.io/contexts/Batch.jsonld",
  "@id": "http://api-hydra.dlcs.io/customers/4/queue/batches/59",
  "@type": "vocab:Batch",
  "errorImages": "http://api-hydra.dlcs.io/customers/4/queue/batches/59/errorImages",
  "images": "http://api-hydra.dlcs.io/customers/4/queue/batches/59/images",
  "completedImages": "http://api-hydra.dlcs.io/customers/4/queue/batches/59/completedImages",
  "submitted": "2016-02-23T20:53:45.999979+00:00",
  "count": 2,
  "completed": 0,
  "errors": 0,
  "finished": "0001-01-01T00:00:00"
}
```





