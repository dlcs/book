# ImageOptimisationPolicy

![](imageOptimisationpolicy.png)

An internal record of how the DLCS optimised your image for tile delivery. Provides A URI to identify which policy was used at registration time for each of your images. This will be needed if you ever want to re-register from origin (e.g., go for a higher or lower quality, etc).


```
/imageOptimisationPolicies
/imageOptimisationPolicies/{imageOptimisationPolicy}
```

## Example

[https://dlcs.azurewebsites.net/imageOptimisationPolicies/fast_lossy](https://dlcs.azurewebsites.net/imageOptimisationPolicies/fast_lossy)

## Supported operations


| Method | Label                                | Expects | Returns                       | Statuses              |
|--------|--------------------------------------|---------|-------------------------------|-----------------------|
| GET    | Retrieve a Image optimisation policy |         | vocab:ImageOptimisationPolicy | 200 OK, 404 Not found |


## Supported properties


### name

The human readable name of the image policy


| domain                        | range      | readonly | writeonly |
|-------------------------------|------------|----------|-----------|
| vocab:ImageOptimisationPolicy | xsd:string | False    | False     |


### technicalDetails

Details of the encoding and tools used. These details are passed to downstream handlers.


| domain                        | range      | readonly | writeonly |
|-------------------------------|------------|----------|-----------|
| vocab:ImageOptimisationPolicy | xsd:string | False    | False     |

