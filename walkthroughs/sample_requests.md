# Sample Requests

This page contains a series of sample cURL requests for the most common operations.

For ease, assume the API is hosted at `api.dlcs` and we have admin credentials "admin:adminpass". Fields have been omitted from return payloads for clarity.

_Note: Each of these steps can be run independently but some refer to previous steps for clarity_

## Create New [Customer](../API_Reference/customer.md)

First create a new customer named "my-customer" with display name of "Friendly Name" by POSTing to `/customers`

```bash
$ curl -X POST https://api.dlcs/customers -v \
 -d '{"name":"my-customer","displayName":"Friendly Name"}' \
 -H "Content-Type: application/json" \
 -u admin:adminpass`
```

This will return a `vocab:Customer` back, check the `@id` property to get the numeric Id for this customer (in this example 4):

```json
{
    "@id": "https://api.dlcs/customers/4",
    "@type": "vocab:Customer",
}
```

> The "Id" and "Name" property are interchangeable in URL requests for a Customer. The following are equivalent: `https://api.dlcs/customers/4/{endpoint}` and `https://api.dlcs/customers/my-customer/{endpoint}`


## API [Key](../API_Reference/key.md) for Customer

In order to use the API we need to create a Key for our new customer. To do this POST to `/customers/{customer}/keys`.

```bash
# note empty body
$ curl -X POST https://api.dlcs/customers/4/keys -v \
 -d '' \
 -u admin:adminpass
```

This will return a `vocab:Key` result, note the `@id` and the `secret` (_`secret` must be recorded now as it cannot be fetched later_)

```json
{
    "@id": "https://api.dlcs/customers/4/keys/my-key",
    "@type": "vocab:Key",
    "secret": "my-key-secret"
}
```


## Create [PortalUser](../API_Reference/portaluser.md)

Before using the API the end user license agreement must be accepted. This can only be done via the Portal UI. 

Note that we are using the Admin credentials here. Customers can create PortalUsers once they have accepted the agreement so the first must be created by an admin.

To create a new portal user:

```bash
$ curl -X POST https://api.dlcs/customers/4/portalUsers -v \
 -d '{ "email": "test@example.com", "password": "plaintext-password" }' \
 -H "Content-Type: application/json" \
 -u admin:adminpass
```


## Create New [Space](../API_Reference/space.md)

Create a new space to store assets, this space will be named "Demo Space".

```bash
$ curl -X POST https://api.dlcs/customers/4/spaces -v \
 -d '{"name":"Demo Space"}' \
 -H "Content-Type: application/json" \
 -u my-key:my-key-secret
```

Again, the return object contains the newly created space key (1 as this is the first space):

```json
{
    "@id": "https://api.dlcs/customers/4/spaces/1",
    "@type": "vocab:Space",
}
```

## [Asset](../API_Reference/image.md) Ingest

See the [walkthroughs](registering_images_via_the_api.md) for more information on registering images via the API.

### Ingest Single Image

To immediately (synchronously) ingest an image named "my-first-image" from an HTTP location. This is the absolute minimum amount of data provided and just enough to get the image into the system, typically you would provide some metadata.

```bash
$ curl -X PUT https://api.dlcs/customers/4/spaces/1/images/my-first-image -v \
 -d '{"origin":"https://example.com/photo-123456"}' \
 -H "Content-Type: application/json" \
 -u my-key:my-key-secret
```

The returned object will contain a bare amount of information about the image. `"family: "I"` signifies that this is an Image.

```json
{
    "@id": "https://api.dlcs/customers/4/spaces/1/images/my-first-image",
    "@type": "vocab:Image",
    "origin": "https://example.com/photo-123456",
    "width": 3449,
    "height": 4368,
    "ingesting": false,
    "family": "I",
}
```

> This may take a couple of seconds to come back as the API is ingesting and transforming the image synchronously.

### [Queue](../API_Reference/queue.md) Assets for Ingest

The recommended/typical usage is to batch a number of images (e.g. 100) for ingestion. This happens asynchronously. For this example, we will ingest 1 image and 1 video file. For clarity the JSON will be sent as an external file:

```json
{
    "@context": "http://www.w3.org/ns/hydra/context.jsonld",
    "@type": "Collection",
    "member": [
        {
            "id": "batch1_image1",
            "space": 1,
            "origin":"https://example.com/photo-789",
            "family": "I",
            "mediaType" : "image/jpeg"
        },
        {
            "id": "batch_video1",
            "space": 1,
            "origin":"https://example.com/video-123",
            "family": "T",
            "mediaType" : "video/mpeg"
        }
    ]
}
```

```bash
$ curl -X PUT https://api.dlcs/customers/4/queue -v \ 
 -d '@batch.json' \
 -H "Content-Type: application/json" \
 -u my-key:my-key-secret
```

This will return details of the batch that has been created:

```json
{
    "@id": "https://api.dlcs/customers/4/queue/batches/570256",
    "@type": "vocab:Batch",
    "images": "https://api.dlcs/customers/4/queue/batches/570256/images",
    "submitted": "2020-05-14T13:01:14.436581+00:00",
    "count": 2,
    "completed": 0,
    "errors": 0,
    "finished": "0001-01-01T00:00:00",
}
```

This payload can be called until `"finished"` has a non-default value.

To view details of the images in the batch:

```bash
$ curl -X GET https://api.dlcs/customers/4/queue/batches/570256/images \
 -u my-key:my-key-secret
```

Which returns details of all of the images in the batch:
```json
{
    "@context": "http://www.w3.org/ns/hydra/context.jsonld",
    "@id": "https://api.dlcs/customers/4/queue/batches/570256/images",
    "@type": "Collection",
    "totalItems": 2,
    "pageSize": 100,
    "member": [
        {
            "@context": "https://api.dlcs/contexts/Image.jsonld",
            "@id": "https://api.dlcs/customers/4/spaces/1/images/batch1_image1",
            "@type": "vocab:Image",
            "created": "2020-05-14T13:01:14.427043+00:00",
            "origin": "https://example.com/photo-789",
            "width": 3449,
            "height": 4368,
            "duration": 0,
            "batch": 570256,
            "finished": "2020-05-14T13:01:21.325248+00:00",
            "ingesting": false,
            "family": "I",
            "mediaType": "image/jpeg"
        },{
            "@context": "https://api.dlcs/contexts/Image.jsonld",
            "@id": "https://api.dlcs/customers/4/spaces/1/images/batch_video1",
            "@type": "vocab:Image",
            "created": "2020-05-14T13:01:14.427676+00:00",
            "origin": "https://example.com/video-123",
            "width": 640,
            "height": 480,
            "duration": 14000,
            "batch": 570256,
            "finished": "2020-05-14T13:01:39.139705+00:00",
            "ingesting": false,
            "family": "T",
            "mediaType": "video/mpeg"
        }
    ]
}
```

Note the different `"family"` ((I)mage and (T)imebased), `"mediaType"` and `"duration"` fields.