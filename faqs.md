# Pilot FAQs

## What is the DLCS?

The Wellcome Library is developing cloud-based infrastructure to provide fast, scalable and highly available services for the delivery of its digital images, and, over time, the provision of full-text search and annotation services.  These services are known as the Digital Library Cloud Services (DLCS).

## What is the DLCS Pilot service?

Although the primary use case for the DLCS is the Wellcome Library, we realised that with a relatively modest additional investment we could, potentially, offer these services to any cultural heritage organisation. In so doing, such organisations would be able to make their digital content available in rich and engaging ways, but do so without incurring the cost of developing and maintaining their own systems infrastructure1. 

To determine whether there is any interest in making use of such a shared service – and ascertain whether the services we are building are those which the community would find useful and affordable – the Wellcome Library is currently inviting institutions who wish to explore how they could make use of this service, to participate in a pilot service.  

## How do I participate in the DLCS Pilot?

To participate in the pilot service you simply need to send an email to Robert Kiley (r.kiley@wellcome.ac.uk) with the following information:

* Your name
* Email address
* Institution
* Estimate of the total number of digital images you have in your collection
* Name of technical contact
* Email address of technical contact

By return, you will be sent further details of the DLCS, including credentials to access the DLCS portal and API services.

## Can I see an example of a Wellcome Library digitised object being delivered via the DLCS?

This example http://universalviewer.io/?manifest=http://wellcomelibrary.org/iiif/b2202296x/dmanifest is being served by the DLCS.  This can be seen by looking at the manifest (http://wellcomelibrary.org/iiif/b2202296x/dmanifest ) and observing that the image end-points are referencing the DLCS.


## Are there costs involved in participating in the DLCS Pilot?

No. The Wellcome Library will not charge you for making use of the DLCS during the pilot.  

Any costs incurred by the participating institution – such as spending time determining how to make use of the DLCS API – will, of course, need to be met by that institution,

## How long will the DLCS Pilot run for?

This pilot will start on the 1st March 2016.  We do not have an end-date as yet, but anticipate in will run for between six and eight months.  All participants will be kept informed as to the progress of the pilot and in any event will be given at last 2 months’ notice.

## What do I need to be able to make use of the DLCS Pilot?

In addition to the credentials needed to access the service (discussed above) you will need:

* A collection of digital images, which do not require any user authentication to view them.  Although the DLCS will be able to support full, delegated authentication (in line with the IIIF Presentation standard) for the pilot we are asking participants to only use “open” images.
* The images to be made available via some web service – so the DLCS can ingest them into its system and return IIIF endpoints (URI’s)
* Some technical skills to interact with the DLCS API.

## How will I interact with the DLCS pilot?

The primary way participants will interact with the DLCS is via the DLCS API.  Further details of this are available at: https://dlcs.gitbooks.io/book/content/API_Reference/index.html 

Users without the ability to make use of the DLCS API can still upload images, via a CSV interface.  This is detailed at: https://dlcs.gitbooks.io/book/content/registering_images_in_the_portal.html.

## Are there any limits on how I use the DLCS Pilot?

During the pilot, participants will be asked to load no more than 10,000 images (or 20 Gb of data) to the DLCS.  Participants will also be required to accept the terms of the End User Licence Agreement.

As this is a pilot – with no Service Level Agreement and the like, participants should be wary of building any integration into live, production systems.
Is the DLCS Pilot just providing IIIF image services?
At launch (March 2016), the DLCS will only provide IIIF image services.

Over the course of the pilot we hope to extend these service to include search (if you have OCR content) and annotation services.  Updates will be provided via the Slack channel and the monthly community calls.

## How do I get support and provide feedback?

All participants will be invited to join the DLCS Slack Channel https://dlcs.slack.com/messages/general/ and this will be the primary means through which support questions can be raised and answered.  Is it also the means by which we will solicit feedback.

In addition a monthly “community call” will be held.  Details of this call – the date, time, dial-in number – will be advertised on the Slack channel.

## What services is the DLCS NOT seeking to emulate?

For the avoidance of doubt we should make clear make clear from the start that the DLCS is not seeking to be:

### A preservation system.  

Though the DLCS will hold copies of images it serves, these will be optimised for fast delivery over the web.  For example, a library may hold a large, uncompressed TIFF file and upload that to the DLCS.  On ingest though, the DLCS will transform this into a fully-optimised JPEG 2000 file and discard the original.

### A library catalogue system.  

Although the DLCS may include resource discovery metadata, derived from a library catalogue, the DLCS is not the system where you would catalogue items.

### A discovery platform
The DLCS is not the means by which readers find content.  This activity still takes place on your own web site; you simply use the DLCS to provide access to the digitised images (and in time, search and annotation services).

### Where can I find more information about IIIF?

Information about the International Image Interoperability Framework (IIIF) can be found at: http://iiif.io 

For a simple guide to both the image and presentation API’s see: https://goo.gl/Ae7iQz 
