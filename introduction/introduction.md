# Digital Library Cloud Services (DLCS)

*A platform for interoperable image delivery, annotation, and search.*

## Why does it exist?

In the past, digitisation efforts were hampered by lack of standards. Content digitised at great expense stagnated in non interoperable silos behind ageing user interfaces. The [International Image Interoperability Framework](http://iiif.io) and the [W3C Web Annotation Data Model](https://www.w3.org/TR/annotation-model/) are emerging open standards that address this problem. The DLCS is a managed implementation of these standards. It starts with the equivalent of "elastic image server" and builds from there. 

## Who can use it?

Anyone from an individual to a large institution. The DLCS will enable smaller collections and libraries without significant infrastructure resources to undertake projects that would otherwise be impractical.

## What does it do?

DLCS provides tools and application programming interfaces (APIs) to manage services for image resources. When you register an image with the DLCS, you make it available as a [IIIF](http://iiif.io) Image API endpoint. This means it can be displayed in any compatible web-based client. You can register just a handful of images, or tens of millions. You can use DLCS APIs to construct IIIF Presentation API resources from your images for complex objects such as digitised books.  

If you have access control requirements the DLCS can enforce your policies to protect your images.

The DLCS will offer read and write services for annotations on your images and other IIIF resources, using Open Annotation / W3C Annotation Data Model. You can integrate with existing annotation tools and services, or use the DLCS to build new applications for discovery, crowdsourcing, curation and other purposes.

The DLCS will be able to perform optical character recognition (OCR) on your images. The OCR results are available in a variety of standard formats including METS-ALTO and transcription annotations.

The DLCS provides high performance search within your IIIF resources and across your entire collection.

## What doesn't it do?

The DLCS is not intended to be a preservation system, digital asset management system, collection management or cataloguing system. It does not provide any user interface for public discovery of your resources. It is designed for integration with all these types of system and more, through its APIs and services.



