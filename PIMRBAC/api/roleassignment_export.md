# Export roleAssignments

Download a list of roleAssignment objects and save as a `.csv` file.
### Prerequisites
The following **scopes** are required to execute this API: 
### HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /scenarios('<id>')/roleAssignments/export
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
If successful, this method returns a `200 OK` response code and  content of type `application/octet-stream`.
### Example
##### Request
Here is an example of the request, which queries all role assignments for a given resource and a target user subject.
<!-- {
  "blockType": "request",
  "name": "get_roleassignments"
}-->
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignments/export?$expand=subject,roleDefinition($expand=resource)&$filter=(roleDefinition/resource/id+eq+'85dfe48a-55d3-49fc-8f36-ee14b7f6f720')+and+(roleDefinition/id+eq+'85dfe48a-55d3-49fc-8f36-ee14b7f6f720_a48d7796-14b4-4889-afef-fbb65a93e5a2')
```
##### Response
Here is an example of the response. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.roleAssignment",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-Type:application/octet-stream
Content-Length:126

77u/77u/QXNzaWdubWVudCBMZXZlbCxVc2VyIEdyb3VwIE5hbWUsUm9sZSBOYW1lLEVtYWlsLEFzc2lnbm1lbnQgVHlwZSxBc3NpZ25tZW43IFN0YXJ0IFRpbWUgKFVUQyksQXNzaWdubWVudCBFbmQgVGltZdAoVVRDKQ0K

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List roleAssignments",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->