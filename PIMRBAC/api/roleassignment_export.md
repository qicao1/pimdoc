# Export roleAssignments

Download a list of roleAssignment objects and save as a `.csv` file.

### HTTP request

```http
GET /scenarios('<id>')/roleAssignments/export
```
### Optional query parameters
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

### Request headers
| Name      |Description|
|:----------|:----------|
| Authorization  | Bearer {code}|

### Request body
Do not supply a request body for this method.
### Response
If successful, this method returns a `200 OK` response code and  content of type `application/octet-stream`.
### Example : save all role assignments as `.csv` file for role Website Contributor in subscription "Wingtip Toys - Prod" 
##### Request

```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignments/export?$expand=subject,roleDefinition($expand=resource)&$filter=(roleDefinition/resource/id+eq+'85dfe48a-55d3-49fc-8f36-ee14b7f6f720')+and+(roleDefinition/id+eq+'85dfe48a-55d3-49fc-8f36-ee14b7f6f720_a48d7796-14b4-4889-afef-fbb65a93e5a2')
```
##### Response
Here is an example of the response. 

```http
HTTP/1.1 200 OK
Content-Type:application/octet-stream
Content-Length:126

77u/77u/QXNzaWdubWVudCBMZXZlbCxVc2VyIEdyb3VwIE5hbWUsUm9sZSBOYW1lLEVtYWlsLEFzc2lnbm1lbnQgVHlwZSxBc3NpZ25tZW43IFN0YXJ0IFRpbWUgKFVUQyksQXNzaWdubWVudCBFbmQgVGltZdAoVVRDKQ0K

```
