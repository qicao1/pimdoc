# roleAssignmentRequest: UpdateAdminDecision

Administrators approve or deny a request for extending expiring roles.

### Prerequisites
The following **scopes** are required to execute this API: 
### HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /scenarios('<id>')/roleAssignmentRequests('<id>')/updateAdmindecision
```

This method can only be applied to requests that are in status of `PendingAdminDecision`.
### Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {code}|

<!--| Workbook-Session-Id  | Workbook session Id that determines if changes are persisted or not. Optional.|-->

### Request body
In the request body, supply the values for:
* Provide `Guid.Empty` for request `id`, the value will be automatically updated when the request is created successfully;
* Provide `id`s of `roleDefinition`, `resource`, and `subject`, then an only role assignment can be identified;
* Provide assignment settings such as `assignmentType`,`schedule`, `requestType` and `reason`.

| Property	   | Type	 |  Description|
|:---------------|:--------|:----------|
|id|String|The id of the role assignment request. Use `Guid.Empty` when request and the value will be automatically updated when the request is created successfully;|
|assignmentType|String|The role assignment type. The value can be ``Eligible`` and ``Member``.|
|requestType|String|The original type of the role assignment request. The value should be `UserExtend`.|
|reason|String|The reason user provided for the role assignment request, as well as the administrator gives for his decision.|
|status|String|The status of the role assignment request. The value should be updated as `AdminApproved` or `AdminDenied`.|
|evaluateOnly|Boolean|Indicates if the API call is for evaluation purpose only.|
|schedule|[schedule](schedule.md)| The schedule of the role assignment request. For status of `AdminApproved`, it is required.|
### Response
If successful, this method returns `200, OK` response code. It does not return anything in the response body.

### Example
Here is an example of how to call this API.
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "roleassignmentrequest_cancel"
}-->
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests('bc6f10e6-6dd9-4393-853e-09e13c036b17_7fd64851-3279-459b-b614-e2b2ba760f5b_7c53453e-d5a4-41e0-8eb1-32d5ec8bfdee')/updateAdminDecision
```
##### Request body
```xml
{
  "id":"00000000-0000-0000-0000-000000000000",
  "roleDefinition":{"id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fbdf93bf-df7d-467e-a4d2-9458aa1360c8","resource":{"id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"}},"subject":{"id":"c178dfee-7236-44b5-a363-e15fc63d91f0"},
  "assignmentType":"Eligible",
  "requestType":"UserExtend",
  "reason":"try extend",
  "schedule":{
    "type":"Once",
    "startDateTime":"2018-02-20T07:31:13.451Z",
    "stopDateTime":"2018-05-21T07:31:13.451Z",
    "isPermanent":false
    },
  "evaluateOnly":false
}
```

##### Response
Here is an example of the response. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.None"
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "roleAssignmentRequest: cancel",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->