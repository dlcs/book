# Questions

### Does my "origin" image need to be available forever?

No. The DLCS needs to see it at registration time, but from then on provides the IIIF Image Service without further reference to it. However, we might want to see it again in the future if we want to change the way we provide the image service.

Internally, the DLCS makes a JPEG 2000 derivative of your source image at registration time. This image is lossy (although of high quality), and optimised for tile delivery in IIIF compatible viewers. More efficient image formats may emerge in future, and we might want to take advantage of these and require the origin image again.

### The DLCS does not preserve my original image, but I'd like it to

Preservation of origin (source) images is not a current feature of the DLCS - but if users want this, we could implement it - e.g., by saving a copy of the registered origin image to low cost archival storage. We think the DLCS would work alongside your own preservation system, but if you don't have one, the DLCS could act as a very simple storage solution.