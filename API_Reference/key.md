# Key

![](key.png)

Credentials for accessing the API. The Key object will only have the accompanying secret field returned once, when a new key is created. Thereafter only the key is available from the API.

To obtain a key and a secret, make an empty POST to this collection with administrator privileges and the returned Key object will include the generated secret.


```
/customers/{customer}/keys
/customers/{customer}/keys/{keyId}
```


## Supported operations


| Method | Label                                                                               | Expects     | Returns   | Statuses                     |
|--------|-------------------------------------------------------------------------------------|-------------|-----------|------------------------------|
| GET    | Returns keys allocated to this customer resource                                    |             | vocab:Key |                              |
| POST   | Submit an empty POST and the DLCS will generate a key and secret. Requires elevated | owl:Nothing | vocab:Key | 201 Key created and returned |

<!-- 
empty POST is returning 500 
GET for specific key /customers/{customer}/keys/{keyId} 500
-->


## Supported properties


### key

API Key


| domain    | range      | readonly | writeonly |
|-----------|------------|----------|-----------|
| vocab:Key | xsd:string | False    | False     |


### secret

API Secret (available at creation time only, or via empty POST by admin)


| domain    | range      | readonly | writeonly |
|-----------|------------|----------|-----------|
| vocab:Key | xsd:string | False    | False     |


