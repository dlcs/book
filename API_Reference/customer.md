# Customer

A customer represents you, the API user. You only have access to one customer, so it is your effective entry point for the API. 

![](customer.png)

## Example

```javascript
{
  "@context": "http://dlcs.azurewebsites.net/contexts/DLCS.Client.Model.Customer.jsonld",
  "@id": "http://dlcs.azurewebsites.net/customers/4",
  "@type": "Customer",
  "name": "iiifly",
  "displayName": "IIIF.ly",
  "portalUsers": "http://dlcs.azurewebsites.net/customers/4/portalUsers",
  "namedQueries": "http://dlcs.azurewebsites.net/customers/4/namedQueries",
  "originStrategies": "http://dlcs.azurewebsites.net/customers/4/originStrategies",
  "authServices": "http://dlcs.azurewebsites.net/customers/4/authServices",
  "roles": "http://dlcs.azurewebsites.net/customers/4/roles",
  "queue": "http://dlcs.azurewebsites.net/customers/4/queue",
  "spaces": "http://dlcs.azurewebsites.net/customers/4/spaces"
}
```

## Links

|URI	|Method	|Accepts	|Returns	|Statuses|	
|--|--|--|--|--|
|/customers/{customer}	|GET	|	|Customer	|200, 403|	
|/customers/{customer}/portalUsers	|GET	|	|PortalUserCollection	|200|	
|/customers/{customer}/portalUsers	|POST	|PortalUser	|PortalUser	|201, 400|	
|/customers/{customer}/namedQueries	|GET	|	|NamedQueryCollection	|200|	
|/customers/{customer}/namedQueries	|POST	|NamedQuery	|NamedQuery	|201, 400|	
|/customers/{customer}/originStrategies	|GET	|	|OriginStrategyCollection	|200|	
|/customers/{customer}/originStrategies	|POST	|OriginStrategy	|OriginStrategy	|201, 400|	
|/customers/{customer}/authServices	|GET	|	|AuthServiceCollection	|200|	
|/customers/{customer}/authServices	|POST	|AuthService	|	|201, 400|	
|/customers/{customer}/roles	|GET	|	|RoleCollection	|200|	
|/customers/{customer}/roles	|POST	|Role	|Role	|201, 400|	
|/customers/{customer}/queue	|GET	|	|Queue	|200|	
|/customers/{customer}/queue	|POST	|ImageCollection	|Batch	|201, 400|	
|/customers/{customer}/spaces	|GET	|	|SpaceCollection	|200|	
|/customers/{customer}/spaces	|POST	|Space	|Space	|201, 400|	
|/customers/{customer}/allImages	|GET	|(query)	|ImageCollection	|200, 400|	

