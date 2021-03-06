# Get roleDefinition

Retrieve the properties and relationships of roledefinition object.
### Prerequisites
The following **scopes** are required to execute this API: 
### HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /scenarios('<id>')/roleDefinitions('<id>')
```
### Optional query parameters
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

### Request headers
| Name      |Description|
|:----------|:----------|
| Authorization  | Bearer {code}|

<!--| Workbook-Session-Id  | Workbook session Id that determines if changes are persisted or not. Optional.|-->

### Request body
Do not supply a request body for this method.
### Response
If successful, this method returns a `200 OK` response code and [roleDefinition](../resources/roledefinition.md) object in the response body.
### Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "get_roledefinition"
}-->
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleDefinitions('85dfe48a-55d3-49fc-8f36-ee14b7f6f720_21d96096-b162-414a-8302-d8354f9d91b2')
```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.roleDefinition"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 174

{
  "@odata.context":"https://api.azrbac.mspim.azure.com/api/v1/$metadata#roleDefinitions/$entity",
  "id":"85dfe48a-55d3-49fc-8f36-ee14b7f6f720_21d96096-b162-414a-8302-d8354f9d91b2",
  "templateId":"21d96096-b162-414a-8302-d8354f9d91b2",
  "displayName":"Azure Service Deploy Release Management Contributor",
  "subjectCount":0,
  "activationRequiredCount":0,
  "assignedCount":0
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get roleDefinition",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->