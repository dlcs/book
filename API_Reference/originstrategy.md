# OriginStrategy

As a customer you can provide information to the DLCS to allow it to fetch your images from their origin endpoints.

Every customer has a default origin strategy, which is for the DLCS to attempt to fetch the image from its origin URL without presenting credentials. This is fine for images that are publicly available, but is unlikely to be appropriate for images you are exposing from your asset management system. You might have a service that is available only to the DLCS, or an FTP site.

| Field |  | Example |
| -- | -- | -- |
| Regex | If this matches the origin URL, this strategy will be used | https://wellcomelibrary.org/service/dlcsorigins/(.*) |
| Protocol | How the DLCS should fetch the images | https+basic |
| Credentials | The credentials to use. These are not exposed by the DLCS API; the value of this property is the path to an object in S3 storage. Customers can use the portal to set these. | | |

Supported protocols:

* http (no credentials expected)
* https+basic (credentials in S3)
* ftp (credentials in S3)
* ftps (credentials in S3)
* s3 (grant permission)
