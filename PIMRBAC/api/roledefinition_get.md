# Get roleDefinition

Retrieve the properties and relationships of roledefinition object.

### HTTP request

```http
GET /scenarios('<id>')/roleDefinitions('<id>')
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
If successful, this method returns a `200 OK` response code and [roleDefinition](../resources/roledefinition.md) object in the response body.
### Example : Get details of role Definition "Azure Service Deploy Release Management Contributor" in subscription "Wingtip Toys - Prod"
##### Request
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleDefinitions('85dfe48a-55d3-49fc-8f36-ee14b7f6f720_21d96096-b162-414a-8302-d8354f9d91b2')
```
##### Response
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 174

{
  "@odata.context":"https://api.azrbac.mspim.azure.com/api/v1/$metadata#roleDefinitions/$entity",
  "id":"85dfe48a-55d3-49fc-8f36-ee14b7f6f720_21d96096-b162-414a-8302-d8354f9d91b2",
  "resourceId":"85dfe48a-55d3-49fc-8f36-ee14b7f6f720",
  "originId":null,
  "templateId":"21d96096-b162-414a-8302-d8354f9d91b2",
  "displayName":"Azure Service Deploy Release Management Contributor",
  "subjectCount":0,
  "activationRequiredCount":0,
  "assignedCount":0
}
```