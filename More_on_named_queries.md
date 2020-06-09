# More on Named Queries

An example of Named Queries is their user by the iiif.ly application to generate a manifest from a set of images.   

When it registers the end user’s images, iiif.ly assigns metadata to group images together, and to preserve the order.

The iiif.ly customer (API user) has configured a Named Query to return a IIIF manifest.

Template for consuming NamedQuery: `https://dlcs.io/iiif-resource/{customer}/{query-name}/{space-name}/{string1}`

NamedQuery as saved in database: `manifest=s1&sequence=n1&canvas=n2&spacename=p1&s1=p2`

The **Named Query** – in response to requests that match this template,

1. Select all the images in {space-name} with a string1 value of {string1} and order them by {number1}
2. Project the images into a manifest with one sequence where each canvas in the sequence corresponds to one image

## Explanation

The following keywords can be used when creating a named query:

| Property Name | Description                                                                                  | Example         |
|---------------|----------------------------------------------------------------------------------------------|-----------------|
| space         | Matches a space by Id (by default named queries will search all images for customer)         | `&space=p1`     |
| spacename     | Matches a space by name (by default named queries will search all images for customer)       | `&spacename=p1` |
| manifest      | How to group images                                                                          | `&manifest=s1`  |
| sequence      | How to filter images in manifest                                                             | `&sequence=n1`  |
| canvas        | Ordering to apply to each image on canvas                                                    | `&canvas=n2`    |
| s1            | String1 metadata field                                                                       | `&manifest=s1`  |
| s2            | String2 metadata field                                                                       | `&s1=p1`        |
| s3            | String3 metadata field                                                                       | `&manifest=s3`  |
| n1            | Number 1 metadata field                                                                      | `&sequence=n1`  |
| n2            | Number 2 metadata field                                                                      | `&canvas=n2`    |
| n3            | Number 3 metadata field                                                                      | `&n1=p2`        |
| p*            | Identifies url parameters.Anything after `iiif-resource/{customer}/{query-name}` (`/1/2/3`) | `&n1=p2`        |
| #*            | When used in template adds the value to end of URL, effectively hardcoding a parameter       | `&manifest=s1`  |

## Example URLs: 

[https://dlcs.io/resource/4/iiifly/28EC11C6/a5425f9b](https://dlcs.io/resource/4/iiifly/28EC11C6/a5425f9b)

[https://universalviewer.io/?manifest=https://dlcs.io/resource/4/iiifly/28EC11C6/a5425f9b](https://universalviewer.io/?manifest=https://dlcs.io/resource/4/iiifly/28EC11C6/a5425f9b)