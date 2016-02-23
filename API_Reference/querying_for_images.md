# Querying for images

Any hyperlink to a collection of images can accept query parameters that filter the returned images. 

* queue.images
* space.images
* batch.images
* batch.completedImages
* batch.errorImages

(TODO - links to mock API examples of these)

Once you have registered images with the DLCS you can query it for information on them. One immediate use of this is to monitor the progress of ongoing registrations. For example, if you registered a batch of 100,000 images it will take some time for the DLCS to process them, and you would like to be able to monitor progress and view any errors that were encountered. You can also query for usage statistics.

You issue a DLCS query by submitting parameters that match the metadata fields, or a serialised JSON query object. This is a pattern for the DLCS to match metadata fields on. The model is very similar to the image registration data model, except you are submitting a filter and expecting all images that match that filter to be returned.

```
curl --user name:password -X GET -d https://api.dlcs.io/customers/3/spaces/4/images?string1=bib343434
```

This returns a Hydra collection.

```
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@id": "https://api.dlcs.io/customers/3/spaces/4/images?string1=bib343434",
  "@type": "Collection",
  "totalItems": "2",
  "member":
    [
        {
            "url":"http://dlcs.io/2/3/76677bd1-705e-4599",
            "space": 3,
            "id": "76677bd1-705e-4599",
            "origin": "https://example.org/dam/images/76677bd1-705e-4599.tiff",
            "string1": "bib343434",
            "number1": 0,
            "tags" : ["cover", "interesting"]        
        },
        {
            "url":"http://dlcs.io/2/3/0bf94941-2c0f-49fd",
            "space": 3,
            "id": "0bf94941-2c0f-49fd",
            "origin": "https://example.org/dam/images/0bf94941-2c0f-49fd.tiff",
            "string1": "bib343434",
            "nu,mber": 1     
        }
    ]
}
```

