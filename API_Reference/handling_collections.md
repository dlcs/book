# Handling Collections

Many of the DLCS resource properties are links that return a *collection* of resources. For example, the images in a space:

```
/customer/34/spaces/12/images
```

This collection resource is defined thus:

### images (🔗)



|domain|range|readonly|writeonly|
|--|--|--|--|
|vocab:Space|hydra:Collection|True|False|


|Method|Label|Expects|Returns|Status|
|--|--|--|--|--|
|GET|Retrieves all Image| |hydra:Collection|200 OK |
|POST|Creates a new Image|vocab:Image|vocab:Image|201 Image created, 400 Bad Request|

The resource returned from this URL is a Hydra collection:

http://www.hydra-cg.com/spec/latest/core/#collections

In some cases, you as the API consumer will supply a collection - you POST a collection of images to your customer queue, e.g., at /customers/34/queue. Here, you would construct a Hydra Collections as the JSON payload of your POST.

Clients of the DLCS API should expect to deal with paged collections in any scenario that returns a collection.

Conversely, the DLCS will **not** accept a paged collection as input (e.g., as a job sent to the queue), because it might not be able to follow the links to subsequent pages. This is also an encouragement to keep batch sizes small (e.g., 100).

### Are the objects that are returned in a collection fully populated?

It depends. We hope the answer to this is "they are when you need them to be" - i.e., when you expect to be able to work with the fields of a resource without having to make further HTTP requests, one per member of the collection. Sometimes the returned collection members will be lightweight, e.g., 

```

   "member":[
      {
         "@id":"https://api.dlcs.io/customers/1",
         "@type":"Customer"
      },
      {
         "@id":"https://api.dlcs.io/customers/2",
         "@type":"Customer"
      },
      {
         "@id":"https://api.dlcs.io/customers/3",
         "@type":"Customer"
      },
      {
         "@id":"https://api.dlcs.io/customers/4",
         "@type":"Customer"
      }
   ]

```

Here you are provided with just the link and the fact that the resource at the other end of the link is a Customer.

### RDF note

> Although in the JSON-LD serialisation, the Hydra Collection's "member" property has an inherent ordering, in the underlying RDF model there is no such ordering. This is because "member" is not defined as a @list in JSON-LD terms [1]. This is an open issue with our use of the Hydra model.


[1] https://www.w3.org/TR/json-ld/#sets-and-lists