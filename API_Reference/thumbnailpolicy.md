
# ThumbnailPolicy
![# ThumbnailPolicy](thumbnailpolicy.png)

To optimise delivery of thumbnails, these are pre-generated on image registration. ThumbnailPolicy details the settings used to create the thumbnails.


`/thumbnailPolicies/{thumbnailPolicy}`

## Example

[https://dlcs.azurewebsites.net/thumbnailPolicies/standard](https://dlcs.azurewebsites.net/thumbnailPolicies/standard)

## Supported operations


| Method | Label                       | Expects | Returns               | Statuses              |
|--------|-----------------------------|---------|-----------------------|-----------------------|
| GET    | Retrieve a Thumbnail policy |         | vocab:ThumbnailPolicy | 200 OK, 404 Not found |


## Supported properties


### name

The human readable name of the image policy


| domain                | range      | readonly | writeonly |
|-----------------------|------------|----------|-----------|
| vocab:ThumbnailPolicy | xsd:string | False    | False     |


### sizes

The bounding box size of the thumbnails to create. For each of these sizes, a thumbnail will be created. Sizes must be arranged Largest -> Smallest. The longest edge of each thumbnail matches this size.


| domain                | range                  | readonly | writeonly |
|-----------------------|------------------------|----------|-----------|
| vocab:ThumbnailPolicy | xsd:nonNegativeInteger | False    | False     |


