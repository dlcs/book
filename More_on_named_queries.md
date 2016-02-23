An example of Named Queries is their user by the iiif.ly application to generate a manifest from a set of images.

When it registers the end user’s images, iiif.ly assigns metadata to group images together, and to preserve the order.

The iiif.ly customer (API user) has configured a Named Query to return a IIIF manifest.

Template: https://dlcs.io/resource/{customer}/{query-name}/{space-name}/{string1}

The **Named Query** – in response to requests that match this template,
1. Select all the images in {space-name} with a string1 value of {string1} and order them by {number1}
2. Project the images into a manifest with one sequence where each canvas in the sequence corresponds to one image

Example: 

https://dlcs.io/resource/4/iiifly/28EC11C6/a5425f9b

http://universalviewer.io/?manifest=https://dlcs.io/resource/4/iiifly/28EC11C6/a5425f9b 