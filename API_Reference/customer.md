# Customer

A customer represents you, the API user. You only have access to one customer, so it is your effective entry point for the API. 

![](customer.png)

|URI	|Method	|Accepts	|Returns	|HTTP Status Code|	
|--|--|--|--|--|
|/customers/{customer}	|GET	|	|Customer	|200, 403|	
|/customers/{customer}/portalUsers	|GET	|	|PortalUserCollection	|200|	
|/customers/{customer}/portalUsers	|POST	|PortalUser	|PortalUser	|201, 400|	
|/customers/{customer}/portalUsers/{portalUser}	|GET	|	|PortalUser	|200, 404|	
|/customers/{customer}/portalUsers/{portalUser}	|PUT	|PortalUser	|PortalUser	|200, 201, 400|	
|/customers/{customer}/portalUsers/{portalUser}	|PATCH	|PortalUser	|PortalUser	|205, 400, 404|	
|/customers/{customer}/portalUsers/{portalUser}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/namedQueries	|GET	|	|NamedQueryCollection	|200|	
|/customers/{customer}/namedQueries	|POST	|NamedQuery	|NamedQuery	|201, 400|	
|/customers/{customer}/namedQueries/{namedQuery}	|GET	|	|NamedQuery	|200, 404|	
|/customers/{customer}/namedQueries/{namedQuery}	|PUT	|NamedQuery	|NamedQuery	|200, 201, 400|	
|/customers/{customer}/namedQueries/{namedQuery}	|PATCH	|NamedQuery	|NamedQuery	|205, 400, 404|	
|/customers/{customer}/namedQueries/{namedQuery}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/originStrategies	|GET	|	|OriginStrategyCollection	|200|	
|/customers/{customer}/originStrategies	|POST	|OriginStrategy	|OriginStrategy	|201, 400|	
|/customers/{customer}/originStrategies/{originStrategy}	|GET	|	|OriginStrategy	|200, 404|	
|/customers/{customer}/originStrategies/{originStrategy}	|PUT	|OriginStrategy	|OriginStrategy	|200, 201, 400|	
|/customers/{customer}/originStrategies/{originStrategy}	|PATCH	|OriginStrategy	|OriginStrategy	|205, 400, 404|	
|/customers/{customer}/originStrategies/{originStrategy}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/authServices	|GET	|	|AuthServiceCollection	|200|	
|/customers/{customer}/authServices	|POST	|AuthService	|	|201, 400|	
|/customers/{customer}/authServices/{authService}	|GET	|	|AuthService	|200, 404|	
|/customers/{customer}/authServices/{authService}	|PUT	|AuthService	|AuthService	|200, 201, 400|	
|/customers/{customer}/authServices/{authService}	|PATCH	|AuthService	|AuthService	|205, 400, 404|	
|/customers/{customer}/authServices/{authService}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/roles	|GET	|	|RoleCollection	|200|	
|/customers/{customer}/roles	|POST	|Role	|Role	|201, 400|	
|/customers/{customer}/roles/{role}	|GET	|	|Role	|200, 404|	
|/customers/{customer}/roles/{role}	|PUT	|Role	|Role	|200, 201, 400|	
|/customers/{customer}/roles/{role}	|PATCH	|Role	|Role	|205, 400, 404|	
|/customers/{customer}/roles/{role}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/queue	|GET	|	|Queue	|200|	
|/customers/{customer}/queue	|POST	|ImageCollection	|Batch	|201, 400|	
|/customers/{customer}/queue/batches	|GET	|	|BatchCollection	|200|	
|/customers/{customer}/queue/batches/{batch}	|GET	|	|Batch	|200|	
|/customers/{customer}/queue/batches/{batch}/images	|GET	|(query)	|ImageCollection	|200, 400, 404|	
|/customers/{customer}/queue/batches/{batch}/errorImages	|GET	|(query)	|ImageCollection	|200, 400, 404|	
|/customers/{customer}/queue/batches/{batch}/completedImages	|GET	|(query)	|ImageCollection	|200, 400, 404|	
|/customers/{customer}/queue/images	|GET	|(query)	|ImageCollection	|200, 400|	
|/customers/{customer}/spaces	|GET	|	|SpaceCollection	|200|	
|/customers/{customer}/spaces	|POST	|Space	|Space	|201, 400|	
|/customers/{customer}/spaces/{space}	|GET	|	|Space	|200, 404|	
|/customers/{customer}/spaces/{space}	|PUT	|Space	|Space	|200, 201, 400|	
|/customers/{customer}/spaces/{space}	|PATCH	|Space	|Space	|205, 400, 404|	
|/customers/{customer}/spaces/{space}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/spaces/{space}/defaultRoles	|GET	|	|RoleCollection	|200|	
|/customers/{customer}/spaces/{space}/defaultRoles	|POST	|RoleCollection?	|RoleCollection	|200, 400|	
|/customers/{customer}/spaces/{space}/images	|GET	|(query)	|ImageCollection	|200, 400|	
|/customers/{customer}/spaces/{space}/images/{image}	|GET	|	|Image	|200, 404|	
|/customers/{customer}/spaces/{space}/images/{image}	|PUT	|Image	|Image	|200, 201, 400|	
|/customers/{customer}/spaces/{space}/images/{image}	|PATCH	|Image	|Image	|205, 400, 404|	
|/customers/{customer}/spaces/{space}/images/{image}	|DELETE	|	|	|205, 404|	
|/customers/{customer}/spaces/{space}/metadata/distinct?field={field}	|GET	|	|string[] or long[]	|200, 400, 404|	
|/customers/{customer}/allImages	|GET	|(query)	|ImageCollection	|200, 400|	
