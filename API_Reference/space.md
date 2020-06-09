# Space

![](space.png)

Spaces allow you to partition images into groups. You can use them to organise your images logically, like folders. You can also define different default settings to apply to images registered in a space. For example, default access control behaviour for all images in a space, or default tags. These can be overridden for individual images. There is no limit to the number of images you can register in a space.


`/customers/{customer}/spaces/{spaceId}`

## Example

[https://dlcs.azurewebsites.net/customers/4/spaces/11](https://dlcs.azurewebsites.net/customers/4/spaces/11)

## Supported operations


| Method | Label                                   | Expects     | Returns     | Statuses                                                       |
|--------|-----------------------------------------|-------------|-------------|----------------------------------------------------------------|
| GET    | Retrieve a Space                        |             | vocab:Space | 200 OK, 404 Not found                                          |
| PUT    | create or replace a Space               | vocab:Space | vocab:Space | 200 OK, 201 Created Space, 404 Not found                       |
| PATCH  | Update the supplied fields of the Space | vocab:Space | vocab:Space | 205 Accepted Space, reset view, 400 Bad request, 404 Not found |
| DELETE | Delete the Space                        |             | owl:Nothing | 205 Accepted Space, reset view, 404 Not found                  |




## Supported properties


### name

Space name


| domain      | range      | readonly | writeonly |
|-------------|------------|----------|-----------|
| vocab:Space | xsd:string | False    | False     |


### created

Date the space was created


| domain      | range        | readonly | writeonly |
|-------------|--------------|----------|-----------|
| vocab:Space | xsd:dateTime | True     | False     |


### defaultTags

Default tags to apply to images created in this space


| domain      | range      | readonly | writeonly |
|-------------|------------|----------|-----------|
| vocab:Space | xsd:string | False    | False     |


### defaultRoles (🔗)

Default roles that will be applied to images in this space


| domain      | range            | readonly | writeonly |
|-------------|------------------|----------|-----------|
| vocab:Space | hydra:Collection | False    | False     |


`/customers/{customer}/spaces/{spaceId}/defaultRoles`


| Method | Label              | Expects    | Returns          | Statuses                           |
|--------|--------------------|------------|------------------|------------------------------------|
| GET    | Retrieves all Role |            | hydra:Collection | 200 OK                             |
| POST   | Creates a new Role | vocab:Role | vocab:Role       | 201 Role created., 400 Bad Request |


### images (🔗)

All the images in the space


| domain      | range            | readonly | writeonly |
|-------------|------------------|----------|-----------|
| vocab:Space | hydra:Collection | True     | False     |


`/customers/{customer}/spaces/{spaceId}/images`


| Method | Label               | Expects     | Returns          | Statuses                            |
|--------|---------------------|-------------|------------------|-------------------------------------|
| GET    | Retrieves all Image |             | hydra:Collection | 200 OK                              |
| POST   | Creates a new Image | vocab:Image | vocab:Image      | 201 Image created., 400 Bad Request |


### metadata (🔗)

Metadata options for the space


| domain      | range          | readonly | writeonly |
|-------------|----------------|----------|-----------|
| vocab:Space | vocab:Metadata | True     | False     |


`/customers/{customer}/spaces/{spaceId}/metadata`


| Method | Label                 | Expects | Returns        | Statuses |
|--------|-----------------------|---------|----------------|----------|
| GET    | Retrieve the metadata |         | vocab:Metadata | 200 OK   |


### storage (🔗)

Storage policy for the space


| domain      | range                 | readonly | writeonly |
|-------------|-----------------------|----------|-----------|
| vocab:Space | vocab:CustomerStorage | True     | False     |


`/customers/{customer}/spaces/{spaceId}/storage`

